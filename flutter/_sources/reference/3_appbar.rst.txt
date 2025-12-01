AppBar 
======

**AppBar** is a built-in widget that provides a **material design app bar** (also called a toolbar) at the top of your app’s screen. It’s commonly used inside a Scaffold widget and typically contains elements like a **title, navigation icons, actions,** and more.

Named Parameters
------------------

**AppBar(**

    1.	**leading:** – for a widget before the title, often an icon or a back button.
	
    2.	**automaticallyImplyLeading:** – a boolean to automatically show a leading widget if needed.
	
    3.	**title:** – the main widget in the app bar, usually text.
	
    4.	**actions:** – a list of widgets to display in a row after the title.
	
    5.	**flexibleSpace:** – a widget that fills the app bar behind the title.
	
    6.	**bottom:** – a PreferredSizeWidget typically used for a tab bar.
	
    7.	**elevation:** – a double value for the shadow under the app bar.
	
    8.	**shadowColor:** – the color of the shadow.
	
    9.	**surfaceTintColor:** – the color that tints the app bar surface.
	
    10.	**shape:** – a shape for the app bar’s material.
	
    11.	**backgroundColor:** – the background color of the app bar.
	
    12.	**foregroundColor:** – the color of the app bar’s text and icons.
	
    13.	**brightness:** (deprecated in favor of systemOverlayStyle) – used to control system bar brightness.
	
    14.	**iconTheme:** – the color and size of the icons.
	
    15.	**actionsIconTheme:** – the theme for the action icons.
	
    16.	**textTheme:** (deprecated) – for setting the text theme of the app bar.
	
    17.	**toolbarHeight:** – a double to set the height of the toolbar.
	
    18.	**leadingWidth:** – a double to set the width of the leading widget.
	
    19.	**toolbarOpacity:** – a double for the toolbar’s opacity.
	
    20.	**bottomOpacity:** – a double for the bottom widget’s opacity.
	
    21.	**toolbarTextStyle:** – the text style for the toolbar.
	
    22.	**titleTextStyle:** – the text style specifically for the title.
	
    23.	**systemOverlayStyle:** – to control the style of the system status bar.

**)**

Examples
-----------

✅ 1. leading:
--------------

Displays a widget before the title (usually an icon or back button).

.. code-block:: dart 

    AppBar(
    leading: Icon(Icons.menu),
    )

✅ 2. automaticallyImplyLeading:
----------------------------------

Whether to imply a default leading widget automatically (e.g., back arrow).

.. code-block:: dart 

    AppBar(
    automaticallyImplyLeading: false,
    )

✅ 3. title:
--------------

Main widget shown in the middle of the AppBar.

.. code-block:: dart 

    AppBar(
    title: Text('My App'),
    )

✅ 4. actions:
---------------

A list of widgets displayed at the end of the AppBar (right side).

.. code-block:: dart 

    AppBar(
    actions: [Icon(Icons.search)],
    )

✅ 5. flexibleSpace:
---------------------

A widget that appears behind the AppBar (e.g., gradients, images).

.. code-block:: dart 

    AppBar(
        flexibleSpace: Container(
            decoration: BoxDecoration(
                gradient: LinearGradient(colors: [Colors.blue, Colors.green]),
            ),
        ),
    )

✅ 6. bottom:
--------------

Widget below the AppBar (commonly used for TabBar).

.. code-block:: dart 

    AppBar(
    bottom: TabBar(
        tabs: [
            Tab(icon: Icon(Icons.home)),
            Tab(icon: Icon(Icons.settings)),
        ]),
    )

✅ 7. elevation:
-----------------

Z-axis shadow depth below the AppBar.

.. code-block:: dart 

    AppBar(
    elevation: 4.0,
    )

✅ 8. shadowColor:
-------------------

Color of the AppBar’s shadow.

.. code-block:: dart 

    AppBar(
    shadowColor: Colors.red,
    )

✅ 9. surfaceTintColor:
------------------------

Color to blend over the AppBar’s surface.

.. code-block:: dart 

    AppBar(
        surfaceTintColor: Colors.yellow,
    )

✅ 10. shape:
---------------

Defines a shape for the AppBar.

.. code-block:: dart 

    AppBar(
        shape: RoundedRectangleBorder(
            borderRadius: BorderRadius.vertical(bottom: Radius.circular(30)),
        ),
    )

✅ 11. backgroundColor:
-------------------------

The background color of the AppBar.

.. code-block:: dart 

    AppBar(
    backgroundColor: Colors.purple,
    )

✅ 12. foregroundColor:
-------------------------

The color for text and icons.

.. code-block:: dart 

    AppBar(
        foregroundColor: Colors.white,
    )

✅ 13. iconTheme:
------------------

Theme for icons in the AppBar.

.. code-block:: dart 

    AppBar(
        iconTheme: IconThemeData(color: Colors.black),
    )

✅ 14. actionsIconTheme:
--------------------------

Theme for action icons (right side).

.. code-block:: dart

    AppBar(
        actionsIconTheme: IconThemeData(color: Colors.red),
    )

✅ 15. toolbarHeight:
-----------------------

Height of the toolbar portion of the AppBar.

.. code-block:: dart 

    AppBar(
        toolbarHeight: 80.0,
    )

✅ 16. leadingWidth:
----------------------

Width of the leading widget space.

.. code-block:: dart 

    AppBar(
        leading: Icon(Icons.menu),
        leadingWidth: 100,
    )

✅ 17. toolbarOpacity:
-------------------------

Opacity of the toolbar section.

.. code-block:: dart 

    AppBar(
        toolbarOpacity: 0.8,
    )

✅ 18. bottomOpacity:
-----------------------

Opacity of the bottom widget (like TabBar).

.. code-block:: dart 

    AppBar(
        bottomOpacity: 0.5,
    )

✅ 19. toolbarTextStyle:
--------------------------

Text style for widgets inside the toolbar (excluding title).

.. code-block:: dart 

    AppBar(
        toolbarTextStyle: TextStyle(color: Colors.orange, fontSize: 18),
    )

✅ 20. titleTextStyle:
-------------------------

Custom text style for the title.

.. code-block:: dart 

    AppBar(
        title: Text('Styled Title'),
        titleTextStyle: TextStyle(color: Colors.white, fontSize: 22),
    )

✅ 21. systemOverlayStyle:
----------------------------

Customize the system status bar style (like text color).

.. code-block:: dart 

    AppBar(
        systemOverlayStyle: SystemUiOverlayStyle.light,
    )

✅ 22. centerTitle:
---------------------

Whether to center the title widget.

.. code-block:: dart

    AppBar(
        title: Text('Centered'),
        centerTitle: true,
    )

✅ 23. scrolledUnderElevation:
--------------------------------

Elevation when content is scrolled under the AppBar (Material 3).

.. code-block:: dart 

    AppBar(
        scrolledUnderElevation: 10.0,
    )

