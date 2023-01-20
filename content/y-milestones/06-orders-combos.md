---
title: "Orders & Combos"
pre: "6. "
weight: 60
date: 2021-02-22T00:53:26-05:00
hidden: true
---

<!-- TODO ADD PANEL FACTORY SOMEWHERE! -->

This page lists the milestone requirements for **Milestone 6** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Game Grub_, offering food of all kinds to celebrate our love of games of all kinds. 

The sixth milestone involves creating combo meals and orders from the items selected in the GUI. We'll use this milestone to explore some software design patterns in our code, as well as learn about using test doubles in our unit tests. With this milestone, most of the work on the core functionality of the GUI will be complete.

## General Requirements

{{< expand "All projects must follow the professional coding standards listed here (click to expand):" >}}

{{< include-local "../_includes/a-requirements.md" >}}

{{< /expand >}}

## Assignment Requirements

#### New Classes

This assignment will add several new classes to the project

###### Order Class

`thatsawrap.data.order.Order` - this class should represent a collection of `Item` objects that make up an order.
* It should implement the **Iterator Pattern**, such that it can be used in a for each loop or enhanced for loop to iterate through all items in the list. 
* It should also support **standard collection methods** such as:
  * Getting the number of items in the collection 
  * Determining if a given **instance** of an `Item` object is contained in the collection. Recall that this should use the identity test, not the equality test.
  * Getting a single item from the collection based on the index of that item.
  * Any other standard collection methods that you feel are helpful. See the [Collection](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html) interface in Java or [Emulating Container Types](https://docs.python.org/3/reference/datamodel.html#emulating-container-types) in Python for additional methods that may be useful.
* It should have the following **attributes**:
  * A private **list of `Item`s**, with methods to add and remove items.
    * **NOTE** - in most languages, the default method to remove an item from a collection will rely on **equality testing**, not **instance testing**. So, you may wish to write this method yourself instead of relying on the underlying collection, in order to keep this and the GUI in sync.
  * A private integer representing the **order number** for this order. 
    * It will be generated using the `OrderNumberSingleton` class discussed below. It should only include a getter. 
  * A private **static** float for the **tax rate**, which is set to 0.125 (12.5%) by default. 
    * It should include **static** methods to get and set the tax rate, which will be used by all `Order` objects. 
    * The tax rate must always be a valid percentage value ranging from 0.0 to 1.0, inclusive, and this should be enforced by the setter.
* It should also have getters for these **virtual attributes or properties**:
  * **Subtotal** - the total sum of the prices for each item in the order.
  * **Tax** - the subtotal multiplied by the tax rate.
  * **Total** - the subtotal plus the tax.
  * **Calories** - the total number of calories in the order.
* All dollar amounts **should not** be rounded to two decimal places by this class. that will be handled by the GUI. 

###### Combo Class

`thatsawrap.data.order.Combo` - this class should implement the `Item` interface, and represent a combo meal consisting of a wrap, a side, and a drink. 
* The class should have the following **attributes**:
  * String **Name** - the name of the combo
  * A **`Wrap`** instance - the wrap in the combo
  * A **`Side`** instance - the side in the combo
  * A **`Drink`** instance - the drink in the combo
* The above attributes should conform to the following:
  * The attributes should have getters and setters.
  * The attributes may be set to `null` or `None` in the constructor to represent a combo yet to be configured.
  * The attributes should have a **clear** method to reset their values back to `null` or `None`. You may have a single method, or one for each attribute. 
* The class should have the following **static attributes**:
  * Float **Discount** 
    * It should have a value .95 ($0.95) by default. 
    * It should include a **static** getter and setter method.
* The class should also implement the **`Item` interface**:
  * A getter for the **price**, that returns the sum of the prices of each item in the combo.
    * **If all items in the combo are populated**, the discount is applied to this total. Otherwise, no discount is applied.
  * A getter for the **calories** that returns the sum of the calories of each item in the combo.
  * A getter for **instructions** that returns a list containing the following:
    * The name of the combo, if set, as the first entry. If not, it should include "Custom Combo" as the first entry.
    * A second entry stating "$`discount` Discount Applied" if all items in the combo are present. If not, this entry should not be included.
* The class should also include the following **methods** not discussed above:
  * A **constructor** that accepts a string for the name. 
    * The constructor should allow the name to be omitted or set to `null` or `None`. The name will only be set by the `ComboBuilder` class discussed below, but users will also be able to configure a custom combo via the GUI that does not include a name.
    * The constructor should set the other attributes to `null` or `None` initially.
  * A getter for all of the **items** in the combo. It should return a list containing each item that is populated.
  * An implementation of the appropriate method to check for **equality** between two objects. 
    * Two combos are considered equal if their wrap, side, drink, and name are equal (they do not have to be the same instances, but each one should be equal). 
    * If any attribute in this object is `null` or `None`, it is considered equal if the matching attribute is also `null` or `None`.
      * This presents a real problem in Java, because calling the `equals()` method on a `null` object will result in an exception. So, you'll have to check if each attribute in this object is `null` first. If so, and the other object's attribute is not `null`, then they are not equal. If this object's attribute is not `null`, you can safely call `equals()` on it, regardless of the other object's attribute. 

###### Combo Builder

`thatsawrap.data.order.ComboBuilder` - a class that implements the **Builder Pattern** and **Factory Method Pattern** to build the available combos described below. 
* It should include a single public **static** method to build a combo that accepts a **string**, and builds and returns the `Combo` object indicated by that string (the name of the combo). 
* For simplicity, it may also include a public **static** getter for the number of combos available. 

{{% notice tip %}}

You don't have to create individual classes for the builder pattern in the `ComboBuilder` class - it is sufficient to just have a private method for building each combo in the class itself. The full Builder pattern is a bit too much boilerplate code for this simple use.

{{% /notice %}}

###### Order Number Singleton

`thatsawrap.data.order.OrderNumberSingleton` - a class that implements the **Singleton Pattern** to generate new order numbers.
* The class should have a non-static integer **next order number** attribute, which is initially set to 1
* It should have one public **static** method **get next order number** that will return the next order number. 
  * This method should call a private **get instance** method to get the actual singleton instance stored as a static attribute in the class. 
  * It should access the **next order number** attribute through that singleton instance.
  * This method should also use thread synchronization techniques to ensure that only a single thread can actually access and update the **next order number** attribute (a `synchronized` statement in Java or a lock in a `with` statement in Python).

###### Panel Factory

`thatsawrap.gui.PanelFactory` - a class that implements the **Factory Method Pattern** to return an instance of a GUI panel for a given wrap, side, or drink.
* It should include one public **static** method that is overloaded to accept two different sets of parameters:
  * **get panel(String name, `PrimaryWindow` parent)** should accept the name of a menu item item as a string, and return a panel that represents a new instance of that item, with the `parent` GUI element as its parent. You should be able to directly feed an action command from a button click in the GUI directly to this method and get the appropriate panel. If the `name` is not recognized, an exception should be thrown.
  * **get panel(`Item` item, `PrimaryWindow` parent)** should accept an instance of an `Item` and return a panel that represents that item, with the `parent` GUI element as its parent. If the `item` is not recognized, an exception should be thrown.
* For now, do not worry about updating this class to handle `Combos` as `Items`. We'll address that in the next milestone. 

#### Updated Classes

There will also be several updates to existing classes.

###### Menu Class

**`Menu`** - update to include the following items:
* A static getter method for **combos** that returns all pre-configured combos described below. This method should use the `ComboBuilder` class discussed below.
* Update the **fullMenu** method to include the combos returned from the method listed above.

###### Menu Panel

**`MenuPanel`** - update to include the following items:
* The button handler method should be updated to use the `PanelFactory` class to acquire the appropriate GUI panel based on the action command received from button that was clicked.

###### Order Panel

`OrderPanel` - update to include the following items:
* When clicking the **Edit** button, it should use the `PanelFactory` class to acquire the appropriate GUI panel based on the item selected in the tree. 
* This class should now include a private **order** attribute that stores the items in the in the sidebar in an `Order` instance as well. 
  * It should be instantiated by the `OrderPanel` constructor.
  * It should be kept up to date as items are added to and removed from the order in the sidebar.
  * Whenever the order is changed, it should be used to update the order number, subtotal, tax, and total elements in the GUI. Prices should be properly formatted as currency values. 
    * See [Currencies](https://docs.oracle.com/javase/tutorial/i18n/format/numberFormat.html) for Java. 
* The GUI should include two new buttons:
  * **New Order** - clicking this button will create a new `Order` instance and reset all appropriate GUI elements for a new order. This will delete any existing order.
    * You may wish to implement a modal dialog that asks the user to confirm before deleting the existing order. See [How to Make Dialogs](https://docs.oracle.com/javase/tutorial/uiswing/components/dialog.html) for Java or [Dialog Windows](https://tkdocs.com/tutorial/windows.html#dialogs) for Python. This is not required but highly recommended!
  * **Checkout** - clicking this button will have no effect at this time. It will be implemented in the next milestone.

### Documentation Comments

All new and updated classes in this milestone should contain full documentation comments. **Every method should be completely documented!**

### Unit Tests

All new classes except `PanelFactory` should include full unit tests that achieve at or near 100% code coverage and adequately test all aspects of the class. In addition, some previous tests may need to be updated to match new requirements.

**Java Only**: You should also update the unit tests for each of the GUI panels created in the previous milestone to use a fake `PrimaryWindow` object instead of creating one in the test. This should make the tests run much faster, and you should be able to see that the code in `PrimaryWindow` is not executing in the code coverage report.

**Python Only**: Sadly, I have yet to figure out if it is possible to properly fake parts of `tkinter` such that the `PrimaryWindow` class can be properly substituted with a fake. No changes are required at this time.

Once this milestone is complete, all classes in the following packages should have unit tests that achieve at or near 100% code coverage:

* `thatsawrap.data.*`
* `thatsawrap.gui.drinks.*`
* `thatsawrap.gui.wraps.*`
* `thatsawrap.gui.sides.*`

The only classes that do not meet this requirement are `PrimaryWindow`, `OrderPanel`, `PanelFactory`, and `MenuPanel` in the `thatsawrap.gui` package. 

## Time Requirements

Completing this project is estimated to require 3-8 hours.

{{% notice tip %}}

_A rough estimate for this milestone would be around 2000 lines of new or updated code. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* New Classes: 40%
  * `Order` - 10%
  * `Combo` - 10%
  * `ComboBuilder` - 10%
  * `OrderNumberSingleton` - 5%
  * `PanelFactory` - 5%
* Unit Tests: 40%
  * `Order` - 15%
  * `Combo` - 15%
  * `ComboBuilder` - 5%
  * `OrderNumberSingleton` - 5%
* Class Updates: 20%
  * `Menu` and unit tests: 5%
  * `MenuPanel`: 5%
  * `OrderPanel`: 10%

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

## Combos

###### Classic

The Godfather, The French Connection, Singin' in the Rain

###### Green

The Wizard of Oz, Snow White, Rocky

###### Hungry

Spartacus, Yankee Doodle Dandy, Forrest Gump

###### Spicy

Some Like It Hot, The French Connection, Forrest Gump

## Unit Tests

This is a suggested list of unit tests you may wish to implement to test your new and updated classes in this milestone. You should be able to reach 100% code coverage in each of these classes. 

###### Order

* When an order is created:
  * It initially has 0 items in it
  * It initially has 0 for the subtotal, tax, total, and calories
* When setting the tax rate:
  * A tax rate less than 0 throws an exception
  * A tax rate greater than 1 throws an eception
* When adding/removing items (use test doubles instead of real objects):
  * The size of the order changes as items are added/removed
  * The totals (subtotal, tax, total, calories) change as items are added/removed
* When checking if the order contains an item:
  * Confirm that containment uses instance comparison and not equality comparison. Create two actual order items (this cannot be done with fakes) that will return true when `equals()` is called. Place one in the order, and use them to confirm that `contains` returns both true and false when given two items that are equal but not the same instance.
  * Confirm that removal uses instance comparison and not equality comparison (same process as above)
* Creation uses `OrderNumberSingleton:
  * Create a fake `OrderNumberSingleton` that returns a value for an order number, then instantiate an `Order` and verify that it received the given order number.
* Tax Rate is global:
  * create two `Order` instances, change the tax rate, and confirm that both use the new tax rate. This is best done by adding an item to each order and checking the `tax` virtual attribute.
* Other tests:
  * Trying to remove an item that is not in the order should not throw an exception.
  * Add fake items to the order, get the iterator, and confirm that the fake items are returned in order.
  * Add fake items to the order, and confirm that each one can be accessed via its index.

###### Combo

* When creating a new combo:
  * The constructor should set the name if provided.
  * The constructor should accept a name of `null` or `None` and handle that case properly
  * The constructor should set the attributes to `null` or `None`
  * The totals of the combo (total, calories) are initially set to 0.
* When setting the discount:
  * A negative discount amount should throw an exception.
  * The discount can be succesfully set to 0.
* As items are added/removed in the combo (use test doubles instead of real objects):
  * The calories and price change correctly
  * If all items are populated, the price includes the discount correctly
  * If not all items are populated, the price should not include the discount
* Discount is global:
  * Create two `Combo` instances, change the discount, and confirm that both use the new discount. This is best done by adding all items to each combo and checking the total price.
* Test Items List:
  * Add fake items to the combo and verify that the list returned by items getter contains those items.
  * Getting a list when the combo is empty results in an empty list.
* Instructions list:
  * The instructions list should contain the combo name if set, or a default message if not set.
  * The instructions list should include a discount message if all combo items are populated.
* Exceptions:
  * Adding the wrong type to the combo throws an exception (try adding a wrap as a side, or adding a combo as a wrap, etc.)
* Equality tests (use test doubles instead of real objects):
  * Two combos containing the same items and name are equal
  * Two combos with different name and same items are not equal
  * Two combos with same name and different items are not equal
  * Two empty combos are equal
  * An empty combo is not equal to a combo containing items
  * A combo is not equal to another object (it should not throw an exception)
  * _You may need to add additional tests to achieve 100% code coverage of the equality method.

###### ComboBuilder

_For these tests, I recommend just checking the types of the wrap, side, and drink items in the Combo returned, as well as the name, rather than using any fake objects. As before, you may wish to make these attributes visible to the test._

* Test that each combo can be built correctly by providing the name
* Test that providing an invalid name throws an exception

###### OrderNumberSingleton

* Call `getNextOrderNumber()` several times and make sure each one is sequential.

## Python tox Updates

I ran into _even more_ issues with Python not running unit tests in tox properly on this assignment. As before, it seems to be the same cause:

* Because pytest is apparently _very_ memory inefficient, the unit tests are killed by Codio once they consume too much memory. To work around this, we'll run our unit tests in batches. 

An updated `tox.ini` file is given below. I recommend replacing your file with this one:

```ini
[tox]
envlist = py39
skipsdist = True

[testenv]
deps = -rrequirements.txt
passenv = DISPLAY
ignore_errors = True
commands = python3 -m mypy -p src --html-report reports/mypy
           python3 -m coverage run --parallel-mode --source src -m pytest test/thatsawrap/data --html=reports/pytest-data/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/thatsawrap/gui/wraps/test_GodfatherPanel.py --html=reports/pytest-items1/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/thatsawrap/gui/wraps/test_WizardPanel.py --html=reports/pytest-items2/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/thatsawrap/gui/wraps/test_SomeLikePanel.py --html=reports/pytest-items3/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/thatsawrap/gui/wraps/test_WestSidePanel.py --html=reports/pytest-items4/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/thatsawrap/gui/wraps/test_SpartacusPanel.py --html=reports/pytest-items5/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/thatsawrap/gui/drinks test/thatsawrap/gui/sides --html=reports/pytest-side-drinks/index.html
           python3 -m coverage combine
           python3 -m coverage html -d reports/coverage
           python3 -m flake8 --docstring-convention google --format=html --htmldir=reports/flake
           python3 -m pdoc --html --force --output-dir reports/doc .
```

The major changes:

* We now run coverage in parallel mode, and specify the test folders in the pytest command. This will run several separate sets of tests. I had to move each large GUI panel to its own test, as I couldn't run them all in a single batch. 
* Notice that the test reports will now be in different folders. The old `reports/pytest` folder will no longer be updated. 
* We added a `coverage combine` command to combine the coverage data from multiple executions of pytest. 
