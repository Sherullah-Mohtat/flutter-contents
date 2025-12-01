RouterConfig
==============

✅ All RouterConfig Parameters
-------------------------------

**RouterConfig(**

    1. **routerDelegate:**
       The RouterDelegate that builds the Navigator tree.
       ⭐ Required for navigation logic.

    2. **routeInformationParser:**
       Parses route information (URL → route data).

    3. **routeInformationProvider:**
       Supplies new route information to the app (URL updates).

    4. **backButtonDispatcher:**
        Handles system back button events (Android / Web back navigation).

    5. **routeInformationReporter:**
        Sends route updates from the app to the OS / browser.

    6. **restorationScopeId:**
        Restoration ID for state restoration.

    7. **widgetBuilder:**
        Builds the root widget around the router (rarely used).

    8. **routerNeglect:**
        Boolean: if true, RouterConfig ignores some route updates.
        Default: false.

**)**

✅1.routerDelegate:
--------------------

✅2.routeInformationParser:
----------------------------

✅3.routeInformationProvider:
------------------------------

✅4.backButtonDispatcher:
--------------------------

✅5.routeInformationReporter:
-------------------------------

✅6.restorationScopeId:
------------------------

✅7.widgetBuilder:
-------------------

✅8.routerNeglect:
-------------------

