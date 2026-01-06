.dart_tool
============

-----------------------
1. What is .dart_tool?
-----------------------

.dart_tool is an **internal working directory** used by **Dart and Flutter tooling.**

It is automatically created and managed by:
	- Dart SDK
	- Flutter CLI
	- pub package manager
	- Build system

**You never create, edit, or manage this folder manually.**

===============================================================================================================

--------------------------------
2. Why does .dart_tool exist?
--------------------------------

Flutter and Dart need a place to store:
	- Dependency resolution results
	- Package graphs
	- Build metadata
	- Tooling caches

Instead of mixing these files with your source code, Dart isolates them inside .dart_tool.

This keeps your project:
	- Clean
	- Deterministic
	- Reproducible across machines

===============================================================================================================

------------------------------
3. What’s inside .dart_tool?
------------------------------

.dart_tool contains:

.. code-block:: bash 

    .dart_tool/
    ├── dartpad/
    ├── flutter_build/
    ├── package_config.json
    ├── package_graph.json
    └── version

Let’s explain each one **clearly.**

===============================================================================================================

**📁 dartpad/**

Purpose:
	- Used internally by DartPad and tooling experiments
	- Stores temporary metadata for Dart execution contexts

For learners:
	- You can safely ignore this folder
	- Flutter manages it automatically

===============================================================================================================

**📁 flutter_build/**

Purpose:
	- Flutter build system metadata
	- Tracks build phases and artifacts
	- Helps Flutter perform incremental builds

This is **not** the same as build/.

.. list-table::
    :header-rows: 1

    * - Folder
      - Role
    * - build/
      - Final compiled outputs
    * - flutter_build/
      - Build orchestration & cache

===============================================================================================================

**📄 package_config.json**

Purpose:
	- Maps Dart package names → filesystem paths
	- Created by flutter pub get

Example:

.. code-block:: json

    {
    "name": "flutter",
    "rootUri": "file:///.../flutter"
    }

Why it matters:
	- Dart uses this file to resolve imports like:

Why it matters:
	- Dart uses this file to resolve imports like:

.. code-block:: dart 

    import 'package:flutter/material.dart';

❌ If this file is missing or corrupted → imports fail.

===============================================================================================================

**📄 package_graph.json**

Purpose:
	- Dependency graph of your project
	- Shows how packages depend on each other

Used by:
	- Flutter tools
	- IDEs
	- Dependency analysis

You usually never open this file.

===============================================================================================================

**📄 version**

Purpose:
	- Records Dart / Flutter tool version
	- Ensures compatibility between cached data and SDK

If versions mismatch, Flutter may **rebuild caches automatically.**

===============================================================================================================

------------------------------------------
4. When is .dart_tool created or updated?
------------------------------------------

Automatically when you run:

.. code-block:: bash 

    flutter pub get
    flutter run
    flutter build
    flutter test

You do **nothing manually.**

===============================================================================================================

--------------------------------------------
5. Should .dart_tool be committed to Git?
--------------------------------------------

❌ NO

.dart_tool is:
	- Machine-specific
	- Re-generated automatically
	- Already listed in .gitignore

Deleting it is safe.

===============================================================================================================

------------------------------
6. Can I delete .dart_tool?
------------------------------

✅ **YES — always safe**

Common use cases:
	- Fix dependency issues
	- Resolve strange build errors
	- Clean environment

.. code-block:: bash 

    rm -rf .dart_tool
    flutter pub get

Flutter will recreate it.

===============================================================================================================

-----------------------------
7. Common beginner mistakes
-----------------------------

- ❌ Editing files inside .dart_tool
- ❌ Trying to understand Flutter by reading .dart_tool
- ❌ Committing .dart_tool to Git
- ❌ Panicking when it reappears after deletion

===============================================================================================================


**Mental model**

.. code-block:: bash 

    .dart_tool = Flutter’s brain cache

- Not source code
- Not configuration
- Not output
- Just **tooling intelligence**

===============================================================================================================

Summary
	- .dart_tool is an internal Dart/Flutter tooling directory
	- Managed automatically
	- Required for package resolution
	- Safe to delete
	- Never edited manually
	- Never committed to Git

