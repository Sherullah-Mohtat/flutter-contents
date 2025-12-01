Scaffold 
========

**Scaffold** is a **layout structure** provided by the **Material Design library** that serves as the **basic visual framework** for building the UI of an app screen.

**Scaffold(**
    
    1.	**appBar:** The top app bar of the scaffold.

    2.	**body:** The primary content of the scaffold.

    3.	**floatingActionButton:** A button that floats above the body content.

    4.	**floatingActionButtonLocation:** This controls where the floating action button is placed.

    5.	**floatingActionButtonAnimator:** This controls the animation of the floating action button.

    6.	**persistentFooterButtons:** A set of buttons that are always visible at the bottom.

    7.	**drawer:** A drawer that slides in from the side for navigation.

    8.	**endDrawer:** A drawer that slides in from the opposite side.

    9.	**bottomNavigationBar:** A bar displayed at the bottom for navigation.

    10.	**bottomSheet:** A persistent bottom sheet.

    11.	**backgroundColor:** The background color of the scaffold.

    12.	**resizeToAvoidBottomInset:** Whether the scaffold should adjust when the keyboard appears.

    13.	**primary:** Whether this scaffold is the primary scaffold in the app.

    14.	**drawerScrimColor:** The color of the scrim that is overlaid when a drawer is open.

    15.	**extendBody:** Whether the body should extend behind the bottom navigation bar.

    16.	**extendBodyBehindAppBar:** Whether the body should extend behind the app bar.


**)** 

✅1.appBar:
-------------

Here is a **very simple Flutter program** that shows what the **appBar: parameter in Scaffold** does.

It adds a bar at the **top of the screen** that can contain a title, icons, and actions.

**✅ Example: Using appBar: in Scaffold**

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
                home: Scaffold(
                    // ✅ appBar parameter
                    appBar: AppBar(
                        title: const Text('My First AppBar'),
                        centerTitle: true,
                        backgroundColor: Colors.blue,
                    ),

                    body: const Center(
                        child: Text(
                            'Hello, World!',
                            style: TextStyle(fontSize: 24),
                        ),
                    ),
                ),
            );
        }
    }

**🧠 What this program teaches you**

+------------------------------+--------------------------------+
| Part                         | Meaning                        |
+==============================+================================+
| Scaffold                     | Main page layout               |
|                              |                                |
| appBar:                      | The top bar of the screen      |
|                              |                                |
| AppBar()                     | Creates the top bar            |
|                              |                                |
| title:                       | Text shown in the bar          |
|                              |                                |
| centerTitle:                 | Centers the text               |    
|                              |                                |
| backgroundColor:             | Changes bar color              |
+------------------------------+--------------------------------+

When you run this app, you will see:

    ✅ A **blue bar at the top**

    ✅ Text **“My First AppBar”** in the center

    ✅ “Hello, World!” in the middle of the screen

**🔁 Remove AppBar to see the difference**

If you **remove the appBar part**, the top bar disappears:

.. code-block:: dart

    Scaffold(
        body: Center(
            child: Text('No AppBar here'),
        ),
    )

This shows the **importance of the appBar: parameter** inside Scaffold.

====================================================================================================================================================

✅2.body:
----------

Here is a **very simple Flutter program** that explains the **body: parameter in Scaffold.**

The body is the **main content area of your screen** — everything you want to show in the middle of the page goes inside it.

**✅ Example: Using body: in Scaffold**

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
                home: Scaffold(

                    // ✅ App bar is optional
                    appBar: AppBar(
                        title: const Text('Scaffold Body Example'),
                    ),

                    // ✅ This is the BODY parameter
                    body: Center(
                        child: Text(
                            'This is the BODY of the Scaffold',
                            style: TextStyle(fontSize: 22),
                        ),
                    ),
                ),
            );
        }
    }

**🧠 What this program teaches**

+-------------------------------+-------------------------------+
| Part                          | Meaning                       |
+===============================+===============================+
| Scaffold                      | Main layout of the page       |
|                               |                               |
| body:                         | The main content area         |
|                               |                               |
| Center                        | Centers the content           |
|                               |                               |
| Text                          | Displays text inside the body |
+-------------------------------+-------------------------------+

When you run this program, you will see:

    ✅ AppBar at the top

    ✅ Text in the **center of the screen**

    ✅ That text is inside the body

This shows that **everything inside the screen is placed using body:.**

**🔁 Change Body to a Different Widget**

Now change the body to a Container:

.. code-block:: dart 

    body: Container(
        color: Colors.orange,
        child: const Center(
            child: Text(
                'New Body Content',
                style: TextStyle(fontSize: 24, color: Colors.white),
            ),
        ),
    ),

Now the **whole screen becomes orange.**

This proves:
    **➡️ body controls the entire main screen area**

**🔑 Important Concept**

In Scaffold:

.. code-block:: dart 

    Scaffold(
        appBar: ...
        body: ...      //← MAIN SCREEN CONTENT
    )

The body: can contain **ANY widget:**

	•	Text

	•	Column

	•	Row

	•	ListView

	•	Container

	•	Stack

	•	Image

	•	Custom widget

✅3.floatingActionButton:
--------------------------

Here is a **very simple Flutter program** that shows what the **floatingActionButton: parameter in Scaffold** does.

The floatingActionButton is the **round button that floats at the bottom-right corner** of the screen by default.

**✅ Simple Example: floatingActionButton in Scaffold**

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
                home: Scaffold(
                    appBar: AppBar(
                        title: const Text('Floating Button Example'),
                    ),

                    body: const Center(
                        child: Text(
                            'Tap the floating button!',
                            style: TextStyle(fontSize: 22),
                        ),
                    ),

                    // ✅ floatingActionButton parameter
                    floatingActionButton: FloatingActionButton(
                        onPressed: () {
                            print("Floating button pressed!");
                        },
                        child: const Icon(Icons.add),
                    ),
                ),
            );
        }
    }

**🧠 What this program teaches**

+----------------------------+------------------------------------+
| Part                       | Meaning                            |
+============================+====================================+
| floatingActionButton:      | Adds a floating button             |
|                            |                                    |
| FloatingActionButton       | The widget for the button          |
|                            |                                    |
| onPressed                  | What happens when you tap it       |
|                            |                                    |
| Icon(Icons.add)            | The + sign on the button           |
+----------------------------+------------------------------------+

When you run this app, you will see:

    ✅ A **round “+” button** at the bottom-right

    ✅ When you tap it, a message prints in the console

    ✅ The button floats ABOVE the body content

**🔁 Change the Button Position**

You can move the button to the **center bottom** like this:

.. code-block:: dart 

    floatingActionButtonLocation: FloatingActionButtonLocation.centerFloat,

Full change:

.. code-block:: dart 

    floatingActionButtonLocation: FloatingActionButtonLocation.centerFloat,

Now the button is **centered at the bottom.**

**🔑 Important Concept**

The floatingActionButton is mainly used for:

    ✅ Add

    ✅ Create

    ✅ Upload

    ✅ New message

    ✅ Scan

    ✅ Quick actions

It is commonly used in apps like **WhatsApp, Gmail, Maps.**

--------------------------------------------------------------------------------------------------------------------------------------------------

**✅ Simple Example: floatingActionButton with MaterialApp.router()**

.. code-block:: dart
        
    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        // ✅ Router configuration
        static final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',
                    builder: (context, state) => const HomePage(),
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                debugShowCheckedModeBanner: false,
                routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(

                appBar: AppBar(
                    title: const Text('FAB with MaterialApp.router'),
                ),

                body: const Center(
                    child: Text(
                        'This page uses MaterialApp.router()',
                        style: TextStyle(fontSize: 20),
                    ),
                ),

                // ✅ floatingActionButton parameter
                floatingActionButton: FloatingActionButton(
                    onPressed: () {
                        print("Floating Action Button Pressed!");
                    },
                    child: const Icon(Icons.add),
                ),

                // ✅ Button position
                floatingActionButtonLocation: FloatingActionButtonLocation.endFloat,
            );
        }
    }

**📌 Important: Add this to pubspec.yaml**

Because this uses **GoRouter,** you must add this dependency:

.. code-block:: dart 

    dependencies:
        flutter:
            sdk: flutter
        go_router: ^14.0.0

Then run:

.. code-block:: bash 

    flutter pub get

**🧠 What this program teaches**

+----------------------------------------+--------------------------------------+
| Part                                   | Meaning                              | 
+========================================+======================================+                
| MaterialApp.router()                   | Used for navigation with Router API  |
+----------------------------------------+--------------------------------------+
| routerConfig:                          | Controls all app routes              |
+----------------------------------------+--------------------------------------+
| Scaffold                               | The page layout                      |
+----------------------------------------+--------------------------------------+ 
| floatingActionButton:                  | Floating button on the page          |
+----------------------------------------+--------------------------------------+
| FloatingActionButtonLocation.endFloat  | Bottom-right location                |
+----------------------------------------+--------------------------------------+

When you run it, you will see:

    ✅ AppBar

    ✅ A text message in the middle

    ✅ A **floating + button** at bottom right

Press the button → It prints a message in the console.

=================================================================================================================================================

✅4.floatingActionButtonLocation:
----------------------------------

Here is a very **simple Flutter program** that shows how the **floatingActionButtonLocation: parameter in Scaffold** works, and it uses **MaterialApp.router()** exactly as you requested.

This example lets you **see the position change clearly**.

**✅ Simple Program: floatingActionButtonLocation with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        // Router configuration
        static final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',
                    builder: (context, state) => const HomePage(),
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                debugShowCheckedModeBanner: false,
                routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
    const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(
                    title: const Text('FAB Location Example'),
                ),

                body: const Center(
                    child: Text(
                        'Look at the position of the button',
                        style: TextStyle(fontSize: 20),
                    ),
                ),

                floatingActionButton: FloatingActionButton(
                    onPressed: () {
                    print("FAB clicked");
                    },
                    child: const Icon(Icons.navigation),
                ),

                // ✅ Change position using floatingActionButtonLocation
                floatingActionButtonLocation:
                    FloatingActionButtonLocation.centerFloat,
            );
        }
    }

**🧠 What this program teaches**

The **important line** is:

.. code-block:: dart 

    floatingActionButtonLocation: FloatingActionButtonLocation.centerFloat,

This moves the button to the **BOTTOM CENTER** of the screen instead of the default bottom-right.

**📍 Try these positions (just change ONE line)**

+-----------------------------------------+----------------------------------------------+
| Location Code                           | Button Position                              |
+=========================================+==============================================+
| FloatingActionButtonLocation.endFloat   | Bottom Right (default)                       |
+-----------------------------------------+----------------------------------------------+
| FloatingActionButtonLocation.startFloat | Bottom Left                                  |
+-----------------------------------------+----------------------------------------------+
| FloatingActionButtonLocation.centerFloat| Bottom Center                                |
+-----------------------------------------+----------------------------------------------+
| FloatingActionButtonLocation.endTop     | Top Right                                    |
+-----------------------------------------+----------------------------------------------+
| FloatingActionButtonLocation.centerTop  | Top Center                                   |
+-----------------------------------------+----------------------------------------------+

Example change:

.. code-block:: dart 

    floatingActionButtonLocation: FloatingActionButtonLocation.endTop,

Now the button moves to the **top-right corner.**

**📌 Dependency Required**

Don’t forget in pubspec.yaml:

.. code-block:: yaml

    dependencies:
        flutter:
            sdk: flutter
        go_router: ^14.0.0

Run:

.. code-block:: bash 

    flutter pub get
   
=================================================================================================================================================

✅5.floatingActionButtonAnimator:
----------------------------------

Here is a **very simple Flutter program** that demonstrates the **floatingActionButtonAnimator: parameter of Scaffold**, using **MaterialApp.router()** as you requested.

This parameter controls **how the Floating Action Button animates** when it changes position (for example: from bottom-right to center).

To make the animation visible, I use a **stateful page and a button tap to change location.**

**✅ Simple Program: floatingActionButtonAnimator with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        // Router configuration
        static final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',
                    builder: (context, state) => const HomePage(),
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                debugShowCheckedModeBanner: false,
                routerConfig: _router,
            );
        }
    }

    class HomePage extends StatefulWidget {
        const HomePage({super.key});

        @override
        State<HomePage> createState() => _HomePageState();
    }

    class _HomePageState extends State<HomePage> {
        // Toggle between two positions
        FloatingActionButtonLocation _location = FloatingActionButtonLocation.endFloat;

        void _changePosition() {
            setState(() {
            _location = _location == FloatingActionButtonLocation.endFloat
                ? FloatingActionButtonLocation.centerFloat
                : FloatingActionButtonLocation.endFloat;
            });
        }

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(
                    title: const Text('FAB Animator Example'),
                ),

                body: const Center(
                    child: Text(
                        'Tap the button to change its position',
                        style: TextStyle(fontSize: 18),
                    ),
                ),

                floatingActionButton: FloatingActionButton(
                    onPressed: _changePosition,
                    child: const Icon(Icons.swap_horiz),
                ),

                // ✅ This changes the position
                floatingActionButtonLocation: _location,

                // ✅ This controls HOW it animates
                floatingActionButtonAnimator:
                    FloatingActionButtonAnimator.scaling,
            );
        }
    }

**🧠 What this program teaches**

The **important new line** is:

.. code-block:: dart 

    floatingActionButtonAnimator: FloatingActionButtonAnimator.scaling,

This means:

    ✅ When the FAB moves, it **scales (shrinks and grows)** during the animation.

There are **2 built-in animators** in Flutter:

+-----------------------------------------+----------------------------------------------+
| Animator                                | Effect                                       |
+=========================================+==============================================+
| FloatingActionButtonAnimator.scaling ✅ | Default scale animation                      |
+-----------------------------------------+----------------------------------------------+
| FloatingActionButtonAnimator.noAnimation| No animation                                 |
+-----------------------------------------+----------------------------------------------+

Try changing this line:

.. code-block:: dart 

    floatingActionButtonAnimator: FloatingActionButtonAnimator.noAnimation,

Now the button will **jump instantly** without smooth animation.

**🧩 Why this is important**

The floatingActionButtonAnimator is used when:

    ✅ FAB position changes

    ✅ Screen layout changes

    ✅ Scaffold updates its geometry

    ✅ You want smooth UI transitions

This is especially useful in **professional apps** with animated UI.

**📌 Dependency Reminder**

In your pubspec.yaml:

.. code-block:: yaml 

    dependencies:
        flutter:
            sdk: flutter
        go_router: ^14.0.0

Then run:

.. code-block:: bash 

    flutter pub get


✅6.persistentFooterButtons:
-----------------------------

Here is a **very simple Flutter program** that demonstrates the **persistentFooterButtons: parameter in Scaffold,** using **MaterialApp.router()** as you requested.

persistentFooterButtons creates **fixed buttons at the bottom** of the screen that stay visible even when the body scrolls.

**✅ Simple Program: persistentFooterButtons with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        // Router configuration
        static final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',
                    builder: (context, state) => const HomePage(),
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                debugShowCheckedModeBanner: false,
                routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(
                    title: const Text('Persistent Footer Example'),
                ),

                body: const Center(
                    child: Text(
                        'Buttons below are fixed (persistent)',
                        style: TextStyle(fontSize: 18),
                    ),
                ),

                // ✅ persistentFooterButtons
                persistentFooterButtons: [
                    TextButton(
                        onPressed: () {
                            print("Cancel pressed");
                        },
                        child: const Text('Cancel'),
                    ),

                    ElevatedButton(
                        onPressed: () {
                            print("Save pressed");
                        },
                        child: const Text('Save'),
                    ),
                ],
            );
        }
    }

**🧠 What this program teaches**

+------------------------------------+----------------------------------------+
| Part                               | Meaning                                |
+====================================+========================================+
| persistentFooterButtons:           | Creates fixed buttons at the bottom    |
+------------------------------------+----------------------------------------+
| TextButton                         | A simple flat button                   |
+------------------------------------+----------------------------------------+
| ElevatedButton                     | A raised button                        |
+------------------------------------+----------------------------------------+
| Position                           | Stays at the bottom of the screen      |
+------------------------------------+----------------------------------------+

When you run the app, you will see:

    ✅ Two buttons at the **bottom of the screen**

    ✅ “Cancel” and “Save”

    ✅ They stay visible all the time

**🔁 Try adding more buttons**

You can add more:

.. code-block:: dart 

    persistentFooterButtons: [
        IconButton(onPressed: () {}, icon: Icon(Icons.home)),
        IconButton(onPressed: () {}, icon: Icon(Icons.favorite)),
        IconButton(onPressed: () {}, icon: Icon(Icons.settings)),
    ],

They will stay in a **horizontal row at the bottom.**

**📌 Dependency Reminder**

In pubspec.yaml:

.. code-block:: yaml 

    dependencies:
        flutter:
            sdk: flutter
        go_router: ^14.0.0

Run: 

.. code-block:: bash 

    flutter pub get

==================================================================================================================================================

✅7.drawer:
------------

Here is a **very simple Flutter program** that demonstrates the **drawer: parameter of Scaffold**, using **MaterialApp.router()** exactly as you requested.

The drawer is the **sliding menu that opens from the left side.**

**✅ Simple Program: drawer with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        // Router configuration
        static final GoRouter _router = GoRouter(
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

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                debugShowCheckedModeBanner: false,
                routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(

                appBar: AppBar(
                    title: const Text('Drawer Example'),
                ),

                // ✅ Drawer parameter
                drawer: Drawer(
                    child: ListView(
                        padding: EdgeInsets.zero,
                        children: [

                            const DrawerHeader(
                                decoration: BoxDecoration(color: Colors.blue),
                                child: Text(
                                    'My Menu',
                                    style: TextStyle(color: Colors.white, fontSize: 24),
                                ),
                            ),

                            ListTile(
                                leading: const Icon(Icons.home),
                                title: const Text('Home'),
                                onTap: () {
                                    Navigator.pop(context); // close drawer
                                },
                            ),

                            ListTile(
                                leading: const Icon(Icons.info),
                                title: const Text('About'),
                                onTap: () {
                                    Navigator.pop(context); // close drawer
                                    context.go('/about');   // go to About page
                                },
                            ),
                        ],
                    ),
                ),

                body: const Center(
                    child: Text(
                    'Swipe from left or tap the menu icon',
                    style: TextStyle(fontSize: 18),
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
                appBar: AppBar(
                    title: const Text('About Page'),
                ),
                body: const Center(
                    child: Text(
                        'You navigated using Drawer!',
                        style: TextStyle(fontSize: 20),
                    ),
                ),
            );
        }
    }

**🧠 What this program teaches**

+-------------------------------+------------------------------------+
| Part                          | Meaning                            |
+===============================+====================================+
| drawer:                       | Adds a left-side sliding menu      |
+-------------------------------+------------------------------------+
| Drawer()                      | The actual drawer widget           |
+-------------------------------+------------------------------------+
| DrawerHeader                  | Top section of drawer              |
+-------------------------------+------------------------------------+
| ListTile                      | Menu item inside drawer            |
+-------------------------------+------------------------------------+
| context.go('/about')          | Go to another page                 |
+-------------------------------+------------------------------------+
| Navigator.pop(context)        | Close the drawer                   |
+-------------------------------+------------------------------------+

When you run this app:

    ✅ You will see a **menu icon (☰) in the AppBar**

    ✅ Tap it → the **drawer slides from the left**

    ✅ Tap **About** → it opens a new page

**📌 Pubspec dependency (Important)**

In pubspec.yaml, you must have:

.. code-block:: yaml 

    dependencies:
        flutter:
            sdk: flutter
        go_router: ^14.0.0

Then:

.. code-block:: bash 

    flutter pub get

==================================================================================================================================================

✅8.endDrawer:
---------------

Here is a **very simple Flutter program** that demonstrates the **endDrawer: parameter in Scaffold**, using **MaterialApp.router()** exactly as you requested.

endDrawer is a drawer that **slides from the RIGHT side** of the screen (opposite of drawer, which comes from the left).

**✅ Simple Program: endDrawer with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        // Router configuration
        static final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',
                    builder: (context, state) => const HomePage(),
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                debugShowCheckedModeBanner: false,
                routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(
                    title: const Text('End Drawer Example'),

                    // ✅ Button to open the END drawer (right side)
                    actions: [
                        Builder(
                            builder: (context) => IconButton(
                                icon: const Icon(Icons.menu),
                                onPressed: () {
                                    Scaffold.of(context).openEndDrawer();
                                },
                            ),
                        ),
                    ],
                ),

                body: const Center(
                    child: Text(
                        'Tap the menu icon on the RIGHT',
                        style: TextStyle(fontSize: 18),
                    ),
                ),

                // ✅ endDrawer parameter (right-side drawer)
                endDrawer: Drawer(
                    child: ListView(
                        padding: EdgeInsets.zero,
                        children: const [

                            DrawerHeader(
                                decoration: BoxDecoration(color: Colors.green),
                                child: Text(
                                    'Right Menu',
                                    style: TextStyle(color: Colors.white, fontSize: 24),
                                ),
                            ),

                            ListTile(
                                leading: Icon(Icons.settings),
                                title: Text('Settings'),
                            ),

                            ListTile(
                                leading: Icon(Icons.person),
                                title: Text('Profile'),
                            ),
                        ],
                    ),
                ),
            );
        }
    }

**🧠 What this program teaches**

+--------------------------------------+--------------------------------------+
| Part                                 | Meaning                              |
+======================================+======================================+
| endDrawer:                           | Drawer that opens from right side    |
+--------------------------------------+--------------------------------------+
| Drawer()                             | The side menu widget                 |
+--------------------------------------+--------------------------------------+
| actions:                             | Right side buttons in the AppBar     |
+--------------------------------------+--------------------------------------+
| Scaffold.of(context).openEndDrawer() | Opens the right drawer               |
+--------------------------------------+--------------------------------------+

When you run the app:

    ✅ You see a **menu icon on the top-right**

    ✅ Tap it → **drawer slides from the right side**

    ✅ Contains “Settings” and “Profile”

**🔑 Difference Between drawer and endDrawer**

+-----------------------------+-------------------------------------+
| drawer                      | endDrawer                           |
+=============================+=====================================+
| Opens from LEFT             | Opens from RIGHT                    |
+-----------------------------+-------------------------------------+
| Common for main menu        | Used for secondary menu             |
+-----------------------------+-------------------------------------+
| Uses menu icon automatically| Needs manual open button            |
+-----------------------------+-------------------------------------+

**📌 Dependency Reminder**

In pubspec.yaml:

.. code-block:: yaml 

    dependencies:
        flutter:
            sdk: flutter
        go_router: ^14.0.0

Then run:

.. code-block:: bash 

    flutter pub get


✅9.bottomNavigationBar:
-------------------------

Here is a **very simple Flutter program** that demonstrates the bottomNavigationBar: parameter in Scaffold, using MaterialApp.router() as you requested.

The bottomNavigationBar creates a **navigation bar at the bottom** of the screen to switch between pages.

**✅ Simple Program: bottomNavigationBar with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        // ✅ Router configuration
        static final GoRouter _router = GoRouter(
            initialLocation: '/',
            routes: [
                GoRoute(
                    path: '/',
                    builder: (context, state) => const HomePage(),
                ),
                GoRoute(
                    path: '/search',
                    builder: (context, state) => const SearchPage(),
                ),
                GoRoute(
                    path: '/profile',
                    builder: (context, state) => const ProfilePage(),
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                debugShowCheckedModeBanner: false,
                routerConfig: _router,
            );
        }
    }

    // ---------------- HOME PAGE ----------------
    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Home')),

                body: const Center(
                    child: Text(
                        'Home Screen',
                        style: TextStyle(fontSize: 22),
                    ),
                ),

                // ✅ bottomNavigationBar
                bottomNavigationBar: BottomNavigationBar(
                    currentIndex: 0,
                    onTap: (index) {
                    if (index == 0) context.go('/');
                    if (index == 1) context.go('/search');
                    if (index == 2) context.go('/profile');
                    },

                    items: const [
                        BottomNavigationBarItem(
                            icon: Icon(Icons.home),
                            label: 'Home',
                        ),
                        BottomNavigationBarItem(
                            icon: Icon(Icons.search),
                            label: 'Search',
                        ),
                        BottomNavigationBarItem(
                            icon: Icon(Icons.person),
                            label: 'Profile',
                        ),
                    ],
                ),
            );
        }
    }

    // ---------------- SEARCH PAGE ----------------
    class SearchPage extends StatelessWidget {
        const SearchPage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Search')),
                body: const Center(
                    child: Text(
                        'Search Screen',
                        style: TextStyle(fontSize: 22),
                    ),
                ),

                bottomNavigationBar: BottomNavigationBar(
                    currentIndex: 1,
                    onTap: (index) {
                        if (index == 0) context.go('/');
                        if (index == 1) context.go('/search');
                        if (index == 2) context.go('/profile');
                    },
                    items: const [
                        BottomNavigationBarItem(icon: Icon(Icons.home), label: 'Home'),
                        BottomNavigationBarItem(icon: Icon(Icons.search), label: 'Search'),
                        BottomNavigationBarItem(icon: Icon(Icons.person), label: 'Profile'),
                    ],
                ),
            );
        }
    }

    // ---------------- PROFILE PAGE ----------------
    class ProfilePage extends StatelessWidget {
        const ProfilePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Profile')),
                body: const Center(
                    child: Text(
                        'Profile Screen',
                        style: TextStyle(fontSize: 22),
                    ),
                ),

                bottomNavigationBar: BottomNavigationBar(
                    currentIndex: 2,
                    onTap: (index) {
                    if (index == 0) context.go('/');
                    if (index == 1) context.go('/search');
                    if (index == 2) context.go('/profile');
                    },
                    items: const [
                        BottomNavigationBarItem(icon: Icon(Icons.home), label: 'Home'),
                        BottomNavigationBarItem(icon: Icon(Icons.search), label: 'Search'),
                        BottomNavigationBarItem(icon: Icon(Icons.person), label: 'Profile'),
                    ],
                ),
            );
        }
    }

**🧠 What this program teaches**

+--------------------------------+--------------------------------+
| Part                           | Meaning                        |
+--------------------------------+--------------------------------+
| bottomNavigationBar:           | Shows a bar at the bottom      |
+--------------------------------+--------------------------------+
| BottomNavigationBar            | The widget that contains tabs  |
+--------------------------------+--------------------------------+
| BottomNavigationBarItem        | Each button (icon + label)     |
+--------------------------------+--------------------------------+
| context.go()                   | Switches page using router     |
+--------------------------------+--------------------------------+
| currentIndex                   | Highlights selected tab        |
+--------------------------------+--------------------------------+


When you run it, you will see:

    ✅ Navigation bar at bottom

    ✅ Three tabs: **Home, Search, Profile**

    ✅ Tapping a tab changes the page

**📌 Dependency Reminder**

In your pubspec.yaml:

.. code-block:: yaml 

    dependencies:
        flutter:
            sdk: flutter
        go_router: ^14.0.0

Then run:

.. code-block:: bash 

    flutter pub get

==================================================================================================================================================

✅10.bottomSheet:
------------------

Here is a **very simple Flutter program** that demonstrates the **bottomSheet: parameter in Scaffold**, using MaterialApp.router() as you requested.

The bottomSheet is a **panel attached to the bottom of the screen** that is always visible (unlike showModalBottomSheet, which appears and disappears).

**✅ Simple Program: bottomSheet with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        // Router configuration
        static final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',
                    builder: (context, state) => const HomePage(),
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                debugShowCheckedModeBanner: false,
                routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(
                    title: const Text('Bottom Sheet Example'),
                ),

                body: const Center(
                    child: Text(
                        'Look at the bottom of the screen ↓',
                        style: TextStyle(fontSize: 20),
                    ),
                ),

                // ✅ bottomSheet parameter
                bottomSheet: Container(
                    height: 80,
                    width: double.infinity,
                    color: Colors.blueGrey,
                    alignment: Alignment.center,
                    child: const Text(
                        'I am a Persistent Bottom Sheet',
                        style: TextStyle(fontSize: 18, color: Colors.white),
                    ),
                ),
            );
        }
    }

**🧠 What this program teaches**

+----------------------------------+------------------------------------+
| Part                             | Meaning                            |
+==================================+====================================+
| bottomSheet:                     | Adds a fixed sheet at the bottom   |
+----------------------------------+------------------------------------+
| Container                        | Used as the sheet UI               |
+----------------------------------+------------------------------------+ 
| height:                          | Controls how tall the sheet is     |
+----------------------------------+------------------------------------+
| width: double.infinity           | Makes it full width                |
+----------------------------------+------------------------------------+
| Always visible                   | Stays on screen forever            |
+----------------------------------+------------------------------------+

When you run this app:

    ✅ You see a **bar-like panel at the bottom**

    ✅ It stays visible all the time

    ✅ The main content is above it

This is the **bottomSheet: parameter of Scaffold** in action.

**🔁 Change the height & color**

Try this:

.. code-block:: dart 

    bottomSheet: Container(
        height: 150,
        color: Colors.orange,
        child: const Center(
            child: Text('Bigger Bottom Sheet'),
        ),
    ),

Now the bottom sheet is bigger and orange.

**❗ Important Difference**

+----------------------------+--------------------------+
| bottomSheet:               | showModalBottomSheet()   |
+----------------------------+--------------------------+
| Always visible             | Opens when needed        |
+----------------------------+--------------------------+
| Fixed                      | Temporary                |
+----------------------------+--------------------------+ 
| Part of Scaffold           | Appears over UI          |
+----------------------------+--------------------------+
| Can’t drag to close        | Can be dismissed         |
+----------------------------+--------------------------+

**📌 Dependency Reminder**

In pubspec.yaml:

.. code-block:: yaml 

    dependencies:
        flutter:
            sdk: flutter
        go_router: ^14.0.0

Then run:

.. code-block:: bash 

    flutter pub get

==================================================================================================================================================

✅11.backgroundColor:
-----------------------

Here is a **very simple Flutter program** that demonstrates the **backgroundColor: parameter in Scaffold,** using **MaterialApp.router()** as you requested.

The backgroundColor changes the **full screen background color** of the Scaffold.

**✅ Simple Program: backgroundColor with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        // Router configuration
        static final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',
                    builder: (context, state) => const HomePage(),
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                debugShowCheckedModeBanner: false,
                routerConfig: _router,
            );
        }
    }

    // ---------------- HOME PAGE ----------------
    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(

                // ✅ This is the important line
                backgroundColor: Colors.lightBlue.shade100,

                appBar: AppBar(
                    title: const Text('Background Color Example'),
                ),

                body: const Center(
                    child: Text(
                    'The Scaffold background is LIGHT BLUE',
                    style: TextStyle(fontSize: 18),
                    ),
                ),
            );
        }
    }

**🧠 What this program teaches**

+------------------------------+--------------------------------------------+
| Part                         | Meaning                                    |
+==============================+============================================+
| backgroundColor:             | Sets the Scaffold’s screen color           |
+------------------------------+--------------------------------------------+
| Colors.lightBlue.shade100    | Light blue background                      |
+------------------------------+--------------------------------------------+
| body:                        | Content is placed on top of the background |
+------------------------------+--------------------------------------------+

When you run this app, you will see:

    ✅ A **light blue background**

    ✅ AppBar at the top

    ✅ Text in the center

This color is controlled ONLY by:

.. code-block:: dart 

    backgroundColor: Colors.lightBlue.shade100,

**🔁 Try different colors**

Change this line to test different colors:

.. code-block:: dart 

    backgroundColor: Colors.green,

.. code-block:: dart 

    backgroundColor: Colors.black,

.. code-block:: dart 

    backgroundColor: Colors.orangeAccent,

You’ll see the screen change immediately.

**📌 Dependency Reminder**

In your pubspec.yaml:

.. code-block:: yaml 

    dependencies:
        flutter:
            sdk: flutter
        go_router: ^14.0.0

Then run:

.. code-block:: bash 

    flutter pub get

===============================================================================================================================================

✅12.resizeToAvoidBottomInset:
-------------------------------

Here is a **very simple Flutter program** that demonstrates the **resizeToAvoidBottomInset: parameter in Scaffold,** using **MaterialApp.router()** just like you asked.

This parameter controls **whether the screen resizes when the keyboard opens.**

**✅ Simple Program: resizeToAvoidBottomInset with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        // Router configuration
        static final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',
                    builder: (context, state) => const HomePage(),
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                debugShowCheckedModeBanner: false,
                routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(

                // ✅ IMPORTANT PARAMETER
                resizeToAvoidBottomInset: false,

                appBar: AppBar(
                    title: const Text('Keyboard Resize Example'),
                ),

                body: Padding(
                    padding: const EdgeInsets.all(20),
                    child: Column(
                        children: const [

                            Text(
                                'Tap the text field to open the keyboard',
                                style: TextStyle(fontSize: 18),
                            ),

                            SizedBox(height: 20),

                            TextField(
                                decoration: InputDecoration(
                                    border: OutlineInputBorder(),
                                    labelText: 'Enter something...',
                                ),
                            ),

                            SizedBox(height: 300),

                            Text(
                                'I stay in the same place',
                                style: TextStyle(fontSize: 18),
                            ),
                        ],
                    ),
                ),
            );
        }
    }

**🧠 What this program teaches**

The **key line** is:

.. code-block:: dart 

    resizeToAvoidBottomInset: false,

This means:

+--------------------+-------------------------------------------+
| Value              | What happens when keyboard opens          |
+====================+===========================================+
| true (default)     | Screen moves up to avoid the keyboard ✅  |
+--------------------+-------------------------------------------+
| false              | Screen does NOT move ❌                   |
+--------------------+-------------------------------------------+

In this example:

    ✅ Keyboard opens

    ✅ **Screen DOES NOT resize**

    ✅ Content may be hidden by keyboard

**🔁 Try changing it to true**

Change this:

.. code-block:: dart 

    resizeToAvoidBottomInset: true,

Now when the keyboard opens:

    ✅ The screen **moves up**

    ✅ The text field stays visible

This is the **default behavior** in most forms.

**📌 When to use false?**

You use:

.. code-block:: dart 

    resizeToAvoidBottomInset: false,

When:

    ✅ You don’t want layout shifting

    ✅ You are using your own scroll system

    ✅ Full-screen UI or games

    ✅ Fixed layout screens

**📌 Dependency Reminder**

In your pubspec.yaml:

.. code-block:: yaml 

    dependencies:
        flutter:
            sdk: flutter
        go_router: ^14.0.0

Then run:

.. code-block:: bash 

    flutter pub get

================================================================================================================================================

✅13.primary:
--------------

Here is a **very simple Flutter program** that demonstrates the **primary: parameter in Scaffold**, using **MaterialApp.router()** (just like you asked).

The primary parameter tells Flutter **whether this Scaffold should align itself to the top system area (status bar / notch) or not.**

**✅ Simple Program: primary with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        // Router configuration
        static final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',
                    builder: (context, state) => const HomePage(),
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                debugShowCheckedModeBanner: false,
                routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(

                // ✅ IMPORTANT PARAMETER
                primary: false,

                appBar: AppBar(
                    title: const Text('Primary Parameter Example'),
                ),

                body: const Center(
                    child: Text(
                        'Set primary: false in Scaffold',
                        style: TextStyle(fontSize: 18),
                    ),
                ),
            );
        }
    }

**🧠 What this program teaches**

The key line is:

.. code-block:: dart 

    primary: false,

+----------------+-----------------------------------------+
| Value          | Behavior                                |
+================+=========================================+
| true (default) | Respects top safe area (status bar). ✅ |
+----------------+-----------------------------------------+
| false          | Does not reserve top padding. ❌        |
+----------------+-----------------------------------------+

When primary: false:

    ✅ The Scaffold does not automatically insert padding at the top

    ✅ Content can go **behind the status bar / notch**

    ✅ Useful for full-screen designs

On some devices, this is very noticeable near the top.

**🔁 Try changing it to true**

Change to:

.. code-block:: dart 

    primary: true,

Now:

    ✅ The screen respects the status bar

    ✅ Automatically adds safe padding

This is the **normal default behavior.**

**🔑 Why is this useful?**

You usually set:

.. code-block:: dart 

    primary: false

When:

    ✅ You want full control of padding

    ✅ You use SafeArea manually

    ✅ You design full-screen elements (games, videos, splash)

**📌 Dependency Reminder**

In your pubspec.yaml:

.. code-block:: yaml 

    dependencies:
        flutter:
            sdk: flutter
        go_router: ^14.0.0

Then run:

.. code-block:: bash 

    flutter pub get

=========================================================================================================================

✅14.drawerScrimColor:
-----------------------

Here is a **very simple Flutter program** that demonstrates the **drawerScrimColor: parameter in Scaffold**, using **MaterialApp.router()** as you requested.

The drawerScrimColor changes the **transparent dark overlay color** that appears on the screen **when the drawer is opened**.

**✅ Simple Program: drawerScrimColor with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        // Router configuration
        static final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',
                    builder: (context, state) => const HomePage(),
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                debugShowCheckedModeBanner: false,
                routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(

                // ✅ IMPORTANT PARAMETER
                drawerScrimColor: Colors.red.withOpacity(0.5),

                appBar: AppBar(
                    title: const Text('Drawer Scrim Color'),
                ),

                // ✅ Normal Drawer (LEFT SIDE)
                drawer: Drawer(
                    child: ListView(
                        padding: EdgeInsets.zero,
                        children: const [

                            DrawerHeader(
                                decoration: BoxDecoration(color: Colors.blue),
                                child: Text(
                                    'Menu',
                                    style: TextStyle(color: Colors.white, fontSize: 24),
                                ),
                            ),

                            ListTile(
                                leading: Icon(Icons.home),
                                title: Text('Home'),
                            ),

                            ListTile(
                                leading: Icon(Icons.settings),
                                title: Text('Settings'),
                            ),
                        ],
                    ),
                ),

                body: const Center(
                    child: Text(
                        'Open the drawer to see the RED overlay',
                        style: TextStyle(fontSize: 18),
                    ),
                ),
            );
        }
    }

**🧠 What this program teaches**

The **important line is:**

.. code-block:: dart 

    drawerScrimColor: Colors.red.withOpacity(0.5),

This means:

    ✅ When drawer opens

    ✅ The background gets a **red transparent overlay**

    ✅ Instead of the default black/gray color

Try opening the drawer and you will see:

🔴 Red shaded screen behind the drawer

**🔁 Try different colors**

Change this line:

.. code-block:: dart 

    drawerScrimColor: Colors.green.withOpacity(0.4),

.. code-block:: dart 

    drawerScrimColor: Colors.blue.withOpacity(0.6),

.. code-block:: dart 

    drawerScrimColor: Colors.transparent,

If you use: 

.. code-block:: dart 

    drawerScrimColor: Colors.transparent,

Then **no dimming / overlay happens at all.**

**🔑 Why use drawerScrimColor?**

It is useful when:

    ✅ You want custom UI design

    ✅ You want brand color behind drawer

    ✅ You want no overlay at all

    ✅ You want light or dark mode matching

**📌 Dependency Reminder**

In your pubspec.yaml add:

.. code-block:: yaml 

    dependencies:
        flutter:
            sdk: flutter
        go_router: ^14.0.0

Then run:

.. code-block:: bash 

    flutter pub get

===============================================================================================================================

✅15.extendBody:
-----------------

Here is a very **simple Flutter program** that demonstrates the **extendBody: parameter in Scaffold,** using **MaterialApp.router()** as you requested.

The extendBody parameter tells Flutter **whether the body should extend behind the bottom widgets, such as the bottomNavigationBar.**

**✅ Simple Program: extendBody with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        // Router configuration
        static final GoRouter _router = GoRouter(
            routes: [
                GoRoute(
                    path: '/',
                    builder: (context, state) => const HomePage(),
                ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                debugShowCheckedModeBanner: false,
                routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(

                // ✅ IMPORTANT PARAMETER
                extendBody: true,

                appBar: AppBar(
                    title: const Text('extendBody Example'),
                ),

                body: Container(
                    color: Colors.orange,
                    child: const Center(
                        child: Text(
                            'The orange body extends behind bottom bar',
                            style: TextStyle(fontSize: 18, color: Colors.white),
                            textAlign: TextAlign.center,
                        ),
                    ),
                ),

                // ✅ Bottom Navigation Bar
                bottomNavigationBar: BottomAppBar(
                    color: Colors.black,
                    child: Container(
                        height: 60,
                        alignment: Alignment.center,
                        child: const Text(
                            'Bottom Bar',
                            style: TextStyle(color: Colors.white, fontSize: 18),
                        ),
                    ),
                ),
            );
        }
    }

**🧠 What this program teaches**

The key line is:

.. code-block:: dart 

    extendBody: true,

+------------------+---------------------------------+
| Value            | Result                          |
+==================+=================================+
| false (default)  | Body stops **above** bottom bar |
+------------------+---------------------------------+
| true ✅          | Body goes **behind** bottom bar |
+------------------+---------------------------------+

When extendBody: true:

    ✅ The **orange body** continues **under the black bar**

    ✅ You can see the color through the transparent parts

    ✅ Useful for modern, layered UI design

**🔁 Compare with false**

Change:

.. code-block:: dart 

    extendBody: false,

Now:

    ✅ The orange area stops before the bar

    ✅ The bar sits on top of a blank area

    ✅ Classic layout style

This helps you understand the difference clearly.

**📌 When to use extendBody**

Use it when:

    ✅ You use BottomAppBar + FAB

    ✅ You want transparent bottom bars

    ✅ You design glass / blur UI

    ✅ You need layered visual effects

**📌 Dependency Reminder**

In your pubspec.yaml:

.. code-block:: yaml 

    dependencies:
        flutter:
            sdk: flutter
        go_router: ^14.0.0

Then run:

.. code-block:: bash 

    flutter pub get

==============================================================================================================================

✅16.extendBodyBehindAppBar:
-----------------------------

Here is a very **simple Flutter program** that demonstrates the **extendBodyBehindAppBar: parameter in Scaffold,** using **MaterialApp.router()** as you requested.

This parameter allows the **body to extend behind (under) the AppBar.**

**✅ Simple Program: extendBodyBehindAppBar with MaterialApp.router()**

.. code-block:: dart 

    import 'package:flutter/material.dart';
    import 'package:go_router/go_router.dart';

    void main() {
        runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        // ✅ Router configuration
        static final GoRouter _router = GoRouter(
            routes: [
            GoRoute(
                path: '/',
                builder: (context, state) => const HomePage(),
            ),
            ],
        );

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                debugShowCheckedModeBanner: false,
                routerConfig: _router,
            );
        }
    }

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(

                // ✅ IMPORTANT PARAMETER
                extendBodyBehindAppBar: true,

                appBar: AppBar(
                    title: const Text('Behind AppBar'),
                    backgroundColor: Colors.black.withOpacity(0.5), // Transparent look
                ),

                body: Container(
                    decoration: const BoxDecoration(
                        gradient: LinearGradient(
                            colors: [Colors.purple, Colors.orange],
                            begin: Alignment.topCenter,
                            end: Alignment.bottomCenter,
                        ),
                    ),
                    child: const Center(
                        child: Text(
                            'Body is behind the AppBar',
                            style: TextStyle(fontSize: 22, color: Colors.white),
                        ),
                    ),
                ),
            );
        }
    }

**🧠 What this program teaches**

The key line is:

.. code-block:: dart 

    extendBodyBehindAppBar: true,

+-----------------+-------------------------+
| Value           | Result                  |
+=================+=========================+
| false (default) | Body starts below AppBar|
+-----------------+-------------------------+
| true ✅         | Body goes behind AppBar |
+-----------------+-------------------------+

In this example:

    ✅ The **gradient body goes behind the AppBar**

    ✅ The AppBar is semi-transparent

    ✅ You can see colors under the AppBar

This is commonly used for:
	•	Image header effects

	•	Transparent AppBar designs

	•	Modern UI / full-screen UI

	•	Parallax effects

**🔁 Compare with false**

Try changing:

.. code-block:: yaml 
    
    dependencies:
        flutter:
            sdk: flutter
        go_router: ^14.0.0

  Then run:

  .. code-block:: bash 

    flutter pub get
