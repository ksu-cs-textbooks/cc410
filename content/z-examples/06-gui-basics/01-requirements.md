---
title: "Assignment Requirements"
weight: 10
pre: "1. "
---

This page lists the example project requirements for **Example 6** in CC 410. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

This example will cover creating new packages, classes, and enumerations within an existing project. Similar to the restaurant project, the examples will cover a smaller subset of those requirements as part of a fictional ice cream shop. 

## General Requirements

This milestone must follow these professional coding standards:

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
* **Unit tests are not required for this example.**
* **Documentation comments are not required for this example, but they are recommended for your own use.**
* **All code submitted must be free of style errors.** We will be using the [Google Style Guide](https://google.github.io/styleguide/) for each language. 
  * **Style errors related to documentation comments (or lack thereof) will be ignored.**
  * Java: Use Checkstyle 8.38+ and the [Google Style Configuration](https://raw.githubusercontent.com/checkstyle/checkstyle/checkstyle-8.38/src/main/resources/google_checks.xml). 
    * You may modify the configuration to allow 4 space indentations instead of 2 space indentations.
  * Python: Use Flake8 with the `flake8-docstrings` and `pep8-naming` plugins. Code should conform to PEP 8 style with Google style docstrings. 
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).

## Assignment Requirements

This milestone should include the following features:

* A `starfleettreats.Main` class that properly loads and displays the program's GUI.
* A `starfleettreats.gui.MainWindow` class that represents the main GUI window.
  * It should contain two panels - a main panel and a sidebar panel.
  * It should also contain two methods: one to load a particular panel into the main panel, and another to load the order screen into the main panel.
* A `starfleettreats.gui.OrderPanel` class to represent the main order screen panel.
  * It should contain two buttons, one for each sundae. They should be automatically generated from the menu.
  * When clicked, those buttons should call a method to load the appropriate panel in to the main panel. 
* A `starfleettreats.gui.SidebarPanel` class to represent the sidebar panel.
  * It should contain labels for order number, subtotal, tax, and total. 
  * It should contain an "Edit" button, that does nothing when clicked.
  * It should also include a list box that can be used to keep track of the order. The list box should expand to fill all remaining vertical space in the window.
* A `starfleettreats.gui.sundaes.TheClassicPanel` class to represent an instance of `TheClassic`.
  * It should include appropriate controls for modifying the ingredients, container, and toppings.
  * When given an instance of `TheClassic` as a parameter to the constructor, the values of the controls should be set to match the values in the instance.
  * It should include a "Save" button that, when clicked, will replace the main panel with the order screen. It **does not** have to store the values in the controls (that will be handled in a later example)
* A `starfleettreats.gui.sundaes.TheChocoPanel` class to represent an instance of `TheChoco`. **You will create this class on your own after watching the video.**
  * It should include appropriate controls for modifying the ingredients, container, and toppings.
  * When given an instance of `TheChoco` as a parameter to the constructor, the values of the controls should be set to match the values in the instance.
  * It should include a "Save" button that, when clicked, will replace the main panel with the order screen. It **does not** have to store the values in the controls (that will be handled in a later example)
  
**See below for GUI sketches.**
  
## Time Requirements

Completing this project is estimated to require 1-2 hours.

## Grading Rubric

This assignment will be graded based on the rubric below:

* `Main` class - 10%
* `MainWindow` class - 10%
* `OrderScreen` class - 10%
* `Sidebar` class - 10%
* `TheClassic` class - 20%
* `TheChoco` class - 40%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.

---
---
---

### Sundaes

##### The Classic (Banana Split)

_it doesn't get more traditional that this_

`starfleettreats.data.sundaes.TheClassic` - The price is **$5.50** and it is **1050** calories. Served in a **Waffle Cone** with **Vanilla Ice Cream** and **Banana**. Comes with **Chocolate, Whipped Cream, and Cherry**. 

##### The Choco (Chocolate and Brownie)

_a chocolate lovers' dream_

`starfleettreats.data.sundaes.TheChoco` - The price is **$7.35** and it is **1275** calories. Served in a **Dish** with **Chocolate Ice Cream** and **Brownie**. Can add **Vanilla Ice Cream**. Comes with **Chocolate, Caramel, and Peanuts**. 

### GUI Sketches

##### Main Window with Order Panel

![Main Screen](/images/e6/sketch.svg)

##### Main Window with Sundae Panel

![Main Screen](/images/e6/sketch2.svg)