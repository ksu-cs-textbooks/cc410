---
title: "Assignment Requirements"
weight: 10
pre: "1. "
---

This page lists the example project requirements for **Example 7B** in CC 410. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

This example will cover updating an existing GUI to handle events, as well as adding some unit tests for our GUI panels. 

## General Requirements

* **All code must be object-oriented.**
  * All executable code must be within a class
    * Python package files such as `__init__.py` and `__main__.py` are exempt.
  * Classes must be organized into packages based on common usage.
* **This project must include automation for compilation and execution.**
  * Java: Use Gradle with the `application` and `jacoco` plugins. The project should compile without errors. 
  * Python: Use tox configured to use Python 3.6 and a requirements file to install libraries. 
* **All code must properly compile or be interpreted.**
  * Java: It must compile using Gradle.
  * Python: It must be interpreted using Python 3.6. Where specified, type hints should be included in the code, and all code should pass a strict Mypy type check.
    * There are instances where Mypy is unable to determine the type of lambda expressions used as commands with buttons. This error can be ignored.
* **Unit tests for `TheChocoPanel` and `TheClassicPanel` are required.**
* **Documentation comments are not required for this example, but they are recommended for your own use.**
* **All code submitted must be free of style errors.** We will be using the [Google Style Guide](https://google.github.io/styleguide/) for each language. 
  * **Style errors related to documentation comments (or lack thereof) will be ignored.**
  * Java: Use Checkstyle 8.38+ and the [Google Style Configuration](https://raw.githubusercontent.com/checkstyle/checkstyle/checkstyle-8.38/src/main/resources/google_checks.xml). 
    * You may modify the configuration to allow 4 space indentations instead of 2 space indentations.
  * Python: Use Flake8 with the `flake8-docstrings` and `pep8-naming` plugins. Code should conform to PEP 8 style with Google style docstrings. 
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).

## Assignment Requirements

This milestone should include the following new GUI features:

* Changes to the previous milestone:
  * Add a "Cancel" button to each of the sundae panels. (_This is included in the starter_)
  * Add a "Delete" button to the `SidebarPanel` panel. (_This is included in the starter_)
  * Switch the list box in the `SidebarPanel` to a tree element (Java `JTree` or tkinter `Treeview`). 
  
Once the entire project is working, you should observe the following behavior on the new tree element.

* When an item is added to the tree element in the `SidebarPanel`, the following should happen:
  * The item's string representation should be a top-level node in the tree.
  * Any special instructions for that item should be represented as child nodes of the top-level node.
  * The item should be shown fully expanded by default.
  * The tree element should only allow the user to select one item at a time.
  
In addition, the following events should be implemented in the GUI:

* When the "Save" button in any of the sundae panels is clicked, the following should happen:
  * The item currently represented by the panel should be updated such that each attribute matches the current status of the associated GUI element.
  * The item should be placed into the tree in the `SidebarPanel` if it is a new item, or the item should be updated if it is being edited.
  * The main panel in `MainWindow` should be replaced with the `OrderScreen` (_This was part of the previous milestone_).
* When the "Cancel" button in any of the sundae panels is clicked, the following should happen: 
  * If an item is being edited, any changes made in the GUI should be discarded (the item should not be changed).
  * The main panel in `MainWindow` should be replaced with the `OrderScreen` (_This was part of the previous milestone_).
* When the "Edit" button in the `SidebarPanel` is clicked, the following should happen:
  * The `OrderItem` that is currently selected should be determined. If the selection is an ingredient of that item, the code should work upwards in the tree to find the `OrderItem`.
  * The appropriate sundae panel should be loaded into the main panel in `MainWindow` and populated with the current status of the item (_Most of this should work from the previous milestone_).
  * If the item is saved via the "Save" button, it's entry in the tree element should be updated without changing the order of the items in the tree.
  * If the changes are cancelled via the "Cancel" button, no changes should be made.
* When the "Delete" button in the `SidebarPanel` is clicked, the following should happen:
  * The `OrderItem` that is currently selected should be determined. If the selection is an ingredient of that item, the code should work upwards in the tree to find the `OrderItem`.
  * That item should be removed from the tree element and any other relevant data structures in the `SidebarPanel` class.

Unit tests should be added to the corresponding test package for the following classes:

* Each sundae panel in `starfleettreats.gui.sundaes`

_See below for a list of suggested unit tests. You should achieve at or near 100% coverage on these classes. We will not unit test the `MainWindow`, `OrderPanel`, or `SidebarPanel` classes in this milestone._
  
## Time Requirements

Completing this project is estimated to require 1-2 hours.

## Grading Rubric

This assignment will be graded based on the rubric below:

* Tree element displays order items correctly: 10%
* "Save" buttons work properly for all items: 20%
* "Cancel" buttons work properly for all items: 10%
* "Edit" button works properly for all items: 20%
* "Delete" button works properly for all items: 10%
* Unit Tests: 30%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.

---
---
---

##### Sundae Panels

Each sundae panel test class should contain unit tests for the following:

* `testDefaultConstructor()` - create the panel without providing an existing element, and assert that it creates a new instance of the correct item.
* `testBadActionCommand()` - call the `actionPerformed()` method with a bad action command, and assert that an exception is not thrown.
* `testContainerComboBox(Container)` - instantiate a panel with an existing item, change the value of the container combo box in the GUI to the `Container` value, and fire a "save" action, then verify that the item has the correct container value.
* `testContainerComboBoxSetCorrectly(Container)` - instantiate a panel with an existing item using the given `Container`, and assert that the Container combo box is set to the correct value. 
* `test<Ingredient>CheckBox()` - instantiate a panel with an existing item, change the value of the ingredient check box in the GUI to a value, and fire a "save" action, then verify that the item has the correct value. Do this for both `true` and `false`.
* `test<Ingredient>CheckBoxSetCorrectly()` - instantiate a panel with an existing item with a given value for ingredient, and assert that the ingredient checkbox is set to the correct value. Do this for both `true` and `false`.
* `testToppingCheckBox(Topping)` - instantiate a panel with an existing item, change the value of the topping check box in the GUI to a value, and fire a "save" action, then verify that the item has the correct value. Do this for both `true` and `false`.
* `testToppingCheckBoxSetCorrectly(Topping)` - instantiate a panel with an existing item with a given value for topping, and assert that the topping checkbox is set to the correct value. Do this for both `true` and `false`.
* `testCancelButton()` - instantiate a panel with an existing item, change several values in the GUI, and fire a "cancel" action, then assert that the item is unchanged from its previous state.

{{% notice note "Update Permissions" %}}

To allow proper unit testing, you may need to relax the permissions on several elements inside of your GUI classes. I recommend using `package-private` in Java, with no modifier - see [this document](https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html). Then, any unit tests that are in the same package can have access to those members. For Python, switching from double underscore private attributes to single underscore protected attributes is sufficient. 

This has already been done on the `item` attribute in the sundae panels.

{{% /notice %}}