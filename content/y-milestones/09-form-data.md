---
title: "Form Data"
pre: "9. "
weight: 90
date: 2021-04-05T00:53:26-05:00
---

This page lists the milestone requirements for **Milestone 9** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Starfleet Subs_, based in the [Star Trek](https://en.wikipedia.org/wiki/Star_Trek) universe. 

The ninth milestone involves augmenting the menu display from the previous project by adding search and filtering functionality via an HTML form.

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

This milestone adds several pieces of functionality to your existing website, mostly based around searching and retrieving menu items.

#### Simple Search via Keywords

Your website should implement a simple search functionality via keywords, which allows the user to enter one or more words, separated by spaces, in a text input field, and then any menu items containing any of those keywords anywhere in the name of the item should be displayed on a results page.

Your search page should be accessible via the `search` route/URL. If you used a template layout that includes a search box, such as the [Bootstrap Sticky Footer with Navbar](https://getbootstrap.com/docs/4.0/examples/sticky-footer-navbar/), you may implement this search functionality using the search box in the default layout. Make sure that you specify the `action` of the form to point to the correct URL, since it will be available on all pages. The form should use the HTTP `POST` method.

You may choose to use the same template for both the search page and the results, or different templates. Also, don't forget to add a link to the `search` URL in your site's navigation in the layout template.

#### Advanced Search and Filter

Your website should also implement an advanced search and filter feature. This page will allow the user to find menu items based on the following criteria:
* Keywords (same as the simple search above)
* Type (entree, side, drink, combo)
* Price Range (minimum & maximum)
* Calories Range (minimum & maximum)

Your advanced search page should include HTML form elements for each of the items given above, arranged to make it clear to the user how to use the form. Try to make it as functional as possible based on the user's intent. For example, if the user doesn't enter any keywords, assume that they wish to find all menu items. Likewise, if the user inputs a maximum price but not a minimum, you should show all items that are less than the maximum price given. When submitted, the form should use the HTTP `POST` method. If any inputs are invalid or cannot be parsed, you should substitute them with reasonable default values.

Your advanced search page should be accessible via the `advancedsearch` route/URL. You should add a link to this URL to your site's navigation.

You **must** use the same template for both the search form and displaying results. If the search form has been completed and submitted, the submitted values should be present in the form where the results are displayed. Likewise, if the form has not been completed or no results are present, the site should clearly present that information to the user. 

#### Search Functions in Menu

The functions required to search and filter the menu should be implemented in the existing `Menu` class as static methods. You **should not** perform any searching in the web application controller itself - it should simply call these methods as needed.

Some recommended functions you may wish to implement:

* `filterKeywords(Iterable<OrderItem> items, String keywords) - returns Iterable<OrderItem>`
* `filterTypes(Iterable<OrderItem> items, boolean entree, boolean side, boolean drink, boolean combo) - returns Iterable<OrderItem>`
  * Alternatively, you could call the appropriate existing methods to collect these types initially before filtering
* `filterPrice(Iterable<OrderItem> items, float min, float max) - returns Iterable<OrderItem>`
* `filterCalories(Iterable<OrderItem> items, int min, int max) - returns Iterable<OrderItem>`

Each new method added to `Menu` should include proper unit tests. You are encouraged to use test doubles (mocks, etc.) to test these methods rather than using actual menu items. 

## Time Requirements

Completing this project is estimated to require **2 - 5** hours.

{{% notice tip %}}

_A rough estimate for this milestone would be around 750 lines of new or updated code, the majority of which is HTML and unit tests. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* Simple Search: 30%
  * Keyword Search: 15%
  * Results: 15%
* Advanced Search: 50%
  * Types: 10%
  * Price: 10%
  * Calories: 10%
  * Results: 20%
* Unit Tests: 20%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.