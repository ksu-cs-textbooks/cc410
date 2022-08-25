---
title: "Documentation & Testing"
pre: "2. "
weight: 30
date: 2021-08-17T00:53:26-05:00
---

This page lists the milestone requirements for **Milestone 2** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _That's a Wrap_, offering wraps of all shapes and sizes to celebrate our favorite movies. 

The second milestone involves writing documentation and unit tests for our existing code base. Our goal is to adequately test each part of our code via **unit tests**, reaching 100% code coverage at a minimum. In addition, we'll add all of the required **documentation comments** in our existing code. 

## General Requirements

{{% notice warning %}}

The first couple of milestones only require a subset of the general requirements introduced in the "Hello Real World" project. Read this section carefully to see what is required for this particular milestone.

{{% /notice %}}

This milestone must follow these professional coding standards:

* **All code must be object-oriented.**
  * All executable code must be within a class
    * Python package files such as `__init__.py` and `__main__.py` are exempt.
  * Classes must be organized into packages based on common usage.
* **This project must include automation for compilation, unit testing, documentation generation, and execution.**
  * Java: Use Gradle with the `application` plugin. The project should compile without errors. You may include a main class in a separate package for testing purposes only.
  * Python: Use tox configured to use Python 3.9 and a requirements file to install libraries. You may include a main class in a separate package for testing purposes only.
* **All code must properly compile or be interpreted.**
  * Java: It must compile using Gradle.
  * Python: It must be interpreted using Python 3.9. Where specified, type hints should be included in the code, and all code should pass a strict Mypy type check.
* **Where specified, code should contain appropriate unit tests that achieve the specified level of code coverage.**
  * Java: Use JUnit 5. You may choose to use Hamcrest for assertions.
  * Python: Use pytest. You may choose to use Hamcrest for assertions.
* **Where specified, code should contain appropriate documentation comments following the language's style guide.**
  * Java: Use javadoc to generate documentation.
  * Python: Use pdoc3 to generate documentation.
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).

{{% expand "Unenforced requirements (click to expand):" %}}

The following requirements **ARE NOT** enforced for this milestone, but will be enforced in later milestones that use the same code. We will focus on learning to meet each of these requirements in future modules. However, you are welcome to "plan ahead" by minimizing the number of style errors in your code and adding some basic documentation where desired. 

{{% notice tip "Naming Standards" %}}

You can make things easier on yourself by following proper naming standards for your language of choice, even though we aren't enforcing a style guide for this milestone.

* **Java** - All names are in CamelCase. Classes start with uppercase, like `ClassName`, methods and attributes start with lowercase like `methodName`. See the [Google Style Guide](https://google.github.io/styleguide/javaguide.html#s5-naming).
* **Python** - All names are lowercase with underscores like `method_name`, with the exception of classes, which are named in CamelCase starting with an uppercase letter like `ClassName`. See the [Google Style Guide](https://google.github.io/styleguide/pyguide.html#s3.16-naming).

It is easier to get this correct from the start, then having to refactor your code later. Of course, major refactoring is also a good lesson that guarantees you'll get it right in the future!

{{% /notice %}}

* **(Milestone 3) All code submitted must be free of style errors.** We will be using the [Google Style Guide](https://google.github.io/styleguide/) for each language. 
  * Java: Use Checkstyle 8.38+ and the [Google Style Configuration](https://raw.githubusercontent.com/checkstyle/checkstyle/checkstyle-8.38/src/main/resources/google_checks.xml). 
    * You may modify the configuration to allow 4 space indentations instead of 2 space indentations.
  * Python: Use Flake8 with the `flake8-docstrings` and `pep8-naming` plugins. Code should conform to PEP 8 style with Google style docstrings. 

{{% /expand %}}

## Assignment Requirements

This milestone should include the following features:

###### Data Types

* Each Wrap, Side, and Drink class should contain complete typing information.
  * Java - this is already handled by the compiler, so no changes are needed.
  * Python - the code should contain complete type annotations and achieve low imprecision percentage in Mypy using strict type checking. 

###### Unit Tests

* Each Wrap, Side, and Drink class should have a corresponding class of unit tests that achieve **100% code coverage** and **adequately test all features of those classes**. 
  * See the discussion below for more information on unit tests to be included.
  * Each unit test should be in a matching package in the `test` directory for the class it is testing.
  * Python - unit tests **do not require type annotations**.
  * Where possible, use **parameterized unit tests** to reduce the number of individual tests written.
  * You may use any form of assertions, including the Hamcrest library.

###### Documentation

* Each Wrap, Side, Drink, and Enumeration class should have all required documentation comments.
  * **Every method must be documented, including parameters and return values.**
  * Checkstyle/Flake8 should not give any errors related to documentation in the `src` directory. 
  * You are encouraged, but not required, to create documentation comments for unit tests.
  * You should be able to generate documentation using javadoc/pdoc3 as shown in the "Hello Real World" project. 
  * You will be graded on the content of the comments - make sure they are descriptive and succinct, with the appropriate sections/tags. 

###### UML Class Diagram

* Create a **UML Class Diagram** representing the structure of this program. 
  * Store the UML diagram as an image file (PNG preferred).
  * Place the image in the root of the project directory (directly inside the `java` or `python` folder).
  * Make sure it is committed to GitHub and included in your project release.
  * You may include additional materials, such as the source file used to create the image.

{{% notice tip "Helpful Hints" %}}

_Some quick tips from when I did this milestone:_

* **DO NOT COPY FROM YOUR SOURCE CODE FROM MILESTONE 1!** Write your unit tests solely using the menu on the previous milestone and the list of tests needed on this milestone. In that way, you will confirm that your tests match the specification and confirm the code is correct, not that your tests match your existing code! Even I found a few errors in my code through writing these unit tests.
* You may wish to create global attributes in your unit test classes and then generalize your unit tests. For example, add a global `PRICE = 0.50` attribute, and then use that value in your unit test. In that way, when you copy and paste unit test code, you can simply change the global attributes to match the item being tested. Many tests can be generalized in that way such that all wraps test classes share the same code for many tests, referring to global attributes that are changed in each class. The same works for drinks and sides.  
* Generalizing the tests for individual ingredients in wraps and drinks (such as `pepperoni` or `cherry`) _can be done_ using reflection or metaprogramming, but **I don't recommend it**. Since each ingredient is an individual attribute, generalization is very complex and prone to errors. Those tests were hard-coded for each individual ingredient in my solution. 
* **Java** users may wish to review the [EnumSource](https://www.baeldung.com/parameterized-tests-junit-5#3-enum) option for parameterized tests using enums.
* **Python** users can use enums directly in parameterized tests, as in `@pytest.mark.parametrize("crust", Crust)`.
* When following Google's style for Java, you are required to include `default` branches in switch statements across enums, which will be unreached in code coverage. This is fine, but a good reason to avoid switch statements, as you will never get 100% code coverage! I ended up changing my model solution to remove switch statements.

_-Russ_

{{% /notice %}}
  
## Time Requirements

Completing this project is estimated to require 3-8 hours.

{{% notice note "Expected Scope" %}}

_In my testing, this milestone requires around 3500-4000 lines of code (including very rudimentary documentation comments) in the unit tests directory. As with the prior milestone, much of the code can be carefully copy-pasted between files with similar attributes. My best suggestion is to pick one of the complex wraps and start there writing unit tests. Once you have the wraps all working, the sides and drinks are pretty easy and use much of the same structure. There are several hundred unit tests in my model solution. I ended up finding half a dozen errors in my model solution for milestone 1, showing the importance of unit testing! -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* Unit Tests - 60%
  * Wrap Classes - 30%
  * Side Classes - 10%
  * Drink Classes - 20%
* Documentation Comments - 30%
  * Wraps Classes - 8%
  * Side Classes - 8%
  * Drink Classes - 8%
  * Enumeration Classes - 6%
* UML Class Diagram - 10%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.
* Any portion of the project which does not meet the general requirements listed above will have a commensurate amount of points deducted.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

{{% notice note "Code Review" %}}

_As part of the grading of all assignments in this course, I will be doing a deep dive into a few classes in your code. This will include leaving detailed comments on code style and format in GitHub. I will usually choose various classes to review at random, and any issues found in that class will be verified in other classes of the same type. - Russ_

{{% /notice %}}


## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.

---
---
---

## Unit Tests

##### Wrap

Each test class should contain unit tests for the following (this is not an exhaustive list, but should get close to 100% coverage):

* When a new object is created:
  * The instructions list should be empty
  * The default shell should be set correctly
  * The addins should be set correctly
  * The calories should be set correctly
* For every shell option:
  * The price should be set correctly, including any surcharges for shell types.
  * The string representation of the item should be correct
* For every ingredient
  * Each ingredient should be included by default
  * Adding or removing an ingredient adds or removes an item in the instructions list
* For every addin:
  * If the addin is included by default, it should be in the addins list on a new object
  * Adding or removing an addin makes the correct modification to the addins list
* Equality tests:
  * Two instances of the same object are equal
  * Two instances with different shells are not equal
  * Two instances with different ingredients are not equal
  * Two instances with different addins are not equal
  * An instance of another object is not equal to an instance of this object (should not cause an exception)
* Other tests:
  * Changing multiple ingredients should add or remove multiple items in the instructions list

##### Sides

Each test class should contain unit tests for the following (this is not an exhaustive list, but should get close to 100% coverage):

* When a new object is created:
  * The default size should be set correctly
* For every size option:
  * The price should be set correctly
  * The calories should be set correctly
  * The string representation of the item should be correct
* Equality tests:
  * Two instances of the same object are equal
  * Two instances with different sizes are not equal
  * An instance of another object is not equal to an instance of this object (should not cause an exception)

##### Drinks

Each test class should contain unit tests for the following (this is not an exhaustive list, but should get close to 100% coverage):

* When a new object is created:
  * The instructions list should be empty
  * The default size should be set correctly
* For every size option:
  * The price should be set correctly
  * The calories should be set correctly
  * The string representation of the item should be correct
* For every flavor
  * Default flavors should be included by default, others should not be included by default
  * Adding or removing a flavor adds or removes an item in the instructions list
* Equality tests:
  * Two instances of the same object are equal
  * Two instances with different sizes are not equal
  * Two instances with different flavors are not equal
  * An instance of another object is not equal to an instance of this object (should not cause an exception)
* Other tests:
  * Changing multiple flavors should add or remove multiple items in the instructions list

{{% notice tip %}}

Remember that unit tests should test a single unit of code. So, make sure your unit tests are as short and concise as possible to allow you to pinpoint individual errors.

**Extra Credit:** After writing all of the unit tests listed above, feel free to suggest any unit tests you feel are missing. Email your added tests to the course help email address and you may earn bug bounty points for your suggestions!

{{% /notice %}}