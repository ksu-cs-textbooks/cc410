---
title: "Assignment Requirements"
weight: 10
pre: "1. "
---

This page lists the example project requirements for **Example 6** in CC 410. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

This example will cover creating various design patterns to represent types of dice.

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
* **No Unit Tests are required for this example. They are added in a later example.**
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

This milestone should include the following features:

* A `SingleDie` class that implements a single die (this is provided)
* A `DiceSet` class that implements the iterator pattern (part of this is provided).
* A `DiceSetBuilder` interface that follows the builder pattern.
* The following implementations of the `DiceSetBuilder` interface
  * `TwoDsixBuilder` - A pair of d6
  * `YachtDiceBuilder` - Five d6's
  * `RpgDiceBuilder` - A standard set of RPG dice - d4, d6, d8, d10, d12, d20, d100
  * `HauntedDiceBuilder` - Eight d3's numbered 0 through 2. 
  * `PigDiceBuilder` - Two d6 with the following faces: nose, tail, feet, back, left, right.
* A `DiceSetFactory` that implements the singleton and factory method patterns. It should provide a method to build the dice sets above based on the following names:
  * `2d6`
  * `yacht`
  * `rpg`
  * `haunted`
  * `pig`
* `Main` class that includes a `game()` method that will create a set of two d6 dice, roll them, and then return a string of the results in the form `[die 1] + [die 2] = [sum]` (this is provided).

## Time Requirements

Completing this project is estimated to require 1-2 hours.

## Grading Rubric

This assignment will be graded based on the rubric below:

* `DiceSet` class - 20%
* `DiceSetBuilder` interface - 20%
* `DiceSetBuilder` implementations - 20%
* `DiceSetFactory` class - 40%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.