Center 
======

**Center** widget is one of the simplest yet most commonly used layout widgets. The Center widget **aligns its child widget to the center** of the available space — both **vertically and horizontally.**


**Center(**

    1.	**key:** → Identifies this widget uniquely in the widget tree.

    2.	**widthFactor:** → Multiplies the child’s width to determine the Center’s width.

    3.	**heightFactor:** → Multiplies the child’s height to determine the Center’s height.

    4.	**child:** → The widget you want to place in the center.

**)**

**🧱 How to Call:**

.. code-block:: dart 
    
    Center(
    key: ValueKey('centerBox'),
    widthFactor: 2.0,
    heightFactor: 2.0,
    child: Text('Kaftarya'),
    )

✅1.key:
--------

**✅ Fixed, minimal example**

**Goal:** use MaterialApp.router() + RouterConfig + key: in Center.

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    // ------------------ App ------------------

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
            routerConfig: _router, // ✅ use RouterConfig
            );
        }
    }

    // ------------------ Router Config ------------------

    // Only routerDelegate – no routeInformationParser / provider
    final RouterConfig<Object> _router = RouterConfig<Object>(
        routerDelegate: _SimpleRouterDelegate(),
    );

    // ------------------ Router Delegate ------------------

    class _SimpleRouterDelegate extends RouterDelegate<Object> with ChangeNotifier, PopNavigatorRouterDelegateMixin<Object> {
        @override
        final GlobalKey<NavigatorState> navigatorKey = GlobalKey<NavigatorState>();

        @override
        Widget build(BuildContext context) {
            return Navigator(
                key: navigatorKey,
                pages: const [
                    MaterialPage(child: HomePage()),
                ],
            );
        }

        @override
        Future<void> setNewRoutePath(Object configuration) async {
            // Nothing to do for this simple example.
        }
    }

    // ------------------ Home Page ------------------

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Center key: example')),
                body: const Center(
                    key: ValueKey('main_center_widget'), // 🔑 key: parameter in Center
                    child: Text('Hello from Center widget'),
                ),
            );
        }
    }

This is the part we are talking about:

.. code-block:: dart 

        body: const Center(
            key: ValueKey('main_center_widget'),
            child: Text('Hello from Center widget'),
        ),

**1. What is key in Flutter? (simple meaning)**

A **key **is just an **ID card for a widget.**

It tells Flutter:

“This widget is THIS one. Don’t mix it with others.”

Flutter rebuilds the screen very fast. When it does that, it needs a way to **recognize which widget is which.** The key helps Flutter do that.

Without a key → Flutter guesses

With a key → Flutter knows exactly

**2. What type of key did you use?**

You used:

.. code-block:: dart 

    ValueKey('main_center_widget')

That means:

	•	The value = 'main_center_widget'

	•	Flutter uses that value to recognise the **Center widget**

	•	As long as this value is the same, Flutter knows this is the same widget

Think of it like:

+---------------------+---------------------+
| Real life           | Flutter             |
+=====================+=====================+
| Student ID          | Key                 |
+---------------------+---------------------+
| Name on card        | Value in ValueKey   |
+---------------------+---------------------+
| Person              | Widget              |
+---------------------+---------------------+

**3. Why do you need a key here?**

Right now, your app only has **one page** and **one Center**, so technically the app will still work **without a key.**

But you added it to **learn and practice:**

.. code-block:: dart 

    key: ValueKey('main_center_widget')

This will become very important when:

    ✅ You have multiple pages

    ✅ You have Lists (ListView / GridView)

    ✅ You move widgets around

    ✅ You update / replace widgets

    ✅ You use animations

In your **restaurant app / Flutter project**, you WILL need keys a lot.

**4. What happens when the page rebuilds?**

Your router uses:

.. code-block:: dart 

    MaterialPage(child: HomePage()),

When something changes, Flutter rebuilds HomePage.

Then it looks at widget tree and says:

    “Okay, I see a Center widget. Does it look like an old one?”

It checks the key:

.. code-block:: dart 

    ValueKey('main_center_widget')

If the key is the same:

	•	Flutter **keeps the 상태 (state)** if needed

	•	Flutter doesn’t destroy and recreate unnecessarily

	•	Keeps animations stable

If key changed or is missing:

	•	Flutter may **destroy the old widget**

	•	Create a new one

	•	Lose state / animation progress

**5. Test it yourself (important for learning)**

Try changing the key to something else:

.. code-block:: dart 

    key: ValueKey('another_center'),

Run the app again.

👉 For you, visually it looks the same

👉 For Flutter, it becomes a **different widget**

That is the power of key.

6. Types of keys (very important to know)

In Flutter you mainly have 4 types:

+--------------+------------------+-----------------------------+
|Key           |Example           |Use                          |
+==============+==================+=============================+
|ValueKey      |ValueKey('home')  |Most common                  |
+--------------+------------------+-----------------------------+
|UniqueKey     |UniqueKey()       |Always new identity          |
+--------------+------------------+-----------------------------+
|ObjectKey     |ObjectKey(user)   |Based on object              |
+--------------+------------------+-----------------------------+
|GlobalKey     |GlobalKey()       |Access widget/state anywher  |
+--------------+------------------+-----------------------------+

You used: **ValueKey** ✅ (best one for learning)

**7. When you MUST use keys**

You MUST use keys when:

	•	Using ListView.builder

	•	Using GridView

	•	Reordering items

	•	Animations with AnimatedSwitcher

	•	Dynamic widgets from data

	•	Your big enterprise app with 150+ tables UI

Example preview:

.. code-block:: dart 

    ListView(
        children: [
            Text('Apple', key: ValueKey('1')),
            Text('Banana', key: ValueKey('2')),
            Text('Orange', key: ValueKey('3')),
        ],
    )

These keys protect items from being mixed up.

**8. Final short summary**

In your program:

.. code-block:: dart 

    key: ValueKey('main_center_widget')

Means:

    ✅ Give identity to Center

    ✅ Helps Flutter track widget

    ✅ Prevents wrong rebuild

    ✅ Used in routing, lists, animations

    ✅ Extremely important for big apps

=============================================================================================================

✅2.widthFactor:
----------------

Here is a **clean, simple, WORKING Flutter program** that uses

    ✅ MaterialApp.router()

    ✅ Center widget

    ✅ **widthFactor: parameter** in Center

    ✅ No errors, no deprecated code.

**✅ Simple Flutter Program – widthFactor in Center (with MaterialApp.router)**

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    // ------------------ App ------------------

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                routerConfig: _router,
            );
        }
    }

    // ------------------ Router Config ------------------

    final RouterConfig<Object> _router = RouterConfig<Object>(
        routerDelegate: _SimpleRouterDelegate(),
    );

    // ------------------ Router Delegate ------------------

    class _SimpleRouterDelegate extends RouterDelegate<Object> with ChangeNotifier, PopNavigatorRouterDelegateMixin<Object> {

        @override
        final GlobalKey<NavigatorState> navigatorKey = GlobalKey<NavigatorState>();

        @override
        Widget build(BuildContext context) {
            return Navigator(
                key: navigatorKey,
                pages: const [
                    MaterialPage(child: HomePage()),
                ],
            );
        }

        @override
        Future<void> setNewRoutePath(Object configuration) async {}
    }

    // ------------------ Home Page ------------------

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Center widthFactor example')),
                body: Center(
                    widthFactor: 2, // ✅ widthFactor parameter
                    child: Container(
                        color: Colors.blue,
                        width: 100,
                        height: 50,
                        child: const Center(
                            child: Text(
                                'Box',
                                style: TextStyle(color: Colors.white),
                            ),
                        ),
                    ),
                ),
            );
        }
    }

**✅ What widthFactor is doing here**

This line is the key:

.. code-block:: dart 

    Center(
        widthFactor: 2,

Your child is:

.. code-block:: dart 

    Container(width: 100, height: 50)

So Flutter calculates the width of Center like this:  

    Center width = child's width × widthFactor
                = 100 × 2

                = 200px

**Without widthFactor**

	•	The Center takes the **full screen width**

**With widthFactor: 2**

	•	The Center becomes **200px wide**

	•	Still centered on the screen

	•	Wraps tightly around the blue box

**✅ Try this for learning**

Change this line:

.. code-block:: dart 

    widthFactor: 2

Test values:

+----------+---------------------+
| Value    | Result              |
+==========+=====================+
| 0.5      | Smaller Center      |
+----------+---------------------+
| 1        | Same as child width |
+----------+---------------------+
| 2        | Double width        |
+----------+---------------------+
| 4        | Very big Center     |
+----------+---------------------+
| null     | Full screen         |
+----------+---------------------+

**📌 Important note (best practice)**

widthFactor only works when:

    ✔ Child has width

    ✘ If child has no width → nothing changes

That’s why I added:

    width: 100,

**One-line explanation**

    **widthFactor = how wide the Center should be compared to its child**

✅3.heightFactor:
-----------------

Here is a c**lean, simple, and error-free Flutter example** using:

    ✅ MaterialApp.router()

    ✅ Center

    ✅ **heightFactor: parameter**

**✅ Simple Flutter Program – heightFactor in Center (MaterialApp.router)**

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    // ------------------ App ------------------

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
                return MaterialApp.router(
                routerConfig: _router,
            );
        }
    }

    // ------------------ Router Config ------------------

    final RouterConfig<Object> _router = RouterConfig<Object>(
        routerDelegate: _SimpleRouterDelegate(),
    );

    // ------------------ Router Delegate ------------------

    class _SimpleRouterDelegate extends RouterDelegate<Object> with ChangeNotifier, PopNavigatorRouterDelegateMixin<Object> {

        @override
        final GlobalKey<NavigatorState> navigatorKey = GlobalKey<NavigatorState>();

        @override
        Widget build(BuildContext context) {
            return Navigator(
                key: navigatorKey,
                pages: const [
                    MaterialPage(child: HomePage()),
                ],
            );
        }

        @override
        Future<void> setNewRoutePath(Object configuration) async {}
    }

    // ------------------ Home Page ------------------

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text('Center heightFactor example')),
                body: Center(
                    heightFactor: 3, // ✅ heightFactor parameter
                    child: Container(
                        color: Colors.green,
                        width: 100,
                        height: 40,
                        child: const Center(
                            child: Text(
                            'Box',
                            style: TextStyle(color: Colors.white),
                            ),
                        ),
                    ),
                ),
            );
        }
    }

**✅ What heightFactor is doing here**

Child height is:

.. code-block:: dart 
     
     height: 40,

You wrote:

.. code-block:: dart 

    heightFactor: 3,

So Flutter calculates the height of the Center like this:

    Center height = child height × heightFactor

                = 40 × 3

                = 120px

**Behavior:**

+--------------------+--------------------------------+
| With heightFactor  | What happens                   |
+====================+================================+
| null               | Center takes full screen height|
+--------------------+--------------------------------+
| 1                  | Same height as child (40px)    |
+--------------------+--------------------------------+
| 2                  | 80px                           |
+--------------------+--------------------------------+
| 3                  | 120px ✅                       |
+--------------------+--------------------------------+
| 5                  | 200px                          |
+--------------------+--------------------------------+

It **still stays perfectly centered vertically** on the screen.

**Very short explanation**

**heightFactor = how tall the Center becomes relative to its child**

**Try this (important for learning)**

Change this line:

.. code-block:: dart 

    heightFactor: 3,

Test values:

	•	0.5 (small)

	•	1

	•	2

	•	4

	•	null (default)

Feel the difference.

=========================================================================================================

✅4.child:
----------

Here is a **clean, simple, working Flutter example** that uses

    ✅ MaterialApp.router()

    ✅ Center

    ✅ the **child: parameter of Center**

**✅ Simple Flutter Program – child in Center (MaterialApp.router)**

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    // ------------------ App ------------------

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
                return MaterialApp.router(
                routerConfig: _router,
            );
        }
    }

    // ------------------ Router Config ------------------

    final RouterConfig<Object> _router = RouterConfig<Object>(
        routerDelegate: _SimpleRouterDelegate(),
    );

    // ------------------ Router Delegate ------------------

    class _SimpleRouterDelegate extends RouterDelegate<Object> with ChangeNotifier, PopNavigatorRouterDelegateMixin<Object> {

        @override
        final GlobalKey<NavigatorState> navigatorKey = GlobalKey<NavigatorState>();

        @override
        Widget build(BuildContext context) {
            return Navigator(
                key: navigatorKey,
                pages: const [
                    MaterialPage(child: HomePage()),
                ],
            );
        }

        @override
        Future<void> setNewRoutePath(Object configuration) async {}
    }

    // ------------------ Home Page ------------------

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return const Scaffold(
                appBar: AppBar(title: Text('Center child example')),
                body: Center(
                    // ✅ child parameter of Center
                    child: Text(
                    'Hello! I am a child of Center',
                    style: TextStyle(fontSize: 20),
                    ),
                ),
            );
        }
    }

**✅ What the child: parameter does**

This line is the key:

.. code-block:: dart 

    child: Text('Hello! I am a child of Center'),

It means:

    The **child widget** is the thing that goes **inside the Center** and gets positioned in the middle of the screen.

Center itself does **not draw anything**.

It only **positions its child:**

	•	Horizontally in the center
    
	•	Vertically in the center

**You can put ANY widget as a child:**

.. code-block:: dart 

    child: Text(...)
    child: Icon(Icons.star)
    child: Image.network(...)
    child: Container(...)
    child: Column(...)

**🔍 Very short explanation**

**Child = the widget you want to center**

Without child, Center has nothing **to show.**
