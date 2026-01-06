kaftarya_app
==============

--------------------------
1. What is kaftarya_app?
--------------------------

kaftarya_app is the root directory of your Flutter project.

When you run:

.. code-block:: bash 

   flutter create --org com.kaftarya --platforms=android,ios,web,macos,windows,linux kaftarya_app

Flutter creates a **single project folder** named kaftarya_app.
Everything related to your application lives **inside this directory.**

Think of kaftarya_app as the **container** for your entire Flutter application.

========================================================================================================

-----------------------------------
2. Why is kaftarya_app important?
-----------------------------------

This folder represents **one Flutter application** that can run on:
	- 📱 Android
	- 🍎 iOS
	- 🌐 Web
	- 🖥 macOS
	- 🪟 Windows
	- 🐧 Linux

All platforms share **one codebase,** managed from this root.

========================================================================================================

--------------------------------------
3. What happens inside kaftarya_app?
--------------------------------------

Inside this directory, Flutter organizes the project into:
	- **Platform-specific folders** (android, ios, web, etc.)
	- **Flutter source code** (lib/)
	- **Configuration files** (pubspec.yaml, analysis_options.yaml)
	- **Build and tooling files** (.dart_tool, build/)

You never run Flutter commands outside this folder.

========================================================================================================

------------------------------------------
4. Commands always run from kaftarya_app
------------------------------------------

Examples:

.. code-block:: bash 

   cd kaftarya_app
   flutter run
   flutter build web
   flutter pub get
   flutter doctor

If you run these commands **outside** kaftarya_app, Flutter will not detect your project.

========================================================================================================

---------------------------------------
5. Naming rules for the root project
---------------------------------------

The name kaftarya_app:
	- ✅ Must be lowercase
	- ✅ Uses underscores instead of spaces
	- ✅ Becomes the **Dart package name**
	- ⚠️ Should not be changed after creation

Changing the root folder name later can break:
	- Imports
	- IDE configuration
	- Build tools

========================================================================================================

**Relation to app identity (--org)**

Your root folder name works together with:

.. code-block:: bash 

   --org com.kaftarya

So the full app identity becomes:
	- **Android package name**
   
com.kaftarya.kaftarya_app
	- **iOS / macOS bundle ID**

com.kaftarya.kaftarya_app

The folder name is part of the **application identity** across platforms.

========================================================================================================

--------------------------------------
6. What you should and should NOT do
--------------------------------------

✅ You should
	- Open this folder in Android Studio / VS Code
	- Run Flutter commands from here
	- Version-control this folder with Git

❌ You should NOT
	- Put Flutter code directly in kaftarya_app/
	- Delete this folder
	- Rename it after creation

========================================================================================================

**Mental model (important)**

.. code-block:: bash 

   kaftarya_app
   │
   ├── Flutter engine
   ├── Dart code (lib/)
   ├── Native shells (android, ios, web…)
   └── Build system

**One folder → one app → all platforms**

========================================================================================================

------------
7. Summary
------------
	- kaftarya_app is the project root
	- It holds everything for your Flutter application
	- All development starts here
	- All platforms are managed from here
	- This is standard, official, and production-ready

========================================================================================================

.. toctree::
   :hidden:
   :maxdepth: 2

   .dart_tool/index 
   .idea/index 
   android/index
   build/index 
   ios/index 
   lib/index 
   linux/index 
   macos/index 
   test/index 
   web/index 
   windows/index 
   .gitignore
   .metadata
   analysis_options 
   kaftarya_app 
   pubspeclock 
   pubspecyaml 
   readme 
    





  
