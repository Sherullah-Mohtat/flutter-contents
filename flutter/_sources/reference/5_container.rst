Container 
=========

**Container** is one of the most commonly used and versatile widgets. It acts as a **box model** that allows you to combine **layout, styling, positioning, and decoration** in a single widget.

**Container(**

    1.	**alignment:** Aligns the child within the container.

    2.	**padding:** Adds padding inside the container.

    3.	**color:** Sets a background color.

    4.	**decoration:** For more complex styling like borders or gradients.

    5.	**foregroundDecoration:** Similar to decoration, but on top of the child.

    6.	**width:** Sets the container’s width.

    7.	**height:** Sets the container’s height.

    8.	**constraints:** Allows you to specify additional constraints on the container’s size.

    9.	**margin:** Adds space around the outside of the container.

    10.	**transform:** Allows you to apply a transformation, like rotation.

    11.	**transformAlignment:** Sets the alignment origin for the transformation.

    12.	**clipBehavior:** Controls how the content is clipped if it overflows the container’s bounds.

    13. **child:** – This is the single widget you want to display inside the Container. It can be any widget, like Text, Image, Icon, Row, Column, even another Container.

**)**

✅1.alignment:
---------------

Here is a **clean, simple, working Flutter program** that uses

    ✅ MaterialApp.router()

    ✅ Container

    ✅ the **alignment: parameter of Container** (not Center)

✅ Simple Flutter Program – alignment in Container (MaterialApp.router)

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
                appBar: AppBar(title: const Text('Container alignment example')),
                body: Container(
                    width: 300,
                    height: 300,
                    color: Colors.grey.shade300,

                    // ✅ alignment parameter in Container
                    alignment: Alignment.topRight,

                    child: Container(
                        width: 100,
                        height: 100,
                        color: Colors.blue,
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

**✅ What alignment: is doing here**

This is the important line:

.. code-block:: dart 

    alignment: Alignment.topRight,

It tells the **outer Container** where to place its **child Container:**

Alignment value
Position
Alignment.center
Center
Alignment.topLeft
Top – Left
Alignment.topRight ✅
Top – Right
Alignment.bottomLeft
Bottom – Left
Alignment.bottomRight
Bottom – Right

So your **blue 100×100 box** is placed at the **top-right corner** of the **300×300 grey container.**

**Very short explanation**

**alignment: = where the child sits inside the Container**

Try this (important for learning)

Change:

.. code-block:: dart 

    alignment: Alignment.topRight,

To: 

.. code-block:: dart 

    alignment: Alignment.topRight,

or 

.. code-block:: dart 

    alignment: Alignment.bottomCenter,

and run again.

==========================================================================================================

✅2.padding:
-------------

Here is a **clean, simple, working Flutter program** that uses

✅ MaterialApp.router()

✅ Container

✅ the **padding: parameter of Container**

**✅ Simple Flutter Program – padding in Container (MaterialApp.router)**

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
                appBar: AppBar(title: const Text('Container padding example')),
                body: Center(
                    child: Container(
                        color: Colors.blue,

                        // ✅ padding parameter in Container
                        padding: const EdgeInsets.all(20),

                        child: const Text(
                            'Hello Flutter',
                            style: TextStyle(color: Colors.white, fontSize: 20),
                        ),
                    ),
                ),
            );
        }
    }

**✅ What padding: is doing**

This line is the key:

.. code-block:: dart 

    padding: const EdgeInsets.all(20),

It means:

    Add **20 pixels of space inside the container**, between the **border** and the **child (Text).**

So the text **does not touch the border.**

Instead, there is a nice space around it.

**🔎 Try these for learning**

Change padding to:

.. code-block:: dart 

    padding: const EdgeInsets.symmetric(horizontal: 40, vertical: 10),

or 

.. code-block:: dart 

    padding: const EdgeInsets.fromLTRB(10, 30, 50, 10),

See how the space changes.

**Very short explanation**

**padding = space INSIDE the Container between the edge and the child**

+--------------+-------------------------------+
| padding      | where the space is            |
+==============+===============================+
| inside       | ✅ between container and child|
+--------------+-------------------------------+
| outside      | ❌ that is margin             |
+--------------+-------------------------------+

========================================================================================================

✅3.color:
-----------

Here is a **clean, simple, working Flutter program** that uses

✅ MaterialApp.router()

✅ Container

✅ the **color: parameter of Container**

**✅ Simple Flutter Program – color in Container (MaterialApp.router)**

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
                appBar: AppBar(title: Text('Container color example')),
                body: Center(
                    child: Container(
                        width: 200,
                        height: 100,

                        // ✅ color parameter in Container
                        color: Colors.orange,

                        child: Center(
                            child: Text(
                                'Colored Box',
                                style: TextStyle(color: Colors.white, fontSize: 18),
                            ),
                        ),
                    ),
                ),
            );
        }
    }

**✅ What color: is doing**

This line is the key:

.. code-block:: dart 

    color: Colors.orange,

It sets the **background color** of the Container.

So here:
	•	Container size = **200 × 100**

	•	Background color = **Orange**

	•	Text is centered inside

**🔎 Try changing the color**

Try:

.. code-block:: dart 

    color: Colors.blue,

or 

.. code-block:: dart 

    color: Colors.green,

or even:

.. code-block:: dart 

    color: Colors.purple.shade700,

You will immediately see the box change color.

==========================================================================================================

✅4.decoration:
----------------

Here is a **clean, simple, working Flutter program** that uses

✅ MaterialApp.router()

✅ Container

✅ the **decoration: parameter of Container**

**✅ Simple Flutter Program – decoration in Container (MaterialApp.router)**

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
        final GlobalKey<NavigatorState> navigatorKey =
            GlobalKey<NavigatorState>();

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
                appBar: AppBar(title: const Text('Container decoration example')),
                body: Center(
                    child: Container(
                        width: 220,
                        height: 120,

                        // ✅ decoration parameter in Container
                        decoration: BoxDecoration(
                            color: Colors.purple,
                            borderRadius: BorderRadius.circular(15),
                            border: Border.all(
                                color: Colors.black,
                                width: 2,
                            ),
                            boxShadow: const [
                                BoxShadow(
                                    color: Colors.grey,
                                    blurRadius: 10,
                                    offset: Offset(4, 4),
                                ),
                            ],
                        ),

                        child: const Center(
                            child: Text(
                                'Decorated Box',
                                style: TextStyle(color: Colors.white, fontSize: 18),
                            ),
                        ),
                    ),
                ),
            );
        }
    }

**✅ What decoration: is doing**

This part is the key:

.. code-block:: dart 

    decoration: BoxDecoration(

With it, you created:

	•	✅ Background color → Colors.purple

	•	✅ Rounded corners → borderRadius: 15

	•	✅ Border → black, thickness 2

	•	✅ Shadow → blurred shadow

All of this is **not possible** with just color: — it is only possible with **decoration:.**

⚠️ Important rule

When you use **decoration:**, you **must NOT** use color: directly in Container.

❌ This is **WRONG:**

.. code-block:: dart 

    color: Colors.blue,
    decoration: BoxDecoration(...),

✅ This is CORRECT (color inside decoration):

.. code-block:: dart 

    decoration: BoxDecoration(
        color: Colors.blue,
    ),

**Very short explanation**

    **decoration: = advanced styling (color + border + shadow + radius + gradient)**

===========================================================================================================

✅5.foregroundDecoration:
--------------------------

Here is a **clean, simple, working Flutter program** that uses

✅ MaterialApp.router()

✅ Container

✅ the **foregroundDecoration: parameter of Container**

**✅ Simple Flutter Program – foregroundDecoration in Container (MaterialApp.router)**

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
                appBar: AppBar(title: const Text('Container foregroundDecoration')),
                body: Center(
                    child: Container(
                        width: 220,
                        height: 120,
                        color: Colors.blue, // ✅ normal background color

                        // ✅ foregroundDecoration on TOP of the child
                        foregroundDecoration: BoxDecoration(
                            color: Colors.black.withOpacity(0.4), // overlay effect
                            border: Border.all(
                                color: Colors.white,
                                width: 2,
                            ),
                        ),

                        child: const Center(
                            child: Text(
                                'Overlay Box',
                                style: TextStyle(color: Colors.white, fontSize: 18),
                            ),
                        ),
                    ),
                ),
            );
        }
    }

**✅ What foregroundDecoration: is doing**

This line:

.. code-block:: dart 

    foregroundDecoration: BoxDecoration(
        color: Colors.black.withOpacity(0.4),
    ),

Means:

    Draw this decoration **on top of the child,** not behind it.

So you get:
	•	✅ Blue background (color:)

	•	✅ Text in the center

	•	✅ Dark transparent overlay ON TOP of everything

	•	✅ White border on top

It is like putting a **transparent glass** on top of the container.

**⚖️ Difference: decoration vs foregroundDecoration**

+------------------------+-------------------------+
| decoration             | foregroundDecoration    |
+========================+=========================+
| Draws behind the child | Draws in front of child |
+------------------------+-------------------------+
| Background effect      | Overlay effect          |
+------------------------+-------------------------+
| Under text/image       | Over text/image         |
+------------------------+-------------------------+

**Very short explanation**

**foregroundDecoration: = style drawn OVER the child**

**Try this for fun**

Change:

.. code-block:: dart 

    color: Colors.black.withOpacity(0.4),

To: 

.. code-block:: dart 

    gradient: LinearGradient(
        colors: [Colors.transparent, Colors.black],
    ),

Creates a cool overlay.

========================================================================================================

✅6.width:
------------

Here is a **clean, simple, working Flutter program** that uses

✅ MaterialApp.router()

✅ Container

✅ the **width: parameter of Container**

**✅ Simple Flutter Program – width in Container (MaterialApp.router)**

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
        final GlobalKey<NavigatorState> navigatorKey =
        GlobalKey<NavigatorState>();

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
                appBar: AppBar(title: Text('Container width example')),
                body: Center(
                    child: Container(
                        // ✅ width parameter in Container
                        width: 250,
                        height: 100,

                        color: Colors.teal,

                        child: Center(
                            child: Text(
                            'Width = 250',
                            style: TextStyle(color: Colors.white, fontSize: 18),
                            ),
                        ),
                    ),
                ),
            );
        }
    }

**✅ What width: is doing**

This is the important line:

.. code-block:: dart 

    width: 250,

t sets the **horizontal size** of the container to **250 pixels.**

So the container becomes:

	•	**Width:** 250 px ✅

	•	**Height:** 100 px

	•	**Color:** Teal

	•	**Position:** Center of the screen (because you wrapped it with Center)

**🔎 Try this for learning**

Change:

.. code-block:: dart 

    width: 250,

TO: 

.. code-block:: dart 

    width: 100,

Then to: 

.. code-block:: dart 

    width: 350,

And run again to see the difference.

**Very short explanation**

**width: = how wide the Container is on the screen (in pixels)**

If you remove width, the Container will try to be as wide as possible.

========================================================================================================

✅7.height:
-------------

Here is a **clean, simple, working Flutter program** that uses

✅ MaterialApp.router()

✅ Container

✅ the **height: parameter of Container**

**✅ Simple Flutter Program – height in Container (MaterialApp.router)**

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
        final GlobalKey<NavigatorState> navigatorKey =
        GlobalKey<NavigatorState>();

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
                appBar: AppBar(title: Text('Container height example')),
                body: Center(
                    child: Container(
                        width: 200,

                        // ✅ height parameter in Container
                        height: 150,

                        color: Colors.indigo,

                        child: Center(
                            child: Text(
                                'Height = 150',
                                style: TextStyle(color: Colors.white, fontSize: 18),
                            ),
                        ),
                    ),
                ),
            );
        }
    }

**✅ What height: is doing**

This line is the **key:**
.. code-block:: dart 

    height: 150,

It sets the **vertical size** of the container to **150 pixels.**

So your container is now:

	•	**Width:** 200 px

	•	**Height:** 150 px ✅

	•	**Color:** Indigo

	•	**Position:** Center of the screen

**🔎 Try this for learning**

Change:

.. code-block:: dart 

    height: 150,

To: 

.. code-block:: dart 

    height: 60,

Or: 

.. code-block:: dart 

    height: 250,

Run again and see how the box becomes shorter or taller.

**Very short explanation**

**height: = how tall the Container is on the screen (in pixels)**

If you remove height, the container will try to fit its child or expand as much as possible.

========================================================================================================

✅8.constraints:
------------------

Here’s a **clean, simple, working Flutter example** that uses

✅ MaterialApp.router()

✅ Container

✅ the **constraints: parameter of Container**

**✅ Simple Flutter Program – constraints in Container (MaterialApp.router)**

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
        final GlobalKey<NavigatorState> navigatorKey =
        GlobalKey<NavigatorState>();

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
                appBar: AppBar(title: const Text('Container constraints example')),
                body: Center(
                    child: Container(
                        // ✅ constraints parameter in Container
                        constraints: const BoxConstraints(
                            minWidth: 150,
                            maxWidth: 300,
                            minHeight: 50,
                            maxHeight: 120,
                        ),
                        color: Colors.orange,

                        child: const Center(
                            child: Text(
                                'Min 150×50, Max 300×120',
                                textAlign: TextAlign.center,
                                style: TextStyle(color: Colors.white),
                            ),
                        ),
                    ),
                ),
            );
        }
    }

**What constraints: is doing here**

This line is the key:

.. code-block:: dart 

    constraints: const BoxConstraints(
        minWidth: 150,
        maxWidth: 300,
        minHeight: 50,
        maxHeight: 120,
    ),

It tells Flutter:
	•	The Container **must be at least** 150 × 50

	•	It **cannot be bigger than** 300 × 120

	•	Flutter chooses the actual size inside that range (here it will usually pick something near the max because it has space).

So:
	•	constraints = a **rule set** for width/height

	•	More powerful than just width: and height:

You can also use helpers like:

.. code-block:: dart 

    constraints: const BoxConstraints.tightFor(width: 200, height: 80),

(works similar to setting width and height directly).

**Super short summary**

**constraints: = control the minimum/maximum size of the Container using BoxConstraints.**


✅9.margin:
------------

Here is a **very simple Flutter example** that shows how to use the **margin** parameter in a Container **using MaterialApp.router().**

This example puts margin (space) **outside** the container so you can see the gap clearly from the screen edges.

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(MyApp());
    }

    // Simple RouterConfig
    final GoRouterConfig = RouterConfig<Object>(
        routerDelegate: _SimpleRouterDelegate(),
        routeInformationParser: _SimpleRouteParser(),
    );

    class MyApp extends StatelessWidget {
        @override
        Widget build(BuildContext context) {
                return MaterialApp.router(
                routerConfig: GoRouterConfig,
            );
        }
    }

    // ---------------- Router Delegate ----------------

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
            onPopPage: (route, result) => route.didPop(result),
            );
        }

        @override
        Future<void> setNewRoutePath(Object configuration) async {}
        }

        // ---------------- Route Parser ----------------

        class _SimpleRouteParser extends RouteInformationParser<Object> {
        @override
        Future<Object> parseRouteInformation(RouteInformation routeInformation) async {
            return Object();
        }
    }

    // ---------------- Home Page ----------------

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(title: const Text("Container Margin Example")),

                body: Container(
                    margin: const EdgeInsets.all(40), // ✅ Margin here
                    color: Colors.orange,
                    child: const Center(
                        child: Text(
                            "This Container has MARGIN",
                            style: TextStyle(fontSize: 18),
                        ),
                    ),
                ),
            );
        }
    }

**What the margin is doing here:**

.. code-block:: dart 

    margin: const EdgeInsets.all(40)

✅ Adds **40 pixels of space outside** the container

✅ Pushes the container away from the screen edges

✅ Margin = outside space

✅ Padding = inside space

If you remove this line, the orange box will touch the edges of the screen.

=====================================================================================================

✅10.transform:
----------------

Here is a **very simple Flutter example** that uses the **transform **parameter in Container **with MaterialApp.router().**

This example **rotates the container** using a transform so you can clearly see the effect.

.. code-block:: 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    // ================= MyApp =================

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                // We use routerDelegate + routeInformationParser directly.
                routerDelegate: _SimpleRouterDelegate(),
                routeInformationParser: _SimpleRouteParser(),
            );
        }
    }

    // ============ Simple RouterDelegate ============

    class _SimpleRouterDelegate extends RouterDelegate<Object> with ChangeNotifier, PopNavigatorRouterDelegateMixin<Object> {

        @override
        final GlobalKey<NavigatorState> navigatorKey = GlobalKey<NavigatorState>();

        @override
        Widget build(BuildContext context) {
            return Navigator(
                key: navigatorKey,
                // Simple route setup with only one page (HomePage)
                onGenerateRoute: (settings) {
                    return MaterialPageRoute(
                    builder: (context) => const HomePage(),
                    );
                },
            );
        }

        @override
        Future<void> setNewRoutePath(Object configuration) async {
            // For this simple example, we don't need to do anything here.
        }
    }

    // ============ Simple RouteInformationParser ============

    class _SimpleRouteParser extends RouteInformationParser<Object> {
        @override
        Future<Object> parseRouteInformation(
            RouteInformation routeInformation) async {
            // For this simple example, just return a dummy object.
            return Object();
        }
    }

    // ============ Home Page ============

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(
                    title: const Text("Container transform example"),
                ),
                body: Center(
                    child: Container(
                        width: 150,
                        height: 150,
                        color: Colors.blue,

                        // ✅ Here is the transform parameter
                        transform: Matrix4.rotationZ(0.4),  // rotate about 0.4 radians

                        alignment: Alignment.center,
                        child: const Text(
                            "Rotated Box",
                            style: TextStyle(color: Colors.white, fontSize: 18),
                        ),
                    ),
                ),
            );
        }
    }

**What the transform is doing here**

.. code-block:: dart

    transform: Matrix4.rotationZ(0.4)

✅ Rotates the container

✅ Uses Matrix4 (a 4×4 transformation matrix)

✅ 0.4 = rotation angle in radians

✅ Changes the **shape direction** without changing layout space

**You can also try other transforms:**

**1. Move (Translate)**

.. code-block:: dart 

    transform: Matrix4.translationValues(30, 50, 0),

**2. Scale (Zoom)**

.. code-block:: dart 

    transform: Matrix4.diagonal3Values(1.5, 1.5, 1),

3. Skew

.. code-block:: dart 

    transform: Matrix4.skewX(0.3),

========================================================================================================

✅11.transformAlignment:
-------------------------

Here is a **very simple and clean Flutter program** that shows how to use the

✅ **transformAlignment** parameter in a Container

✅ **with MaterialApp.router()**

✅ and **NO deprecated APIs**

This example rotates the box from the **top-left corner** instead of the center — so you can clearly see what transformAlignment does.

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    // ================= MyApp =================

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                routerDelegate: _SimpleRouterDelegate(),
                routeInformationParser: _SimpleRouteParser(),
            );
        }
    }

    // ============ Simple Router Delegate ============

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

                // ✅ New Flutter method (not deprecated)
                onDidRemovePage: (page) {
                    // Do nothing
                },
            );
        }

        @override
        Future<void> setNewRoutePath(Object configuration) async {}
    }

    // ============ Simple RouteInformationParser ============

    class _SimpleRouteParser extends RouteInformationParser<Object> {
        @override
        Future<Object> parseRouteInformation(RouteInformation routeInformation) async {
            return Object();
        }
    }

    // ================= Home Page =================

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(
                    title: const Text("transformAlignment Example"),
                ),
                body: Center(
                    child: Container(
                        width: 150,
                        height: 150,
                        color: Colors.red,

                        // ✅ Rotate the container
                        transform: Matrix4.rotationZ(0.6),

                        // ✅ Change the point of rotation (VERY IMPORTANT)
                        transformAlignment: Alignment.topLeft,

                        alignment: Alignment.center,
                        child: const Text(
                            "Top-Left Rotation",
                            style: TextStyle(color: Colors.white),
                            textAlign: TextAlign.center,
                        ),
                    ),
                ),
            );
        }
    }

**What transformAlignment is doing here**

.. code-block:: dart 

    transformAlignment: Alignment.topLeft

Normally a container rotates **from the center.**

With transformAlignment, you change the **pivot point:**

+---------------------------------+------------------------------------+
| Alignment Value                 | Rotation Point                     |
+=================================+====================================+
| Alignment.center                | Rotates from the center (default)  |
+---------------------------------+------------------------------------+
| Alignment.topLeft               | Rotates from top-left corner       |
+---------------------------------+------------------------------------+
| Alignment.bottomRight           | Rotates from bottom-right          |
+---------------------------------+------------------------------------+
| Alignment.centerLeft            | Rotates from left side             |
+---------------------------------+------------------------------------+

Try this too 👇

.. code-block:: dart 

    transformAlignment: Alignment.bottomRight,

or 

.. code-block:: dart 

    transformAlignment: Alignment.centerLeft,

and see how the rotation changes.

========================================================================================================

✅12.clipBehavior:
--------------------

Here is a very **simple, clean Flutter program** that demonstrates the

✅ **clipBehavior parameter in Container**

✅ using **MaterialApp.router()**

✅ using **NO deprecated APIs**

✅ and makes the **clipping effect clearly visible**

This example puts a **large child inside a small container.**

clipBehavior decides whether the child is **cut (clipped) or allowed to overflow.**

**✅ Full Working Example — clipBehavior in Container**

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    // ================= MyApp =================

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                routerDelegate: _SimpleRouterDelegate(),
                routeInformationParser: _SimpleRouteParser(),
            );
        }
    }

    // ============ Router Delegate ============

    class _SimpleRouterDelegate extends RouterDelegate<Object> with ChangeNotifier, PopNavigatorRouterDelegateMixin<Object> {

        @override
        final GlobalKey<NavigatorState> navigatorKey =
        GlobalKey<NavigatorState>();

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

    // ============ Route Information Parser ============

    class _SimpleRouteParser extends RouteInformationParser<Object> {
        @override
        Future<Object> parseRouteInformation(
            RouteInformation routeInformation) async {
            return Object();
        }
    }

    // ================= Home Page =================

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(
                    title: const Text("clipBehavior in Container"),
                ),
                body: Center(
                    child: Container(
                        width: 150,
                        height: 150,

                        // ✅ MUST use decoration when using clipBehavior
                        decoration: BoxDecoration(
                            color: Colors.blue,
                            borderRadius: BorderRadius.circular(20),
                        ),

                        // ✅ clipBehavior is valid now
                        clipBehavior: Clip.hardEdge,

                        child: const Text(
                            "This text is clipped inside the rounded container",
                            style: TextStyle(color: Colors.white, fontSize: 16),
                            textAlign: TextAlign.center,
                        ),
                    ),
                ),
            );
        }
    }

What clipBehavior is doing

.. code-block:: dart 

    clipBehavior: Clip.hardEdge,

Because the text is **bigger than the container**, clipping happens.

**Try these values and see the difference:**

.. code-block:: dart 

    clipBehavior: Clip.none,       // ❌ No clipping — text goes outside
    clipBehavior: Clip.hardEdge,   // ✅ cuts extra content (fast)
    clipBehavior: Clip.antiAlias,  // ✅ smooth clipping
    clipBehavior: Clip.antiAliasWithSaveLayer, // ✅ best quality (slower)

**✅ Remember**

	•	clipBehavior only works when **child content goes out of bounds**

	•	Container must have a **fixed width & height**

	•	It’s most useful with images, text or animated widgets

======================================================================================================

✅13.child:
--------------

Here is a very **simple Flutter example** that demonstrates the

✅ **child: parameter in Container**

✅ using **MaterialApp.router()**

✅ with **correct router types (no errors, no deprecated code)**

This example puts a Text widget as the child of a Container so you can clearly see what the child parameter does.

**✅ Simple Working Program — child in Container**

.. code-block:: dart 

    import 'package:flutter/material.dart';

    void main() {
        runApp(const MyApp());
    }

    // ================= MyApp =================

    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return MaterialApp.router(
                routerDelegate: _SimpleRouterDelegate(),
                routeInformationParser: _SimpleRouteParser(),
            );
        }
    }

    // ============ Router Delegate ============

    class _SimpleRouterDelegate extends RouterDelegate<Object> with ChangeNotifier, PopNavigatorRouterDelegateMixin<Object> {
        @override
        final GlobalKey<NavigatorState> navigatorKey =
        GlobalKey<NavigatorState>();

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

    // ============ Route Information Parser ============

    class _SimpleRouteParser extends RouteInformationParser<Object> {
        @override
        Future<Object> parseRouteInformation(
            RouteInformation routeInformation) async {
            return Object();
        }
    }

    // ================= Home Page =================

    class HomePage extends StatelessWidget {
        const HomePage({super.key});

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                appBar: AppBar(
                    title: const Text("Container child example"),
                ),
                body: Center(
                    child: Container(
                        width: 200,
                        height: 200,
                        color: Colors.green,

                        // ✅ child parameter
                        child: const Center(
                            child: Text(
                                "I am the CHILD",
                                style: TextStyle(
                                    color: Colors.white,
                                    fontSize: 20,
                                    fontWeight: FontWeight.bold,
                                ),
                            ),
                        ),
                    ),
                ),
            );
        }
    }

**What the child parameter does**

.. code-block:: dart 

    child: const Center(
        child: Text("I am the CHILD"),
    )

•	child = **the widget inside the Container**

•	Container = parent

•	Text / Image / Button / Column etc. = **child**

•	Without child → the container is just an empty box

You can also put other widgets as child. Example:

.. code-block:: dart 

    child: Image.network("https://via.placeholder.com/150"),

Or

.. code-block:: dart 

    child: Icon(Icons.star, size: 50),