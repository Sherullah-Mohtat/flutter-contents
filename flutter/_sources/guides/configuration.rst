Configuration
================

Confuguration Notes
--------------------

**Meaning of “configuration” inside a Flutter project**

After creating a Flutter project, **configuration** refers to all the files and settings that control how your app behaves on different platforms (Android, iOS, web, macOS, Windows, Linux).

These are settings you usually must adjust before building or publishing your app.

**⭐ 1. Flutter project main configuration files**

Here are the important configuration files:

**1️⃣ pubspec.yaml**

This is the **main configuration file.**

You configure:

	•	App name

	•	Description

	•	Dependencies (packages)

	•	Assets (icons, images, fonts)

	•	Environment version

	•	App version

	•	App icons

**2️⃣ Platform-specific configuration**

Each platform has its own configuration folder.


**📱 Android Configuration**

Located in:

.. code-block::

    android/app/

Important files:

**✔ AndroidManifest.xml**

Controls:

	•	App name

	•	Permissions (camera, location, Bluetooth, internet)

	•	App icon

	•	Splash screen

**✔ build.gradle**

Controls:

	•	minSdk

	•	targetSdk

	•	versionCode

	•	versionName

**✔ MainActivity.kt**

Entry point for native Android code.

**🍏 iOS Configuration**

Located in:

.. code-block:: bash 

    ios/Runner/

Important files:

**✔ Info.plist**

Controls:

	•	App name

	•	App permissions

	•	Camera/microphone usage text

	•	URL schemes

**✔ Runner.xcodeproj**

Used when publishing to App Store.

**💻 macOS Configuration**

Located in:

.. code-block:: bash 

    macos/Runner/

Contains:
	•	Info.plist
	•	macOS settings
	•	App icon
	•	Permissions

**🌐 Web Configuration**

Located in:

.. code-block:: bash 

    web/

Important files:

**✔ index.html**

Controls:

	•	Title

	•	Meta tags

	•	Icon

**✔ manifest.json**

Controls:

	•	Name

	•	Icons

	•	Theme color

**🪟 Windows Configuration**

Located in:

.. code-block:: bash 

    windows/runner/

Controls:
	•	Window size
	•	Title
	•	Icons

**🐧 Linux Configuration**

Located in:

.. code-block:: bash 

    linux/

Contains:

	•	CMakeLists

	•	Runner files

	•	App metadata

**3. Flutter-wide configuration commands**

You can also configure Flutter using commands:

.. code-block:: bash 

    flutter config --enable-web
    flutter config --enable-linux-desktop
    flutter config --enable-macos-desktop
    flutter config --enable-windows-desktop

These change your Flutter tool configuration.

**Final Simple Definition (Flutter-specific)**

    **Configuration in Flutter = all the settings inside each platform folder and pubspec.yaml that control how your app behaves on Android, iOS, web, macOS, Windows, and Linux.**
    
✅1.Shared Flutter config (pubspec.yaml)
-----------------------------------------

This file affects **all platforms** (Android, iOS, Web, Desktop…).

Path:

.. code-block:: bash 

    kaftarya_app/
      pubspec.yaml

**1.1 What kind of things do we configure here?**

	•	App **version**

	•	App **dependencies** (packages)

	•	**Assets** (images, JSON, etc.)

	•	**Fonts**

**🔹 Example 1 — Change app version**

Default (when project is created):

.. code-block:: yaml 

    version: 1.0.0+1

If you want to release a new version (for store), change:

.. code-block:: yaml 

    version: 1.1.0+2

	•	1.1.0 → user sees this in Play Store / App Store

	•	+2 → internal build number used by Android/iOS

👉 This is **configuration:** you changed how the app identifies its version on all platforms.

**🔹 Example 2 — Add an image asset**

Say you add this file:

.. code-block:: bash 

    assets/images/logo.png

Now you must register it in pubspec.yaml:

.. code-block:: yaml 

    flutter:
        uses-material-design: true

    assets:
        - assets/images/logo.png

Then you can use it in your Dart code:

.. code-block:: dart 

    Image.asset('assets/images/logo.png')

👉 That “tell Flutter where my image is” is also **configuration.**

**🔹 Example 3 — Add a package (dependency)**

You want to use http package:

In pubspec.yaml:

.. code-block:: yaml 

    dependencies:
        flutter:
            sdk: flutter

        http: ^1.2.0

Then run:

.. code-block:: bash 

    flutter pub get

Now you can:

.. code-block:: dart 

    import 'package:http/http.dart' as http;

👉 Here you configured your project to use a new library.

So for now, remember:

    **pubspec.yaml = global settings for version, packages, assets, fonts.**

Now let’s go platform by platform.

✅2.Android
-------------

Main Android folder:

.. code-block:: bash 

    kaftarya_app/
        android/

We’ll touch **two main files:**

	1.	android/app/src/main/AndroidManifest.xml

	2.	android/app/build.gradle

**2.1 AndroidManifest.xml**

Path:

.. code-block:: bash 

    android/app/src/main/AndroidManifest.xml

This file configures:

	•	App **name** (older style)

	•	App **permissions** (camera, internet, location…)

	•	Launch activity, deep links (later)

**✅ Example A — Add Internet & Camera permission**

Default may look like:

.. code-block:: bash 

    <manifest xmlns:android="http://schemas.android.com/apk/res/android"
        package="com.kaftarya.kaftarya_app">
        
        <application
            android:name="${applicationName}"
            android:icon="@mipmap/ic_launcher"
            android:label="kaftarya_app">
            
            <activity
                android:name=".MainActivity"
                ... >
                ...
            </activity>
        </application>
    </manifest>

If you want to use **camera** and **internet**, modify it to

.. code-block:: bash 

    <manifest xmlns:android="http://schemas.android.com/apk/res/android"
        package="com.kaftarya.kaftarya_app">

        <!-- ✅ Permissions configuration -->
        <uses-permission android:name="android.permission.INTERNET" />
        <uses-permission android:name="android.permission.CAMERA" />

        <application
            android:name="${applicationName}"
            android:icon="@mipmap/ic_launcher"
            android:label="Kaftarya App"> <!-- ✅ Renamed app label -->

            <activity
                android:name=".MainActivity"
                ... >
                ...
            </activity>
        </application>
    </manifest>

Here you did **configuration:**

	•	You **added** permissions.

	•	You **changed** android:label from kaftarya_app → Kaftarya App.

**2.2 android/app/build.gradle**

Path:

.. code-block:: bash 

    android/app/build.gradle

This file configures:

	•	applicationId (package name Android uses)

	•	minSdkVersion (minimum Android version)

	•	targetSdkVersion

	•	Some build settings

Example default:

.. code-block:: dart 

    android {
        defaultConfig {
            applicationId "com.kaftarya.kaftarya_app"
            minSdkVersion 21
            targetSdkVersion 34
            versionCode flutterVersionCode.toInteger()
            versionName flutterVersionName
        }
    }

**✅ Example B — Change applicationId and minSdkVersion**

If later you want to change the package name to:

.. code-block:: bash 

    com.kaftarya.app
    
Change configuration to:

.. code-block:: bash  

    defaultConfig {
        applicationId "com.kaftarya.app"   // ✅ new ID
        minSdkVersion 23                   // ✅ new minimum Android version
        targetSdkVersion 34
        versionCode flutterVersionCode.toInteger()
        versionName flutterVersionName
    }

That’s Android **configuration:** you are telling:

	•	Who I am (applicationId)

	•	What OS versions I support (minSdkVersion)

For now, that’s enough for Android.

➡️ Next: iOS.


✅3.iOS
--------

Main iOS folder:

.. code-block:: bash 

    kaftarya_app/
        ios/

The two most important:

	1.	ios/Runner/Info.plist

	2.	Xcode settings (bundle ID, signing)

**3.1 Info.plist**

Path:

.. code-block:: bash

    ios/Runner/Info.plist

Info.plist = structured key/value configuration for iOS app.

You configure:

	•	App name shown under the icon

	•	Permissions messages (camera, microphone, location)

	•	Other app behavior

**✅ Example C — Change iOS app name**

Inside Info.plist you’ll find something like:

.. code-block:: bash 

    <key>CFBundleName</key>
    <string>kaftarya_app</string>

Change to:

.. code-block:: bash 

    <key>CFBundleName</key>
    <string>Kaftarya App</string>

Now on your iPhone home screen, under the icon you see **Kaftarya App.**

**✅ Example D — Add camera permission text**

iOS requires you to explain why you need camera.

Add these lines inside the <dict>...</dict> of Info.plist:

.. code-block:: bash 

    <key>NSCameraUsageDescription</key>
    <string>This app uses the camera to scan QR codes and take product photos.</string>

Now, when the app requests camera, the system shows this message.

That’s **iOS configuration.**

3.2 Bundle ID (Xcode project)

In Xcode (Runner target), you configure **Bundle Identifier**, like:

.. code-block:: bash 

    com.kaftarya.kaftaryaApp

This must match what you use for App Store.

You don’t see it as code here, but this is a **platform configuration** step, same idea as Android applicationId.

That’s enough deep config examples for iOS.

➡️ Next: **Web.**

✅4.Web
--------

Main folder:

.. code-block:: bash 

    kaftarya_app/
        web/
    
Key files:

	1.	web/index.html

	2.	web/manifest.json

**4.1 web/index.html**

Path:

.. code-block:: bash 

    web/index.html

This is the HTML shell that loads your Flutter app in the browser.

**✅ Example E — Change browser tab title** 

Default:

.. code-block:: html 

    <title>kaftarya_app</title>

Change to:

.. code-block:: html 

    <title>Kaftarya – Restaurant App</title>

Now the browser shows **Kaftarya – Restaurant App** in the tab.

**✅ Example F — Add simple description (SEO)**

Inside <head>:

.. code-block:: html 

    <meta name="description" content="Kaftarya: a smart restaurant management app built with Flutter.">

Now search engines and social previews see this description.

That’s **web configuration.**

**4.2 web/manifest.json**

Path:

.. code-block:: bash 

    web/manifest.json

This is for PWA (Progressive Web App) behavior.

Example:

.. code-block:: json 

    {
        "name": "Kaftarya App",
        "short_name": "Kaftarya",
        "start_url": "/",
        "display": "standalone",
        "background_color": "#ffffff",
        "theme_color": "#2196f3",
        "icons": [
            {
                "src": "icons/Icon-192.png",
                "sizes": "192x192",
                "type": "image/png"
            }
        ]
    }

**✅ Example G — Change theme color**

If you want a dark theme:

.. code-block:: json 

    "theme_color": "#000000",
    "background_color": "#000000",

When user adds web app to home screen, these control splash and browser UI color.

➡️ Next: **macOS.**

✅5.macOS
-----------

Main folder:

.. code-block:: text 

    kaftarya_app/
        macos/

Important parts:

	1.	macos/Runner/Info.plist

	2.	App window behavior

**5.1 macos/Runner/Info.plist**

Very similar to iOS.

**✅ Example H — Change macOS app name**

You’ll see:

.. code-block:: xml 

    <key>CFBundleName</key>
    <string>kaftarya_app</string>

Change to:

.. code-block:: xml 

    <key>CFBundleName</key>
    <string>Kaftarya Desktop</string>

Now in the macOS title bar / app menu, it appears as **Kaftarya Desktop.**

**5.2 Customizing the initial window size**

For that you usually edit MainFlutterWindow.swift (but this is a bit more advanced). At the start, default is okay, so we can keep macOS simple for now.

➡️ Next: **Windows.**

✅6.Windows
-------------

Folder:

.. code-block:: text 

    kaftarya_app/
        windows/

Key files:

	1.	windows/runner/flutter_window.cpp

**6.1 flutter_window.cpp – configure window title/size**

You’ll see code like this:

.. code-block:: cpp 

    bool FlutterWindow::OnCreate() {
        if (!FlutterWindowBase::OnCreate())
            return false;

        flutter_controller_ = std::make_unique<flutter::FlutterViewController>(
            project_, L"Kaftarya App");

        SetChildContent(flutter_controller_->view()->GetNativeWindow());
        return true;
    }

**✅ Example I — Change window title**

Change:

.. code-block:: cpp 

    flutter_controller_ = std::make_unique<flutter::FlutterViewController>(
    project_, L"Kaftarya App");

to: 

.. code-block:: cpp 

    flutter_controller_ = std::make_unique<flutter::FlutterViewController>(
    project_, L"Kaftarya Desktop");

Now Windows app window title bar shows “Kaftarya Desktop”.

You can also adjust default size in similar code.

➡️ Finally: **Linux.**

✅7.Linux
------------

Folder:

.. code-block:: text 

    kaftarya_app/
        linux/

Key files:

	1.	linux/my_application.cc

**7.1 my_application.cc – app name / behavior**

You might see something like:

.. code-block:: cpp 

    MyApplication::MyApplication()
    : GtkApplication("com.kaftarya.kaftarya_app", G_APPLICATION_FLAGS_NONE) {}

**✅ Example J — Change application ID (Linux)**

Change to:

.. code-block:: cpp 

    MyApplication::MyApplication()
    : GtkApplication("com.kaftarya.kaftarya_desktop", G_APPLICATION_FLAGS_NONE) {}

That’s a **Linux-specific configuration.**

Final mental picture
------------------------

•	**pubspec.yaml** → global config (version, dependencies, assets)

•	**Android** → AndroidManifest.xml, app/build.gradle

•	**iOS** → Info.plist, Xcode bundle ID & signing

•	**Web** → index.html, manifest.json

•	**macOS** → Info.plist, window behavior

•	**Windows** → flutter_window.cpp (title, size)

•	**Linux** → my_application.cc (app ID)
