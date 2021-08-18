---
title: "Inheritance"
pre: "3. "
weight: 40
date: 2021-01-23T00:53:26-05:00
---

This page lists the milestone requirements for **Milestone 3** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Starfleet Subs_, based in the [Star Trek](https://en.wikipedia.org/wiki/Star_Trek) universe. 

The third milestone involves refactoring our code to take advantage of **inheritance** and the use of **interfaces**. We'll also need to update our documentation and unit tests accordingly.

## General Requirements

{{% notice warning %}}

This project is the first that requires **ALL** general requirements introduced in the "Hello Real World" project. Read this section carefully to see what is required for this particular milestone.

{{% /notice %}}

This milestone must follow these professional coding standards:

* **All code must be object-oriented.**
  * All executable code must be within a class
    * Python package files such as `__init__.py` and `__main__.py` are exempt.
  * Classes must be organized into packages based on common usage.
* **This project must include automation for compilation, unit testing, style checking, documentation generation, and execution.**
  * Java: Use Gradle with the `application` plugin. The project should compile without errors. You may include a main class in a separate package for testing purposes only.
  * Python: Use tox configured to use Python 3.6 and a requirements file to install libraries. You may include a main class in a separate package for testing purposes only.
* **All code must properly compile or be interpreted.**
  * Java: It must compile using Gradle.
  * Python: It must be interpreted using Python 3.6. Where specified, type hints should be included in the code, and all code should pass a strict Mypy type check with low imprecision percentage.
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
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).

## Assignment Requirements

This milestone should include the following features:

* A new `starfleetsubs.data.menu.OrderItem` interface that is implemented by all entrée, side, and drink classes
  * See below for the description of what this interface should contain
* New abstract base classes for each type of menu item:
  * Entrées should inherit from `starfleetsubs.data.entrees.Entree` base class
  * Sides should inherit from the `starfleetsubs.data.sides.Side` base class
  * Drinks should inherit from the `starfleetsubs.data.drinks.Drink` base class
* Each new base class should contain all elements that are shared by each type of menu item
  * See below for the description of what the base classes should contain
* A new **static** class `starfleetsubs.data.menu.Menu` that contains the full menu
  * See below for the description of what this `Menu` class should contain
* Updated unit tests for each menu item to check for proper typing
  * Each menu item should implement the `OrderItem` interface
  * Each menu item should inherit from the correct parent class
  * Each class except `Menu` and `OrderItem` should report near 100% code coverage. 
* Add a unit test class for `Menu` to confirm that each possible menu item is present in the menu. 
* Update the **UML Class Diagram** to represent the new structure of the code. 
* Make sure all code is **free from style errors** using Checkstyle/Flake8. 
  
## Time Requirements

Completing this project is estimated to require 3-8 hours.

{{% notice tip %}}

_A rough estimate for this milestone would be around 1000 lines of new or updated code, and around 500 lines of redundant code removed. It could vary widely based on how you choose to implement the inheritance between the base classes and the interface. My model solution for this milestone now contains 526 unit tests in total. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* `OrderItem` Interface - 25%
* Base Classes - 30%
  * `Entree` Base Class - 10%
  * `Side` Base Class - 10%
  * `Drink` Base Class - 10%
* `Menu` Class - 20%
* Updated Unit Tests - 10%
* `Menu` Unit Tests - 10%
* UML Class Diagram - 5%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.

---
---
---

## New Classes

##### OrderItem Interface

The `starfleetsubs.data.menu.OrderItem` class should be created as an interface that can be implemented by all other menu items. It should contain the following elements as abstract methods/properties:
* A getter for **Price**
* A getter for **Calories**
* A getter for **Special Instructions**

Each menu item (entrées, sides, and drinks) should be refactored to implement this interface. This will require some changes:

* **Price** and **Calories** is straightforward
* **Special Instructions** requires some modification
  * **Entrées** - the **Special Instructions** list should now include each of the **Condiments** on the entrée. This could be done via the new `Entree` base class.
  * **Sides** - the **Special Instructions** getter will need to be added, and it should just return an empty list since sides do not have special instructions. This can be done via the new `Side` base class. 
  * **Drinks** - no changes needed

Accordingly, the **unit tests** for some of these classes will need updated, as discussed below.

##### Base Classes

Each of the three types of menu items should directly inherit from a new abstract base class. These classes should not be instantiated!

* `starfleetsubs.data.entrees.Entree` is the base class for all entrée items. It should include the following elements that are common to all entrée classes:
  * **Bread** - attribute with getter and setter.
  * **Condiments** - attribute with getter, **Add Condiment** and **Remove Condiment** methods.
  * **Price** - abstract getter. This should be overridden in the subclass to return the correct price.
  * **Calories** - abstract getter. This should be overridden in the subclass to return the correct calories.
  * **Special Instructions** - getter. This should be overridden in the subclass to return the correct list of special instructions. 
    * One easy way to do this: the method in the superclass could be used to add the list of condiments to the list, and then the subclass method could call the superclass method as part of its code. 
* `starfleetsubs.data.sides.Side` is the base class for all side items. It should include the following elements that are common to all side classes:
  * **Size** - getter and setter.
  * **Price** - abstract getter. This should be overridden in the subclass to return the correct price based on the size.
  * **Calories** - abstract getter. This should be overridden in the subclass to return the correct calories based on the size.
  * **Special Instructions** - getter. This should simply return an empty list, and does not need overridden.
* `starfleetsubs.data.drinks.Drink` is the base class for all drink items. It should include the following elements that are common to all drink classes:
  * **Size** - getter and setter.
  * **Price** - abstract getter. This should be overridden in the subclass to return the correct price based on the size.
  * **Calories** - abstract getter. This should be overridden in the subclass to return the correct calories based on the size.
  * **Special Instructions** - abstract getter. This should be overridden in the subclass to return the correct list of special instructions. 

{{% notice tip %}}

You may choose to implement the `OrderItem` interface on the three base classes described below, which will then be inherited by each menu item, instead of explicitly implementing the interface on each menu item itself. Some of the elements described on these base classes are already defined in the `OrderItem` interface, so if you implement the interface at the base class level you do not need to redefine the abstract methods from the interface within the abstract base classes. Either approach is valid!

If you choose to inherit from the `OrderItem` interface in the base classes in Python, the base class should not inherit from `ABC` - that is already covered as part of the interface. If you do, Mypy will present an error stating that it "cannot determine consistent method resolution order."

You may also need to refactor some `private` attributes (with double underscores in Python) to `protected` attributes (single underscores in Python) as they move from the subclass to the superclass. In Java, these are just attributes as expected. In Python, it is simplest to declare those in the constructor of the superclass (such as `self._size = Size.SMALL`), then make sure you call that constructor using `super().__init__()` in the subclass' constructor.

{{% /notice %}}

##### Menu Class

The `starfleetsubs.data.menu.Menu` class should be a class that has static getter methods for these four elements:

* `entrees` - a list of `OrderItem` elements containing an instance of all available entrées (7 in total).
* `sides` - a list of `OrderItem` elements containing an instance of all available sides. Since each side is available in three sizes, the list should include an instance of all three sizes of each side item (12 in total).
* `drinks` - a list of `OrderItem` elements containing an instance of all available drinks. Since each drink is available in three sizes, the list should include an instance of all three sizes of each drink item (15 in total).
* `fullmenu` - a combined list of all menu items (34 in total).

In Java, these lists should use a subclass of the [List](https://docs.oracle.com/javase/8/docs/api/java/util/List.html) interface. In Python, these methods should use the built-in Python [list](https://docs.python.org/3/library/stdtypes.html#list) data type. Since they are static methods, they **cannot** be constructed as Python properties using the `@property` decorator.

## Unit Tests

The following updates must be made to the existing unit tests in this project to accommodate these code changes:

##### Entrées

Add:
* `InheritsFromEntree()` - check if a given object inherits from the base `Entree` class. 
* `ImplementsOrderItem()` - check if a given object implements the interface `OrderItem`.
* `ChangeCondimentSetsSpecialInstructions(Condiment)` - for each condiment, check that changing it from and to the default value will add and remove the correct item from the `SpecialInstructions` list.

Update:
* `SpecialInstructionsInitiallyEmpty()` should be renamed `SpecialInstructionsInitiallyCondiments()` and should now verify that the initial set of condiments is in the special instructions list. 

##### Sides

Add:
* `InheritsFromSide()` - check if a given object inherits from the base `Side` class. 
* `ImplementsOrderItem()` - check if a given object implements the interface `OrderItem`.
* `SpecialInstructionsEmpty()` - check that the **Special Instructions** list is always empty.

##### Drinks

Add:
* `InheritsFromDrink()` - check if a given object inherits from the base `Drink` class. 
* `ImplementsOrderItem()` - check if a given object implements the interface `OrderItem`.

{{% notice tip %}}

To check for type compatibility, use the `object instanceof Class` operator in Java, or the `isinstance(object, Class)` method in Python as part of an assertion statement. Hamcrest also includes a few matchers for this, such as `isA` (Java) or `instance_of()` (Python).

{{% /notice %}}

##### Menu

Create a new test class for the `Menu` static class:

* `IncludesAllEntrees()` - test that the `entrees` list contains an instance of each entrée class 
* `IncludesAllSides()` - test that the `sides` list contains an instance of each side class for each size
* `IncludesAllDrinks()` - test that the `drinks` list contains an instance of each drink class for each size
* `IncludesAllItems()` - test that the `fullmenu` list contains an instance of every menu item. 
