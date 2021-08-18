---
title: "Website Basics"
pre: "8. "
weight: 80
date: 2021-03-24T00:53:26-05:00
---

This page lists the milestone requirements for **Milestone 8** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Starfleet Subs_, based in the [Star Trek](https://en.wikipedia.org/wiki/Star_Trek) universe. 

The eighth milestone involves moving into the web by creating a data-driven website to display the menu and some other information about the restaurant.

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

###### Web Framework

Add a Web Framework to the existing project.

* **Java** - Install the [Spring](https://spring.io/) framework using the [Spring Initializr](https://start.spring.io/). It should include the Spring Boot DevTools, Spring Web, and Thymeleaf Template Engine as dependencies.
* **Python** - Install the [Flask](https://flask.palletsprojects.com/en/1.1.x/) framework and the [Flask-Classful](https://flask-classful.teracy.org/) extension. You may also wish to install `python-dotenv` to use a `.flaskenv` file. 

{{% notice warning %}}

**Java Users** - You will need to remove the `'org.junit.jupiter:junit-jupiter-api:5.6.2'` entry from the `testImplementation` section of the dependencies. It conflicts with the version provided by Spring.

**Python Users** - You may ignore any type errors from `flask_classful` by adding `#type: ignore` after the import line.

{{% /notice %}}

###### Web Code

* Create a new `starfleetsubs.web` package.
* Create a `starfleetsubs.web.MenuController` class to act as the controller. It should include the following routes:
  * `/` - a home page for the application.
  * `/about` - an about page with the text given at the bottom of the page.
  * `/menu` - a page that includes the entire menu (all predefined combos, entrees, sides, and drinks). 
    * It should use the existing `Menu` class to collect these items. 
    * You may add additional methods (with requisite unit tests) to the `Menu` class as desired.
* Update the required files to launch the web application properly as shown in the example video.

###### Templates

Create a base layout file including the following:

* Valid HTML5 structure
* A &lt;title&gt; element including the page name, followed by ` - Starfleet Subs`
* A &lt;body&gt; containing:
  * &lt;nav&gt; that contains links to all pages in the application
  * &lt;main&gt; containing all the content in the page
  * &lt;footer&gt; containing the following copyright notice: "&copy; 2021 Starfleet Subs"
* It is recommended (but not required) to build upon an existing template. You may wish to review the [Bootstrap Examples](https://getbootstrap.com/docs/4.6/examples/). 

Create the following template files to match the routes listed above:

* `index.html` contains an &lt;h1&gt; tag with the title "Starfleet Subs" and the following text in a paragraph (you may add additional text as desired):

> Welcome to Starfleet Subs! Our motto: to boldly eat a sandwich where no sandwich has been eaten before!

* `about.html` contains an &lt;h1&gt; tag with the title "About Starfleet Subs" and the following text in a paragraph (you may add additional text as desired):

> Starfleet Subs was developed as part of the CC 410 course at Kansas State University by &lt;your name here&gt;.

* `menu.html` contains the following content:
  * an &lt;h1&gt; containing "Menu"
  * an &lt;h2&gt; containing the four categories of menu items (entree, side, drink, combo)
  * Each menu item should be placed in a &lt;div&gt; with the class `menu-item`. It should include:
    * The name of the item
    * The price of the item
    * The calories of the item
    * _If the item comes in multiple sizes, the price and calories for each size should be listed!_
  * You may use additional HTML elements & CSS style to improve the readability of this page as you see fit! As with the GUI project, this is your chance to explore a bit. 
    * The model solution uses the [Card](https://getbootstrap.com/docs/4.6/components/card/) component and [Row Columns](https://getbootstrap.com/docs/4.6/layout/grid/#row-columns) in Bootstrap. 
  * Under the "Combo" heading, add a note that any entree, side, and drink may be combined for a combo discount, and print the current combo discount value as well. (_Hint: you'll have to send this through the controller to the template somehow..._)

{{% notice tip %}}

You can format currency values directly in your templates! See [Formatting Currencies in Spring using Thymeleaf](https://www.baeldung.com/spring-thymeleaf-currencies) for Java or using the familiar Python [String.format()](https://realpython.com/python-formatted-output/) function as demonstrated in this [StackOverflow](https://stackoverflow.com/a/31158813) comment.

{{% /notice %}}

## Time Requirements

Completing this project is estimated to require **2 - 5** hours.

{{% notice tip %}}

_A rough estimate for this milestone would be around 500 lines of new or updated code, the majority of which is HTML. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* Web Framework Installation: 10%
* Web Code: 30%
  * Index & About Routes: 10%
  * Menu Route: 20%
* Templates: 60%
  * Layout Template: 20%
  * Index & About Templates: 10%
  * Menu Template: 30%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.

---
---
---

## Web Sketches

Below is a screenshot from the model solution for some web design inspiration.

![Main Window](/images/410_m8_menu.png)