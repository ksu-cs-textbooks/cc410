---
title: "Hello Real World"
pre: "0. "
weight: 10
date: 2020-12-29T00:53:26-05:00
---

This page lists the milestone requirements for the **Example 1 - Hello Real World** project. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

This assignment mimics the traditional "Hello World" project that most programmers learn as their first program, but done following professional coding standards and guidelines. In effect, this is how a professional coder would write "Hello World" as a project for work. 

## General Requirements

All projects must follow these professional coding standards:

* **All code must be object-oriented.**
  * All executable code must be within a class
    * Python package files such as `__init__.py` and `__main__.py` are exempt.
  * Classes must be organized into packages based on common usage.
* **All projects must include automation for testing, style checking, and documentation generation.**
  * Java: Use Gradle with the `application`, `jacoco`, and `checkstyle` plugins.
  * Python: Use tox configured to use Python 3.6 and a requirements file to install libraries.
* **All code must properly compile and be executable.**
  * Java: It must compile and execute using Gradle.
  * Python: It must execute using Python 3.6. Where specified, type hints should be included in the code, and all code should pass a strict Mypy type check.
* **All code submitted must be free of style errors.** We will be using the [Google Style Guide](https://google.github.io/styleguide/) for each language. 
  * Java: Use Checkstyle 8.38+ and the [Google Style Configuration](https://raw.githubusercontent.com/checkstyle/checkstyle/checkstyle-8.38/src/main/resources/google_checks.xml). 
    * You may modify the configuration to allow 4 space indentations instead of 2 space indentations.
  * Python: Use Flake8 with the `flake8-docstrings` and `pep8-naming` plugins. Code should conform to PEP 8 style with Google style docstrings. 
* **Where specified, code should contain appropriate unit tests that achieve the specified level of code coverage.**
  * Java: Use JUnit 5. You may choose to use Hamcrest for assertions.
  * Python: Use pytest. You may choose to use Hamcrest for assertions.
* **Where specified, code should contain appropriate documentation comments following the language's style guide.**
  * Java: Use javadoc to generate documentation.
  * Python: Use pdoc3 to generate documentation.
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).

## Assignment Requirements

This project should include the following features:

* **A `HelloWorld` class that contains a `main` method.**
  * The `main` method should print "Hello World" if no command line arguments are received.
  * The `main` method should print "Hello {arg}" if a command line argument is received.
* **Unit tests that achieve 100% code coverage in the `HelloWorld` class**, properly testing both with and without command-line arguments.
* **Documentation comments following the language's documentation standards** for each class, method, and any class attributes.
  * Python: All `.py` files should also include a file docstring, including `__init__.py` and `__main__.py` files for packages.
* **All variables and methods in the `HelloWorld` class must include explicit data types**
  * Java: no changes are needed since Java already requires this. 
  * Python: add type hints to all methods and variables. Type hints in the `HelloWorld` class must not use `Any` as a type. 
  
## Time Requirements

Completing this project is estimated to require 2-5 hours depending on familiarity with the tools involved.

## Grading Rubric

This assignment will be graded based on the rubric below:

* `HelloWorld` class - 30%
* Unit Tests - 30%
* Documentation - 20%
* Automation - 20%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.
* Any portion of the project that does not pass a style check will have its grade reduced by 30% of the total points available on that portion.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.