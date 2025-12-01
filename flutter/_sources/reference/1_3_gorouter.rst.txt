GoRouter
==========

All named parameters
----------------------

Here is the **complete and numbered list of named parameters of GoRouter in Flutter (go_router package)** as of current stable versions. These are only the parameters that belong directly to the GoRouter constructor:

**GoRouter(**

    1.	**routes: (required)**
	•	List of all app routes (GoRoute, ShellRoute, etc.)

    2.	**extraCodec:**
	•	Controls how extra data is encoded/decoded for state restoration

    3.	**initialLocation:**
	•	The starting path of your app (e.g. /, /login)

    4.	**observers:**
	•	List of NavigatorObserver for navigation events

    5.	**debugLogDiagnostics:**
	•	Prints route matching and navigation logs for debugging

    6.	**redirect:**
	•	Global redirect logic for auth, onboarding, etc.

    7.	**redirectLimit:**
	•	Prevents infinite redirect loops (default: 5)

    8.	**navigatorKey:**
	•	Controls main Navigator’s state

    9.	**restorationScopeId:**
	•	Used for Android/iOS state restoration

    10.	**routerNeglect:**
	•	Prevents route changes from updating the URL

    11.	**onException:**
	•	Catches and handles routing exceptions

**)**

✅1.routes:
-------------

Here is a **very simple and clean Flutter example** that shows how to use the **routes: parameter in GoRouter** together with **MaterialApp.router().**

This example has **two pages:**

	•	Home page (/)

	•	About page (/about)

And a button to move between them.

**✅ pubspec.yaml (required package)**

Make sure you add go_router first:

.. code-block:: dart 

    dependencies:
        flutter:
            sdk: flutter
        go_router: ^13.2.0

Then run:

.. code-block:: dart 

    flutter pub get

**✅ main.dart (Complete working example)**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(MyApp());
    }

    // ✅ GoRouter with routes: parameter
    final GoRouter _router = GoRouter(
        routes: [

            // Home Page
            GoRoute(
            path: '/',
            builder: (context, state) => const HomePage(),
            ),

            // About Page
            GoRoute(
            path: '/about',
            builder: (context, state) => const AboutPage(),
            ),
        ],
    );

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                title: 'GoRouter Routes Example',

                // ✅ Connect GoRouter here
                routerConfig: _router,
            );
        }
    }

    /* -------------------- HOME PAGE -------------------- */
    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            // ✅ Go to About Page
                            context.go('/about');
                        },
                        child: const Text('Go to About Page'),
                    ),
                ),
            );
        }
    }

    /* -------------------- ABOUT PAGE -------------------- */
    class AboutPage extends StatelessWidget {
        const AboutPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('About Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            // ✅ Go back to Home
                            context.go('/');
                        },
                        child: const Text('Back to Home'),
                    ),
                ),
            );
        }
    }

**🔹 What this example shows**

+-------------------------+---------------------------------------+
| Item                    | Meaning                               |
+=========================+=======================================+
| routes:                 | Where we define app pages in GoRouter |
+-------------------------+---------------------------------------+
| MaterialApp.router()    | Required to use GoRouter              |
+-------------------------+---------------------------------------+
| context.go('/about')    | Navigates to About page               |
+-------------------------+---------------------------------------+
| context.go('/')         | Returns to Home                       |
+-------------------------+---------------------------------------+

===================================================================================================

✅2.extraCodec:
-----------------

Here is a very **simple, clean example** that shows how to use the **extraCodec: parameter in GoRouter** with **MaterialApp.router()**.

The extraCodec is used when you want to send **non-primitive objects** (custom classes) through extra: in GoRouter and make them work with state restoration and **web deep-linking.**

In this example we:

    ✅ Create a User class

    ✅ Create a Codec<User, Object?>

    ✅ Pass a User object using extra:

    ✅ Decode it using extraCodec

**✅ 1. Full Working Example (main.dart)**

.. code-block:: dart 

    import 'dart:convert';
    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    /* -------------------- CUSTOM CLASS -------------------- */
    class User {
        final String name;
        final int age;

        User(this.name, this.age);

        Map<String, dynamic> toJson() => {
                'name': name,
                'age': age,
            };

        factory User.fromJson(Map<String, dynamic> json) {
            return User(json['name'], json['age']);
        }
    }

    /* -------------------- EXTRA CODEC -------------------- */
    class UserCodec extends Codec<User, Object?> {
        const UserCodec();

        @override
        Converter<User, Object?> get encoder => const _UserEncoder();

        @override
        Converter<Object?, User> get decoder => const _UserDecoder();
    }

    class _UserEncoder extends Converter<User, Object?> {
        const _UserEncoder();

        @override
        Object? convert(User input) {
            return input.toJson(); // Convert User to Map
        }
    }

    class _UserDecoder extends Converter<Object?, User> {
        const _UserDecoder();

        @override
        User convert(Object? input) {
            final map = input as Map<String, dynamic>;
            return User.fromJson(map); // Convert Map to User
        }
    }

    /* -------------------- ROUTER -------------------- */
    final GoRouter _router = GoRouter(
        extraCodec: const UserCodec(),   // ✅ IMPORTANT PART
        routes: [

            GoRoute(
                path: '/',
                builder: (context, state) => const HomePage(),
            ),

            GoRoute(
                path: '/profile',
                builder: (context, state) {
                    final user = state.extra as User;

                    return ProfilePage(user: user);
                },
            ),

        ],
    );

    /* -------------------- APP -------------------- */
    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                title: 'GoRouter extraCodec Example',
                routerConfig: _router,
            );
        }
    }

    /* -------------------- HOME -------------------- */
    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            final user = User('Sherullah', 25);

                            // ✅ Pass custom object using extra
                            context.go('/profile', extra: user);
                        },
                        child: const Text('Go to Profile'),
                    ),
                ),
            );
        }
    }

    /* -------------------- PROFILE -------------------- */
    class ProfilePage extends StatelessWidget {
        final User user;

        const ProfilePage({super.key, required this.user});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Profile')),
                body: Center(
                    child: Column(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                            Text('Name: ${user.name}', style: const TextStyle(fontSize: 22)),
                            Text('Age: ${user.age}', style: const TextStyle(fontSize: 22)),
                            const SizedBox(height: 30),
                            ElevatedButton(
                                onPressed: () {
                                    context.go('/');
                                },
                                child: const Text('Back to Home'),
                            ),
                        ],
                    ),
                ),
            );
        }
    }

**✅ What extraCodec is doing here**

+----------------------------------------+---------------------------------------+
| Part                                   | Meaning                               |
+========================================+=======================================+
| User                                   | Custom Dart class                     |
+----------------------------------------+---------------------------------------+
| UserCodec                              | Converts User  Map                    |
+----------------------------------------+---------------------------------------+
| extraCodec: UserCodec()                | Allows GoRouter to serialize extra:   |
+----------------------------------------+---------------------------------------+
| context.go('/profile', extra: user);   | Sends custom object                   |
+----------------------------------------+---------------------------------------+
| final user  state.extra as User;       | Receives object                       |
+----------------------------------------+---------------------------------------+

Without extraCodec, a **custom class will break state restoration or web URL reload.**

**🔑 Simple Rule to Remember**

Use:

    ✅ extra: "Hello" → No codec needed

    ✅ extra: 123 → No codec needed

    ✅ extra: MyClass() → ✅ Needs extraCodec

====================================================================================================

✅3.initialLocation:
----------------------

Here is a **very simple and clear Flutter example** showing how to use the **initialLocation: parameter in GoRouter** with **MaterialApp.router().**

This tells your app **which page to open first when the app starts.**

In this example, the app will **start on the About page** (/about) instead of the Home page.

**✅ Full working main.dart example**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    /* -------------------- ROUTER -------------------- */
    final GoRouter _router = GoRouter(
    
        // ✅ The FIRST screen when the app opens
        initialLocation: '/about',

        routes: [

            GoRoute(
                path: '/',
                builder: (context, state) => const HomePage(),
            ),

            GoRoute(
                path: '/about',
                builder: (context, state) => const AboutPage(),
            ),
        ],
    );

    /* -------------------- APP -------------------- */
    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                title: 'Initial Location Example',
                routerConfig: _router,
            );
        }
    }

    /* -------------------- HOME -------------------- */
    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            context.go('/about');  // Go to About
                        },
                        child: const Text('Go to About Page'),
                    ),
                ),
            );
        }
    }

    /* -------------------- ABOUT -------------------- */
    class AboutPage extends StatelessWidget {
        const AboutPage({super.key});

        @override
            Widget build(BuildContext context) {
                return Scaffold(
                appBar: AppBar(title: const Text('About Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            context.go('/');  // Go to Home
                        },
                        child: const Text('Back to Home'),
                    ),
                ),
            );
        }
    }

**🔍 Key line (most important)**

.. code-block:: dart 

    initialLocation: '/about',
    
That one line makes:

    ✅ **App start on About page**

    ✅ Without pressing any button

    ✅ No need for home: parameter

**✅ Summary**

+------------------+----------------------------------+
| Parameter        | Purpose                          |
+==================+==================================+
| initialLocation  |Decides first page on app launch  |
+------------------+----------------------------------+
| Used in          | GoRouter()                       |
+------------------+----------------------------------+
| Works with       | MaterialApp.router()             |
+------------------+----------------------------------+

===================================================================================================

✅4.observers:
---------------

Here is a **simple, clean Flutter example** showing how to use the **observers: parameter in GoRouter** with MaterialApp.router().

The observers parameter lets you **listen to navigation events** (like pushing a new route, popping a route). We will create a simple NavigatorObserver and print messages whenever navigation happens.

**✅ Full working main.dart example (with observers)**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    /* -------------------- ROUTER -------------------- */
    final GoRouter _router = GoRouter(
        routes: [
            GoRoute(
                path: '/',
                name: 'home',
                builder: (context, state) => const HomePage(),
            ),
            GoRoute(
                path: '/about',
                name: 'about',
                builder: (context, state) => const AboutPage(),
            ),
        ],
    );

    /* -------------------- APP -------------------- */
    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                title: 'GoRouter pop example',
                routerConfig: _router,
            );
        }
    }

    /* -------------------- HOME PAGE -------------------- */
    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            // ✅ Use push so that we CAN pop later
                            context.push('/about');
                        },
                        child: const Text('Go to About'),
                    ),
                ),
            );
        }
    }

    /* -------------------- ABOUT PAGE -------------------- */
    class AboutPage extends StatelessWidget {
        const AboutPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('About Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            // ✅ This is safe because we used push()
                            context.pop();
                        },
                        child: const Text('Back (pop) to Home'),
                    ),
                ),
            );
        }
    }

**🧠 What’s happening here?**

+-------------------------------+------------------------------+
| Part                          | Description                  |
+===============================+==============================+
| MyRouteObserver               | Custom observer class        |
+-------------------------------+------------------------------+
| didPush()                     | Runs when a route is opened  |
+-------------------------------+------------------------------+
| didPop()                      | Runs when a route is closed  |
+-------------------------------+------------------------------+
| observers: [MyRouteObserver()]| Registers the observer       |
+-------------------------------+------------------------------+
| context.go()                  | Push-like navigation         |
+-------------------------------+------------------------------+
| context.pop()                 | Pop navigation               |
+-------------------------------+------------------------------+

When you run this app and navigate, you will see **log messages in the console:**

.. code-block:: bash 

    ✅ Pushed route: about
    🔙 Popped route: about

**✅ Why is observers useful?**

You can use it for:

	•	Analytics (Firebase, GA)

	•	Debugging

	•	Tracking screen changes

	•	Logging page views

====================================================================================================

✅5.debugLogDiagnostics:
-------------------------

Here is a **very simple Flutter example** showing how to use the
**debugLogDiagnostics: parameter in GoRouter** with **MaterialApp.router().**

This setting tells GoRouter to **print detailed navigation logs** in the console.
It is used only for **debugging** (don’t use it in production).

**✅ Full working example – main.dart**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    /* -------------------- ROUTER -------------------- */
    final GoRouter _router = GoRouter(

        // ✅ Important parameter
        debugLogDiagnostics: true,

        routes: [

            GoRoute(
                path: '/',
                name: 'home',
                builder: (context, state) => const HomePage(),
            ),

            GoRoute(
                path: '/about',
                name: 'about',
                builder: (context, state) => const AboutPage(),
            ),
        ],
    );

    /* -------------------- APP -------------------- */
    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                title: 'GoRouter Debug Example',
                routerConfig: _router,
            );
        }
    }

    /* -------------------- HOME PAGE -------------------- */
    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            context.go('/about');
                        },
                        child: const Text('Go to About'),
                    ),
                ),
            );
        }
    }

    /* -------------------- ABOUT PAGE -------------------- */
    class AboutPage extends StatelessWidget {
        const AboutPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('About Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            context.go('/');
                        },
                        child: const Text('Back to Home'),
                    ),
                ),
            );
        }
    }

**✅ Most important line**

.. code-block:: dart 

    debugLogDiagnostics: true,

This tells GoRouter:

    “Print every navigation step in the console so I can see what is going on.”

**✅ Example logs you’ll see in Console**

When app starts:

.. code-block:: bash 

    [GoRouter] Initial route location: /
    [GoRouter] Router configured with 2 routes

When button is pressed:

.. code-block:: bash 

    [GoRouter] going to /about
    [GoRouter] setting new location: /about

When going back:

.. code-block:: bash 

    [GoRouter] going to /
    [GoRouter] setting new location: /

This is perfect for:

	•	Finding routing bugs

	•	Seeing deep link problems

	•	Debugging back stack issues

**✅ When to use / not use**

+--------------------+--------------------+
| Use it when        | Don’t use when     |
+====================+====================+
| Debugging          | Production release |
+--------------------+--------------------+
| Learning GoRouter  | Release APK/IPA    |
+--------------------+--------------------+
| Finding errors     | Live app           |
+--------------------+--------------------+

To turn off later:

.. code-block:: dart 

    debugLogDiagnostics: false,

(or completely remove the line)

========================================================================================================

✅6.redirect:
--------------

Here is a **very simple Flutter example** showing how to use the
**redirect: parameter in GoRouter** with **MaterialApp.router().**

In this example, we simulate a **login system:**

	•	If the user is **NOT logged in**, any page redirects to /login

	•	If the user **IS logged in, /login** redirects to /

**✅ Full working main.dart (with redirect)**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    /* -------------------- FAKE LOGIN STATE -------------------- */
    // Change this to true/false to test redirect
    bool isLoggedIn = false;

    /* -------------------- ROUTER -------------------- */
    final GoRouter _router = GoRouter(

        // ✅ REDIRECT PARAMETER
        redirect: (BuildContext context, GoRouterState state) {

            final bool loggingIn = state.uri.toString() == '/login';

            // If not logged in, send to login page
            if (!isLoggedIn && !loggingIn) {
                return '/login';
            }

            // If logged in and trying to access login page again
            if (isLoggedIn && loggingIn) {
                return '/';
            }

            // No redirect
            return null;
        },

        routes: [

            GoRoute(
                path: '/',
                builder: (context, state) => const HomePage(),
            ),

            GoRoute(
                path: '/login',
                builder: (context, state) => const LoginPage(),
            ),

            GoRoute(
                path: '/about',
                builder: (context, state) => const AboutPage(),
            ),
        ],
    );

    /* -------------------- APP -------------------- */
    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                title: 'GoRouter redirect example',
                routerConfig: _router,
            );
        }
    }

    /* -------------------- LOGIN PAGE -------------------- */
    class LoginPage extends StatelessWidget {
        const LoginPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Login Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            // Simulate login
                            isLoggedIn = true;

                            // Refresh router
                            _router.refresh();

                            // Go to home after login
                            context.go('/');
                        },
                        child: const Text('Login'),
                    ),
                ),
            );
        }
    }

    /* -------------------- HOME PAGE -------------------- */
    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home Page')),
                body: Center(
                    child: Column(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [

                            const Text(
                                'You are logged in',
                                style: TextStyle(fontSize: 22),
                            ),

                            const SizedBox(height: 20),

                            ElevatedButton(
                                onPressed: () {
                                    context.go('/about');
                                },
                                child: const Text('Go to About'),
                            ),

                            const SizedBox(height: 20),

                            ElevatedButton(
                                onPressed: () {
                                    // Simulate logout
                                    isLoggedIn = false;
                                    _router.refresh();

                                    context.go('/login');
                                },
                                child: const Text('Logout'),
                            ),

                        ],
                    ),
                ),
            );
        }
    }

    /* -------------------- ABOUT PAGE -------------------- */
    class AboutPage extends StatelessWidget {
        const AboutPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('About Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            context.go('/');
                        },
                        child: const Text('Back to Home'),
                    ),
                ),
            );
        }
    }

**🔥 The key part (redirect parameter)**

.. code-block:: dart 

    redirect: (context, state) {
        final loggingIn = state.uri.toString() == '/login';

        if (!isLoggedIn && !loggingIn) {
            return '/login';
        }

        if (isLoggedIn && loggingIn) {
            return '/';
        }

        return null;
    },

**What it does**

+--------------------------+----------------------------+
| Situation                | Result                     |
+==========================+============================+
| Not logged in + any page | → /login                   |
+--------------------------+----------------------------+
| Logged in + try /login   | → /                        |
+--------------------------+----------------------------+
| Logged in + normal page  | No redirect                |
+--------------------------+----------------------------+

**✅ Why redirect is important**

You use it for:

	•	Login / logout

	•	Admin-only pages

	•	Role-based security

	•	Onboarding flows

	•	First-time user flows

==========================================================================================================

✅7.redirectLimit:
-------------------

Here is a **clean, minimal Flutter example** showing how to use the
**redirectLimit: parameter in GoRouter** together with **MaterialApp.router().**

In this demo, we intentionally create a redirect loop so you can see how redirectLimit stops it.

**✅ Full working main.dart – with redirectLimit**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    /* -------------------- ROUTER -------------------- */
    final GoRouter _router = GoRouter(

        // ✅ Maximum number of redirects allowed
        redirectLimit: 3,

        // ✅ This redirect causes a loop (on purpose)
        redirect: (context, state) {
            if (state.uri.toString() == '/a') {
                return '/b';
            }
            if (state.uri.toString() == '/b') {
                return '/a';
            }
            return null;
        },

        routes: [
            GoRoute(
                path: '/',
                builder: (context, state) => const HomePage(),
            ),
            GoRoute(
                path: '/a',
                builder: (context, state) => const PageA(),
            ),
            GoRoute(
                path: '/b',
                builder: (context, state) => const PageB(),
            ),
        ],
    );

    /* -------------------- APP -------------------- */
    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                title: 'GoRouter redirectLimit demo',
                routerConfig: _router,
            );
        }
    }

    /* -------------------- HOME PAGE -------------------- */
    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            // ✅ Start redirect loop here
                            context.go('/a');
                        },
                        child: const Text('Go to Page A'),
                    ),
                ),
            );
        }
    }

    /* -------------------- PAGE A -------------------- */
    class PageA extends StatelessWidget {
        const PageA({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                body: Center(
                    child: Text(
                        'Page A',
                        style: TextStyle(fontSize: 24),
                    ),
                ),
            );
        }
    }

    /* -------------------- PAGE B -------------------- */
    class PageB extends StatelessWidget {
        const PageB({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                body: Center(
                    child: Text(
                        'Page B',
                        style: TextStyle(fontSize: 24),
                    ),
                ),
            );
        }
    }

**✅ What redirectLimit is doing here**

Means:

If GoRouter redirects more than **3 times in a row,** it will **stop and throw an error** instead of looping forever.

**Our redirect loop:**

.. code-block:: bash

    /a → /b → /a → /b → /a → ...

Because the limit is 3, GoRouter will stop after the 3rd redirect and show an error in the console like:

.. code-block:: bash 

    Too many redirects: /a -> /b -> /a -> /b

This **protects your app from crashing** or freezing.

**✅ When should you really use redirectLimit?**

+---------------------------+----------------------------+
| Use it when               | Why                        |
+===========================+============================+
| You use redirect a lot    | Prevent errors             |
+---------------------------+----------------------------+
| You have auth logic       | Prevent infinite redirect  |
+---------------------------+----------------------------+
| You have role-based logic | Prevent loop               |
+---------------------------+----------------------------+
| Production apps           | Safety feature             |
+---------------------------+----------------------------+

Normally you don’t change it, but now **you know exactly how it works.**

=======================================================================================================

✅8.navigatorKey:
------------------

Here is a **simple, clean Flutter example** that shows how to use the
**navigatorKey: parameter in GoRouter** with **MaterialApp.router().**

navigatorKey lets you **control the main Navigator from anywhere** (for dialogs, pop, push, etc.).

**✅ Full working example – navigatorKey in GoRouter**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
    runApp(const MyApp());
    }

    /* -------------------- GLOBAL NAVIGATOR KEY -------------------- */
    final GlobalKey<NavigatorState> _rootNavigatorKey = GlobalKey<NavigatorState>();

    /* -------------------- ROUTER -------------------- */
    final GoRouter _router = GoRouter(
        navigatorKey: _rootNavigatorKey,   // ✅ use navigatorKey here

        routes: [
            GoRoute(
                path: '/',
                builder: (context, state) => const HomePage(),
            ),
            GoRoute(
                path: '/second',
                builder: (context, state) => const SecondPage(),
            ),
        ],
    );

    /* -------------------- APP -------------------- */
    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                title: 'navigatorKey + GoRouter demo',
                routerConfig: _router,
            );
        }
    }

    /* -------------------- HOME PAGE -------------------- */
    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home Page')),
                body: Center(
                    child: Column(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                            // ✅ Normal navigation using GoRouter
                            ElevatedButton(
                            onPressed: () {
                                context.push('/second');
                            },
                            child: const Text('Go to Second Page'),
                            ),

                            const SizedBox(height: 20),

                            // ✅ Use navigatorKey only for dialog
                            ElevatedButton(
                                onPressed: () {
                                    final ctx = _rootNavigatorKey.currentContext!;
                                    showDialog(
                                        context: ctx,
                                        builder: (dialogContext) {
                                            return AlertDialog(
                                                title: const Text('Hello'),
                                                content: const Text('This dialog uses navigatorKey.'),
                                                actions: [
                                                    TextButton(
                                                        onPressed: () {
                                                            Navigator.of(dialogContext).pop();
                                                        },
                                                        child: const Text('Close'),
                                                    ),
                                                ],
                                            );
                                        },
                                    );
                                },
                                child: const Text('Show Dialog via navigatorKey'),
                            ),
                        ],
                    ),
                ),
            );
        }
    }

    /* -------------------- SECOND PAGE -------------------- */
    class SecondPage extends StatelessWidget {
        const SecondPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Second Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            // ✅ Use GoRouter to go back (no Navigator.pop here)
                            context.pop();
                        },
                        child: const Text('Back to Home'),
                    ),
                ),
            );
        }
    }

**✅ Key part you must remember**

.. code-block:: dart 

    final GlobalKey<NavigatorState> _rootNavigatorKey = GlobalKey<NavigatorState>();

    final GoRouter _router = GoRouter(
        navigatorKey: _rootNavigatorKey,
        routes: [...]
    );

That is **the real use of navigatorKey in GoRouter.**

It allows you to do things like:

    ✅ Navigate without BuildContext

    ✅ Show dialogs from services

    ✅ Control navigation globally

    ✅ Manage overlays and popups

**✅ When should YOU use navigatorKey?**

Use it when:

	•	You need navigation **inside a service**

	•	You need to **show dialog from anywhere**

	•	You want **full control** (advanced apps)

	•	You use **ShellRoute with nested navigators**

==========================================================================================================

✅9.restorationScopeId:
-------------------------

Here is a **very simple and clean Flutter example** showing how to use the
**restorationScopeId: parameter in GoRouter** with **MaterialApp.router().**

restorationScopeId is used for **state restoration**. It allows Flutter to restore the navigation state (for example, after the app is killed and reopened by the OS).

    You won’t “see” anything on screen, but this enables iOS/Android to remember your last route automatically in the background.

**✅ Full working example using restorationScopeId**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    /* -------------------- ROUTER -------------------- */
    final GoRouter _router = GoRouter(
        // ✅ Enable state restoration for GoRouter
        restorationScopeId: 'app_router',

        routes: [
            GoRoute(
                path: '/',
                builder: (context, state) => const HomePage(),
            ),
            GoRoute(
                path: '/details',
                builder: (context, state) => const DetailsPage(),
            ),
        ],
    );

    /* -------------------- APP -------------------- */
    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                title: 'State Restoration Example',
                restorationScopeId: 'material_app', // ✅ optional but recommended
                routerConfig: _router,
            );
        }
    }

    /* -------------------- HOME PAGE -------------------- */
    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            context.push('/details');
                        },
                        child: const Text('Go to Details'),
                    ),
                ),
            );
        }
    }

    /* -------------------- DETAILS PAGE -------------------- */
    class DetailsPage extends StatelessWidget {
        const DetailsPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Details Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            context.pop();
                        },
                        child: const Text('Back'),
                    ),
                ),
            );
        }
    }

**⭐ The two important lines**

**In GoRouter**

.. code-block:: dart 

    restorationScopeId: 'app_router',

In MaterialApp.router (recommended but optional)

.. code-block:: dart 

    restorationScopeId: 'material_app',

These IDs just have to be **unique strings.**

**✅ What this actually does**

When state restoration is enabled on the device:

	•	Open the app

	•	Go to /details

	•	Minimize or kill the app

	•	OS restores the app

	•	✅ It can **bring you back to /details automatically**

This is powerful for:

    ✅ Big apps

    ✅ Multi-page flows

    ✅ Forms

    ✅ Long usage sessions

**🧠 Easy rule to remember**

+--------------------------------+--------------------------------+
| Where                          | Why                            |
+================================+================================+
| GoRouter.restorationScopeId    | Restores navigation state      |
+--------------------------------+--------------------------------+
| MaterialApp.restorationScopeId | Enables app state restoration  |
+--------------------------------+--------------------------------+
| String value                   | Can be any unique text         |
+--------------------------------+--------------------------------+

==========================================================================================================

✅10.routerNeglect:
--------------------

Here is a **simple, clean Flutter example** that shows how to use the
**routerNeglect: parameter in GoRouter** with **MaterialApp.router().**

routerNeglect is mainly useful for **Flutter Web.**
When it is set to true, **GoRouter will NOT update the browser URL** when you navigate.

On mobile it still works fine — you won’t see a difference — but on the **Web**, the URL bar will not change.

**✅ Simple working example – routerNeglect**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    /* -------------------- ROUTER -------------------- */
    final GoRouter _router = GoRouter(

        // ✅ Important: ignores changing browser URL
        routerNeglect: true,

        routes: [
            GoRoute(
                path: '/',
                builder: (context, state) => const HomePage(),
            ),
            GoRoute(
                path: '/profile',
                builder: (context, state) => const ProfilePage(),
            ),
        ],
    );

    /* -------------------- APP -------------------- */
    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                title: 'routerNeglect Example',
                routerConfig: _router,
            );
        }
    }

    /* -------------------- HOME PAGE -------------------- */
    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            // Navigate to Profile
                            context.go('/profile');
                        },
                        child: const Text('Go to Profile'),
                    ),
                ),
            );
        }
    }

    /* -------------------- PROFILE PAGE -------------------- */
    class ProfilePage extends StatelessWidget {
        const ProfilePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Profile Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            // Navigate back to Home
                            context.go('/');
                        },
                        child: const Text('Back to Home'),
                    ),
                ),
            );
        }
    }

**🔍 The important line**

.. code-block:: dart 

    routerNeglect: true,

**What it actually does**

+--------------------------------+-----------------------------------+
| Situation                      | Result                            |
+================================+===================================+
| routerNeglect: true            | ✅ URL does NOT change in browser |
+--------------------------------+-----------------------------------+
| routerNeglect: false (default) | ✅ URL does change (/, /profile)  |
+--------------------------------+-----------------------------------+

On **Android / iOS:** no visible difference

On **Web:** this controls the **address bar**

**✅ When should you use routerNeglect?**

Use it when:

	•	You don’t want the URL to change on Web

	•	You use your own URL system

	•	You want privacy in routes

	•	You want single-page experience without URL updates

Do **not** use it if you want:

	•	Deep links

	•	Shareable URLs

	•	Browser back/forward working with URLs

=========================================================================================================

✅11.onException:
-------------------

Here is a **simple, working Flutter program** that shows how to use the
**onException: parameter in GoRouter** with **MaterialApp.router().**

onException is used to **catch routing errors** (for example: when a user navigates to a page that does not exist, or when a builder throws an error) and **handle them gracefully.**

In this example:

	•	We handle the error

	•	Print it in the console

	•	Redirect the user to a custom Error Page

**✅ Full working example – onException**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    /* -------------------- ROUTER -------------------- */
    final GoRouter _router = GoRouter(
        // In your version the 3rd param is GoRouter (NOT error)
        onException: (BuildContext context, GoRouterState state, GoRouter router) {
            debugPrint('❌ Routing problem. Tried path: ${state.uri}');

            // Avoid infinite loop: only redirect if not already on /error
            if (state.uri.toString() != '/error') {
                router.go('/error');   // ✅ use router, NOT context.go
            }
        },

        routes: [
            GoRoute(
                path: '/',
                builder: (context, state) => const HomePage(),
            ),
            GoRoute(
                path: '/profile',
                builder: (context, state) => const ProfilePage(),
            ),
            GoRoute(
                path: '/error',
                builder: (context, state) => const ErrorPage(),
            ),
        ],
    );

    /* -------------------- APP -------------------- */
    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                title: 'GoRouter onException demo',
                routerConfig: _router, // 🔴 no const here
            );
        }
    }

    /* -------------------- HOME PAGE -------------------- */
    class HomePage extends StatelessWidget {
    const HomePage({super.key});

    @override
    Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home')),
                body: Center(
                    child: Column(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                            ElevatedButton(
                                onPressed: () => context.go('/profile'),
                                child: const Text('Go to Profile (valid)'),
                            ),
                            const SizedBox(height: 20),
                            ElevatedButton(
                                // ❌ Invalid route: will trigger onException
                                onPressed: () => context.go('/unknown-page'),
                                child: const Text('Go to INVALID route'),
                            ),
                        ],
                    ),
                ),
            );
        }
    }

    /* -------------------- PROFILE PAGE -------------------- */
    class ProfilePage extends StatelessWidget {
        const ProfilePage({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                body: Center(
                    child: Text(
                        'Profile Page',
                        style: TextStyle(fontSize: 24),
                    ),
                ),
            );
        }
    }

    /* -------------------- ERROR PAGE -------------------- */
    class ErrorPage extends StatelessWidget {
        const ErrorPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Error Page')),
                body: Center(
                    child: Column(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                            const Text(
                                'Something went wrong ❌',
                                style: TextStyle(fontSize: 22),
                            ),
                            const SizedBox(height: 20),
                            ElevatedButton(
                                onPressed: () => context.go('/'),
                                child: const Text('Back to Home'),
                            ),
                        ],
                    ),
                ),
            );
        }
    }

**🧠 What is onException in GoRouter?**

onException is a **global error handler for routing problems**
in your app.

It runs when:
	•	A user navigates to a **route that doesn’t exist**

(e.g. /unknown-page)

	•	A **route builder crashes**

	•	A deep link fails

	•	There is a **navigation parsing error**

Instead of your app crashing, you get a chance to **log the error and redirect to a safe page.**

**✅ Real signature in your GoRouter version (14.8.1)**

From your errors, your version uses **this signature:**

.. code-block:: dart 

    onException: (BuildContext context, GoRouterState state, GoRouter router) {
        // handle error here
    }

Not GoRouterException, and not Object error.

**Meaning of the 3 parameters:**

+----------------------------+---------------------------------+
| Parameter                  | Meaning                         |
+============================+=================================+
| BuildContext context       | Current (but unsafe) context    |
+----------------------------+---------------------------------+
| GoRouterState state        | The route that failed           |
+----------------------------+---------------------------------+
| GoRouter router            | The main router instance ✅     |
+----------------------------+---------------------------------+

That’s why we must use:

.. code-block:: dart 

    router.go('/error');

and **NOT:**

.. code-block:: dart 

    context.go('/error');   // ❌ causes "No GoRouter found in context"

**📌 Simple Example**

.. code-block:: dart 

    final GoRouter _router = GoRouter(
        onException: (context, state, router) {
                print('❌ Error when going to: ${state.uri}');

                if (state.uri.toString() != '/error') {
                router.go('/error');   // safe redirect
            }
        },

        routes: [
            GoRoute(path: '/', builder: (c, s) => const HomePage()),
            GoRoute(path: '/error', builder: (c, s) => const ErrorPage()),
        ],
    );

If you press a button like this:

.. code-block:: dart 

    context.go('/wrong-path');

GoRouter will:

	1.	Fail to find /wrong-path

	2.	Call onException

	3.	You redirect to /error via router.go('/error')

No crash ✅

Nice error page ✅

**✅ Why onException is useful in real projects**

You can use it for:

    ✅ Show “Page not found” page

    ✅ Log issues to server / Firebase

    ✅ Prevent crashes

    ✅ Show error message to user

    ✅ Recover from broken deep links

**⚠️ Common mistakes (you already discovered these)**

+-------------------------------------------+----------------------------+
| Mistake                                   | Problem                    |
+===========================================+============================+
| Using GoRouterException                   | ❌ Doesn’t exist           |
+-------------------------------------------+----------------------------+
| Using context.go() inside onException     | ❌ No GoRouter in context  |
+-------------------------------------------+----------------------------+
| Using errorBuilder + onException together | ❌ Assertion error         |
+-------------------------------------------+----------------------------+
| Not checking current route                | ❌ Infinite redirect loop  |
+-------------------------------------------+----------------------------+

**📌 The golden rule**

Inside onException → **always use router.go(...)**

Never use context.go(...) there.