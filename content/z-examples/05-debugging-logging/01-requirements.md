---
title: "Assignment Requirements"
weight: 10
pre: "1. "
---

This page lists the example project requirements for **Example 5** in CC 410. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

This example will cover debugging errors in a couple of existing projects.

## General Requirements

This milestone must follow these professional coding standards:

* **All code must be object-oriented.**
  * All executable code must be within a class
    * Python package files such as `__init__.py` and `__main__.py` are exempt.
  * Classes must be organized into packages based on common usage.
* **This project must include automation for compilation, unit testing, documentation generation, and execution.**
  * Java: Use Gradle with the `application` plugin. The project should compile without errors. You may include a main class in a separate package for testing purposes only.
  * Python: Use tox configured to use Python 3.6 and a requirements file to install libraries. You may include a main class in a separate package for testing purposes only.
* **All code must properly compile or be interpreted.**
  * Java: It must compile using Gradle.
  * Python: It must be interpreted using Python 3.6. Where specified, type hints should be included in the code, and all code should pass a strict Mypy type check.
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).

{{% expand "Unenforced requirements (click to expand):" %}}

The following requirements **ARE NOT** enforced for this milestone:

* **Where specified, code should contain appropriate unit tests that achieve the specified level of code coverage.**
  * _Unit tests are already provided._
* **Where specified, code should contain appropriate documentation comments following the language's style guide.**
  * _Documentation comments will not be graded._
* **All code submitted must be free of style errors.** We will be using the [Google Style Guide](https://google.github.io/styleguide/) for each language. 
  * Provided code already is free of style errors.
  * Good style is recommended, but will not be graded.

{{% /expand %}}

## Assignment Requirements

This milestone should include the following features:

* Find and fix the errors in the provided `TicTacToe` and `SudokuFourModel` files such that the unit tests will pass.
* Include some basic logging in both files as directed in the video. 
* Create/Update `README.md` to describe how you used the Codio debugger and/or logger to fix the errors.
  
## Time Requirements

Completing this project is estimated to require 1 hour.

## Grading Rubric

This assignment will be graded based on the rubric below:

* `TicTacToe` passes tests - 10%
* `SudokuFourModel` passes tests - 10%
* Logging - 20%
  * `TicTacToe` - 10%
  * `SudokuFourModel` - 10%
* `README.md` file discussion - 60%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.