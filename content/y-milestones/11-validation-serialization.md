---
title: "Validation & Serialization"
pre: "11. "
weight: 110
date: 2021-04-21T00:53:26-05:00
---

This page lists the milestone requirements for **Milestone 11** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Starfleet Subs_, based in the [Star Trek](https://en.wikipedia.org/wiki/Star_Trek) universe. 

The eleventh milestone involves adding form validation and serialization to the existing project, specifically targeted at custom menu items.

## General Requirements

This milestone must follow these professional coding standards:

* **All code must be object-oriented.**
  * All executable code must be within a class
    * Python package files such as `__init__.py` and `__main__.py` are exempt.
  * Classes must be organized into packages based on common usage.
* **This project must include automation for compilation, unit testing, style checking, documentation generation, and execution.**
  * Java: Use Gradle with the `application` plugin. The project should compile without errors.
  * Python: Use tox configured to use Python 3.6 and a requirements file to install libraries.
* **All code must properly compile or be interpreted.**
  * Java: It must compile using Gradle.
  * Python: It must be interpreted using Python 3.6. Where specified, type hints should be included in the code, and all code should pass a strict Mypy type check with low imprecision percentage.
    * Classes in the `starfleetsubs.gui` package **do not require** type hints in Python, though you may continue to use them if they are helpful. Any errors from Mypy originating in these classes will be ignored.
* **Where specified, code should contain appropriate unit tests that achieve the specified level of code coverage.**
  * Java: Use JUnit 5. You may choose to use Hamcrest for assertions.
  * Python: Use pytest. You may choose to use Hamcrest for assertions.
* **Where specified, code should contain appropriate documentation comments following the language's style guide.**
  * Java: Use javadoc to generate documentation.
  * Python: Use pdoc3 to generate documentation.
* **All code submitted must be free of style errors.** We will be using the [Google Style Guide](https://google.github.io/styleguide/) for each language. 
  * Java: Use Checkstyle 8.38+ and the [Google Style Configuration](https://raw.githubusercontent.com/checkstyle/checkstyle/checkstyle-8.38/src/main/resources/google_checks.xml). 
    * You may modify the configuration to allow 4 space indentations instead of 2 space indentations.
  * Python: Use Flake8 with the `flake8-docstrings` and `pep8-naming` plugins. Code should conform to PEP 8 style with Google style docstrings. 
  * **All HTML must conform to the HTML5 standard.** Use the [W3C Validator](https://validator.w3.org/) to check your rendered pages if desired.
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).

## Assignment Requirements

This milestone consists of two portions: adding form validation to the forms for creating and editing custom items, and serializing those custom items to a file.

### Form Validation

Update the forms for creating and editing custom menu items to perform server-side validation. This should use the built-in features of either Java Spring or Python Flask, as demonstrated in the example video. The following validation rules should be enforced:

* The `name` of the custom menu item should not be null, and have at least 3 characters.
* The `price` of the custom menu item must be greater than or equal to 0, and support no more than 2 decimal places. You may either use a validator for this or implement rounding in the setter for this item.
* The `calories` of the custom menu item must be greater than or equal to 0.

When validation fails, the user should be taken back to the form, where the entered values are still present and the validation errors are clearly displayed. 

{{% notice tip %}}

Java developers will need to change the `price` attribute to use the `BigDecimal` class ([Javadoc](https://docs.oracle.com/javase/8/docs/api/java/math/BigDecimal.html)) in order to enforce a limit on the number of digits using a validator. I recommend maintaining the existing getter and setters for `price` (adapting them to use the value in the new `BigDecimal` class) and then adding new getters and setters for this attribute. Likewise, in the HTML form, you'll use the new `BigDecimal` attribute instead of the existing `price`. See the example video for details.

{{% /notice %}}

### Serialization

Update the application to use serialization to store and load the list of custom items. You may choose any file format (XML, JSON, or binary, or another of your choosing). See the serialization examples on GitHub ([Java](https://github.com/K-State-Computational-Core/serialization-examples-java) or [Python](https://github.com/K-State-Computational-Core/serialization-examples-python)) as well as the textbook for code you can use.

* The custom menu items should be loaded into memory when the singleton instance of the `CustomItemList` class is created. In Java, this would most likely be the `getInstance()` method, while in Python it would be in the `__new__()` method. So, when the user first visits the `/customitems` page, the previously saved custom items should appear.
* The `CustomItemList` class should implement a new method called `save` that will serialize the current contents of the custom item list to a file.
* The application should add a new HTTP POST route to the `CustomItemController` with the path `/customitems/save` that will save the existing custom items list to file by calling the new `save` method. 
* Add an HTML form to the `/customitems` index page containing a button to save the custom items by sending a POST request to the new route. This form will be very similar to the one used on the page for deleting items.

The code should include proper exception handling when reading and writing files, as well as ensuring the file is properly closed. In Java, a [try with resources](Yhttps://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html) statement is recommended. In Python, a [with inside a try](https://realpython.com/python-exceptions/) structure is recommended. You may simply catch the generic exception and print it to the terminal instead of handling multiple exception types.

As proof of working serialization, create the following custom menu item and serialize it to a file, then ensure that file is committed to your Git repository when committing this project.

* **Name**: The Roddenberry
* **Price**: 8.19
* **Calories**: 1921

## Time Requirements

Completing this project is estimated to require **2 - 5** hours.

{{% notice tip %}}

_A rough estimate for this milestone would be around 100 lines of new or updated code.-Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* Validation: 30%
  * Name: 10%
  * Price: 10%
  * Calories: 10%
* Serialization: 70%
  * Save: 30%
  * Load: 30%
  * Preloaded Entry "The Roddenberry": 10%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.