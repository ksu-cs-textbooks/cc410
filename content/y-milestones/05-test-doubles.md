---
title: "Test Doubles"
pre: "5. "
weight: 50
---

This page lists the milestone requirements for **Milestone 6** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Game Grub_, offering food of all kinds to celebrate our love of games of all kinds. 

The fifth milestone involves writing unit tests for the order, combo, and associated classes created in the previous milestone. These unit tests will make extensive use of test doubles. 

## General Requirements

{{< expand "All projects must follow the professional coding standards listed here (click to expand):" >}}

{{< include-local "../_includes/a-requirements.md" >}}

{{< /expand >}}

## Assignment Requirements

### Unit Tests

The following new classes should contain unit tests that achieve at or near 100% code coverage and adequately test all aspects of the class. 

* `Order`
* `Combo`
* `ComboBuilder`
* `OrderNumberSingleton`

Test doubles **must be used** where noted in the discussion below. In general, any time a test refers to another class other than the one being tested, it should use a test double instead of an instance of that class.

In addition, some previous tests may need to be updated to match new requirements.

* `Menu` - add tests for combos and updated full menu

Once this milestone is complete, all classes in the following packages should have unit tests that achieve at or near 100% code coverage:

* `gamegrub.data.*`

## Time Requirements

Completing this project is estimated to require 3-8 hours.

{{% notice tip %}}

_A rough estimate for this milestone would be around 2000 lines of new or updated code. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* Unit Tests: 90%
  * `Order` - 30%
  * `Combo` - 30%
  * `ComboBuilder` - 15%
  * `OrderNumberSingleton` - 15%
* Class Updates: 10%
  * `Menu` unit tests: 10%

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

This is a suggested list of unit tests you may wish to implement to test your new and updated classes in this milestone. You should be able to reach 100% code coverage in each of these classes. 

###### Order

* When an order is created:
  * It initially has 0 items in it
  * It initially has 0 for the subtotal, tax, total, and calories
* When setting the tax rate:
  * A tax rate less than 0 throws an exception
  * A tax rate greater than 1 throws an exception
* When adding/removing items (**use test doubles instead of real objects**):
  * The size of the order changes as items are added/removed
  * The totals (subtotal, tax, total, calories) change as items are added/removed
* When checking if the order contains an item:
  * Confirm that containment uses instance comparison and not equality comparison. Create two actual order items (_this cannot be done with test doubles_) that will return true when `equals()` is called. Place one in the order, and use them to confirm that `contains` returns both true and false when given two items that are equal but not the same instance.
  * Confirm that removal uses instance comparison and not equality comparison (same process as above)
* Creation uses `OrderNumberSingleton:
  * Create a test double `OrderNumberSingleton` that returns a value for an order number, then instantiate an `Order` and verify that it received the given order number.
* Tax Rate is global:
  * create two `Order` instances, change the tax rate, and confirm that both use the new tax rate. This is best done by adding an item to each order and checking the `tax` virtual attribute.
* Other tests:
  * Trying to remove an item that is not in the order should not throw an exception.
  * Add test double items to the order, get the iterator, and confirm that the fake items are returned in order.
  * Add test double items to the order, and confirm that each one can be accessed via its index.

###### Combo

* When creating a new combo:
  * The constructor should set the name if provided.
  * The constructor should accept a name of `null` or `None` and handle that case properly
  * The constructor should set the attributes to `null` or `None`
  * The totals of the combo (total, calories) are initially set to 0.
* When setting the discount:
  * A negative discount amount should throw an exception.
  * The discount can be successfully set to 0.
* As items are added/removed in the combo (**use test doubles instead of real objects**):
  * The calories and price change correctly
  * If all items are populated, the price includes the discount correctly
  * If not all items are populated, the price should not include the discount
* Discount is global:
  * Create two `Combo` instances, change the discount, and confirm that both use the new discount. This is best done by adding all items to each combo and checking the total price.
* Test Items List:
  * Add test double items to the combo and verify that the list returned by items getter contains those items.
  * Getting a list when the combo is empty results in an empty list.
* Instructions list:
  * The instructions list should contain the combo name if set, or a default message if not set.
  * The instructions list should include a discount message if all combo items are populated.
* Exceptions:
  * Adding the wrong type to the combo throws an exception (try adding an entree as a side, or adding a combo as an entree, etc.)
* Equality tests (use test doubles instead of real objects):
  * Two combos containing the same items and name are equal
  * Two combos with different name and same items are not equal
  * Two combos with same name and different items are not equal
  * Two empty combos are equal
  * An empty combo is not equal to a combo containing items
  * A combo is not equal to another object (it should not throw an exception)
  * _You may need to add additional tests to achieve 100% code coverage of the equality method.

###### ComboBuilder

_For these tests, I recommend just checking the types of the entree, side, and drink items in the Combo returned, as well as the name, rather than using any test double objects. As before, you may wish to make these attributes visible to the test._

* Test that each combo can be built correctly by providing the name
* Test that providing an invalid name throws an exception

###### OrderNumberSingleton

* Call `getNextOrderNumber()` several times and make sure each one is sequential.
