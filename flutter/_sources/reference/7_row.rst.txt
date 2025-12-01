Row 
===

**Row** is a **layout widget** that arranges its child widgets **horizontally** — from left to right (or **right to left**, depending on the text direction).

**Named Parameters:**
---------------------

**Row(**

    1.	**key:** — Identifier for the widget (for uniqueness in widget tree).
	
    2.	**mainAxisAlignment:** — Controls how children are aligned horizontally (along the main axis).
	
    3.	**mainAxisSize:** — Determines how much horizontal space the Row should occupy.
	
    4.	**crossAxisAlignment:** — Controls how children are aligned vertically (cross axis).
	
    5.	**textDirection:** — Defines the direction of text (left-to-right or right-to-left).
	
    6.	**verticalDirection:** — Defines the order of children vertically (up or down).
	
    7.	**textBaseline:** — Used for aligning text vertically by their baseline (requires CrossAxisAlignment.baseline).
	
    8.	**children:** — A list of widgets displayed horizontally.

**)**

**Examples:**
-------------

**Simple example for each of the 8 named parameters** in the **Row** widget — each one shown **separately**, so you can clearly see how it works.

All examples use the same base structure:

.. code-block:: dart 

    import 'package:flutter/material.dart';
    void main() => runApp(const MyApp());
    class MyApp extends StatelessWidget {
        const MyApp({super.key});

        @override
        Widget build(BuildContext context) {
            return const MaterialApp(
                home: Scaffold(
                  body: ExampleRow(),
                ),
            );
        }
    }

Now let’s go parameter by parameter 👇

✅1️⃣ key
------------

.. code-block:: dart 

    class ExampleRow extends StatelessWidget {
        const ExampleRow({super.key});

        @override
        Widget build(BuildContext context) {
            return Row(
                key: const Key('my_row_key'),
                children: const [
                    Icon(Icons.star),
                    Text('Row with Key'),
                ],
            );
        }
    }

💡 Adds a unique identifier to the widget, useful for state or testing.


✅2️⃣ mainAxisAlignment
-------------------------

.. code-block:: dart 

    class ExampleRow extends StatelessWidget {
        const ExampleRow({super.key});

        @override
        Widget build(BuildContext context) {
            return Row(
                mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                children: const [
                    Icon(Icons.home),
                    Icon(Icons.favorite),
                    Icon(Icons.settings),
                ],
            );
        }
    }

💡 Controls horizontal spacing between children.

✅3️⃣ mainAxisSize
--------------------

.. code-block:: dart 

    class ExampleRow extends StatelessWidget {
        const ExampleRow({super.key});

        @override
        Widget build(BuildContext context) {
            return Center(
                child: Container(
                    color: Colors.amber[100],
                    child: Row(
                        mainAxisSize: MainAxisSize.min,
                        children: const [
                            Icon(Icons.home),
                            Icon(Icons.star),
                        ],
                    ),
                ),
            );
        }
    }

💡 MainAxisSize.min makes the row shrink to the width of its children.

✅4️⃣ crossAxisAlignment
--------------------------

.. code-block:: dart 

    class ExampleRow extends StatelessWidget {
        const ExampleRow({super.key});

        @override
        Widget build(BuildContext context) {
            return Container(
                height: 100,
                color: Colors.blue[50],
                child: Row(
                    crossAxisAlignment: CrossAxisAlignment.end,
                    children: const [
                        Text('Top'),
                        Text('Bottom', style: TextStyle(fontSize: 30)),
                    ],
                ),
            );
        }
    }

💡 Aligns children vertically (top, bottom, center, etc.).

✅5️⃣ textDirection
---------------------

.. code-block:: dart 

    class ExampleRow extends StatelessWidget {
        const ExampleRow({super.key});

        @override
        Widget build(BuildContext context) {
            return Row(
                textDirection: TextDirection.rtl, // right to left(rtl) ro ltr for left
                children: const [
                    Icon(Icons.arrow_back),
                    Icon(Icons.arrow_forward),
                ],
            );
        }
    }

💡 Lays out children from right to left instead of left to right.

✅6️⃣ verticalDirection
-------------------------

.. code-block:: dart 

    class ExampleRow extends StatelessWidget {
        const ExampleRow({super.key});

        @override
        Widget build(BuildContext context) {
            return Container(
                height: 100,
                color: Colors.green[50],
                child: Row(
                    crossAxisAlignment: CrossAxisAlignment.start,
                    verticalDirection: VerticalDirection.up,
                    children: const [
                        Text('First'),
                        Text('Second', style: TextStyle(fontSize: 24)),
                    ],
                ),
            );
        }
    }

💡 Reverses the vertical order of children.

✅7️⃣ textBaseline
--------------------

.. code-block:: dart 

    class ExampleRow extends StatelessWidget {
        const ExampleRow({super.key});

        @override
        Widget build(BuildContext context) {
            return Row(
                crossAxisAlignment: CrossAxisAlignment.baseline,
                textBaseline: TextBaseline.alphabetic,
                children: const [
                    Text('Hello', style: TextStyle(fontSize: 20)),
                    Text('World', style: TextStyle(fontSize: 40)),
                ],
            );
        }
    }

💡 Aligns text widgets by their text baseline (useful for mixed font sizes).

✅8️⃣ children
----------------

.. code-block:: dart 

    class ExampleRow extends StatelessWidget {
        const ExampleRow({super.key});

        @override
        Widget build(BuildContext context) {
            return Row(
                children: const [
                    Icon(Icons.coffee),
                    Icon(Icons.fastfood),
                    Icon(Icons.local_pizza),
                ],
            );
        }
    }

💡 Defines the list of widgets shown horizontally inside the row.

