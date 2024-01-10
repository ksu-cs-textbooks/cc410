---
title: "Orders & Combos"
pre: "8. "
weight: 80
---

This page lists the milestone requirements for **Milestone 8** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Starfleet Subs_, based in the [Star Trek](https://en.wikipedia.org/wiki/Star_Trek) universe.

The eighth milestone involves creating combo meals and orders from the items selected in the GUI. We'll use this milestone to explore some software design patterns in our code, as well as learn about using test doubles in our unit tests. With this milestone, most of the work on the core functionality of the GUI will be complete.

## General Requirements

{{< expand "All projects must follow the professional coding standards listed here (click to expand):" >}}

{{< include-local "../../../_includes/a-requirements.md" >}}

{{< /expand >}}

## Assignment Requirements

#### New Features

This milestone introduces one new feature to the project. Instead of specifying a particular set of classes and structure, it is up to you as the developer to determine how to best implement this feature. Some hints are given in the related example project.

###### Update GUI Panels to Handle Orders & Combos

Add updated buttons and panels to the GUI to facilitate creation and customization of combos created as part of the previous milestone. It should have the following features:

* Users should be able to directly select one of the pre-built combos included in the previous milestone and add it to the order.
* Users should be able to create a custom combo consisting of a entree, side, and/or drink of their choice.
  * You do not have to enforce the requirement that a combo contains all items to be added to the order. However, the combo should only get the discount if all items are populated. The existing `Combo` class should handle this as defined in a previous milestone.
* Any entree, side, or drink in the combo should also be customizable.
* Some of the code in the `OrderPanel` class will need to be updated to properly handle combos.
  * Combos should be displayed with the title "Combo" as the topmost element in the tree. 
  * The name of the combo should be the first child node, if set. If not set, a default name may be used.
  * If the combo is eligible for the discount, that message should be displayed as the second child node of the combo.(Hint: both of these are present in the instructions list returned from the combo class!)
  * Each item in the combo should be displayed below the combo name and discount message as a child node.
  * The instructions for each item in the combo should be displayed as child nodes of the appropriate item.
* In effect, combos will have 3 levels in the tree instead of the usual 2 for other order items.
*   This means that some of the logic for handling item selection and updates will need to be carefully updated. 
  * You may choose to simply write special cases for handling combos instead of generalizing or using recursion (the tree will be limited to 3 levels of depth, not including the single hidden root node).
* Any new functionality should not interfere with previous functionality. This means:
  * All individual entrees, sides, and drinks can be added to the order and customized.
  * Any items in the order can be selected and edited.
    * If an item is part of a combo, you may choose to load the screen for editing the entire combo instead of the item selected - this is up to you!

{{% notice info "Hints" %}}

At the bottom of this page is a GUI sketch of one possible way to build a screen for customizing a combo. It is designed to reuse the existing panels for each menu item. We will refer to this class as `ComboPanel` in this document. In your implementation, you are encouraged to reuse existing code whenever possible - try to stick to the [Don't Repeat Yourself](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) principle. Some hints for this particular implementation:

* Instead of each panel using the `PrimaryWindow` class/type as its parent, we can abstract that to a `ParentPanel` interface that is implemented by both the `PrimaryWindow` class and `ComboPanel`. This allows the existing order item panels to use the new `ComboPanel` as its parent. 
* Use combo boxes to allow users to select from existing items to add to the combo. Add a listener/event handler for when the combobox is changed, and use that to change the panel for that item.
* Include a default option representing "no selection" in the combo boxes to allow users to clear out a particular option. 
* Recall that the panels for each menu item will call a method in the parent panel when the item is saved. This can be used to retrieve the updated item from the panel when the "Save" button is clicked in the combo customization panel. Here's the basic order of events:
  1. Click "Save" in `ComboPanel`
  2. Fire "save" event in item panel
  3. Receive item from panel via the panel calling the save method in its parent (which is now `ComboPanel` instead of `PrimaryWindow`)
  4. Update the combo order item
  5. Call the save method in the `PrimaryWindow` to add the item to the order.
* You may choose to add additional getters to the classes in the `data` package as desired.
* In Python, you may have a circular reference in your `PanelFactory` since it could be used from within `ComboPanel`, but also will be used to create instances of `ComboPanel`. A way to resolve this would be to create a `ComboPanelFactory` to handle combos, and adapt the code where `PanelFactory` is used to direct combo instances to the new `ComboPanelFactory` instead.

{{% /notice %}}

###### Unit Tests

Your new GUI panel(s) should include some basic **unit tests** modeled after the tests used for the item panels. Specifically, you should test the following:

* Selecting a particular entree, side, or drink in the appropriate GUI element causes a panel of the correct type to be loaded.
* Receiving a combo as input containing a particular entree, side, or drink causes the panel of the correct type to be loaded.
* Selecting a particular entree, side, or drink to be included in the combo via the GUI causes an item of that type to be added to the resulting `Combo` object when it is saved.
* Selecting the "no selection" option will remove that item from an existing `Combo` object when it is saved.
* Cancelling will result in no changes being made to the `Combo` object.

You should use test doubles (stubs, fakes, or mocks) in these unit tests to mimic the other parts of the application, including the order items and associated panels. The goal is to only test the new GUI panel(s) in isolation. This may not be possible in Python due to issues with mocking classes from `tkinter`.

#### New Classes

This assignment will add one new class to the project

###### Panel Factory

`sfsubs.gui.PanelFactory` - a class that implements the **Factory Method Pattern** to return an instance of a GUI panel for a given entree, side, or drink.
* It should include one public **static** method that is overloaded to accept two different sets of parameters:
  * **get panel(String name, `PrimaryWindow` parent)** should accept the name of a menu item item as a string, and return a panel that represents a new instance of that item, with the `parent` GUI element as its parent. You should be able to directly feed an action command from a button click in the GUI directly to this method and get the appropriate panel. If the `name` is not recognized, an exception should be thrown.
  * **get panel(`Item` item, `PrimaryWindow` parent)** should accept an instance of an `Item` and return a panel that represents that item, with the `parent` GUI element as its parent. If the `item` is not recognized, an exception should be thrown.
* Once you have created your GUI panels for handling combos as outlined above, it should also be integrated into this factory class.

#### Updated Classes

There will also be several updates to existing classes.

###### Menu Panel

**`MenuPanel`** - update to include the following items:
* The button handler method should be updated to use the new `PanelFactory` class to acquire the appropriate GUI panel based on the action command received from button that was clicked.

###### Order Panel

`OrderPanel` - update to include the following items:
* When clicking the **Edit** button, it should use the `PanelFactory` class to acquire the appropriate GUI panel based on the item selected in the tree. 
* This class should now include a private **order** attribute that stores the items in the sidebar in an `Order` instance as well. 
  * It should be instantiated by the `OrderPanel` constructor.
  * It should be kept up to date as items are added to and removed from the order in the sidebar.
  * Whenever the order is changed, it should be used to update the order number, subtotal, tax, and total elements in the GUI. Prices should be properly formatted as currency values. 
    * See [Currencies](https://docs.oracle.com/javase/tutorial/i18n/format/numberFormat.html) for Java. 
* The GUI should include two new buttons:
  * **New Order** - clicking this button will create a new `Order` instance and reset all appropriate GUI elements for a new order. This will delete any existing order.
    * You may wish to implement a modal dialog that asks the user to confirm before deleting the existing order. See [How to Make Dialogs](https://docs.oracle.com/javase/tutorial/uiswing/components/dialog.html) for Java or [Dialog Windows](https://tkdocs.com/tutorial/windows.html#dialogs) for Python. This is not required but highly recommended!
  * **Checkout** - clicking this button will have no effect at this time. It will be implemented in a future milestone.

### Documentation Comments

All new and updated classes in this milestone should contain full documentation comments. **Every method should be completely documented!**

### Unit Tests

Some previous tests may need to be updated to match new requirements.

Once this milestone is complete, all classes in the following packages should continue to have unit tests that achieve at or near 100% code coverage:

* `sfsubs.data.*`
* `sfsubs.gui.drinks.*`
* `sfsubs.gui.entrees.*`
* `sfsubs.gui.sides.*`

The only classes that do not meet this requirement are `PrimaryWindow`, `OrderPanel`, `PanelFactory`, and `MenuPanel` in the `sfsubs.gui` package. 

Any new classes created to handle editing combos should include unit tests. Refer to the associated example project for some ideas of how to unit test that class.

## Time Requirements

Completing this project is estimated to require 3-8 hours.

{{% notice tip %}}

_A rough estimate for this milestone would be around 2000 lines of new or updated code. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* GUI for Combos & Unit Tests: 50%
* New Classes: 20%
  * `PanelFactory`
* Class Updates: 30%
  * `OrderPanel` - 20%
  * `MenuPanel` - 10%

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

#### Sample Combo Customization GUI

![Combo Window](/images/m7/410_m7_gui.svg)

