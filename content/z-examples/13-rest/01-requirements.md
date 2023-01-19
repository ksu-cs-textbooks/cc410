---
title: "Assignment Requirements"
weight: 10
pre: "1. "
---

This page lists the example project requirements for **Example 13** in CC 410. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

This example will cover updating an existing project to allow editing and deleting of movies following a RESTful architectural style.

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
* **Unit tests are not required.**
* **Documentation comments are not required for this example, but they are recommended for your own use.**
* **All code submitted must be free of style errors.** We will be using the [Google Style Guide](https://google.github.io/styleguide/) for each language. 
  * **Style errors related to documentation comments (or lack thereof) will be ignored.**
  * Java: Use Checkstyle 10.6.0+ and the [Google Style Configuration](https://raw.githubusercontent.com/checkstyle/checkstyle/checkstyle-10.6.0/src/main/resources/google_checks.xml). 
    * You may modify the configuration to allow 4 space indentations instead of 2 space indentations.
  * Python: Use Flake8 with the `flake8-docstrings` and `pep8-naming` plugins. Code should conform to PEP 8 style with Google style docstrings. 
  * **All HTML must conform to the HTML5 standard.** Use the [W3C Validator](https://validator.w3.org/) to check your rendered pages if desired.
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).

## Assignment Requirements

This milestone should include a new controller `RestMovieContoller` that follows a RESTful architectural style. Specifically, it should include the following URL routes:

| HTTP Method | URL Path | Description | CRUD Method |
|:-----------:|----------|-------------|:-----------:|
| GET | `/movies` | Display all movies. | Read All |
| GET | `/movies/{id}` | Display a single movie | Read One |
| GET | `/movies/{id}/edit` | Display a form to edit the movie | N/A |
| POST | `/movies/{id}` | Update the movie | Update |
| GET | `/movies/{id}/delete` | Display a warning page before deleting a movie | N/A |
| POST | `/movies/{id}/delete` | Delete the movie | Destroy |
 
## Time Requirements

Completing this project is estimated to require 1-2 hours.

## Grading Rubric

This assignment will be graded based on the rubric below:

* Read All Route - 10%
* Read One Route - 30%
* Edit Form & Route - 30%
* Delete Form & Route - 30%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes 