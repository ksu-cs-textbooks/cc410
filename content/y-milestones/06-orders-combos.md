---
title: "Orders & Combos"
pre: "6. "
weight: 60
date: 2021-02-22T00:53:26-05:00
---

This page lists the milestone requirements for **Milestone 6** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Hero Pizza_, celebrating the heroes from cartoons, comic books, movies, and more. 

The sixth milestone involves creating combo meals and orders from the items selected in the GUI. We'll use this milestone to explore some software design patterns in our code, as well as learn about using test doubles in our unit tests. With this milestone, most of the work on the core functionality of the GUI will be complete.

## General Requirements

{{% expand "All projects must follow the professional coding standards listed here (click to expand):" %}}

{{% include-local "../_includes/a-requirements.md" %}}

{{% /expand %}}

## Assignment Requirements

#### New Classes

* `heropizza.data.menu.Order` - this class should represent a collection of `Food` objects that make up an order.

  * It should implement the **Iterator Pattern**, such that it can be used in a for each loop or enhanced for loop to iterate through all items in the list. 
  * It should also support **standard collection methods** such as:
    * Getting the number of items in the collection 
    * Determining if a given **instance** of an `Food` object is contained in the collection. Recall that this should use the identity test, not the equality test.
    * Getting a single item from the collection based on the index of that item.
    * Any other standard collection methods that you feel are helpful. See the [Collection](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html) interface in Java or [Emulating Container Types](https://docs.python.org/3/reference/datamodel.html#emulating-container-types) in Python for additional methods that may be useful.
  * It should have the following **attributes**:
    * A private **list of `Foods`**, with methods to add and remove items.
      * **NOTE** - in most languages, the default method to remove an item from a collection will rely on **equality testing**, not **instance testing**. So, you may wish to write this method yourself instead of relying on the underlying collection, in order to keep this and the GUI in sync.
    * A private integer representing the **order number** for this order. 
      * It will be generated using the `OrderNumberSingleton` class discussed below. It should only include a getter. 
    * A private **static** float for the **tax rate**, which is set to 0.15 (15%) by default. 
      * It should include **static** methods to get and set the tax rate, which will be used by all `Order` objects. 
      * The tax rate must always be a valid percentage value ranging from 0.0 to 1.0, inclusive, and this should be enforced by the setter.
  * It should also have getters for these **virtual attributes or properties**:
    * **Subtotal** - the total sum of the prices for each item in the order.
    * **Tax** - the subtotal multiplied by the tax rate.
    * **Total** - the subtotal plus the tax.
    * **Calories** - the total number of calories in the order.
  * All dollar amounts **should not** be rounded to two decimal places by this class. that will be handled by the GUI. 

* `heropizza.data.menu.Combo` - this class should implement the `Food` interface, and represent a combo meal consisting of an pizza, two sides, and drink. 
  * The class should have the following **attributes**:
    * String **Name** - the name of the combo
    * A **`Pizza`** instance - the pizza in the combo
    * Two **`Side`** instances - the sides in the combo
    * A **`Drink`** instance - the drink in the combo
  * The above attributes should conform to the following:
    * The attributes should have getters and setters.
    * The attributes may be set to `null` or `None` in the constructor to represent a combo yet to be configured.
    * The attributes should have a **clear** method to reset their values back to `null` or `None`. You may have a single method, or one for each attribute. 
  * The class should have the following **static attributes**:
    * Float **Discount** 
      * It should have a value 1.25 ($1.25) by default. 
      * It should include a **static** getter and setter method.
  * The class should also implement the **`Food` interface**:
    * A getter for the price, that returns the sum of the prices of each item in the combo.
      * **If all four items in the combo are populated**, the discount is applied to this total. Otherwise, no discount is applied.
    * A getter for the calories that returns the sum of the calories of each item in the combo.
    * A getter for modifications that returns a list containing the following:
      * The name of the combo, if set. If not, it should include "Custom Combo" as the first entry.
      * A second entry stating "$1.25 Discount Applied" if all four items in the combo are present. If not, this entry should not be included.
  * The class should also include the following **methods** not discussed above:
    * A **constructor** that accepts a string for the name. 
      * The constructor should allow the name to be omitted or set to `null` or `None`. The name will only be set by the `ComboBuilder` class discussed below, but users will also be able to configure a custom combo via the GUI that does not include a name.
      * The constructor should set the other attributes to `null` or `None` initially.
    * A getter for all of the **items** in the combo
      * It should return a list containing each item that is populated.
    * An implementation of the appropriate method to check for **equality** between two objects. 
      * Two combos are considered equal if their pizza, sides, drink, and name are equal (they do not have to be the same instances, just equal). 
      * If any attribute in this object is `null` or `None`, it is considered equal if the matching attribute is also `null` or `None`.
        * This presents a real problem in Java, because calling the `equals()` method on a `null` object will result in an exception. So, you'll have to check if each attribute in this object is `null` first. If so, and the other object's attribute is not `null`, then they are not equal. If this object's attribute is not `null`, you can safely call `equals()` on it, regardless of the other object's attribute. 
      * The two sides may be present in any order.
        * Again, this makes this method a bit tricky, since you'll have to properly handle multiple cases.

* `heropizza.data.menu.ComboBuilder` - a class that implements the **Builder Pattern** to build the available combos described below. 
  * It should include a single public **static** method to build a combo that accepts an integer as input, and builds and returns the `Combo` object indicated by the integer. 
  * For simplicity, it may also include a public **static** getter for the number of combos available. 

* `heropizza.data.menu.OrderNumberSingleton` - a class that implements the **Singleton Pattern** to generate new order numbers.
  * The class should have a non-static integer **next order number** attribute, which is initially set to 1
  * It should have one public **static** method **get next order number** that will return the next order number. 
    * This method should call a private **get instance** method to get the actual singleton instance stored as a static attribute in the class. 
    * It should access the **next order number** attribute through that singleton instance.
    * This method should also use thread synchronization techniques to ensure that only a single thread can actually access and update the **next order number** attribute (a `synchronized` statement in Java or a lock in a `with` statement in Python).

* `heropizza.gui.PanelFactory` - a class that implements the **Factory Method Pattern** to return an instance of a GUI panel for a given pizza, side, or drink.
  * It should include one public **static** method that is overloaded to accept two different sets of parameters:
    * **get panel(String name, `MainWindow` parent)** should accept the name of a menu item item as a string, and return a panel that represents a new instance of that item, with the `parent` GUI element as its parent. You should be able to directly feed an action command from a button click in the GUI directly to this method and get the appropriate panel. If the `name` is not recognized, an exception should be thrown.
    * **get panel(`Food` item, `MainWindow` parent)** should accept an instance of an `Food` and return a panel that represents that item, with the `parent` GUI element as its parent. If the `item` is not recognized, an exception should be thrown.
  * For now, do not worry about updating this class to handle `Combos` as `Foods`. We'll address that in the next milestone. 

#### Updated Classes

* **`Menu`** - update to include the following items:
  * A static getter method for **combos** that returns all pre-configured combos described below. This method should use the `ComboBuilder` class discussed below.
  * Update the **fullMenu** method to include the combos returned from the method listed above.

* **`OrderPanel`** - update to include the following items:
  * The button handler method should be updated to use the `PanelFactory` class to acquire the appropriate GUI panel based on the action command received from button that was clicked.

* `SidebarPanel` - update to include the following items:
  * When clicking the **Edit** button, it should use the `PanelFactory` class to acquire the appropriate GUI panel based on the item selected in the tree. 
  * This class should now include a private **order** attribute that stores the items in the in the sidebar in an `Order` instance as well. 
    * It should be instantiated by the `SidebarPanel` constructor.
    * It should be kept up to date as items are added to and removed from the order in the sidebar.
    * Whenever the order is changed, it should be used to update the order number, subtotal, tax, and total elements in the GUI. Prices should be properly formatted as currency values. 
      * See [Currencies](https://docs.oracle.com/javase/tutorial/i18n/format/numberFormat.html) for Java. 
  * The GUI should include two new buttons:
    * **New Order** - clicking this button will create a new `Order` instance and reset all appropriate GUI elements for a new order. This will delete any existing order.
      * You may wish to implement a modal dialog that asks the user to confirm before deleting the existing order. See [How to Make Dialogs](https://docs.oracle.com/javase/tutorial/uiswing/components/dialog.html) for Java or [Dialog Windows](https://tkdocs.com/tutorial/windows.html#dialogs) for Python. This is not required but highly recommended!
    * **Checkout** - clicking this button will have no effect at this time. It will be implemented in the next milestone.

### Unit Tests

All new classes except `PanelFactory` should include full unit tests that achieve at or near 100% code coverage and adequately test all aspects of the class. In addition, some previous tests may need to be updated to match new requirements.

**Java Only**: You should also update the unit tests for each of the GUI panels created in the previous milestone to use a fake `MainWindow` object instead of creating one in the test. This should make the tests run much faster, and you should be able to see that the code in `MainWindow` is not executing in the code coverage report.

**Python Only**: Sadly, I have yet to figure out if it is possible to properly fake parts of `tkinter` such that the `MainWindow` class can be properly substituted with a fake. No changes are required at this time.

Once this milestone is complete, all classes in the following packages should have unit tests that achieve at or near 100% code coverage:

* `heropizza.data.*`
* `heropizza.gui.drinks.*`
* `heropizza.gui.pizzas.*`
* `heropizza.gui.sides.*`

The only classes that do not meet this requirement are `MainWindow`, `OrderPanel`, `PanelFactory`, and `SidebarPanel` in the `heropizza.gui` package. 

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
  * `OrderPanel`: 5%
  * `SidebarPanel`: 10%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.

---
---
---

## Combos

###### 1 - Radical

The Mikey, Snarf Sticks, Mjolnir, Starfire

###### 2 - Tubular

The Wolverine, Batwings, Sailor Moon, Groot

###### 3 - Bodacious

The He-Man, Snarf Sticks, Sailor Moon, Samurai Jack

###### 4 - Groovy 

The Jem, Sailor Moon, Batwings, Bubbles

###### 5 - Gnarly 

The Captain Planet, Snarf Sticks, Mjolnir, Katara

## Unit Tests

This is a suggested list of unit tests you may wish to implement to test your new and updated classes in this milestone. You should be able to reach 100% code coverage in each of these classes. 

##### Order

* `SizeIs0Initially()` - the size of the order is initially 0.
* `TotalsAre0Initially()` - the subtotal, tax, and total are 0 initially.
* `NegativeTaxRateThrowsException()` - setting the tax rate to a negative value throws an exception.
* `TaxRateOver100ThrowsException()` - setting the tax rate to a value over 1.0 throws an exception.
* `AddItemsUpdatesSize()` - add a few fake items one at a time and check size after each one.
* `AddItemsUpdatesTotals()` - add a few fake items one at a time and check subtotal, tax, and total after each one.
* `AddItemsUpdatesCalories()` - add a few fake items one at a time and check calories after each one.
* `ContainsUsesInstanceComparison()` - confirm that the `contains` method uses instance comparison. Create two actual order items (this cannot be done with fakes) that will return true when `equals()` is called. Place one in the order, and use them to confirm that `contains` returns both true and false when given two items that are equal but not the same instance.
* `RemoveUsesInstanceComparison()` - confirm that the `remove` method uses instance comparison. Create two actual order items (this cannot be done with fakes) that will return true when `equals()` is called. Place both in in the order, then remove one and confirm that the correct one was removed using contains. You may wish to do this twice, removing the first one added once and the second one added the second time.
* `OrderNumberFromSingleton()`- confirm that the `Order` class is using `OrderNumberSingleton`. Create a fake `OrderNumberSingleton` that returns a value for an order number, then instantiate an `Order` and verify that it received the given order number.
* `TaxRateSetGlobally()` - create two `Order` instances, change the tax rate, and confirm that both use the new tax rate. This is best done by adding an item to each order and checking the `tax` virtual attribute.
* `RemoveMissingItemDoesNotThrow()` - removing an item not in the order should not throw an exception.
* `IteratorContainsItems()` - add fake items to the order, get the iterator, and confirm that the fake items are returned in order.
* `GetItemsByIndex()` - add fake items to the order, and confirm that each one can be accessed via its index.

##### Combo

* `ConstructorSetsName()` - the constructor should set the name. 
* `ConstructorAcceptsNullName()` - the constructor should accept `null` or `None` for the name.
* `ConstructorSetsItemsToNull()` - the constructor should set the pizza, sides, and drink elements to `null` or `None`. 
* `SetDiscountToNegativeThrowsException()` - setting the discount to a negative value throws an exception.
* `CanSetDiscountToZero()` - setting the discount to 0 does not throw an exception.
* `PriceZeroNoItems()` - the price should be 0 if all items are `null` or `None`.
* `CaloriesZeroNoItems()` - the calories should be 0 if all items are `null` or `None`.
* `PriceAllItems()` - add fake items to combo and verify that the price is summed correctly (remember to take off the discount).
* `CaloriesAllItems()` - add fake items to combo and verify that the calories is summed correctly.
* `NoDiscountWhenItemMissing()` - add up to three items to the combo and verify that the price is correct and does not include discount.
* `DiscountSetGlobally()` - create two `Combo` instances, change the discount, and confirm that both use the new discount. This is best done by adding three items to each combo and checking the total price.
* `ItemsListCorrect()` - add fake items to the combo and verify that the list returned by items getter contains those items.
* `ItemsListEmpty()` - getting a list when the combo is empty results in an empty list.
* `ModificationsHasDiscount()` - modifications list should include a discount message if all combo items are populated.
* `AddingComboToComboThrowsException()` - adding a combo as an item to a combo throws an exception.
* `TwoCombosEqual()` - create two combos containing the same name and fake objects and test that they are equal. 
* `TwoCombosNotEqual()` - create two combos with different names but the same fake objects, and test that they are not equal.
* `TwoEmptyCombosEqual()` - create two empty combos with `null` or `None` names and test that they are equal.
* `TwoCombosOneEmptyNotEqual()` - create two combos, one empty, one not, and test that they are not equal.
* `DifferentObjectNotEqual()` - confirm that equality test will return `false` when given a different type of object.

_You may need to add additional tests of the `equals()` method in Java to achieve 100% code coverage._ 

##### ComboBuilder

_For these tests, I recommend just checking the types of the pizza, sides, and drink items in the Combo returned, as well as the name, rather than using any fake objects. As before, you may wish to make these attributes visible to the test._

* `Combo1()` - Combo 1 is built correctly
* `Combo2()` - Combo 2 is built correctly
* `Combo3()` - Combo 3 is built correctly
* `Combo4()` - Combo 4 is built correctly
* `Combo5()` - Combo 5 is built correctly
* `BadComboThrowsException()` - a bad combo number should throw an exception

##### OrderNumberSingleton

* `SequentialOrderNumbers` - call `getNextOrderNumber()` several times and make sure each one is sequential.

## Python tox Updates

I ran into _even more_ issues with Python not running unit tests in tox properly on this assignment. As before, it seems to be the same cause:

* Because pytest is apparently _very_ memory inefficient, the unit tests are killed by Codio once they consume too much memory. To work around this, we'll run our unit tests in batches. 

An updated `tox.ini` file is given below. I recommend replacing your file with this one:

```ini
[tox]
envlist = py36
skipsdist = True

[testenv]
deps = -rrequirements.txt
passenv = DISPLAY
ignore_errors = True
commands = python3 -m mypy -p src --html-report reports/mypy
           python3 -m coverage run --parallel-mode --source src -m pytest test/heropizza/data --html=reports/pytest-data/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/heropizza/gui/pizzas/test_TheMikeyPanel.py --html=reports/pytest-pizzas1/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/heropizza/gui/pizzas/test_TheJeanGreyPanel.py --html=reports/pytest-pizzas2/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/heropizza/gui/pizzas/test_TheWolverinePanel.py --html=reports/pytest-pizzas3/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/heropizza/gui/pizzas/test_TheSheRaPanel.py --html=reports/pytest-pizzas4/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/heropizza/gui/pizzas/test_TheJemPanel.py --html=reports/pytest-pizzas5/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/heropizza/gui/pizzas/test_TheHeManPanel.py --html=reports/pytest-pizzas6/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/heropizza/gui/pizzas/test_TheCaptainPlanetPanel.py --html=reports/pytest-pizzas7/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/heropizza/gui/drinks test/heropizza/gui/sides --html=reports/pytest-side-drinks/index.html
           python3 -m coverage combine
           python3 -m coverage html -d reports/coverage
           python3 -m flake8 --docstring-convention google --format=html --htmldir=reports/flake
           python3 -m pdoc --html --force --output-dir reports/doc .
```

The major changes:

* We now run coverage in parallel mode, and specify the test folders in the pytest command. This will run several separate sets of tests. I had to move each large GUI panel to its own test, as I couldn't run them all in a single batch. 
* Notice that the test reports will now be in different folders. The old `reports/pytest` folder will no longer be updated. 
* We added a `coverage combine` command to combine the coverage data from multiple executions of pytest. 