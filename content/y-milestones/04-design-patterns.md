---
title: "Design Patterns"
pre: "4. "
weight: 40
---

This page lists the milestone requirements for **Milestone 4** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Game Grub_, offering food of all kinds to celebrate our love of games of all kinds. 

The fourth milestone involves creating a class to track orders made at the restaurant, a class for combo meals, and more. It also includes many different design patterns to improve the structure of the code. 

## General Requirements

{{< expand "All projects must follow the professional coding standards listed here (click to expand):" >}}

{{< include-local "../_includes/a-requirements.md" >}}

{{< /expand >}}

## Assignment Requirements

#### New Classes

This assignment will add several new classes to the project

###### Order Class

`gamegrub.data.order.Order` - this class should represent a collection of `Item` objects that make up an order.
* It should implement the **Iterator Pattern**, such that it can be used in a for each loop or enhanced for loop to iterate through all items in the list. 
* It should also support **standard collection methods** such as:
  * Getting the number of items in the collection 
  * Determining if a given **instance** of an `Item` object is contained in the collection. Recall that this should use the identity test, not the equality test.
  * Getting a single item from the collection based on the index of that item.
  * Any other standard collection methods that you feel are helpful. See the [Collection](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/Collection.html) interface in Java or [Emulating Container Types](https://docs.python.org/3.10/reference/datamodel.html#emulating-container-types) in Python for additional methods that may be useful.
* It should have the following **attributes**:
  * A private **list of `Item`s**, with methods to add and remove items.
    * **NOTE** - in most languages, the default method to remove an item from a collection will rely on **equality testing**, not **instance testing**. So, you may wish to write this method yourself instead of relying on the underlying collection, in order to keep this and the GUI in sync.
  * A private integer representing the **order number** for this order. 
    * It will be generated using the `OrderNumberSingleton` class discussed below. It should only include a getter. 
  * A private **static** float for the **tax rate**, which is set to 0.115 (11.5%) by default. 
    * It should include **static** methods to get and set the tax rate, which will be used by all `Order` objects. 
    * The tax rate must always be a valid percentage value ranging from 0.0 to 1.0, inclusive, and this should be enforced by the setter.
* It should also have getters for these **virtual attributes or properties**:
  * **Subtotal** - the total sum of the prices for each item in the order.
  * **Tax** - the subtotal multiplied by the tax rate.
  * **Total** - the subtotal plus the tax.
  * **Calories** - the total number of calories in the order.
* All dollar amounts **should not** be rounded to two decimal places by this class. That will be handled later in the GUI. 

###### Combo Class

`gamegrub.data.combo.Combo` - this class should implement the `Item` interface, and represent a combo meal consisting of an entree, a side, and a drink. 
* The class should have the following **attributes**:
  * String **Name** - the name of the combo
  * A **`Entree`** instance - the entree in the combo
  * A **`Side`** instance - the side in the combo
  * A **`Drink`** instance - the drink in the combo
* The above attributes should conform to the following:
  * The attributes should have getters and setters.
  * The attributes may be set to `null` or `None` in the constructor to represent a combo yet to be configured.
  * The attributes should have a **clear** method to reset their values back to `null` or `None`. You may have a single method, or one for each attribute. 
* The class should have the following **static attributes**:
  * Float **Discount** 
    * It should have a value .80 ($0.80) by default. 
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
    * Two combos are considered equal if their entree, side, drink, and name are equal (they do not have to be the same instances, but each one should be equal). 
    * If any attribute in this object is `null` or `None`, it is considered equal if the matching attribute is also `null` or `None`.
      * This presents a real problem in Java, because calling the `equals()` method on a `null` object will result in an exception. So, you'll have to check if each attribute in this object is `null` first. If so, and the other object's attribute is not `null`, then they are not equal. If this object's attribute is not `null`, you can safely call `equals()` on it, regardless of the other object's attribute. 

###### Combo Builder

`gamegrub.data.combo.ComboBuilder` - a class that implements the **Builder Pattern** and **Factory Method Pattern** to build the available combos described below. 
* It should include a single public **static** method to build a combo that accepts a **string**, and builds and returns the `Combo` object indicated by that string (the name of the combo). 
* For simplicity, it may also include a public **static** getter for the number of combos available. 

{{% notice tip %}}

You don't have to create individual classes for the builder pattern in the `ComboBuilder` class - it is sufficient to just have a private method for building each combo in the class itself. The full Builder pattern is a bit too much boilerplate code for this simple use.

{{% /notice %}}

###### Order Number Singleton

`gamegrub.data.order.OrderNumberSingleton` - a class that implements the **Singleton Pattern** to generate new order numbers.
* The class should have a non-static integer **next order number** attribute, which is initially set to 1
* It should have one public **static** method **get next order number** that will return the next order number. 
  * This method should call a private **get instance** method to get the actual singleton instance stored as a static attribute in the class. 
  * It should access the **next order number** attribute through that singleton instance.
  <!--* This method should also use thread synchronization techniques to ensure that only a single thread can actually access and update the **next order number** attribute (a `synchronized` statement in Java or a lock in a `with` statement in Python).-->

#### Updated Classes

There will also be several updates to existing classes.

###### Menu Class

**`Menu`** - update to include the following items:
* A static getter method for **combos** that returns all pre-configured combos described below. This method should use the `ComboBuilder` class discussed below.
* Update the **fullMenu** method to include the combos returned from the method listed above.

### Documentation Comments

All new and updated classes in this milestone should contain full documentation comments. **Every method should be completely documented!**

### Unit Tests

No new unit tests are required for this milestone. They will be added in the next milestone.

## Time Requirements

Completing this project is estimated to require 3-8 hours.

{{% notice tip %}}

_A rough estimate for this milestone would be around 1000 lines of new or updated code. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* New Classes: 90%
  * `Order` - 30%
  * `Combo` - 30%
  * `ComboBuilder` - 15%
  * `OrderNumberSingleton` - 15%
* Class Updates: 10%
  * `Menu` class: 10%

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

###### Game Night

Jenga Nachos, Catan Skewers, Sorry Soda

###### Roll the Dice

Yahtzee Poke, Potato Dice, Candy Land Shake

###### Big Appetite

Chess Chicken Parmesan, Risk Bites, Cranium Coffee

###### The Winner

Monopoly Bowl, Potato Dice, Sorry Soda
