---
title: "Assignment Requirements"
weight: 10
pre: "1. "
---

This page lists the example project requirements for **Example 2** in CC 410. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

This example will cover creating new packages, classes, and enumerations within an existing project. Similar to the restaurant project, the examples will cover a smaller subset of those requirements as part of a fictional ice cream shop. 

## General Requirements

{{% notice warning %}}

The first couple of milestones only require a subset of the general requirements introduced in the "Hello Real World" project. Read this section carefully to see what is required for this particular milestone.

{{% /notice %}}

This milestone must follow these professional coding standards:

* **All code must be object-oriented.**
  * All executable code must be within a class
    * Python package files such as `__init__.py` and `__main__.py` are exempt.
  * Classes must be organized into packages based on common usage.
* **This project must include automation for compilation and execution.**
  * Java: Use Gradle with the `application` plugin. The project should compile without errors. You may include a main class in a separate package for testing purposes only.
  * Python: Use tox configured to use Python 3.9 and a requirements file to install libraries. You may include a main class in a separate package for testing purposes only.
* **All code must properly compile or be interpreted.**
  * Java: It must compile using Gradle.
  * Python: It must be interpreted using Python 3.9. Where specified, type hints should be included in the code, and all code should pass a strict Mypy type check.
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
* **(Milestone 2) Where specified, code should contain appropriate unit tests that achieve the specified level of code coverage.**
  * Java: Use JUnit 5. You may choose to use Hamcrest for assertions.
  * Python: Use pytest. You may choose to use Hamcrest for assertions.
* **(Milestone 2) Where specified, code should contain appropriate documentation comments following the language's style guide.**
  * Java: Use javadoc to generate documentation.
  * Python: Use pdoc3 to generate documentation.

{{% /expand %}}

## Assignment Requirements

This milestone should include the following features:

* Sundae classes - 1
  * Declared in the `starfleettreats.data.sundaes` package
* Enumeration classes - 2
  * Declared in the `starfleettreats.data.enums` package

See the **Starfleet Treats Menu** section below for descriptions of what each class should contain.
  
## Time Requirements

Completing this project is estimated to require 1 hour.

## Grading Rubric

This assignment will be graded based on the rubric below:

* Sundae classes - 70%
* Enumeration classes - 30%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.

---
---
---

### Sundaes

Each sundae should be stored in an appropriately named class in the `starfleettreats.data.sundaes` package. Each sundae should include an attribute for the following data:
  * **Container** - a `Container` value (see below). It should have a **getter** and **setter** method.
  * **Toppings** - a Java [HashSet](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html) or a Python [set](https://docs.python.org/3.9/library/stdtypes.html#list) of `Topping` values (see below). 
    * This attribute should have a **getter** method that returns a **shallow copy** of the set to prevent external modification. See [HashSet's Copy Constructor (Java)](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html#HashSet-java.util.Collection-) or [set.copy (Python)](https://docs.python.org/3.9/library/stdtypes.html#frozenset.copy). 
    * This attribute should also have methods for **Add Topping** and **Remove Topping** to modify the list of toppings. 
    
In addition, each sundae should have the ability to return the following data through an appropriate **getter** method. The data may be stored as attributes or hard coded directly into the method. 
  * **Price** - a Java `double` or Python `float` value. 
  * **Calories** - an `int` value.
  * **Special Instructions** - a Java [LinkedList](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html) of `String` values or a Python [list](https://docs.python.org/3.9/library/stdtypes.html#list) of `str` values. 
    * If stored as an attribute, it should return a **shallow copy** of the list to prevent external modification. See [LinkedList's Copy Constructor (Java)](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html#LinkedList-java.util.Collection-) or [list.copy (Python)](https://docs.python.org/3.9/library/stdtypes.html#typesseq-mutable). 

Each sundae class should also override the default string representation method (`toString()` in Java or `__str__()` in Python) and return a string that properly describes the sundae. The string should be formatted as "{sundae name} in a {container}", such as "The Classic in a Waffle Cone".

It should also override the default equality method (`equals()` in Java or `__eq__()` in Python). Two items should be considered equal only if the values of all attributes are equal. 

Each sundae description will include a list of ingredients included on the sundae. Those ingredients should be represented using Boolean attributes that are set to `true` by default, with appropriate **getter** and **setter** methods. Changing any of these to `false` will cause a "Hold {ingredient}" message, such as "Hold Vanilla", to be added to the **Special Instructions** list. Likewise, changing it back to `true` will remove the appropriate message. If all ingredients are at their default values, the **Special Instructions** list should be empty. 

Likewise, each sundae description will include a **Price**, number of **Calories**, a default value for **Container** and a default set of **Toppings**. Those attributes should be populated appropriately in the constructor for the sundae. Changes to the **Container** and **Toppings** attributes will not affect the **Special Instructions** attribute. Likewise, the **Price** and number of **Calories** will remain constant, regardless of other attributes. 

##### The Classic (Banana Split)

_it doesn't get more traditional that this_

`starfleettreats.data.sundaes.TheClassic` - The price is **$5.50** and it is **1050** calories. Served in a **Waffle Cone** with **Vanilla** and **Banana**. Comes with **Chocolate, Whipped Cream, and Cherry**. 

---

### Enumerations

Each enumeration should be stored in an appropriately named class in the `starfleetsubs.data.enums` package. Each enumeration should be stored in an appropriately named class in the `starfleetsubs.data.enums` package. Each enumeration class should also override the default string representation method (`toString()` in Java or `__str__()` in Python) and return a string that properly describes the item. Python developers may also wish to override the `__repr__()` method to return this value as well.


##### Containers

_a vessel to contain the deliciousness_

`starfleettreats.data.enums.Container` - **Dish**, **Cake Cone**, **Waffle Cone**

##### Toppings

_build your own top-notch treat_

`starfleettreats.data.enums.Topping` - **Chocolate**, **Whipped Cream**, **Cherry**, **Caramel**, **Peanuts**