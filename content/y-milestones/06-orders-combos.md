---
title: "Orders & Combos"
pre: "6. "
weight: 60
date: 2021-02-22T00:53:26-05:00
---

This page lists the milestone requirements for **Milestone 6** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Starfleet Subs_, based in the [Star Trek](https://en.wikipedia.org/wiki/Star_Trek) universe. 

The sixth milestone involves creating combo meals and orders from the items selected in the GUI. We'll use this milestone to explore some software design patterns in our code, as well as learn about using test doubles in our unit tests. With this milestone, most of the work on the core functionality of the GUI will be complete.

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
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).

## Assignment Requirements

### New Classes

`starfleetsubs.data.menu.Order` - this class should represent a collection of `OrderItem` objects that make up an order.

* It should implement the **Iterator Pattern**, such that it can be used in a for each loop or enhanced for loop to iterate through all items in the list. 
* It should also support standard collection methods such as:
  * Getting the number of items in the collection (`size()` in Java or `__len__()` in Python). 
  * Determining if a given instance of an `OrderItem` object is contained in the collection (`contains(item)` in Java or `__contains__(item)` in Python). Recall that this should use the identity test, not the equality test.
  * Getting a single item from the collection based on the index of that item (either a `get(i)` method in Java or `__getitem__(i)` in Python).
  * Any other standard collection methods that you feel are helpful. See the [Collection](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html) interface in Java or [Emulating Container Types](https://docs.python.org/3/reference/datamodel.html#emulating-container-types) in Python for additional methods that may be useful.
* It should have the following attributes:
  * A private list `items` of `OrderItems`, with methods to add and remove items, as well as the iterator pattern methods discussed above.
    * **NOTE** - in most languages, the default method to remove an item from a collection will rely on equality testing, not instance testing. So, you may wish to write this method yourself instead of relying on the underlying collection, in order to keep this and the GUI in sync.
  * A private integer representing the `orderNumber` for this order. It will be generated using the `OrderNumberSingleton` class discussed below. It should only include a getter. 
  * A private **static** float for the `taxRate`, which is set to 0.12 (12%) by default. It should include **static** methods to get and set the tax rate, which will be used by all `Order` objects. The tax rate must be a valid percentage value ranging from 0.0 to 1.0, inclusive.
* It should also have getters for these three virtual attributes or properties:
  * float `subtotal` - the total sum of the prices for each item in the order.
  * float `tax` - the `subtotal` multiplied by the `taxRate`
  * float `total` - the `subtotal` plus the `tax`. 
  * int `calories` - the total number of calories in the order.
* All dollar amounts **should not** be rounded to two decimal places by this class. that will be handled by the GUI. 

`starfleetsubs.data.menu.Combo` - this class should implement the `OrderItem` interface, and represent a combo meal consisting of an entrée, side, and drink. 
* It should have the following attributes:
  * A string `name` - the name of the combo, which does not require a getter (you may add one) or setter. This attribute can be set to `null` or `None`.
  * An `Entree` named `entree` - the entrée in the combo, which does not require a getter (you may add one) or setter. This attribute can be set to `null` or `None`. It should include a `removeEntree()` method to set the value to `null` or `None`.
  * A `Side` named `side` - the side in the combo, which does not require a getter (you may add one) or setter. This attribute can be set to `null` or `None`. It should include a `removeSide()` method to set the value to `null` or `None`.
  * A `Drink` named `drink` - the drink in the combo, which does not require a getter (you may add one) or setter. This attribute can be set to `null` or `None`. It should include a `removeDrink()` method to set the value to `null` or `None`.
  * A **static** float `discount` - it has a value 0.5 ($0.50) by default. It should include **static** methods to get and set the discount, which will be used by all `Combo` objects.
* It should also comply with the `OrderItem` interface:
  * A getter for `price` that returns the sum of the prices of each item. **If all three items in the combo are populated**, the discount is applied to this total. Otherwise, no discount is applied.
  * A getter for `calories` that returns the sum of the calories of each item.
  * A getter for `specialInstructions` that returns the name of the combo, if set, followed by the line `"$0.50 Discount Applied"` if all three items are populated. It should not include any other items. (The discount value should be updated to match the static `discount` attribute.)
* It should also include the following methods:
  * A constructor that accepts a string for the `name`. The constructor should allow the name to be omitted or set to `null` or `None`. The `name` will only be set by the `ComboBuilder` class discussed below, but users will also be able to configure a custom combo via the GUI that does not include a name. The constructor should set the `entree`, `side` and `drink` attributes to `null` or `None` initially.
  * An `addItem()` method that accepts an `OrderItem` object and places it in the appropriate attribute (`entree`, `side` or `drink`). It should replace the existing item in that attribute, if any. If the `OrderItem` is not one of the three types listed above, it should throw an appropriate exception.
  * A `getItems()` method that returns list of the items included in the combo, if any. If none are included, then return an empty list.  
  * An implementation of the `equals()` or `__eq__()` method to check for equality. Two combos are considered equal if their entree, side, drink, and name are equal (they do not have to be the same instances, just equal). If any attribute in this object is `null` or `None`, it is considered equal if the matching attribute is also `null` or `None`.
    * This presents a real problem in Java, because calling the `equals()` method on a `null` object will result in an exception. So, you'll have to check if each attribute in this object is `null` first. If so, and the other object's attribute is not `null`, then they are not equal. If this object's attribute is not `null`, you can safely call `equals()` on it, regardless of the other object's attribute. 

`starfleetsubs.data.menu.ComboBuilder` - a class that implements the **Builder Pattern** to build the available combos described below. 
* It should include a single public **static** method `buildCombo()` that accepts an integer as input, and builds and returns the `Combo` object indicated by the integer. 
* For simplicity, it may also include a public **static** getter for the number of combos available. 

`starfleetsubs.data.menu.OrderNumberSingleton` - a class that implements the **Singleton Pattern** to generate new order numbers.
* The class should have a non-static integer `nextOrderNumber` attribute, which is initially set to 1
* It should have one public **static** method `getNextOrderNumber()` that will return the next order number. 
  * This method should call a private `getInstance()` method to get the actual singleton instance stored as a static attribute in the class. 
  * It should access the `nextOrderNumber` attribute through that singleton instance.
  * This method should also use thread synchronization techniques to ensure that only a single thread can actually access and update the `nextOrderNumber` attribute (a `synchronized` statement in Java or a lock in a `with` statement in Python).

`starfleetsubs.gui.PanelFactory` - a class that implements the **Factory Method Pattern** to return an instance of a GUI panel for a given entrée, side, or drink.
* It should include one public **static** method that is overloaded to accept two different sets of parameters:
  * `getPanel(String name, MainWindow parent)` should accept the name of a menu item item as a string, and return a panel that represents a new instance of that item, with the `parent` GUI element as its parent. You should be able to directly feed an action command from a button click in the GUI directly to this method and get the appropriate panel. If the `name` is not recognized, an exception should be thrown.
  * `getPanel(OrderItem item, MainWindow parent)` should accept an instance of an `OrderItem` and return a panel that represents that item, with the `parent` GUI element as its parent. If the `item` is not recognized, an exception should be thrown.
* For now, do not worry about updating this class to handle `Combos` as `OrderItems`. We'll address that in the next milestone. 

### Updated Classes

`Menu` - update to include the following items:
* A `getCombos()` method that returns all pre-configured combos described below. This method should use the `ComboBuilder` class discussed below.
* Updated the `getFullMenu()` method to include the combos returned from `getCombos()` in its output.

`OrderPanel` - update to include the following items:
* The `actionPerformed` method should be updated to use the `PanelFactory` class to acquire the appropriate GUI panel based on the action command received from button that was clicked.

`SidebarPanel` - update to include the following items:
* When clicking the "Edit" button, it should use the `PanelFactory` class to acquire the appropriate GUI panel based on the item selected in the tree. 
* This class should now include a private `Order` attribute that stores the items in the order. 
  * It should be instantiated by the `SidebarPanel` constructor.
  * It should be kept up to date as items are added to and removed from the order.
  * Whenever the order is changed, it should update the order number, subtotal, tax, and total elements in the GUI. Prices should be properly formatted as currency values. 
    * See [Currencies](https://docs.oracle.com/javase/tutorial/i18n/format/numberFormat.html) for Java. 
* The GUI should include two new buttons:
  * "New Order" - clicking this button will create a new `Order` instance and reset all appropriate GUI elements for a new order. This will delete any existing order.
    * You may wish to implement a modal dialog that asks the user to confirm before deleting the existing order. See [How to Make Dialogs](https://docs.oracle.com/javase/tutorial/uiswing/components/dialog.html) for Java or [Dialog Windows](https://tkdocs.com/tutorial/windows.html#dialogs) for Python. This is not required but highly recommended!
  * "Checkout" - clicking this button will have no effect at this time. It will be implemented in the next milestone.

### Unit Tests

All new classes except `PanelFactory` should include full unit tests that achieve at or near 100% code coverage and adequately test all aspects of the class. In addition, some previous tests may need to be updated to match new requirements.

**Java Only**: You should also update the unit tests for each of the GUI panels created in the previous milestone to use a fake `MainWindow` object instead of creating one in the test. This should make the tests run much faster, and you should be able to see that the code in `MainWindow` is not executing in the code coverage report.

**Python Only**: Sadly, I have yet to figure out if it is possible to properly fake parts of `tkinter` such that the `MainWindow` class can be properly substituted with a fake. No changes are required at this time.

Once this milestone is complete, all classes in the following packages should have unit tests that achieve at or near 100% code coverage:

* `starfleetsubs.data.*`
* `starfleetsubs.gui.drinks.*`
* `starfleetsubs.gui.entrees.*`
* `starfleetsubs.gui.sides.*`

The only classes that do not meet this requirement are `MainWindow`, `OrderPanel`, `PanelFactory`, and `SidebarPanel` in the `starfleetsubs.gui` package. 

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

###### 1 - Original Series

The Kirk, Bones McCoy, Altair Water

###### 2 - Next Generation

The Riker, Data Chips, The Picard

###### 3 - Voyage Beyond

The Janeway, Enterprise, The Guinan

###### 4 - Warrior's Way

The Gagh, Borg, The Worf

###### 5 - Galaxy Class

The Scotty, Enterprise, The Troi

###### 6 - Judgement of Humanity

The Q, Borg, The Picard

## Unit Tests

This is a suggested list of unit tests you may wish to implement to test your new and updated classes in this milestone. You should be able to reach 100% code coverage in each of these classes. 

##### Order

* `SizeIs0Initially()` - the size of the order is initially 0.
* `TotalsAre0Initially()` - the subtotal, tax, and total are 0 initially.
* `NegativeTaxRateThrowsException()` - setting the tax rate to a negative value throws an exception.
* `TaxRateOver100ThrowsException()` - setting the tax rate to a value over 1.0 throws an exception.
* `AddItemsUpdatesSize()` - add three fake items one at a time and check size after each one.
* `AddItemsUpdatesTotals()` - add three fake items one at a time and check subtotal, tax, and total after each one.
* `AddItemsUpdatesCalories()` - add three fake items one at a time and check calories after each one.
* `ContainsUsesInstanceComparison()` - confirm that the `contains` method uses instance comparison. Create two actual order items (this cannot be done with fakes) that will return true when `equals()` is called. Place one in the order, and use them to confirm that `contains` returns both true and false when given two items that are equal but not the same instance.
* `RemoveUsesInstanceComparison()` - confirm that the `removeItem` method uses instance comparison. Create two actual order items (this cannot be done with fakes) that will return true when `equals()` is called. Place both in in the order, then remove one and confirm that the correct one was removed using contains. You may wish to do this twice, removing the first one added once and the second one added the second time.
* `OrderNumberFromSingleton()`- confirm that the `Order` class is using `OrderNumberSingleton`. Create a fake `OrderNumberSingleton` that returns a value for an order number, then instantiate an `Order` and verify that it received the given order number.
* `TaxRateSetGlobally()` - create two `Order` instances, change the tax rate, and confirm that both use the new tax rate. This is best done by adding an item to each order and checking the `tax` virtual attribute.
* `RemoveMissingItemDoesNotThrow()` - removing an item not in the order should not throw an exception.
* `IteratorContainsItems()` - add fake items to the order, get the iterator, and confirm that the fake items are returned in order.
* `GetItemsByIndex()` - add fake items to the order, and confirm that each one can be accessed via its index.

##### Combo

* `ConstructorSetsName()` - the constructor should set the name. This is visible as the first element in the special instructions list.
* `ConstructorAcceptsNullName()` - the constructor should accept `null` or `None` for the name.
* `ConstructorSetsItemsToNull()` - the constructor should set the entree, side, and drink elements to `null` or `None`. 
* `SetDiscountToNegativeThrowsException()` - setting the discount to a negative value throws an exception.
* `CanSetDiscountToZero()` - setting the discount to 0 does not throw an exception.
* `PriceZeroNoItems()` - the price should be 0 if all items are `null` or `None`.
* `CaloriesZeroNoItems()` - the calories should be 0 if all items are `null` or `None`.
* `PriceAllItems()` - add fake entree, side, and drink to combo and verify that the price is summed correctly (remember to take off the discount).
* `CaloriesAllItems()` - add fake entree, side, and drink to combo and verify that the calories is summed correctly.
* `NoDiscountWhenItemMissing()` - add two of the three items to the combo and verify that the price is correct and does not include discount.
* `DiscountSetGlobally()` - create two `Combo` instances, change the discount, and confirm that both use the new discount. This is best done by adding three items to each combo and checking the total price.
* `AddEntreeUpdatesEntree()` - add an `Entree` to the combo using `addItem()` and verify that it is placed in the `entree` attribute. You may need to make the attribute visible to the test.
* `AddSideUpdatesSide()` - add a `Side` to the combo using `addItem()` and verify that it is placed in the `side` attribute. You may need to make the attribute visible to the test.
* `AddDrinkUpdatesDrink()` - add a `Drink` to the combo using `addItem()` and verify that it is placed in the `drink` attribute. You may need to make the attribute visible to the test.
* `ItemsListCorrect()` - add fake items to the combo and verify that the list returned by `getItems()` contains them.
* `ItemsListEmpty()` - getting a list when the combo is empty results in an empty list.
* `SpecialInstructionsHasDiscount()` - special instructions should contain "$0.50 Discount Applied" if all three items are populated.
* `AddingComboToComboThrowsException()` - adding a combo as an item to a combo throws an exception.
* `TwoCombosEqual()` - create two combos containing the same name and fake objects and test that they are equal. 
* `TwoCombosNotEqual()` - create two combos with different names but the same fake objects, and test that they are not equal.
* `TwoEmptyCombosEqual()` - create two empty combos with `null` or `None` names and test that they are equal.
* `TwoCombosOneEmptyNotEqual()` - create two combos, one empty, one not, and test that they are not equal.
* `DifferentObjectNotEqual()` - confirm that equality test will return `false` when given a different type of object.

_You may need to add additional tests of the `equals()` method in Java to achieve 100% code coverage._ 

##### ComboBuilder

_For these tests, I recommend just checking the types of the entree, side, and drink item in the Combo returned, as well as the name, rather than using any fake objects. As before, you may wish to make these attributes visible to the test._

* `Combo1()` - Combo 1 is built correctly
* `Combo2()` - Combo 2 is built correctly
* `Combo3()` - Combo 3 is built correctly
* `Combo4()` - Combo 4 is built correctly
* `Combo5()` - Combo 5 is built correctly
* `Combo6()` - Combo 6 is built correctly
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
           python3 -m coverage run --parallel-mode --source src -m pytest test/starfleetsubs/data --html=reports/pytest-data/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/starfleetsubs/gui/entrees/test_TheGaghPanel.py --html=reports/pytest-entrees1/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/starfleetsubs/gui/entrees/test_TheJanewayPanel.py --html=reports/pytest-entrees2/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/starfleetsubs/gui/entrees/test_TheKirkPanel.py --html=reports/pytest-entrees3/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/starfleetsubs/gui/entrees/test_TheQPanel.py --html=reports/pytest-entrees4/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/starfleetsubs/gui/entrees/test_TheRikerPanel.py --html=reports/pytest-entrees5/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/starfleetsubs/gui/entrees/test_TheScottyPanel.py --html=reports/pytest-entrees6/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/starfleetsubs/gui/entrees/test_TheSpockPanel.py --html=reports/pytest-entrees7/index.html
           python3 -m coverage run --parallel-mode --source src -m pytest test/starfleetsubs/gui/drinks test/starfleetsubs/gui/sides --html=reports/pytest-side-drinks/index.html
           python3 -m coverage combine
           python3 -m coverage html -d reports/coverage
           python3 -m flake8 --docstring-convention google --format=html --htmldir=reports/flake
           python3 -m pdoc --html --force --output-dir reports/doc .
```

The major changes:

* We now run coverage in parallel mode, and specify the test folders in the pytest command. This will run several separate sets of tests. I had to move each large GUI panel to its own test, as I couldn't run them all in a single batch. 
* Notice that the test reports will now be in different folders. The old `reports/pytest` folder will no longer be updated. 
* We added a `coverage combine` command to combine the coverage data from multiple executions of pytest. 