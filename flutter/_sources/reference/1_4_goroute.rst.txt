GoRoute
=========

All named parameters
----------------------

The **correct and complete numbered list of named parameters of GoRoute in Flutter (go_router package)**. These are only the parameters that belong to the **GoRoute constructor**

**GoRoute(**

    1.	**path:** (required)
	•	The URL path (e.g. '/', '/login', '/profile/:id')

    2.	**name:**
	•	Optional route name for context.goNamed()

    3.	**builder:**
	•	Builds a widget for the route

    4.	**pageBuilder:**
	•	Builds a custom Page (advanced navigation)

    5.	**routes:**
	•	Child/sub routes (nested routes)

    6.	**redirect:**
	•	Redirect logic for this route only

    7.	**onExit:**
	•	Runs when leaving the route (can prevent leaving)

    8.	**parentNavigatorKey:**
	•	Tells the route which navigator to use (ShellRoute use)

**)**

✅1.path:
----------

Here is **the simplest and cleanest Flutter example** that demonstrates the **path: parameter in GoRoute** using **MaterialApp.router().**

I made it **very short, no errors**, and **perfect for beginners.**

**✅ Simple Program — Using path: in GoRoute with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(MyApp());
    }

    class MyApp extends StatelessWidget {
        MyApp({super.key});

        // -------------------------------
        // GoRouter with path:
        // -------------------------------
        final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',           // 👈 Home path
                    builder: (context, state) => const HomePage(),
                ),
                GoRoute(
                    path: '/about',      // 👈 About page path
                    builder: (context, state) => const AboutPage(),
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            context.go('/about');   // 👈 navigate using path
                        },
                        child: const Text('Go to About'),
                    ),
                ),
            );
        }
    }

    class AboutPage extends StatelessWidget {
        const AboutPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('About')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            context.go('/');        // 👈 back to home
                        },
                        child: const Text('Go Back Home'),
                    ),
                ),
            );
        }
    }

**✅ Explanation (Very Simple)**

**🔹 path: '/'**

This defines the Home page.

**🔹 path: '/about'**

This defines the About page.

**🔹 Navigation**

You go to a path using:

.. code-block:: dart 

    context.go('/about');

And go back:

.. code-block:: dart 

    context.go('/');

=======================================================================================================

✅2.name:
----------

Here is a very **simple, clean, error-free example** showing how to use the **name: parameter in GoRoute **with **MaterialApp.router().**

**✅ Simple Program — Using name: in GoRoute with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(MyApp());
    }

    class MyApp extends StatelessWidget {
        MyApp({super.key});

        // --------------------------------
        // GoRouter using name:
        // --------------------------------
        final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',                  
                    name: 'home',               // 👈 route name
                    builder: (context, state) => const HomePage(),
                ),
                GoRoute(
                    path: '/about',
                    name: 'about',              // 👈 route name
                    builder: (context, state) => const AboutPage(),
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            context.goNamed('about');    // 👈 navigate using name
                        },
                        child: const Text('Go to About'),
                    ),
                ),
            );
        }
    }

    class AboutPage extends StatelessWidget {
        const AboutPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('About')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            context.goNamed('home');     // 👈 navigate using name
                        },
                        child: const Text('Go Back Home'),
                    ),
                ),
            );
        }
    }

**✅ Explanation (Very Easy)**

**🔹 name: 'home'**

Gives a **name** to the route.

**🔹 context.goNamed('about')**

Navigate using the route name instead of URL path.

**🔹 Benefits of using name:**

	•	Cleaner navigation

	•	Easy to pass parameters

	•	Avoid hard-coding URLs

	•	Works great for big apps

==========================================================================================================

✅3.builder:
-------------

Here is the **simplest possible** program that demonstrates the **builder: parameter in GoRoute** using **MaterialApp.router().**

Very clean, easy, and beginner-friendly.

**✅ Simple Program — Using builder: in GoRoute with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(MyApp());
    }

    class MyApp extends StatelessWidget {
        MyApp({super.key});

        // -------------------------------
        // GoRouter using builder:
        // -------------------------------
        final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',          
                    builder: (context, state) => const HomePage(),   // 👈 using builder
                ),
                GoRoute(
                    path: '/about',
                    builder: (context, state) => const AboutPage(),  // 👈 using builder
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                routerConfig: _router,   // 👈 connect router
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            context.go('/about');   // 👈 navigate
                        },
                        child: const Text('Go to About'),
                    ),
                ),
            );
        }
    }

    class AboutPage extends StatelessWidget {
        const AboutPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('About')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            context.go('/');        // 👈 back home
                        },
                        child: const Text('Go Back Home'),
                    ),
                ),
            );
        }
    }

**✅ Explanation (Very Easy)**

**🔹 builder: (context, state) => Widget**

The **builder** returns the **Widget** you want to show for this route.

**🔹 Why use builder?**

	•	Easy

	•	Clean

	•	Best for simple static pages

	•	No extra animation or advanced options

===========================================================================================================

✅4.pageBuilder:
-----------------

Here is the **cleanest, simplest, no-error** example that demonstrates the **pageBuilder: parameter in GoRoute** using **MaterialApp.router().**

This example returns a **custom transition page,** which is what pageBuilder: is normally used for.

**✅ Simple Program — Using pageBuilder: in GoRoute with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(MyApp());
    }

    class MyApp extends StatelessWidget {
        MyApp({super.key});

        // -------------------------------------
        // GoRouter using pageBuilder:
        // -------------------------------------
        final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',
                    pageBuilder: (context, state) {
                    return MaterialPage(
                        child: const HomePage(),
                    );
                    },
                ),
                GoRoute(
                    path: '/about',
                    pageBuilder: (context, state) {
                        return CustomTransitionPage(
                            child: const AboutPage(),
                            transitionsBuilder: (context, animation, secondaryAnimation, child) {
                                return FadeTransition(
                                    opacity: animation,
                                    child: child,
                                );
                            },
                        );
                    },
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
            routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            context.go('/about');
                        },
                        child: const Text('Go to About (Fade Transition)'),
                    ),
                ),
            );
        }
    }

    class AboutPage extends StatelessWidget {
        const AboutPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('About')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            context.go('/');
                        },
                        child: const Text('Go Back Home'),
                    ),
                ),
            );
        }
    }

**✅ Explanation (Very Easy)**

🔹 pageBuilder:

This returns a **Page object**, not a widget.

You can return:

	•	MaterialPage

	•	CupertinoPage

	•	CustomTransitionPage

	•	NoTransitionPage

**🔹 Why use pageBuilder?**

	•	Add animations (fade, slide, scale, rotate)

	•	Use platform-specific pages (iOS/Android)

	•	More control than builder:

**🔹 In this example:**

	•	/ uses a simple **MaterialPage**

	•	/about uses a **CustomTransitionPage** with fade animation

========================================================================================================

✅5.routes:
------------

Here is the **simplest possible example **that demonstrates the **routes: parameter in GoRoute** using **MaterialApp.router().**

This example shows:

    ✔ parent route

    ✔ child routes (nested)

    ✔ using routes: inside a GoRoute

**✅ Simple Program — Using routes: in GoRoute with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(MyApp());
    }

    class MyApp extends StatelessWidget {
        MyApp({super.key});

        // ------------------------------------------------
        // GoRouter using routes: (nested child routes)
        // ------------------------------------------------
        final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',
                    builder: (context, state) => const HomePage(),

                    // 👇 Child routes under "/"
                    routes: [
                        GoRoute(
                            path: 'about',                    // full path becomes: /about
                            builder: (context, state) => const AboutPage(),
                        ),
                        GoRoute(
                            path: 'contact',                  // full path becomes: /contact
                            builder: (context, state) => const ContactPage(),
                        ),
                    ],
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home')),
                body: Column(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: [
                        ElevatedButton(
                            onPressed: () => context.go('/about'),
                            child: const Text('Go to About'),
                        ),
                        ElevatedButton(
                            onPressed: () => context.go('/contact'),
                            child: const Text('Go to Contact'),
                        ),
                    ],
                ),
            );
        }
    }

    class AboutPage extends StatelessWidget {
        const AboutPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('About')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () => context.go('/'),
                        child: const Text('Go Home'),
                    ),
                ),
            );
        }
    }

    class ContactPage extends StatelessWidget {
        const ContactPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Contact')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () => context.go('/'),
                        child: const Text('Go Home'),
                    ),
                ),
            );
        }
    }

**✅ Explanation (Very Easy)**

**🔹 routes: in GoRoute**

The routes: parameter defines **child routes** (nested routes).

**🔹 Structure in this program**

,, code-block:: bash 

    /           → HomePage
    /about      → AboutPage   (child)
    /contact    → ContactPage (child)

**🔹 Why use child routes?**

	•	Organize large apps easily

	•	Create nested pages under a parent

	•	Cleaner URL structure 

========================================================================================================

✅6.redirect:
--------------

Here is a **very simple, clean, beginner-friendly** program demonstrating the **redirect: parameter in GoRoute** using **MaterialApp.router().**

👉 No authentication logic

👉 No complex code

👉 Only the basic redirect feature

**✅ Simple Program — Using redirect: in GoRoute with MaterialApp.router()**

This example redirects:

	•	If user tries to go to /profile,

    they get redirected to /login.

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(MyApp());
    }

    class MyApp extends StatelessWidget {
        MyApp({super.key});

        // ---------------------------------------
        // GoRouter using redirect:
        // ---------------------------------------
        final GoRouter _router = GoRouter(
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
                    path: '/profile',
                    builder: (context, state) => const ProfilePage(),

                    // 👇 redirect rule
                    redirect: (context, state) {
                        bool isLoggedIn = false;      // 👈 for demo only
                        if (!isLoggedIn) {
                            return '/login';            // redirect to login page
                        }
                        return null;                  // allow navigation
                    },
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
            routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home')),
                body: Center(
                        child: ElevatedButton(
                        onPressed: () => context.go('/profile'),
                        child: const Text('Go to Profile'),
                    ),
                ),
            );
        }
    }

    class LoginPage extends StatelessWidget {
        const LoginPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Login')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () => context.go('/'),
                        child: const Text('Back to Home'),
                    ),
                ),
            );
        }
    }

    class ProfilePage extends StatelessWidget {
        const ProfilePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Profile')),
                body: const Center(
                    child: Text('Welcome to your profile!'),
                ),
            );
        }
    }

**✅ Explanation (Very Easy)**

**🔹 redirect: (context, state) { ... }**

This function decides:

	**•	Should the user stay on this page?**

	**•	Or should they be redirected to another page?**

**🔹 In our example:**

.. code-block:: dart 

    bool isLoggedIn = false;

ince the user is “not logged in,” going to /profile automatically sends them to:

.. code-block:: bash 

    /login 

**🔹 return null;**

Means “no redirect → allow user to enter the page.”

========================================================================================================

✅7.onExit:
------------

✅8.parentNavigatorKey:
------------------------

