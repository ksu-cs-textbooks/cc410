---
title: "Assignment Requirements"
weight: 10
pre: "1. "
---

This page lists the example project requirements for **Example 7** in CC 410. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

This example will cover creating new packages, classes, and enumerations within an existing project. Similar to the restaurant project, the examples will cover a smaller subset of those requirements as part of a fictional ice cream shop. 

## General Requirements

* **All code must be object-oriented.**
  * All executable code must be within a class
    * Python package files such as `__init__.py` and `__main__.py` are exempt.
  * Classes must be organized into packages based on common usage.
* **This project must include automation for compilation and execution.**
  * Java: Use Gradle with the `application` and `jacoco` plugins. The project should compile without errors. 
  * Python: Use tox configured to use Python 3.10 and a requirements file to install libraries. 
* **All code must properly compile or be interpreted.**
  * Java: It must compile using Gradle.
  * Python: It must be interpreted using Python 3.10. Where specified, type hints should be included in the code, and all code should pass a strict Mypy type check.
    * There are instances where Mypy is unable to determine the type of lambda expressions used as commands with buttons. This error can be ignored.
* **Some unit tests are required for this example - see below.**
* **Documentation comments are not required for this example, but they are recommended for your own use.**
* **All code submitted must be free of style errors.** We will be using the [Google Style Guide](https://google.github.io/styleguide/) for each language. 
  * **Style errors related to documentation comments (or lack thereof) will be ignored.**
  * Java: Use Checkstyle 10.6.0+ and the [Google Style Configuration](https://raw.githubusercontent.com/checkstyle/checkstyle/checkstyle-10.6.0/src/main/resources/google_checks.xml). 
    * You may modify the configuration to allow 4 space indentations instead of 2 space indentations.
  * Python: Use Flake8 with the `flake8-docstrings` and `pep8-naming` plugins. Code should conform to PEP 8 style with Google style docstrings. 
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).

## Assignment Requirements

{{% notice info "Dice Names" %}}

In this assignment, we'll refer to standard numerical dice following the method used by many RPGs. A  "dx" is a dice with "x" sides, numbered from 1 through x". So, a standard six-sided cube die numbered 1 through 6 is referred to as a "d6".
    
{{% /notice %}}

This milestone should include the following unit test classes and methods:

* `DiceSet` tests
  * `SumWorksCorrectly` - confirm that the `sum` method in `DiceSet` works properly by using fake dice and method stubs.
* `Main` tests
  * `TestGameMethod` - confirm that the `game` method acquires a set of two d6 from the factory, and then make sure it prints the correct output and calls `roll` at least once, using fakes, method stubs, test spies, and faking the static class.
  
## Time Requirements

Completing this project is estimated to require 1 hour.

## Grading Rubric

This assignment will be graded based on the rubric below:

* `DiceSet` unit test - 50%
* `Main` unit test - 50%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.