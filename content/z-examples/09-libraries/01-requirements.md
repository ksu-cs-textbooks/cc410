---
title: "Assignment Requirements"
weight: 10
pre: "1. "
---

This page lists the example project requirements for **Example 9** in CC 410. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

This example will cover updating an existing GUI to handle events, as well as adding some unit tests for our GUI panels. 

## General Requirements

* **All code must be object-oriented.**
  * All executable code must be within a class
    * Python package files such as `__init__.py` and `__main__.py` are exempt.
  * Classes must be organized into packages based on common usage.
* **This project must include automation for compilation and execution.**
  * Java: Use Gradle with the `application` and `jacoco` plugins. The project should compile without errors. 
  * Python: Use tox configured to use Python 3.9 and a requirements file to install libraries. 
* **All code must properly compile or be interpreted.**
  * Java: It must compile using Gradle.
  * Python: It must be interpreted using Python 3.9. Where specified, type hints should be included in the code, and all code should pass a strict Mypy type check.
    * There are instances where Mypy is unable to determine the type of lambda expressions used as commands with buttons. This error can be ignored.
* **Unit tests for `ComboPanel` are required.**
* **Documentation comments are not required for this example, but they are recommended for your own use.**
* **All code submitted must be free of style errors.** We will be using the [Google Style Guide](https://google.github.io/styleguide/) for each language. 
  * **Style errors related to documentation comments (or lack thereof) will be ignored.**
  * Java: Use Checkstyle 8.38+ and the [Google Style Configuration](https://raw.githubusercontent.com/checkstyle/checkstyle/checkstyle-8.38/src/main/resources/google_checks.xml). 
    * You may modify the configuration to allow 4 space indentations instead of 2 space indentations.
  * Python: Use Flake8 with the `flake8-docstrings` and `pep8-naming` plugins. Code should conform to PEP 8 style with Google style docstrings. 
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).

## Assignment Requirements

This milestone should include the following new GUI features:

##### Combo Panel

Demonstrate the ability to select a panel based on a combo box, and display that panel within a new panel that is not `MainWindow`

* Create a new `ParentPanel` interface to act as a shared interface between `MainWindow` and `ComboPanel`
  * Both `MainWindow` and `ComboPanel` should implement this interface.
  * The interface should have methods for `loadOrderPanel()`, and either `addItem()` (Java) or `save_item` (Python).
* Create a new `SundaePanel` base class for the Sundae panels
  * It should include the method for reacting to events
  * It should extend the base Panel class for the GUI being used
* Create a new `ComboPanel` class
  * It should include a combo box used to select the menu item, and then it should load and display the panel for that item within itself.
  * The "Save" button in the item's panel should be hidden, and instead the "Save" and "Cancel" buttons should be included in the `ComboPanel`.
  * When clicked, the "Save" and "Cancel" buttons should properly save the item selected.

Create a set of unit tests for `ComboPanel` that verify it will load the correct panel when the combo box value is updated.

##### Checkout

Create the ability to check out using a credit card via the `RestaurantRegister` library. We will also mock up the portions required for checking out via cash.

* **Java**
  * Download and install the latest JAR file release from [GitHub](https://github.com/K-State-Computational-Core/restaurantregister-java/releases).
  * View the [Javadoc](https://k-state-computational-core.github.io/restaurantregister-java/) for specifics of how to use it.
  * Review the [Source Code](https://github.com/K-State-Computational-Core/restaurantregister-java/tree/main/app/src/main/java/edu/ksu/cs/cc410/register) if desired.
  * All library classes are in the `edu.ksu.cs.cc410.register` package.
  * Post any questions or bugs regarding the library to the [GitHub Issues](https://github.com/K-State-Computational-Core/restaurantregister-java/issues) page.
  * Pull requests for bug fixes are welcome! However, in general we won't greatly change or enhance the functionality of the library overall.
* **Python**
  * Download and install the latest wheel file release from [GitHub](https://github.com/K-State-Computational-Core/restaurantregister-python/releases).
  * View the [Documentation](https://k-state-computational-core.github.io/restaurantregister-python/) for specifics of how to use it.
  * Review the [Source Code](https://github.com/K-State-Computational-Core/restaurantregister-python/tree/main/cc410/register) if desired.
  * All library classes are in the `cc410.register` package.
  * Post any questions or bugs regarding the library to the [GitHub Issues](https://github.com/K-State-Computational-Core/restaurantregister-python/issues) page.
  * Pull requests for bug fixes are welcome! However, in general we won't greatly change or enhance the functionality of the library overall.
  
## Time Requirements

Completing this project is estimated to require 1-2 hours.

## Grading Rubric

This assignment will be graded based on the rubric below:

* `ComboPanel` works correctly - 30%
* `ComboPanel` unit tests - 20%
* Install `RestaurantRegister` library - 20%
* Card payment works correctly - 30%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.