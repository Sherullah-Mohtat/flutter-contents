Installation
=============








macOS Terminal
----------------

**⭐ Create Flutter Project Recommended way (for long-term, professional apps)**

.. code-block:: bash 

    flutter create --org com.kaftarya --platforms=android,ios,web,macos,windows,linux kaftarya_app

**📌 What this command will generate**

+--------------+----------------+
| Platform     | Status         |
+==============+================+
| Android      | ✔ Kotlin       |
+--------------+----------------+
| iOS          | ✔ Swift        |
+--------------+----------------+
| Web          | ✔ Enabled      |
+--------------+----------------+
| macOS        | ✔ Enabled      |
+--------------+----------------+
| Windows      | ✔ Enabled      |
+--------------+----------------+
| Linux        | ✔ Enabled      |
+--------------+----------------+

**📌 After running the command**

Go into your project:

.. code-block:: bash 

    cd kaftarya_app

Run on macOS:

.. code-block:: bash 

    flutter run -d macos

Run on iOS:

.. code-block:: bash 

    open -a Simulator
    flutter run -d ios

Run Web:

.. code-block:: bash 

    flutter run -d chrome

Run Windows (if you build on Windows):

.. code-block:: bash 

    flutter run -d windows

Run Linux (if you build on Linux):

.. code-block:: bash 

    flutter run -d linux

**⚠️ Important for macOS users**

On macOS, you **cannot** build Windows or Linux apps directly.

But the project **will still include** their folders.

To build them:

	•	Windows app → open same project on Windows

	•	Linux app → open same project on Linux

But Web, iOS, macOS, Android all work on macOS natively.