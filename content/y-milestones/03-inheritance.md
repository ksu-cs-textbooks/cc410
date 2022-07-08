---
title: "Inheritance"
pre: "3. "
weight: 40
date: 2021-08-17T00:53:26-05:00
---

This page lists the milestone requirements for **Milestone 3** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _That's a Wrap_, offering wraps of all shapes and sizes to celebrate our favorite movies. 

The third milestone involves refactoring our code to take advantage of **inheritance** and the use of **interfaces**. We'll also need to update our documentation and unit tests accordingly.

## General Requirements

{{% notice warning %}}

This project is the first that requires **ALL** general requirements introduced in the "Hello Real World" project. Read this section carefully to see what is required for this particular milestone.

{{% /notice %}}

{{< expand "All projects must follow the professional coding standards listed here (click to expand):" >}}

{{< include-local "../_includes/a-requirements.md" >}}

{{< /expand >}}

## Assignment Requirements

This milestone should include the following features:

###### Interface

* A new `thatsawrap.data.menu.Item` interface that is implemented by all wrap, side, and drink classes
  * It is highly recommended to do this by implementing the interface on the new base classes listed below.
  * See below for the description of what this interface should contain

###### Base Classes

* New abstract base classes for each type of menu item:
  * Wraps should inherit from `thatsawrap.data.wraps.Wrap` base class
  * Sides should inherit from the `thatsawrap.data.sides.Side` base class
  * Drinks should inherit from the `thatsawrap.data.drinks.Drink` base class
* Each new base class should contain all elements that are shared by each type of menu item
  * See below for the description of what the base classes should contain

###### Menu Class

* A new **static** class `thatsawrap.data.menu.Menu` that contains the full menu
  * See below for the description of what this `Menu` class should contain

###### Unit Tests

* Updated unit tests for each menu item to check for proper typing
  * Each menu item should implement the `Item` interface
  * Each menu item should inherit from the correct base class
  * Each class except `Menu` and `Food` should report near 100% code coverage. 
* Add a unit test class for `Menu` to confirm that each possible menu item is present in the menu.

###### Updated Documentation and Style

* Update the **UML Class Diagram** to represent the new structure of the code. 
* Make sure all code is **free from style errors** using Checkstyle/Flake8. 
  
## Time Requirements

Completing this project is estimated to require 3-8 hours.

{{% notice note "Expected Scope" %}}

_A rough estimate for this milestone would be around 1000 lines of new or updated code, and around 500 lines of redundant code removed. It could vary widely based on how you choose to implement the inheritance between the base classes and the interface. My model solution for this milestone now contains about 100 more unit tests in total. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* `Item` Interface - 25%
* Base Classes - 30%
  * `Wrap` Base Class - 10%
  * `Side` Base Class - 10%
  * `Drink` Base Class - 10%
* `Menu` Class - 20%
* Updated Unit Tests - 10%
* `Menu` Unit Tests - 10%
* UML Class Diagram - 5%

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

## New Classes

##### Item Interface

The `thatsawrap.data.menu.Item` class should be created as an interface that can be implemented by all other menu items. It should contain the following elements as abstract methods/properties:
* A getter for **Price**
* A getter for **Calories**
* A getter for **Instructions**

Each menu item (wraps, sides, and drinks) should be refactored to implement this interface. This will require some changes:

* **Price** and **Calories** is straightforward
* **Instructions** requires some changes
  * **Wraps** - the **Instructions** list should now include each of the **Addins** added to each item. This could be done via the new `Wrap` base class.
  * **Sides** - the **Instructions** getter will need to be added, and it should just return an empty list since sides do not have instructions. This can be done via the new `Side` base class. 
  * **Drinks** - no changes needed

Accordingly, the **unit tests** for some of these classes will need updated, as discussed below.

##### Base Classes

Each of the three types of menu items should directly inherit from a new abstract base class. These classes should not be instantiated!

* `thatsawrap.data.wraps.Wrap` is the base class for all wrap items. It should include the following elements that are common to all wrap classes:
  * **Shell** - attribute with getter and setter.
  * **Addins** - attribute with getter, **Add Addins** and **Remove Addins** methods.
  * **Price** - abstract getter. This should be overridden in the subclass to return the correct price.
  * **Calories** - abstract getter. This should be overridden in the subclass to return the correct calories.
  * **Instructions** - getter. This should be overridden in the subclass to return the correct list of instructions. 
    * One easy way to do this: the method in the superclass could be used to add the list of addins to the list, and then the subclass method could call the superclass method as part of its code and then add the ingredient changes itself. 
* `thatsawrap.data.sides.Side` is the base class for all side items. It should include the following elements that are common to all side classes:
  * **Size** - getter and setter.
  * **Price** - abstract getter. This should be overridden in the subclass to return the correct price based on the size.
  * **Calories** - abstract getter. This should be overridden in the subclass to return the correct calories based on the size.
  * **Instructions** - getter. This should simply return an empty list, and does not need overridden.
* `thatsawrap.data.drinks.Drink` is the base class for all drink items. It should include the following elements that are common to all drink classes:
  * **Size** - getter and setter.
  * **Price** - abstract getter. This should be overridden in the subclass to return the correct price based on the size.
  * **Calories** - abstract getter. This should be overridden in the subclass to return the correct calories based on the size.
  * **Instructions** - abstract getter. This should be overridden in the subclass to return the correct list of ingredients changed. 

{{% notice tip "Many Valid Approaches" %}}

You may choose to implement the `Item` interface on the three base classes described below, which will then be inherited by each menu item, instead of explicitly implementing the interface on each menu item itself. Some of the elements described on these base classes are already defined in the `Item` interface, so if you implement the interface at the base class level you do not need to redefine the abstract methods from the interface within the abstract base classes. Either approach is valid, though going through the base class makes things simpler down the road!

If you choose to inherit from the `Item` interface in the base classes in Python, the base class should not inherit from `ABC` - that is already covered as part of the interface. If you do, Mypy will present an error stating that it "cannot determine consistent method resolution order."

You may also need to refactor some `private` attributes (with double underscores in Python) to `protected` attributes (single underscores in Python) as they move from the subclass to the superclass. In Java, these are just attributes as expected. In Python, it is simplest to declare those in the constructor of the superclass (such as `self._size = Size.INDIE`), then make sure you call that constructor using `super().__init__()` in the subclass' constructor.

{{% /notice %}}

##### Menu Class

The `thatsawrap.data.menu.Menu` class should be a class that has static getter methods for these four elements:

* `wraps` - a list of `Item` elements containing an instance of all available wraps (5 in total).
* `sides` - a list of `Item` elements containing an instance of all available sides. Since each side is available in three sizes, the list should include an instance of all three sizes of each side item (9 in total).
* `drinks` - a list of `Item` elements containing an instance of all available drinks. Since each drink is available in three sizes, the list should include an instance of all three sizes of each drink item (9 in total).
* `fullmenu` - a combined list of all menu items (23 in total).

In Java, these lists should use a subclass of the [List](https://docs.oracle.com/javase/8/docs/api/java/util/List.html) interface. In Python, these methods should use the built-in Python [list](https://docs.python.org/3/library/stdtypes.html#list) data type. Since they are static methods, they **cannot** be constructed as Python properties using the `@property` decorator.

## Unit Tests

The following updates must be made to the existing unit tests in this project to accommodate these code changes:

##### Wraps

* When a new object is created:
  * The instructions list should now contain entries for each of the addins present by default
* Check inheritance:
  * Check if the object inherits from the correct base class
  * Check if the object implements the `Item` interface
* For each addin:
  * Check that adding or removing the addin will add or remove that element from the instructions list.

##### Sides

* When a new object is created:
  * The instructions list should be empty
* Check inheritance:
  * Check if the object inherits from the correct base class
  * Check if the object implements the `Item` interface


##### Drinks

* Check inheritance:
  * Check if the object inherits from the correct base class
  * Check if the object implements the `Item` interface

{{% notice tip "Checking Types in Unit Tests" %}}

To check for type compatibility, use the `object instanceof Class` operator in Java, or the `isinstance(object, Class)` method in Python as part of an assertion statement. Hamcrest also includes a few matchers for this, such as `isA` (Java) or `instance_of()` (Python).

{{% /notice %}}

##### Menu

* Test that the wraps list contains an instance of each wrap
* Test that the sides list contains an instance of each side for each size
* Test that the drinks list contains an instance of each drink for each size
* Test that the full menu list contains an instance of each menu item in the lists above
