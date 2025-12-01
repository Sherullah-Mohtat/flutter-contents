MaterialApp
===========

**MaterialApp** is a **core widget** that serves as the **entry point** for most Flutter apps that follow **Material Design** guidelines (Google’s design system).

All Named Parameters
--------------------

Named parameters in the latest Flutter MaterialApp as of now. 

**MaterialApp(**

    1.	**home:** This is the widget for the default route of the app.

    2.	**title:** A string that describes the app, used by the device to show what your app is called.
	
    3.	**theme:** This parameter takes a ThemeData object to define the app’s theme.
	
    4.	**routes:** A map of route names to the builder functions for those routes.
	
    5.	**initialRoute:** The route that the app shows when it starts up.
	
    6.	**debugShowCheckedModeBanner:** A boolean that determines if the debug banner is shown.
	
    7.	**locale:** Sets the app’s locale.

    8.	**localizationsDelegates:** A list of delegates for localization.

    9.	**navigatorKey:** A key that provides control over the navigator.

    10.	**onGenerateRoute:** A function that’s called to generate routes that aren’t defined in the routes table.
	
    11.	**onUnknownRoute:** A function called when a named route is requested but not found.

    12.	**navigatorObservers:** A list of observers for the navigator.

    13.	**builder:** A function that wraps the whole app.

    14.	**themeMode:** Allows you to switch between light and dark themes.

    15.	**darkTheme:** Defines the theme to use when the device is in dark mode.
        
    16.	**color:** The color to use for the app’s back button in Android’s task switcher.

    17.	**highContrastTheme:** A theme used when the device requests a high contrast theme.

    18.	**highContrastDarkTheme:** The dark version of the high contrast theme.

    19.	**localeResolutionCallback:** A callback that’s used to determine the app’s locale.

    20.	**supportedLocales:** A list of locales that the app supports.

    21.	**scrollBehavior:** This allows you to customize the scroll physics and how the app responds to scrolling behavior.
	
    22.	**checkerboardRasterCacheImages:** This is a debugging parameter to show a checkerboard pattern when images are being raster cached.
	
    23. **checkerboardOffscreenLayers:** Used for debugging to show a checkerboard on offscreen layers.
	
    24.	**useInheritedMediaQuery:** This allows the app to inherit the media query from the parent, which can help in some advanced layout scenarios.
	
    25.	**restorationScopeId:** This is used for state restoration, helping to restore the app state when the app is restarted.
   
    26.	**onGenerateTitle:** This is a function that returns the app’s title at runtime, which can be useful if you want to generate the title dynamically based on some logic.
	
    27.	**actions:** This is a map of intent keys to action objects, which can help with handling shortcuts and other actions.
	
    28.	**onGenerateInitialRoutes:** This is a function that can be used to generate the initial set of routes.
    
    29.	**shortcuts:** This allows you to define keyboard shortcuts for your app by mapping keys to intents.
	
    30. **scaffoldMessengerKey:**  — A key to use when building the ScaffoldMessenger. 

    31. **showPerformanceOverlay:**

    32.	**key:** — A Flutter Widget key for the MaterialApp.

    33.	**onNavigationNotification:** — A callback (NotificationListenerCallback<NavigationNotification>) for navigation notifications.  

    34.	**debugShowMaterialGrid:** — A boolean to display a baseline grid overlay (for design/debug). 

    35.	**showSemanticsDebugger:** — A boolean that shows an overlay of semantic (accessibility) information. 

    36.	**localeListResolutionCallback:** — A callback (LocaleListResolutionCallback?) to choose locale when a list of locales is provided. 

    37.	**themeAnimationDuration:** — A Duration controlling how long theme change animations take. 

    38.	**themeAnimationCurve:** — A Curve controlling the animation curve when the theme changes. 

    39.	**themeAnimationStyle:** — (Optional) style object for theme animation overrides.  


**);**

Examples
----------

✅ 1. home:
-------------

➡️ The default screen (widget) shown when the app starts. Usually wrapped in a Scaffold to provide structure (app bar, body, etc.).

.. code-block:: dart 

    @override
    Widget build(BuildContext context) {
        return const MaterialApp(
            debugShowCheckedModeBanner: false,

            // 👇 THIS IS THE home: PARAMETER
            home: Scaffold(
                body: Center(
                    child: Text(
                        'This is the HOME screen!',
                        style: TextStyle(fontSize: 24),
                    ),
                ),
            ),
        );
    }

✅ 2. title:
-------------

➡️ Used by the OS (like Android’s app switcher or iOS VoiceOver) to describe your app. Not shown in the UI.

**✔ title:** is the name of your app.

**It is mainly used by:**

    •	Android task manager 

    •	Android recent apps list

    •	Some OS-level UI elements

    •	Accessibility tools (screen readers)

**Example:**
    When you open Android “Recent Apps” → you will see this name under the app.

**📌 Important Notes About title:**

    ▪ iOS does NOT use this title

    ▪ iOS uses the app name from Xcode project, not this parameter.

    ▪ Doesn’t display on screen

**title:** does NOT show inside the UI.
It is not visible to the user on the home screen.

.. code-block:: dart 

    @override
    Widget build(BuildContext context) {
        return const MaterialApp(
            debugShowCheckedModeBanner: false,

            // 👇 THIS IS THE title: PARAMETER
            title: 'Kaftarya App',

            home: Scaffold(
                body: Center(
                    child: Text(
                        'MaterialApp title example',
                        style: TextStyle(fontSize: 22),
                    ),
                ),
            ),
        );
    }

✅ 3. theme:
-------------

➡️ Defines the overall light theme of your app—colors, font, icon themes, etc.

The theme: parameter controls the entire look & design of your app.

.. code-block:: dart 

    @override
    Widget build(BuildContext context) {
        return MaterialApp(
            debugShowCheckedModeBanner: false,

            // 👇 THIS IS THE theme: PARAMETER
            theme: ThemeData(
                primarySwatch: Colors.blue,
                brightness: Brightness.light,
            ),

            home: const Scaffold(
                appBar: AppBar(
                    title: Text('Theme Example'),
                ),
                body: Center(
                    child: Text(
                        'This text follows the app theme!',
                        style: TextStyle(fontSize: 20),
                    ),
                ),
            ),
        );
    }

✅ 4. routes:
--------------

➡️ A map of named routes and their widgets. Allows you to navigate using Navigator.pushNamed(context, '/about').

•	When someone opens route ’/’ → show HomePage

•	When someone opens route ’/second’ → show SecondPage

🎯 How navigation works

    ➤ To go to another screen:
        Navigator.pushNamed(context, '/second');

    ➤ To go back:
        Navigator.pop(context);

.. code-block:: dart 

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS THE routes: PARAMETER
                routes: {
                    '/': (context) => const HomePage(),        // default home route
                    '/second': (context) => const SecondPage(), // second route
                },
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            // 👇 navigate using route name
                            Navigator.pushNamed(context, '/second');
                        },
                        child: const Text('Go to Second Page'),
                    ),
                ),
            );
        }
    }

    class SecondPage extends StatelessWidget {
        const SecondPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Second Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            // 👇 go back
                            Navigator.pop(context);
                        },
                        child: const Text('Go Back'),
                    ),
                ),
            );
        }
    }   

✅ 5. initialRoute:
---------------------

➡️ By default, Flutter starts at route '/'.

But if you set:

.. code-block:: dart 

    initialRoute: '/login',

Then the app opens LoginPage first, even though we have HomePage at '/'.

🎯 When should you use initialRoute:?

You use it for:
	•	showing login screen first

	•	showing onboarding or welcome page first

	•	opening a specific page depending on a condition

	•	redirecting user based on saved login state

**Example:**
   
.. code-block:: dart 

     initialRoute: userLoggedIn ? '/dashboard' : '/login';

📌 Important Notes
	1.	The route used in initialRoute must exist inside routes:.

	2.	If you use home: and initialRoute: together:
        **initialRoute wins**, and **home is ignored.**

.. code-block:: dart

    import 'package:flutter/material.dart';

    void main() {
    runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS THE initialRoute PARAMETER
                initialRoute: '/login',

                // 👇 These routes must contain the initialRoute
                routes: {
                    '/': (context) => const HomePage(),
                    '/login': (context) => const LoginPage(),
                    '/dashboard': (context) => const DashboardPage(),
                },
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () => Navigator.pushNamed(context, '/login'),
                        child: const Text('Go to Login'),
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
                appBar: AppBar(title: const Text('Login Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () => Navigator.pushNamed(context, '/dashboard'),
                        child: const Text('Login → Dashboard'),
                    ),
                ),
            );
        }
    }

    class DashboardPage extends StatelessWidget {
        const DashboardPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Dashboard')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () => Navigator.pushNamed(context, '/'),
                        child: const Text('Go to Home'),
                    ),
                ),
            );
        }
    }

✅ 6. debugShowCheckedModeBanner:
----------------------------------

➡️ Removes the red “DEBUG” banner shown in debug mode.

.. code-block:: dart 

    MaterialApp(debugShowCheckedModeBanner: false,);
    
✅ 7. locale:
--------------

➡️ Forces the app to use a specific language (e.g., English - United States).
    locale: tells Flutter which language and region your app should use.

🎯 Why do we need localizationsDelegates and supportedLocales?

Flutter needs to know:
    1.	Which languages your app supports → supportedLocales
    2.	Which translation mechanisms to use → localizationsDelegates

Without these, localization will not work.

.. code-block:: dart 

    @override
    Widget build(BuildContext context) {
        return MaterialApp(
            debugShowCheckedModeBanner: false,

            // 👇 THIS IS THE locale: PARAMETER
            locale: const Locale('en', 'US'),   // language = English, country = United States

            // 👇 Required for localization support
            localizationsDelegates: const [
                GlobalMaterialLocalizations.delegate,
                GlobalWidgetsLocalizations.delegate,
                GlobalCupertinoLocalizations.delegate,
            ],

            supportedLocales: const [
                Locale('en', 'US'),
                Locale('es', 'ES'),
                Locale('fa', 'AF'),   // Pashto / Afghanistan example
            ],

            home: const HomePage(),
        );
    }

✅ 8. localizationsDelegates:
------------------------------

➡️ Provides resources (translations, formats) for specific languages, used for internationalization.

.. code-block:: dart 

    MaterialApp(
        // 👇 Required for localization support
        localizationsDelegates: const [
            GlobalMaterialLocalizations.delegate,
            GlobalWidgetsLocalizations.delegate,
            GlobalCupertinoLocalizations.delegate,
        ],
    );

✅ 9. navigatorKey: 
--------------------

➡️ Lets you control navigation outside of the BuildContext, such as from a service or notification.

Normally, you navigate like this:

.. code-block:: dart 

    Navigator.pushNamed(context, '/second');

But sometimes you don’t have context **—for example:**

.. code-block:: dart 

    myNavigatorKey.currentState!.pushNamed('/login');

No context needed — just the global key.


	•	inside a **service class**

	•	inside a **provider**

	•	inside a **background function**

	•	inside a **Bloc**
    
	•	outside of widgets

In those cases, navigatorKey gives you a global navigation controller.

**🎯 Why use navigatorKey?**

    ✓ Navigate from anywhere

    ✓ Show dialogs without context

    ✓ Works even in background logic

    ✓ Useful in authentication systems

    ✓ Useful in state managers (Provider, Bloc, Riverpod)

.. code-block:: dart 

    import 'package:flutter/material.dart';

    // 👇 Create a global navigator key
    final GlobalKey<NavigatorState> myNavigatorKey = GlobalKey<NavigatorState>();

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS navigatorKey:
                navigatorKey: myNavigatorKey,

                routes: {
                    '/': (context) => const HomePage(),
                    '/second': (context) => const SecondPage(),
                },
             );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            // 👇 Navigate WITHOUT using context
                            myNavigatorKey.currentState!.pushNamed('/second');
                        },
                        child: const Text('Go to Second Page (no context)'),
                    ),
                ),
            );
        }
    }

    class SecondPage extends StatelessWidget {
        const SecondPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Second Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            // 👇 Pop without context
                            myNavigatorKey.currentState!.pop();
                        },
                        child: const Text('Go Back (no context)'),
                    ),
                ),
            );
        }
    }

✅ 10. onGenerateRoute:
-------------------------

➡️ Called when a route is not found in routes. You can return a custom screen dynamically.

onGenerateRoute is used when:

	•	You want **full control** of navigation

	•	You want to **pass data/arguments**

	•	You want to **handle dynamic routes**

	•	The route is **not listed in routes: map**

This example has **two pages:**
	•	**HomePage**

	•	**SecondPage** (receives a message)

**📝 What is onGenerateRoute:?**

onGenerateRoute is a function that gets called every time navigation happens.

It gives you:
	•	the route name (settings.name)

	•	any arguments passed (settings.arguments)

Using this, you return:

.. code-block:: dart 

    MaterialPageRoute(builder: ...)

**🎯 Why use onGenerateRoute:?**

✔ When you want dynamic routing

✔ When you want to pass data easily

✔ When you want central navigation logic

✔ When you need logging, analytics, deep links

✔ When using Navigator 1.0 advanced features

.. code-block:: dart 

   
    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS onGenerateRoute:
                onGenerateRoute: (settings) {
                    switch (settings.name) {
                        case '/':
                        return MaterialPageRoute(
                            builder: (context) => const HomePage(),
                        );

                        case '/second':
                        // 👇 Read arguments sent to this route
                        final message = settings.arguments as String?;

                        return MaterialPageRoute(
                            builder: (context) => SecondPage(message: message),
                        );
                    }

                    // 👇 If route doesn't exist
                    return MaterialPageRoute(
                        builder: (context) => const UnknownPage(),
                    );
                },
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            Navigator.pushNamed(
                                context,
                                '/second',
                                arguments: 'Hello from HomePage!', // 👈 Sending data
                            );
                        },
                        child: const Text('Go to Second Page'),
                    ),
                ),
            );
        }
    }

    class SecondPage extends StatelessWidget {
        final String? message;

        const SecondPage({super.key, this.message});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Second Page')),
                body: Center(
                    child: Text(
                        message ?? 'No message received',
                        style: const TextStyle(fontSize: 20),
                    ),
                ),
            );
        }
    }

    class UnknownPage extends StatelessWidget {
        const UnknownPage({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                body: Center(
                    child: Text(
                        '404 - Page Not Found!',
                        style: TextStyle(fontSize: 22),
                    ),
                ),
            );
        }
    }

✅ 11. onUnknownRoute:
-----------------------

**📝 What is onUnknownRoute:?**

It is a fallback route handler used when:
	•	The user navigates to a route that is not registered

	•	The route name doesn’t exist in routes:

	•	The route name doesn’t exist in onGenerateRoute:

Without this parameter, Flutter would crash with:

.. code-block:: dart 

    Could not find a generator for route /wrongRoute

With onUnknownRoute, Flutter shows your custom 404 page instead.

**🎯 Why use onUnknownRoute:?**

    ✔ Prevents app crashes

    ✔ Shows a friendly error screen

    ✔ Good for production apps

    ✔ Useful for dynamic routing situations

    ✔ Helps with debugging wrong route names

🗂️ Priority Order in Flutter Routing

Flutter decides routes in this order:
	1.	**routes:** → if exists, use it

	2.	**onGenerateRoute:** → if matches logic, use it

	3.	**onUnknownRoute:** → fallback

	4.	Otherwise crash (if no fallback exists)

**🌟 Minimal Version**

.. code-block:: dart 

    onUnknownRoute: (_) => MaterialPageRoute(
        builder: (_) => Text('Page Not Found'),
    ),

**✅ Simple Example Showing onUnknownRoute: in MaterialApp**

onUnknownRoute: is used when the user tries to navigate to a route that does NOT exist in the app.

Flutter will show a custom 404 page instead of crashing.

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                routes: {
                    '/': (context) => const HomePage(),
                    // no other routes on purpose
                },

                // 👇 THIS IS onUnknownRoute:
                onUnknownRoute: (settings) {
                    return MaterialPageRoute(
                        builder: (context) => const UnknownPage(),
                    );
                },
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            // 👇 Try to open a route that DOES NOT exist
                            Navigator.pushNamed(context, '/wrongRoute');
                        },
                        child: const Text('Go to INVALID route'),
                    ),
                ),
            );
        }
    }

    class UnknownPage extends StatelessWidget {
        const UnknownPage({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                body: Center(
                    child: Text(
                        '404 - Page Not Found',
                        style: TextStyle(fontSize: 24, color: Colors.red),
                    ),
                ),
            );
        }
    }

✅ 12. navigatorObservers:
---------------------------

**📝 What is navigatorObservers:?**

navigatorObservers: allows you to watch navigation events.

You can detect when:

	•	user moves to a new page (push)

	•	user goes back (pop)

	•	user replaces a page (replace)

	•	route is removed (remove)

**🎯 What does our example observer do?**

Our custom class:

.. code-block:: dart 

    class MyNavigatorObserver extends NavigatorObserver { ... }

Prints:

**When user goes to /second:**

.. code-block:: bash 

    📌 didPush → Moved to: /second

**When user goes back:**

.. code-block:: bash 

    📌 didPop → Returned from: /second

This is extremely helpful for:

    ✓ Analytics

    ✓ Logging

    ✓ Tracking user navigation

    ✓ Debugging

    ✓ Monitoring page transitions

    ✓ App state management

🌟 Minimal Version

.. code-block:: dart 

    navigatorObservers: [MyNavigatorObserver()],

Or use Flutter’s default ones like:

.. code-block:: dart 

    navigatorObservers: [HeroController()],

**⚡ Real use cases**

**✔ Track which pages user opened**

**✔ Send page analytics to Firebase / Mixpanel**

**✔ Track user flow inside app**

**✔ Debug unexpected navigation**

**✔ Log transitions during development**

.. code-block:: dart 

    import 'package:flutter/material.dart';

    // 👇 Create a simple custom NavigatorObserver
    class MyNavigatorObserver extends NavigatorObserver {
        @override
        void didPush(Route route, Route? previousRoute) {
            print('📌 didPush → Moved to: ${route.settings.name}');
        }

        @override
        void didPop(Route route, Route? previousRoute) {
            print('📌 didPop → Returned from: ${route.settings.name}');
        }
    }

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                routes: {
                    '/': (context) => const HomePage(),
                    '/second': (context) => const SecondPage(),
                },

                // 👇 THIS IS THE navigatorObservers: PARAMETER
                navigatorObservers: [
                    MyNavigatorObserver(), // custom observer
                ],
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home Page')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            Navigator.pushNamed(context, '/second');
                        },
                        child: const Text('Go to Second Page'),
                    ),
                ),
            );
        }
    }

    class SecondPage extends StatelessWidget {
        const SecondPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Second Page')),
                    body: Center(
                        child: ElevatedButton(
                            onPressed: () {
                                Navigator.pop(context);
                            },
                            child: const Text('Go Back'),
                        ),
                )       ,
            );
        }
    }


✅ 13. builder:
----------------

➡️ Useful to inject widgets like MediaQuery, Theme, Directionality, or overlays.
builder: lets you wrap every screen with a widget.

It is useful for:

    •	Adding a global padding

    •	Adding a global theme wrapper

    •	Adding overlay widgets

    •	Adding custom font scaling

    •	Debug borders

    •	Global direction (LTR/RTL)

    •	Adding a banner to every page

**✅ Simple Example Showing builder: in MaterialApp**

This example wraps every page inside a SafeArea using builder:.

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS THE builder: PARAMETER
                builder: (context, child) {
                    return SafeArea(
                        child: child!, // 👈 wraps the entire app inside SafeArea
                    );
                },

                home: const HomePage(),
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                body: Center(
                    child: Text(
                        'This page is inside SafeArea from builder:',
                        textAlign: TextAlign.center,
                    ),
                ),
            );
        }
    }

**📝 What does builder: do?**

builder: gives you a function:

.. code-block:: dart 

    builder: (BuildContext context, Widget? child) {
        return WrappedWidget(child: child);
    }

This means:

✔ You can **wrap all screens**
✔ You can **modify UI globally**
✔ You can **apply effects once** instead of repeating in every page

**🎯 Why use builder:?**

    **✔ Add SafeArea globally**

    → No need for SafeArea on every page.

    **✔ Add Direction (RTL/LTR)**

    → Wrap with Directionality.

    **✔ Add global overlay (loading spinner, banner, etc.)**

    **✔ Debug layouts**

    → Wrap with Container + border.

    **✔ Add a global text scaler**

    → Useful when controlling font size across the app.

**🌟 Example 2: Add a red border around the whole app**

.. code-block:: dart 

    builder: (context, child) {
        return Container(
            decoration: BoxDecoration(border: Border.all(color: Colors.red, width: 4)),
            child: child,
        );
    },

**🌟 Example 3: Force RTL (Right-to-left)**

.. code-block:: dart 

    builder: (context, child) {
        return Directionality(
            textDirection: TextDirection.rtl,
            child: child!,
        );
    },

**🌟 Example 4: Add a global loading overlay**

.. code-block:: dart 

    builder: (context, child) {
        return Stack(
            children: [
                child!,
                Positioned(
                    bottom: 20,
                    right: 20,
                    child: Text("Global Overlay"),
                )
            ],
        );
    },

**⚡ Extremely Simple Version**

.. code-block:: dart 

    MaterialApp(
        builder: (context, child) => child!,
    )

✅ 14. themeMode:
------------------

➡️ Controls whether to use light theme, dark theme, or follow system setting.

themeMode: decides **whether your app uses Light Theme, Dark Theme, or System Theme.**

**✅ Simple Example Showing themeMode: in MaterialApp**

This example shows:

	•	Light theme

	•	Dark theme

	•	themeMode to choose between them

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatefulWidget {
        const MyApp({super.key});

        @override
        State<MyApp> createState() => _MyAppState();
    }

    class _MyAppState extends State<MyApp> {
        bool isDark = false;

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 Light Theme
                theme: ThemeData(
                    brightness: Brightness.light,
                    primarySwatch: Colors.blue,
                ),

                // 👇 Dark Theme
                darkTheme: ThemeData(
                    brightness: Brightness.dark,
                ),

                // 👇 THIS IS THE themeMode: PARAMETER
                themeMode: isDark ? ThemeMode.dark : ThemeMode.light,

                home: HomePage(
                    toggleTheme: () {
                        setState(() {
                            isDark = !isDark;
                        });
                    },
                ),
            );
        }
    }

    class HomePage extends StatelessWidget {
        final VoidCallback toggleTheme;

        const HomePage({super.key, required this.toggleTheme});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('themeMode Example')),
                body: Center(
                    child: ElevatedButton(
                        onPressed: toggleTheme,
                        child: const Text('Toggle Light/Dark Theme'),
                    ),
                ),
            );
        }
    }

**📝 What is themeMode:?**

    themeMode: tells Flutter which theme to use:

    **✔ ThemeMode.light**

    → Always use the light theme

    **✔ ThemeMode.dark**

    → Always use the dark theme

    **✔ ThemeMode.system**

    → Follow the device setting (user’s Android/iOS dark mode)

**🎯 Minimal Example**

If you don’t need a toggle button:

.. code-block:: dart 

    MaterialApp(
        theme: ThemeData.light(),
        darkTheme: ThemeData.dark(),
        themeMode: ThemeMode.system,
    );

**🌟 Example: Force Dark Mode**

.. code-block:: dart 

    themeMode: ThemeMode.dark,

**🌟 Example: Force Light Mode**

.. code-block:: dart 

    themeMode: ThemeMode.light,

**🌟 Example: Follow System Setting**

.. code-block:: dart 

    themeMode: ThemeMode.system,

**⚡ Important Notes**
	1.	You **must** provide both:

.. code-block:: dart 

    theme:
    darkTheme:

Otherwise, Flutter cannot switch between them.
	2.	themeMode: only chooses **which one to use.**

✅ 15. darkTheme:
------------------

➡️ Defines the theme used when the system is in dark mode and themeMode is set to ThemeMode.system.

**📝 What is darkTheme:?**

darkTheme: defines **how your app looks when dark mode is ON.**

It is used **only when:**

.. code-block:: dart 

    themeMode: ThemeMode.dark

or the device is in dark mode with:

.. code-block:: dart 

    themeMode: ThemeMode.system

**🎯 Why do we need darkTheme:?**

Because:
    •	Dark mode needs different colors

    •	Text contrast must change

    •	Background becomes dark

    •	Buttons/icons adapt to dark mode

**Example: Force Dark Mode**

Ignore system setting and always use dark theme:

.. code-block:: dart 

    MaterialApp(
        theme: ThemeData.light(),
        darkTheme: ThemeData.dark(),
        themeMode: ThemeMode.dark,
    );

**🌞 Example: Force Light Mode**

.. code-block:: dart 

    themeMode: ThemeMode.light,

**⚡ Minimal Version**

.. code-block:: dart 

    MaterialApp(
        theme: ThemeData.light(),
        darkTheme: ThemeData.dark(),
        home: HomePage(),
    );

**✅ Simple Example Showing darkTheme: in MaterialApp**

This example provides light theme + dark theme, and uses system setting to decide which one to show.

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 Light Theme
                theme: ThemeData(
                    brightness: Brightness.light,
                    primarySwatch: Colors.blue,
                ),

                // 👇 THIS IS THE darkTheme: PARAMETER
                darkTheme: ThemeData(
                    brightness: Brightness.dark,
                    primarySwatch: Colors.deepPurple,
                ),

                // 👇 Follow system (Light / Dark)
                themeMode: ThemeMode.system,

                home: const HomePage(),
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text("darkTheme Example")),
                body: Center(
                    child: Text(
                        'Switch your device to Dark Mode!',
                        style: Theme.of(context).textTheme.headlineSmall,
                    ),
                ),
            );
        }
    }

✅ 16. color:
---------------

➡️ Used on Android for the app preview in the task switcher (background color).

**📝 What does color: do in MaterialApp?**

The color: parameter sets the **primary color** used by:

    •	Android **task switcher background**

    •	Window background color (sometimes)

    •	When app is minimized or shown in “Recent Apps” screen

    •	The color of the “app” square preview

It **does NOT** change the on-screen UI color.

Example:

.. code-block:: dart 

    color: Colors.red,

This makes your app preview in the Android recent apps menu **red.**

**❗ Important**

color: is **NOT** for UI colors.

It’s NOT the same as:

	•	theme.primaryColor

	•	AppBar(color: ...)

	•	Scaffold(backgroundColor: ...)

It only affects **system UI / task manager.**

**🌟 Quick Example: Change “Recent Apps” color**

.. code-block:: dart 

    color: Colors.green,

When you open the Android **Recent Apps,** your app tile becomes green.

**⚡ Minimal Usage**

.. code-block:: dart 

    MaterialApp(color: Colors.orange)

**✅ Simple Example Showing color: in MaterialApp**

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS THE color: PARAMETER
                color: Colors.blue,

                home: const HomePage(),
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                body: Center(
                    child: Text(
                        'MaterialApp color: example',
                        style: TextStyle(fontSize: 22),
                    ),
                ),
            );
        }
    }

✅ 17. highContrastTheme:
--------------------------

**📝 What is highContrastTheme:?**

It is a special theme that Flutter uses when the system requests **high-contrast UI** for accessibility.

Typical changes include:
	•	**Thicker borders**

	•	**Stronger color contrast**

	•	**Bolder text**

	•	**More visible elements**

	•	**Better readability**

**🎯 How to view the high contrast theme?**

To test it:

**On Android:**

Settings → Accessibility → **High Contrast Text** → ON

**On iPhone/iPad:**

Settings → Accessibility → **Increase Contrast**

Then reopen the app → Flutter will automatically switch to highContrastTheme.

**🌟 Minimal Version**

.. code-block:: dart 

    MaterialApp(
        theme: ThemeData.light(),
        highContrastTheme: ThemeData.highContrastLight(),
    );

**🎨 Example with High Contrast Dark Theme Too**

.. code-block:: dart 

    highContrastTheme: ThemeData.highContrastLight(),
    highContrastDarkTheme: ThemeData.highContrastDark(),

**✅ Simple Example Showing highContrastTheme: in MaterialApp**

highContrastTheme: is used when the user enables High Contrast mode on their device (for accessibility).
This is often used by people with low vision.

Flutter automatically switches to this theme when High Contrast is ON in device accessibility settings.

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // Normal theme
                theme: ThemeData(
                    brightness: Brightness.light,
                ),

                // 👇 THIS IS THE highContrastTheme: PARAMETER
                highContrastTheme: ThemeData(
                    brightness: Brightness.light,
                    colorScheme: const ColorScheme.highContrastLight(),
                    textTheme: const TextTheme(
                        bodyLarge: TextStyle(fontSize: 26, fontWeight: FontWeight.bold),
                        bodyMedium: TextStyle(fontSize: 20),
                    ),
                ),

                home: const HomePage(),
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('High Contrast Theme Example')),
                body: const Center(
                    child: Text(
                        'Turn ON high contrast in device settings!',
                        textAlign: TextAlign.center,
                    ),
                ),
            );
        }
    }

✅ 18. highContrastDarkTheme:
------------------------------

**📝 What is highContrastDarkTheme:?**

It is the **dark version** of the high-contrast theme.

Used when:

+-------------------+-------------------+---------------------------------------------+
| Dark Mode         | High Contrast     |              Which Theme?                   |
+===================+===================+=============================================+
| ❌ No             | ❌ No             | theme (light)                               |
+-------------------+-------------------+---------------------------------------------+
| ✔ Yes             | ❌ No             | darkTheme                                   |
+-------------------+-------------------+---------------------------------------------+
| ✔ Yes             | ✔ Yes             | highContrastDarkTheme                       |
+-------------------+-------------------+---------------------------------------------+
| ❌ No             | ✔ Yes             | highContrastTheme                           |
+-------------------+-------------------+---------------------------------------------+

**🎯 Why do we need it?**

High-contrast dark theme improves accessibility:
	•	Brighter text on darker backgrounds

	•	Stronger contrast for readability

	•	Clear separation between UI elements

	•	Better for people with low vision

**🌙 Minimal Version**

.. code-block:: dart 

    MaterialApp(
        darkTheme: ThemeData.dark(),
        highContrastDarkTheme: ThemeData.highContrastDark(),
        themeMode: ThemeMode.dark,
    );

**⚡ Bonus: If you also want highContrastTheme (light)**

.. code-block:: dart 

    highContrastTheme: ThemeData.highContrastLight(),
    highContrastDarkTheme: ThemeData.highContrastDark(),

**✅ Simple Example Showing highContrastDarkTheme: in MaterialApp**

This example gives your app:

	•	a **normal light theme**

	•	a **normal dark theme**

	•	a **high-contrast dark theme** (for accessibility)

Flutter will automatically use **highContrastDarkTheme** when:

👉 The device is in **Dark Mode**
AND
👉 **High Contrast** is turned ON in device accessibility settings.

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // Normal Light Theme
                theme: ThemeData(
                    brightness: Brightness.light,
                ),

                // Normal Dark Theme
                darkTheme: ThemeData(
                    brightness: Brightness.dark,
                ),

                // 👇 THIS IS THE highContrastDarkTheme: PARAMETER
                highContrastDarkTheme: ThemeData(
                    brightness: Brightness.dark,
                    colorScheme: const ColorScheme.highContrastDark(),
                    textTheme: const TextTheme(
                        bodyLarge: TextStyle(fontSize: 26, fontWeight: FontWeight.bold),
                        bodyMedium: TextStyle(fontSize: 20),
                    ),
                ),

                // Follow system (Light / Dark)
                themeMode: ThemeMode.system,

                home: const HomePage(),
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                body: Center(
                    child: Text(
                        'Switch your device to:\nDark Mode + High Contrast ON',
                        textAlign: TextAlign.center,
                    ),
                ),
            );
        }
    }

✅ 19. localeResolutionCallback:
----------------------------------

➡️ You can decide how to choose the right Locale based on device settings and supported locales.

**📝 What does localeResolutionCallback: do?**

Whenever your app starts, Flutter checks:
	1.	**What is the device language?**

	2.	**Do we support that language?**

	3.	**If not, which language should we choose instead?**

You decide the logic.

**🎯 Example: Device = Farsi (fa_AF)**
	•	Your app supports: en_US, es_ES, ps_AF

	•	Device is using: fa_AF (Farsi)

Since Farsi is not supported → the callback decides:

Use the fallback locale (usually en_US)

**🌍 Real use cases of localeResolutionCallback**

**✔ Fallback language selection**

Choose “English” if your app does not support user’s language.

**✔ Custom language priority logic**

Example: choose Pashto for any Afghanistan region.

.. code-block:: dart 

    if (deviceLocale.countryCode == 'AF') return Locale('ps', 'AF');

**✔ Debug which locale Flutter picks**

Useful while developing multilingual apps.

**✔ Multi-language apps with dynamic behavior**

**🌟 Minimal Version**

.. code-block:: dart 

    localeResolutionCallback: (deviceLocale, supportedLocales) {
        return supportedLocales.first;
    },

**⚡ Example: If device language is Arabic → use English**

.. code-block:: dart 

    localeResolutionCallback: (device, supported) {
        if (device?.languageCode == 'ar') {
            return const Locale('en', 'US');
        }
        return device;
    },

**✅ Simple Example Showing localeResolutionCallback: in MaterialApp**

localeResolutionCallback: allows you to **control which locale (language) your app should use** when the user’s device language doesn’t match your supported languages.

This example prints which locale Flutter selected.

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:flutter_localizations/flutter_localizations.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                supportedLocales: const [
                    Locale('en', 'US'),
                    Locale('es', 'ES'),
                    Locale('ps', 'AF'),  // Pashto
                ],

                localizationsDelegates: const [
                    GlobalMaterialLocalizations.delegate,
                    GlobalWidgetsLocalizations.delegate,
                    GlobalCupertinoLocalizations.delegate,
                ],

                // 👇 THIS IS localeResolutionCallback:
                localeResolutionCallback: (deviceLocale, supportedLocales) {
                    print("📌 Device Locale = $deviceLocale");

                    // If device locale is supported → use it
                    if (deviceLocale != null) {
                        for (var locale in supportedLocales) {
                            if (locale.languageCode == deviceLocale.languageCode) {
                                print("✅ Using Supported Locale = $locale");
                                return locale;
                            }
                        }
                    }

                    // Otherwise → fallback to first supported locale
                    print("⚠️ Device Not Supported → Using Default = ${supportedLocales.first}");
                    return supportedLocales.first;
                },

                home: const HomePage(),
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                body: Center(
                    child: Text(
                        'localeResolutionCallback Example',
                        style: TextStyle(fontSize: 22),
                    ),
                ),
            );
        }
    }



✅ 20. supportedLocales:
--------------------------

➡️ Lists all the locales your app can work with (for translation, formatting, etc.).

**📝 What does supportedLocales: do?**

It defines the **list of languages your app can display.**

Flutter uses this list to:
	•	Match the device language

	•	Decide which localization files to load

	•	Choose fonts, direction (LTR/RTL), number formatting, etc.

Example:

.. code-block:: dart 

    supportedLocales: [
        Locale('en', 'US'),
        Locale('ps', 'AF'),
    ]

If device language = Pashto → app uses Pashto automatically.

**🎯 Why you need supportedLocales?**

Because Flutter cannot guess which languages your app supports.
You must list them manually.


**🌍 How does Flutter choose the locale?**

Flutter checks:
	1.	Device locale

	2.	If device locale is in supportedLocales → USE IT

	3.	Otherwise → use the **first** locale in the list

This matches “fallback locale” concept.

**📌 Example: If phone is set to Spanish**

App picks:

.. code-block:: dart 

    Locale('es', 'ES'),

If Spanish is not supported, app falls back to:

.. code-block:: dart 

    Locale('en', 'US')   // first item in the list

**🌟 Minimal Version**

.. code-block:: dart 

    supportedLocales: [
        Locale('en'),
    ],

**⚡ Real Example for your Pashto App**

.. code-block:: dart 

    supportedLocales: const [
        Locale('ps', 'AF'),
        Locale('en', 'US'),
    ],

**✅ Simple Example Showing supportedLocales: in MaterialApp**

supportedLocales: tells Flutter **which languages your app supports.**

Example supports:
	•	English (US)

	•	Spanish (Spain)

	•	Pashto (Afghanistan)

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:flutter_localizations/flutter_localizations.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 REQUIRED for language support
                localizationsDelegates: const [
                    GlobalMaterialLocalizations.delegate,
                    GlobalWidgetsLocalizations.delegate,
                    GlobalCupertinoLocalizations.delegate,
                ],

                // 👇 THIS IS supportedLocales:
                supportedLocales: const [
                    Locale('en', 'US'),  // English
                    Locale('es', 'ES'),  // Spanish
                    Locale('ps', 'AF'),  // Pashto
                ],

                home: const HomePage(),
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                body: Center(
                    child: Text(
                        'supportedLocales Example',
                        style: TextStyle(fontSize: 22),
                    ),
                ),
            );
        }
    }

✅ 21. scrollBehavior:
------------------------

➡️ Allows customizing how scrolling behaves globally (e.g., removing overscroll glow, customizing drag).

**📝 What does scrollBehavior: do?**

Defines how scrolling works in the entire app:

    ✔ Removes overscroll glow

    ✔ Controls touch vs mouse drag

    ✔ Controls scroll physics

    ✔ Allows web-style scrolling

    ✔ Makes macOS/iPad scrollbars visible

    ✔ Allows middle-click scrolling on desktop

**🎯 Example 2: Enable mouse + touch scrolling everywhere**

.. code-block:: dart 

    scrollBehavior: const MaterialScrollBehavior().copyWith(
        dragDevices: {
            PointerDeviceKind.touch,
            PointerDeviceKind.mouse,
        },
    ),

This allows scrolling with:
	•	Touch

	•	Mouse drag

	•	Trackpad

**🌟 Example 3: Always show scrollbars**

.. code-block:: dart 

    scrollBehavior: const MaterialScrollBehavior().copyWith(
    scrollbars: true,
    ),

**🌟 Example 4: iOS Bounce Effect Everywhere**

.. code-block:: dart 

    class BounceScrollBehavior extends MaterialScrollBehavior {
        @override
        ScrollPhysics getScrollPhysics(BuildContext context) {
            return const BouncingScrollPhysics();
        }
    }

Then: 

.. code-block:: dart

    scrollBehavior: BounceScrollBehavior(),

**⚡ Minimal Version**

.. code-block:: dart 

    scrollBehavior: MaterialScrollBehavior(),

**✅ Simple Program Showing scrollBehavior: in MaterialApp**

This program **removes the blue glow effect** when scrolling on Android by using a custom ScrollBehavior.

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    // 👇 Custom Scroll Behavior (removes the glowing overscroll effect)
    class NoGlowScrollBehavior extends ScrollBehavior {

        @override
        Widget buildOverscrollIndicator(BuildContext context, Widget child, ScrollableDetails details) {
            return child; // 👈 No glow
        }
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS scrollBehavior:
                scrollBehavior: NoGlowScrollBehavior(),

                home: const HomePage(),
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text("scrollBehavior Example")),
                body: ListView.builder(
                    itemCount: 30,
                    itemBuilder: (context, index) {
                        return ListTile(
                            title: Text("Item ${index + 1}"),
                        );
                    },
                ),
            );
        }
    }

✅ 22. checkerboardRasterCacheImages:
---------------------------------------

➡️ Shows a checkerboard pattern over images being rasterized (for debug performance analysis).

**📝 What does checkerboardRasterCacheImages do?**

When set to true:

.. code-block:: dart 

   checkerboardRasterCacheImages: true

Flutter overlays a **checkerboard grid** over any raster-cached image.

This helps developers detect:
	•	Which images are being cached

	•	Which UI sections are expensive

	•	If caching is happening too often

	•	If an animation or image is causing jank

**🎯 When should you use this?**

**Only during debugging!**

    ✔ When debugging performance

    ✔ When diagnosing slow/laggy animations

    ✔ When testing UI caching behavior

**NEVER use in production — it adds ugly debug patterns.**

**🌟 Minimal Version**

.. code-block:: dart 

    MaterialApp(
        checkerboardRasterCacheImages: true,
    )

**⚡ Bonus Example: Disable it**

.. code-block:: dart 

    checkerboardRasterCacheImages: false,

(Default is **false.**)

**✅ Simple Example Showing checkerboardRasterCacheImages: in MaterialApp**

This parameter is **only for debugging.**
It shows a **checkerboard pattern** over images that Flutter is caching (raster cache).

Useful when diagnosing:
	•	jank

	•	laggy animations

	•	heavy UI

	•	performance issues

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS checkerboardRasterCacheImages:
                checkerboardRasterCacheImages: true,

                home: const HomePage(),
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text("checkerboardRasterCacheImages Example")),
                body: Center(
                    child: Image.network(
                        'https://flutter.github.io/assets-for-api-docs/assets/widgets/owl.jpg',
                        width: 250,
                    ),
                ),
            );
        }
    }

✅ 23. checkerboardOffscreenLayers:
------------------------------------

➡️ Shows a checkerboard over offscreen layers that are cached by Flutter (debug only).

**✅ Simple Example Showing checkerboardOffscreenLayers: in MaterialApp**

checkerboardOffscreenLayers is used **only for debugging performance.**
It highlights (with a checkerboard pattern) any **offscreen layers** that Flutter is rendering.

Offscreen layers happen when:
	•	Widgets use Opacity

	•	Widgets use clips (ClipRRect, ClipPath)

	•	Widgets are rendered in a separate layer

	•	Complex UI effects require extra drawing steps

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS checkerboardOffscreenLayers:
                checkerboardOffscreenLayers: true,

                home: const HomePage(),
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text("checkerboardOffscreenLayers Example")),

                // 👇 Offscreen rendering happens here because of Opacity + ClipRRect
                body: Center(
                    child: Opacity(
                        opacity: 0.8,
                        child: ClipRRect(
                                borderRadius: BorderRadius.circular(30),
                                child: Image.network(
                                    'https://flutter.github.io/assets-for-api-docs/assets/widgets/owl.jpg',
                                    width: 250,
                            ),
                        ),
                    ),
                ),
            );
        }
    }
 
**📝 What does checkerboardOffscreenLayers: do?**

When set to **true:**

.. code-block:: dart 

    checkerboardOffscreenLayers: true

Flutter overlays a **checkerboard pattern** on UI parts that require **offscreen rendering.**

These are expensive operations and can cause:
	•	Jank

	•	Poor frame rates

	•	Slow animations

	•	Battery usage spikes

This helps developers visually identify UI elements that are too heavy.

**🎯 When offscreen layers happen?**

Common reasons:

**✔ Using Opacity()**

Makes Flutter draw the widget on another layer first.

**✔ Using clipping widgets**
	•	ClipRRect

	•	ClipOval

	•	ClipPath

**✔ Using shadows or masks**

These also cause extra composition layers.

**✔ Complex animations**

Some transitions create offscreen layers temporarily.

⚠️ Important Notes

	•	This is **debug-only**

	•	Do **NOT** use in production
	•	It adds ugly checkerboard patterns

	•	Default value is: **false**

🌟 Minimal Version

.. code-block:: dart 

    MaterialApp(
        checkerboardOffscreenLayers: true,
    );

**⚡ Bonus Example: Turn it OFF**

.. code-block:: dart 

    checkerboardOffscreenLayers: false,

✅ 24. useInheritedMediaQuery:
--------------------------------

➡️ Forces the app to use inherited MediaQuery from its parent. Useful in embedded apps or portals.

**✅ Simple Example Showing useInheritedMediaQuery: in MaterialApp**

useInheritedMediaQuery: tells Flutter whether the **MediaQuery values**
(screen size, brightness, text scale, padding, safe area, etc.)
should come from the **parent widget** instead of being created fresh by MaterialApp.

You mainly use it when your app is inside another Flutter app
(e.g., embedding Flutter inside a native Android/iOS app).

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS useInheritedMediaQuery:
                // It tells MaterialApp to use the existing MediaQuery from above.
                useInheritedMediaQuery: true,

                home: const HomePage(),
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            // Getting MediaQuery info
            final size = MediaQuery.of(context).size;

            return Scaffold(
                appBar: AppBar(title: const Text("useInheritedMediaQuery Example")),
                body: Center(
                    child: Text(
                        "Screen Width: ${size.width}\nScreen Height: ${size.height}",
                        textAlign: TextAlign.center,
                        style: const TextStyle(fontSize: 20),
                    ),
                ),
            );
        }
    }

**📝 What does useInheritedMediaQuery: do?**

**✔ When false (default)**

.. code-block:: dart 

    useInheritedMediaQuery: false

MaterialApp **creates its own MediaQuery** (based on screen size from platform window).

**✔ When true**

.. code-block:: dart

    useInheritedMediaQuery: true

MaterialApp **inherits MediaQuery from parent widget.**

This is important when:

	•	Embedding Flutter inside a native app view

	•	Running Flutter inside another Flutter widget tree

	•	You need consistent text scaling

	•	You want to pass custom safe area insets

**🎯 Why would you use this?**

**1. Embedding Flutter inside parent UI**

If Flutter is inside a small area of a native app,
the parent gives MediaQuery (size, orientation).

**2. Applying custom text scaling**

If parent sets:

.. code-block:: dart 

    MediaQuery(data: MediaQueryData(textScaleFactor: 1.5))

Then all Flutter children can inherit it.

**3. Shared SafeArea settings**

Parent SafeArea can control child widgets.

**🌟 Minimal Example**

.. code-block:: dart 

    MaterialApp(useInheritedMediaQuery: true)

**⚡ Practical Example (Advanced)**

Parent widget provides a custom MediaQuery:

.. code-block:: dart 

    return MediaQuery(
        data: MediaQuery.of(context).copyWith(textScaleFactor: 2.0),
        child: MaterialApp(
            useInheritedMediaQuery: true,
            home: HomePage(),
        ),
    );

Now the entire app uses **large text**, inherited from parent.

✅ 25. restorationScopeId:
---------------------------

➡️ Allows saving and restoring UI state even after the app is killed and restarted.

**✅ Simple Example Showing restorationScopeId: in MaterialApp**

restorationScopeId enables **state restoration**, meaning your app can
automatically remember data when closed and restore it when reopened.

This example restores the counter value even after the app is killed.

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS GIVES THE APP A RESTORATION SCOPE
                restorationScopeId: 'app_root',

                home: const CounterPage(),
            );
        }
    }

    // 👇 A page that restores state
    class CounterPage extends StatefulWidget {
        const CounterPage({super.key});

        @override
        State<CounterPage> createState() => _CounterPageState();
    }

    class _CounterPageState extends State<CounterPage> with RestorationMixin {
        // 👇 Restorable counter value
        final RestorableInt _counter = RestorableInt(0);

        @override
        String? get restorationId => 'counter_page';

        @override
        void restoreState(RestorationBucket? oldBucket, bool initialRestore) {
            registerForRestoration(_counter, 'counter_value');
        }

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('restorationScopeId Example')),
                body: Center(
                    child: Text(
                        'Counter: ${_counter.value}',
                        style: const TextStyle(fontSize: 24),
                    ),
                ),
                floatingActionButton: FloatingActionButton(
                    child: const Icon(Icons.add),
                    onPressed: () {
                        setState(() {
                            _counter.value++;
                        });
                    },
                ),
            );
        }
    }

**📝 What is restorationScopeId:?**

This ID enables **State Restoration** in your app.

It tells Flutter:

“This MaterialApp is the root of all restore-able widgets.”

**🎯 What does State Restoration mean?**

When the app is:
	•	closed

	•	killed by OS

	•	moved to background

	•	reopened

Flutter restores:
	•	counters

	•	scroll positions

	•	text fields

	•	tab selections

	•	navigation stacks

If programmed using **RestorationMixin.**

**🌟 How it works in this example?**

**When user taps + button**

Counter becomes **1, 2, 3…**

If the app is killed

(or closed manually)

When reopened

Counter value is restored to the same number.

Because:

.. code-block:: dart 

    restorationScopeId: 'app_root';

And the page uses:

.. code-block:: dart 

    RestorationMixin & RestorableInt

**⚡ Minimal Version**

.. code-block:: dart 

    MaterialApp(
        restorationScopeId: 'root',
    )

**🧠 When should you use state restoration?**

    ✔ Apps with forms

    ✔ Multi-step processes

    ✔ Checkout screens

    ✔ Data-entry apps

    ✔ Navigation-heavy apps

    ✔ When your app must remember state after being closed

✅ 26. onGenerateTitle:
------------------------

➡️ Instead of setting a static title, you can generate it dynamically (like reading from locale or preferences).

**✅ Simple Example Showing onGenerateTitle: in MaterialApp**

onGenerateTitle: lets you **generate the app title dynamically at runtime**

instead of using a fixed title: string.

This title appears in:
	•	Android **Recent Apps** list

	•	Window title (Desktop apps)

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS onGenerateTitle:
                onGenerateTitle: (context) {
                    // You can generate the title dynamically here
                    return "Welcome, Kaftarya!";
                },

                home: const HomePage(),
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                body: Center(
                    child: Text(
                        'onGenerateTitle Example',
                        style: TextStyle(fontSize: 22),
                    ),
                ),
            );
        }
    }

**📝 What does onGenerateTitle: do?**

It is a **callback function** that returns a **string.**

Flutter uses this title to display:
	•	App name in **Android Recent Apps**

	•	Window title on **Flutter Desktop**

	•	App metadata in some OS environments

**🎯 Why use onGenerateTitle: instead of title:?**

**✔ Create title based on system language (Localization)**

.. code-block:: dart 

    onGenerateTitle: (context) => AppLocalizations.of(context)!.appName,

**✔ Create title based on user settings**

Example: “Hello John”, “Kaftarya Admin”, etc.

**✔ Use data or logic to compute the title**

**🌍 Example: Localized Title**

If you use localization (.arb):

.. code-block:: dart 

    onGenerateTitle: (context) {
        return AppLocalizations.of(context)!.appTitle;
    }

**⚡ Minimal Version**

.. code-block:: dart 

    onGenerateTitle: (_) => "My App",

**🚀 Summary**

+-----------------------+-----------------------------------+-------------------------------------------------+
| Parameter             | Type                              | Purpose                                         |
+=======================+===================================+=================================================+
| title:                | String                            | Fixed app title                                 |
+-----------------------+-----------------------------------+-------------------------------------------------+
| onGenerateTitle:      | Function                          | Dynamic/app-generated title                     |
+-----------------------+-----------------------------------+-------------------------------------------------+

✅ 27. actions:
----------------

➡️ Maps Intents to Actions for app-wide accessibility, keyboard shortcuts, and command handling.

**✅ Simple Program Explaining actions: in MaterialApp**

actions: allows you to define **global shortcut actions**, often used with shortcuts: for keyboard shortcuts.

It is mainly used on:
	•	Desktop apps

	•	Web apps

	•	Apps using keyboard input

**✔ Example: Press SPACE BAR to change background color**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:flutter/services.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 GLOBAL KEYBOARD SHORTCUTS
                shortcuts: const {
                    LogicalKeySet(LogicalKeyboardKey.space): ActivateIntent(),
                },

                // 👇 ACTIONS: what happens when shortcuts trigger
                actions: {
                    ActivateIntent: CallbackAction(
                        onInvoke: (intent) {
                            print("SPACE key pressed globally!");
                            return null;
                        },
                    ),
                },

                home: const HomePage(),
            );
        }
    }

    class HomePage extends StatefulWidget {
        const HomePage({super.key});

        @override
        State<HomePage> createState() => _HomePageState();
    }

    class _HomePageState extends State<HomePage> {
        Color color = Colors.white;

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text("actions: Example")),
                body: Container(
                    color: color,
                    child: Center(
                        child: ElevatedButton(
                            child: const Text("Press SPACE to change color"),
                            onPressed: () {
                                setState(() {
                                    color = Colors.primaries[
                                        DateTime.now().millisecond % Colors.primaries.length];
                                });
                            },
                        ),
                    ),
                ),
            );
        }
    }

**📝 What does actions: do?**

It defines **what happens** when a shortcut is triggered.

In the example:
	•	shortcuts: → maps SPACE key to an ActivateIntent

	•	actions: → what to do when that intent fires

**🎯 Real uses for actions::**

    ✔ Keyboard shortcuts (Ctrl+C, Ctrl+S, Enter)

    ✔ Desktop compatibility

    ✔ Accessibility actions

    ✔ Menu shortcuts

    ✔ Global hotkeys in Flutter apps

**🌟 Minimal Version**

.. code-block:: dart 

    actions: {
        ActivateIntent: CallbackAction(onInvoke: (_) => print("activated")),
    }

✅ 28. onGenerateInitialRoutes:
--------------------------------

➡️ Creates the initial navigation stack when the app starts, instead of using just initialRoute.

**✅ Simple Program for onGenerateInitialRoutes: in MaterialApp**

onGenerateInitialRoutes: lets you define **custom initial routes** when the app starts.

This example shows how the app chooses which screen to show first depending on logic.

**✔ Example: If userLoggedIn = true → go to Dashboard**

**✔ Otherwise → show LoginPage**



.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        final bool userLoggedIn = false; // change to true to test

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS onGenerateInitialRoutes:
                onGenerateInitialRoutes: (String initialRoute) {
                    if (userLoggedIn) {
                        return [
                            MaterialPageRoute(builder: (_) => const DashboardPage())
                        ];
                    } else {
                        return [
                            MaterialPageRoute(builder: (_) => const LoginPage())
                        ];
                    }
                },

                routes: {
                    '/login': (_) => const LoginPage(),
                    '/dashboard': (_) => const DashboardPage(),
                },
            );
        }
    }

    class LoginPage extends StatelessWidget {
        const LoginPage({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                body: Center(child: Text("Login Page")),
            );
        }
    }

    class DashboardPage extends StatelessWidget {
        const DashboardPage({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                body: Center(child: Text("Dashboard Page")),
            );
        }
    }

**📝 What does onGenerateInitialRoutes: do?**

	•	It decides **which routes to load first**

	•	Runs before any navigation happens

	•	Allows custom app-launch behavior

	•	Useful for:
        •	login redirection

        •	onboarding flow

        •	saved state restoration

        •	deep links

✅ 29. shortcuts:
------------------

➡️ Maps keyboard keys (or gestures) to Intents, supporting shortcut features for desktop or web apps.

**✅ Simple Program for shortcuts: in MaterialApp**

shortcuts: maps keyboard keys to **Intents.**

Here pressing **CTRL + N** prints a message.

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:flutter/services.dart';

    void main() => runApp(const MyApp());

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS shortcuts:
                shortcuts: const {
                    SingleActivator(LogicalKeyboardKey.keyN, control: true):
                        NewIntent(),
                },

                actions: {
                    NewIntent: CallbackAction<NewIntent>(
                        onInvoke: (intent) {
                            print("CTRL + N pressed!");
                            return null;
                        },
                    ),
                },

                home: const HomePage(),
            );
        }
    }

    class NewIntent extends Intent {
        const NewIntent();
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                body: Center(child: Text("Press CTRL + N")),
            );
        }
    }

**✔ What does shortcuts: do?**
	•	Listens to keyboard combinations.

	•	Maps keyboard key → Intent.

✅ 30. scaffoldMessengerKey:
------------------------------

**✅ Simple Example Showing scaffoldMessengerKey: in MaterialApp**

scaffoldMessengerKey: allows you to show **SnackBars from anywhere —**
even **without BuildContext**, even outside widgets (e.g., services, controllers).

We will create:

	•	**a global ScaffoldMessenger key**

	•	a button that shows a SnackBar **using the key**

(NOT using ScaffoldMessenger.of(context))

**✔ Complete Working Example**

.. code-block:: dart 

    import 'package:flutter/material.dart';

    // 👇 Create a global key for ScaffoldMessenger
    final GlobalKey<ScaffoldMessengerState> messengerKey =
        GlobalKey<ScaffoldMessengerState>();

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS scaffoldMessengerKey:
                scaffoldMessengerKey: messengerKey,

                home: const HomePage(),
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text("scaffoldMessengerKey Example")),
                body: Center(
                    child: ElevatedButton(
                        onPressed: () {
                            // 👇 Showing snackbar WITHOUT context
                            messengerKey.currentState!.showSnackBar(
                                const SnackBar(
                                    content: Text("Hello from scaffoldMessengerKey!"),
                                ),
                            );
                        },
                        child: const Text("Show SnackBar"),
                    ),
                ),
            );
        }
    }

**📝 What is scaffoldMessengerKey:?**

It gives your app a **global ScaffoldMessenger controller** so you can show:

	•	SnackBars

	•	MaterialBanners

	•	Hide existing SnackBars

**from anywhere,** not only from widgets.

**🎯 Why use scaffoldMessengerKey?**

Because this works:

.. code-block:: dart 

    messengerKey.currentState!.showSnackBar(...)

Even inside:
	•	ViewModels

	•	Controllers

	•	Services

	•	Bloc / Provider

	•	Background logic

	•	Async callbacks

**You don’t need:**

.. code-block:: dart 

    ScaffoldMessenger.of(context)

Which requires a widget context.

---------------------------------------------------------------------------------------------------

**🌟 Minimal Version**

.. code-block:: dart 

    MaterialApp(
        scaffoldMessengerKey: GlobalKey<ScaffoldMessengerState>(),
    )

**⚡ Real Use Cases**

	•	Showing SnackBar when a **network request fails**

	•	Showing SnackBar from **API service class**

	•	Showing messages from **Bloc/Provider**

	•	Showing global messages such as:

	•	Login success

	•	Error sending request

	•	Data saved

	•	Payment failed

✅ 31. showPerformanceOverlay:
--------------------------------

**✅ Simple Example Showing showPerformanceOverlay: in MaterialApp**

The **performance overlay** is a built-in Flutter debugging tool.
It shows **FPS, GPU usage, UI thread performance**, and frame rendering stats.

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS showPerformanceOverlay:
                showPerformanceOverlay: true,

                home: const HomePage(),
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text("showPerformanceOverlay Example")),
                body: const Center(
                    child: Text(
                        "Performance Overlay is Visible\nLook at the top-right corner!",
                        textAlign: TextAlign.center,
                        style: TextStyle(fontSize: 20),
                    ),
                ),
            );
        }
    }

**📝 What does showPerformanceOverlay: do?**

When set to **true:**

.. code-block:: dart 

    showPerformanceOverlay: true

**✔ Top graph: UI thread**

Shows how fast Flutter is building frames
(should stay under 16ms for 60fps).

**✔ Bottom graph: GPU thread**

Shows how fast Flutter is painting frames.

If bars go above the line → **frame drops or jank.**

🎯 What is it used for?

**This is a debug tool, used to check:**

	•	FPS (frames per second)

	•	UI lag

	•	GPU overload

	•	Slow animations

	•	Rendering problems

	•	Expensive widgets

	•	jank issues

This is extremely helpful for game-like apps or complex animations.

**⚠️ Important Notes**

	•	Only for debugging

	•	Do NOT use in production

	•	Adds performance graphs on screen

	•	Default is: false

**🌟 Minimal Version**

.. code-block:: dart 

    MaterialApp(showPerformanceOverlay: true)

✅ 32. key:
------------

**✅ Now: Simple program for key: parameter in MaterialApp**

The key: parameter is used to identify this instance of MaterialApp in the widget tree.

It is useful when:

	•	Rebuilding UI

	•	Reloading widgets

	•	Controlling widget identity

	•	Testing

**🧪 Simple Example Showing key: in MaterialApp**

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(
            // 👇 THIS IS THE key: PARAMETER
            MyApp(key: const Key('MyMaterialApp')),
        );
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});   // receives the key

        @override
        Widget build(BuildContext context) {
                return const MaterialApp(
                home: HomePage(),
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                body: Center(
                    child: Text(
                        'key: parameter example',
                        style: TextStyle(fontSize: 22),
                    ),
                ),
            );
        }
    }

**🧠 What does key: actually do?**

key: helps Flutter:

	•	Identify a widget **uniquely**

	•	Decide when to **reuse** or **rebuild** a widget

	•	Improve **performance**

	•	Maintain **state correctly**

Example:

.. code-block:: dart 

    MaterialApp(
        key: const ValueKey('main_app'),
    )

If you don’t change the key → Flutter **keeps the same app**
If you change the key → Flutter **forces a rebuild**

**✅ Super simple explanation**

**key: is an ID for a widget**

Like a student ID number:

	•	Not visible

	•	Used internally

	•	Helps Flutter track things


✅ 33. onNavigationNotification:
---------------------------------

**✅ Simple program to describe onNavigationNotification:**

This listens to **navigation events** (page changes).

It’s like a “listener” for navigation.

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                debugShowCheckedModeBanner: false,

                // 👇 THIS IS onNavigationNotification
                onNavigationNotification: (notification) {
                    print("📢 Navigation happened!");

                    // You can check the depth of the navigation stack
                    print("Current stack depth: ${notification.depth}");

                    return true; // allow notification to continue
                },

                routes: {
                    '/': (context) => const HomePage(),
                    '/second': (context) => const SecondPage(),
                },
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
                        child: const Text("Go to Second Page"),
                        onPressed: () {
                            Navigator.pushNamed(context, '/second');
                        },
                    ),
                ),
            );
        }
    }

    class SecondPage extends StatelessWidget {
        const SecondPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Second')),
                body: Center(
                    child: ElevatedButton(
                        child: const Text("Go Back"),
                        onPressed: () => Navigator.pop(context),
                    ),
                ),
            );
        }
    }

**📝 What is onNavigationNotification?**

It runs **every time navigation changes,** like:

	•	Page opened

	•	Page closed

	•	Page popped

	•	Page pushed

You can use it for:

    ✅ Logging

    ✅ Analytics

    ✅ Tracking user flow

    ✅ Debugging

✅ 34. debugShowMaterialGrid:
-------------------------------

**✅ Simple program for debugShowMaterialGrid: in MaterialApp**

This shows a **material design grid** on top of your app for UI alignment checking (debugging only).

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(MaterialApp(
            // 👇 THIS IS debugShowMaterialGrid:
            debugShowMaterialGrid: true,

            home: const Scaffold(
                body: Center(
                        child: Text(
                        "Material Grid ON",
                        style: TextStyle(fontSize: 24),
                    ),
                ),
            ),
        ));
    }

**🧠 What happens?**
	•	You will see a **grid overlay**

	•	It helps with:

	•	Alignment

	•	Spacing

	•	Layout precision

	•	Used only in **design & debugging**

	•	Never use in production


✅ 35. showSemanticsDebugger:
------------------------------

**🔍 What is showSemanticsDebugger?**

showSemanticsDebugger is used for **accessibility debugging.**

	•	When set to **true ➜** Flutter shows an **overlay box** on every widget.

	•	The overlay displays **semantic information** like:

	•	Label

	•	Role (button, text, image, etc.)

	•	Value

	•	Accessibility hints

This is mainly used to **debug apps for visually-impaired users** who use screen readers such as:

	•	TalkBack (Android)

	•	VoiceOver (iOS)

**👀 What you will SEE on screen**

When you run the app with:

.. code-block:: dart 

    showSemanticsDebugger: true,

You will notice:

✅ Colored rectangles around widgets

✅ Labels on Text and Buttons

✅ Hierarchy of widget accessibility tree

This shows how **screen readers “see” your app.**

**✅ When should you use this?**

Use it when:
	•	You are building an accessible app

	•	Testing for blind users

	•	Improving UX for screen readers

Set it back to false (or remove it) for production:

.. code-block:: dart 

    showSemanticsDebugger: false,

**✅ Simple program to describe showSemanticsDebugger:**

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                // ✅ This turns ON the Semantics Debugger overlay
                showSemanticsDebugger: true,

                home: Scaffold(
                    appBar: AppBar(
                        title: const Text('Semantics Demo'),
                    ),
                    body: const Center(
                        child: Column(
                            mainAxisAlignment: MainAxisAlignment.center,
                            children: [
                                Text('Hello Kaftarya'),
                                SizedBox(height: 20),
                                ElevatedButton(
                                    onPressed: null,
                                    child: Text('Press Me'),
                                ),
                            ],
                        ),
                    ),
                ),
            );
        }
    }

✅ 36. localeListResolutionCallback:
--------------------------------------

**🔍 What is localeListResolutionCallback?**

This parameter is used to:

✅ Detect the **user’s device language(s)**

✅ Compare them with your **app’s supported languages**

✅ Choose the **best matching language for your app**

It runs **automatically** when the app starts and receives:

.. code-block:: dart 

    (List<Locale>? deviceLocales, Iterable<Locale> supportedLocales)

**In simple words:**

“Flutter hands you the phone’s language list and your app’s language list — now YOU choose which one to use.”

**🧠 Example Scenario**

Assume:
	•	Phone language = Spanish (es_ES)

	•	Your supported languages are: English, Spanish, French

This function will:

.. code-block:: bash 

    MATCH FOUND → Spanish is selected

If phone language = German (de_DE)…

.. code-block:: bash 

    NO MATCH → Default to English

**✅ When should you use this?**

You use localeListResolutionCallback when:

	•	Supporting **multiple languages**

	•	Want to **customize fallback logic**

	•	Want full control over language selection

**📌 Key Difference**

+------------------------------------+--------------------------------------------------+
| Feature                            | Purpose                                          |
+====================================+==================================================+
| locale                             | Force one fixed language                         |
+------------------------------------+--------------------------------------------------+
| supportedLocales                   | List of allowed languages                        |
+------------------------------------+--------------------------------------------------+
| localeResolutionCallback           | Handles only one device locale                   |
+------------------------------------+--------------------------------------------------+
| ✅ localeListResolutionCallback    | Handles multiple device locales (best choice)    |
+------------------------------------+--------------------------------------------------+

**✅ Simple program to describe localeListResolutionCallback:**

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                // 🌍 Languages your app supports
                supportedLocales: const [
                    Locale('en', 'US'),
                    Locale('es', 'ES'),
                    Locale('fr', 'FR'),
                ],

                // ✅ This is the main focus of your question
                localeListResolutionCallback: (List<Locale>? deviceLocales,
                    Iterable<Locale> supportedLocales) {

                        print("Device locales: $deviceLocales");
                        print("Supported locales: $supportedLocales");

                        // Example logic: If device is Spanish → return Spanish
                        for (var locale in deviceLocales!) {
                        for (var supported in supportedLocales) {
                            if (locale.languageCode == supported.languageCode) {
                                return supported;
                            }
                        }
                    }

                    // If nothing matches → fallback to English (US)
                    return const Locale('en', 'US');
                },

                home: const Scaffold(
                    body: Center(
                        child: Text(
                            "Hello Kaftarya",
                            style: TextStyle(fontSize: 24),
                        ),
                    ),
                ),
            );
        }
    }

✅ 37. themeAnimationDuration:
-------------------------------

**🔍 What is themeAnimationDuration?**

themeAnimationDuration controls:

**How long the animation takes when switching between themes**

.. code-block:: dart 

    themeAnimationDuration: Duration(seconds: 2)

This means:
	•	When the theme changes (light ↔ dark),

	•	The animation will take **2 seconds** to complete

**🧠 Try changing the duration**

Try these:

.. code-block:: dart 

    themeAnimationDuration: Duration(milliseconds: 200)

👉 Very fast animation

.. code-block:: dart 

    themeAnimationDuration: Duration(seconds: 5)

👉 Very slow animation (clear smooth transition)

**👀 What you will see**

When you press **Change Theme:**

    ✅ Background color slowly changes

    ✅ Text color transitions smoothly

    ✅ AppBar color animates

Not instant jump – it’s **animated.**

**✅ When to use this**

Use it when:
	•	You allow users to switch **light / dark mode**

	•	You want a **smooth professional animation effect**

	•	You want control over animation speed

⚠️ Important Note

This only works when:

.. code-block:: dart 

    themeMode is changed at runtime

If the theme is fixed, this animation won’t apply.

**✅ Simple program to describe themeAnimationDuration:**

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatefulWidget {
        const MyApp({super.key});

        @override
        State<MyApp> createState() => _MyAppState();
    }

    class _MyAppState extends State<MyApp> {
        bool isDarkMode = false;

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                // ✅ This controls how fast the theme change animates
                themeAnimationDuration: const Duration(seconds: 2),

                // Light theme
                theme: ThemeData.light(),

                // Dark theme
                darkTheme: ThemeData.dark(),

                // Switch between them
                themeMode: isDarkMode ? ThemeMode.dark : ThemeMode.light,

                home: Scaffold(
                    appBar: AppBar(
                        title: const Text('Theme Animation Demo'),
                    ),
                    body: Center(
                        child: ElevatedButton(
                            onPressed: () {
                                setState(() {
                                    isDarkMode = !isDarkMode;
                                });
                            },
                            child: const Text('Change Theme'),
                        ),
                    ),
                ),
            );
        }
    }

✅ 38. themeAnimationCurve:
----------------------------

**🔍 What is themeAnimationCurve?**

themeAnimationCurve defines **how the animation behaves over time.**

In simple words:

It controls HOW the animation moves, not how long it takes.

Example

.. code-block:: dart 

    themeAnimationCurve: Curves.easeInOut

This means:

	•	Starts slow ✅

	•	Gets fast in the middle ✅

	•	Ends slow ✅

**🎯 Try other curves**

You can change the curve to see different animations:

.. code-block:: dart 

    themeAnimationCurve: Curves.linear        // constant speed
    themeAnimationCurve: Curves.bounceOut     // bouncy effect
    themeAnimationCurve: Curves.easeIn        // slow → fast
    themeAnimationCurve: Curves.fastOutSlowIn // very smooth

Each one gives a **different feel** to the theme change.

**✅ Quick Difference Table**

+-----------------------------+---------------------------------------+
| Parameter                   | Controls                              |
+=============================+=======================================+
| themeAnimationDuration      | How long the animation takes          |
+-----------------------------+---------------------------------------+
| ✅ themeAnimationCurve      | How it moves during that time         |
+-----------------------------+---------------------------------------+

So if you set:

.. code-block:: dart 

    Duration(seconds: 2)
    Curves.bounceInOut

→ The animation takes **2 seconds and bounces while changing**

**✅ When to use this**

Use it when:
	•	You care about **UX / UI quality**

	•	You want natural looking transitions

	•	You want your app to feel premium and smooth

**✅ Simple program to describe themeAnimationCurve:**

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatefulWidget {
        const MyApp({super.key});

        @override
        State<MyApp> createState() => _MyAppState();
    }

    class _MyAppState extends State<MyApp> {
        bool isDarkMode = false;

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                // ✅ Duration of the animation
                themeAnimationDuration: const Duration(seconds: 2),

                // ✅ Shape/style of the animation
                themeAnimationCurve: Curves.easeInOut,

                theme: ThemeData.light(),
                darkTheme: ThemeData.dark(),

                themeMode: isDarkMode ? ThemeMode.dark : ThemeMode.light,

                home: Scaffold(
                    appBar: AppBar(title: const Text('Theme Curve Demo')),
                    body: Center(
                        child: ElevatedButton(
                            onPressed: () {
                                setState(() {
                                    isDarkMode = !isDarkMode;
                                });
                            },
                            child: const Text('Change Theme'),
                        ),
                    ),
                ),
            );
        }
    }

✅ 39. themeAnimationStyle:
----------------------------

**🔍 What is themeAnimationStyle in simple words?**

It controls **WHAT TYPE of animation** is used when the theme changes.

+------------------------------------+-----------------------------------------+
| Value                              | Meaning                                 |
+====================================+=========================================+
| AnimationStyle.noAnimation         | Switch theme instantly (no movement)    |
+------------------------------------+-----------------------------------------+
| AnimationStyle.standard            | Smooth, normal theme animation ✅       |
+------------------------------------+-----------------------------------------+
| AnimationStyle.custom              | You define your own style               |
+------------------------------------+-----------------------------------------+

**🎯 Try this experiment**

Change:

.. code-block:: dart 

    themeAnimationStyle: AnimationStyle.noAnimation,

Now when you press **Change Theme:**

✅ The screen changes instantly
❌ No fade / smooth effect

Then switch to:

.. code-block:: dart 

    themeAnimationStyle: AnimationStyle.standard,

**✅ Relationship with others**

+------------------------+---------------------------------+
| Parameter              | Controls                        |
+========================+=================================+
| themeAnimationDuration | How long it takes               |
+------------------------+---------------------------------+
| themeAnimationCurve    | How it moves                    |
+------------------------+---------------------------------+
| ✅ themeAnimationStyle | What type of animation          |
+------------------------+---------------------------------+

**✅ Simple example using themeAnimationStyle**

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatefulWidget {
        const MyApp({super.key});

        @override
        State<MyApp> createState() => _MyAppState();
    }

    class _MyAppState extends State<MyApp> {
        bool isDark = false;

        @override
        Widget build(BuildContext context) {
            return MaterialApp(
                // ✅ NEW PARAMETER: Theme Animation Style
                themeAnimationStyle: AnimationStyle.standard,

                // These two still work with it
                themeAnimationDuration: const Duration(seconds: 2),
                themeAnimationCurve: Curves.easeInOut,

                theme: ThemeData.light(),
                darkTheme: ThemeData.dark(),

                themeMode: isDark ? ThemeMode.dark : ThemeMode.light,

                home: Scaffold(
                    appBar: AppBar(
                        title: const Text("Theme Animation Style"),
                    ),
                    body: Center(
                        child: ElevatedButton(
                            onPressed: () {
                                setState(() {
                                    isDark = !isDark;
                                });
                            },
                            child: const Text("Change Theme"),
                        ),
                    ),
                ),
            );
        }
    }