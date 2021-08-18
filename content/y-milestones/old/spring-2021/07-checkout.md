---
title: "Checkout"
pre: "7. "
weight: 65
date: 2021-03-06T00:53:26-05:00
---

This page lists the milestone requirements for **Milestone 7** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Starfleet Subs_, based in the [Star Trek](https://en.wikipedia.org/wiki/Star_Trek) universe. 

The seventh milestone involves finalizing the GUI for creating combos, and handling the steps to check out and pay for an order, including printing a receipt. The purpose is to continue to learn how to use and modify an existing GUI and interface with an external library. 

{{% notice warning %}}

Fewer hints will be given as to the overall structure of your implementation for this milestone. Therefore, you will have to make some decisions about how you feel this milestone should be best achieved and the overall structure of your code!

When in doubt, feel free to contact the course instructor to discuss possible ideas. You may also choose to write small "demo" implementations either in this project or one of the related example projects before committing to a particular solution.

{{% /notice %}}

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

It is best to think of this assignment as one consisting of two distinct parts.

### Part 1 - Update GUI Panels to Handle Combos

Add updated buttons and panels to the GUI to facilitate creation and customization of combos created as part of the previous milestone. It should have the following features:

* Users should be able to directly select one of the pre-built combos included in the previous milestone and add it to the order.
* Users should be able to create a custom combo consisting of an entrée, side, and/or drink of their choice.
  * You do not have to enforce the requirement that a combo contains all three items to be added to the order. However, the combo should only get the discount if all three items are populated. The existing `Combo` class should handle this as defined in the previous milestone.
* Any entrée, side, or drink in the combo should also be customizable.
* Some of the code in the `SidebarPanel` class will need to be updated to properly handle combos.
  * Combos should be displayed with the name of the combo as the topmost element in the tree. If the name is not set, a default name may be used.
  * If the combo is eligible for the discount, that message should be displayed as a child node of the combo. 
  * Each item in the combo should be displayed below the combo name as a child node.
  * The special instructions of each item in the combo should be displayed as child nodes of the appropriate item.
  * In effect, combos will have 3 levels in the tree instead of the usual 2 for other order items.
  * This means that some of the logic for handling item selection and updates will need to be carefully updated. 
    * You may choose to simply write special cases for handling combos instead of generalizing or using recursion (the tree will be limited to 3 levels of depth, not including the single hidden root node).
* Any new functionality should not interfere with previous functionality. This means:
  * All individual entrées, sides, and drinks can be added to the order and customized.
  * Any items in the order can be selected and edited.
    * If an item is part of a combo, you may choose to load the screen for editing the entire combo instead of the item selected - this is up to you!

##### Hints for Part 1

At the bottom of this page is a GUI sketch of one possible way to build a screen for customizing a combo. It is designed to reuse the existing panels for each menu item. We will refer to this class as `ComboPanel` in this document. In your implementation, you are encouraged to reuse existing code whenever possible - try to stick to the [Don't Repeat Yourself](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) principle. Some hints for this particular implementation:

* Instead of each panel using the `MainWindow` class/type as its parent, we can abstract that to a `ParentPanel` interface that is implemented by both the `MainWindow` class and `ComboPanel`. This allows the existing order item panels to use the new `ComboPanel` as its parent. 
* Use combo boxes to allow users to select from existing items to add to the combo. Add a listener/event handler for when the combobox is changed, and use that to change the panel for that item.
* Include a default option representing "no selection" in the combo boxes to allow users to clear out a particular option. 
* Recall that the panels for each menu item will call a method in the parent panel when the item is saved. This can be used to retrieve the updated item from the panel when the "Save" button is clicked in the combo customization panel. Here's the basic order of events:
  1. Click "Save" in `ComboPanel`
  2. Fire "save" event in item panel
  3. Receive item from panel via the panel calling the save method in its parent (which is now `ComboPanel` instead of `MainWindow`)
  4. Update the combo order item
  5. Call the save method in the `MainWindow` to add the item to the order.
* You may choose to add additional getters to the classes in the `data` package as desired.
* In Python, you may have a circular reference in your `PanelFactory` since it could be used from within `ComboPanel`, but also will be used to create instances of `ComboPanel`. A way to resolve this would be to create a `ComboPanelFactory` to handle combos, and adapt the code where `PanelFactory` is used to direct combo instances to the new `ComboPanelFactory` instead.

##### Unit Tests

Your new GUI panel(s) should include some basic **unit tests** modeled after the tests used for the item panels. Specifically, you should test the following:

* Selecting a particular entrée, side, or drink in the appropriate GUI element causes a panel of the correct type to be loaded.
* Receiving a combo as input containing a particular entrée, side, or drink causes the panel of the correct type to be loaded.
* Selecting a particular entrée, side, or drink to be included in the combo via the GUI causes an item of that type to be added to the resulting `Combo` object when it is saved.
* Selecting the "no selection" option will remove that item from an existing `Combo` object when it is saved.
* Cancelling will result in no changes being made to the `Combo` object.

You should use test doubles (stubs, fakes, or mocks) in these unit tests to mimic the other parts of the application, including the order items and associated panels. The goal is to only test the new GUI panel(s) in isolation. This may not be possible in Python due to issues with mocking classes from `tkinter`.

### Part 2 - Checkout

Implement the functionality for a user to checkout and complete an order. This process will make use of an external library to handle credit cards, cash transactions, and printing a receipt. First, you'll need to install the `register` library into your application:

* **Java**
  * Download and install the latest JAR file release from [GitHub](https://github.com/K-State-Computational-Core/restaurantregister-java/releases).
  * View the [Javadoc](https://k-state-computational-core.github.io/restaurantregister-java/) for specifics of how to use it.
  * Review the [Source Code](https://github.com/K-State-Computational-Core/restaurantregister-java/tree/main/app/src/main/java/edu/ksu/cs/cc410/register) if desired.
  * All library classes are in the `edu.ksu.cs.cc410.register` package.
  * Post any questions or bugs regarding the library to the [GitHub Issues](https://github.com/K-State-Computational-Core/restaurantregister-java/issues) page.
  * Pull requests for bug fixes are welcome! However, in general we won't greatly change or enhance the functionality of the library overall.
* **Python**
  * Download and install the latest wheel file release from [GitHub](https://github.com/K-State-Computational-Core/restaurantregister-python/releases).
  * View the [Documentation](https://k-state-computational-core.github.io/restaurantregister-python/) for specifics of how to use it.
  * Review the [Source Code](https://github.com/K-State-Computational-Core/restaurantregister-python/tree/main/cc410/register) if desired.
  * All library classes are in the `cc410.register` package.
  * Post any questions or bugs regarding the library to the [GitHub Issues](https://github.com/K-State-Computational-Core/restaurantregister-python/issues) page.
  * Pull requests for bug fixes are welcome! However, in general we won't greatly change or enhance the functionality of the library overall.

When the user clicks the "Checkout" button in the GUI, they should be presented with the following options:

* Pay by Credit/Debit Card
* Pay by Cash
* Cancel

Clicking "Cancel" will return to the main GUI screen without changing the existing order. 

Otherwise, see the descriptions below for the process of paying by credit/debit card or cash.

You may wish to use modal dialogs in various places in this milestone to present responses or error message to the user. See [How to Make Dialogs](https://docs.oracle.com/javase/tutorial/uiswing/components/dialog.html) for Java or [Dialog Windows](https://tkdocs.com/tutorial/windows.html#dialogs) for Python.

{{% notice tip %}}

Read this entire section before attempting to build this part of the application. You may wish to develop the wrapper classes and unit tests discussed in the unit testing section first, then use those wrappers in your eventual GUI panels. The design of the wrappers may inform the overall interaction design in the GUI.

{{% /notice %}}

##### Pay by Credit Card

When a user chooses to pay by credit card, the application should call the appropriate method of the `CardReader` class in the external library. That method will return one of the `CardTransactionResult` enumeration values, which describes the result. If the response is `APPROVED`, the transaction is completed and the application may proceed to print the receipt (see the description below). Otherwise, the appropriate error message from the `CardTransactionResult` should be displayed to the user, and they may choose to try again.

{{% notice note %}}

The `CardReader` class will return `APPROVED` roughly 40% of the time, and each other result will be returned around 10% of the time each.

{{% /notice %}}

##### Pay by Cash

When the user chooses to pay by cash, the application should show a window where the user can enter the cash denominations and amounts provided from the customer. One possible GUI sketch for this window is included at the bottom of this page.

The GUI should include a "Cancel" button that can be used at any time to cancel the cash transaction and return back to the main GUI screen without changing the existing order.

The `CashDrawer` class in the external library is used to keep track of the available amount of each denomination in the drawer and to balance transactions. Each transaction begins by opening the drawer and providing the expected amount to be deposited. Then, while the drawer is open, cash denominations are added to the drawer from the customer and any change given back is deducted from the drawer. When the drawer is closed, the amount it contains must equal the previous amount plus the expected transaction amount. In addition, the total value in the drawer and the count of each denomination in the drawer may be accessed when the drawer is closed. 

{{% notice warning %}}

Your project must only instantiate a `CashDrawer` instance once, when the project is first launched. It should use that same `CashDrawer` instance for all transactions, updating it as needed, until the application is closed.

{{% /notice %}}

Cash denominations are listed in the `CashDenomination` enum, which includes both the name and value of each denomination. 

If the customer has not provided enough money to pay for the transaction, your application should now allow it to be finalized. Your application should also handle making appropriate change from the cash drawer when finalizing a transaction. This includes determining the count of each denomination to be given back to the customer. Some tips for completing this portion of the project:

* The contents of the drawer cannot be queried while the drawer is open, nor can the contents of the drawer be updated while it is closed. The external library will throw exceptions if this rule is violated.
* To make change, find the amount to be given back and work from the highest denomination to the lowest. Make use of division and modulo arithmetic. (This is exactly backwards to how you were most likely taught to do this in your head!) If you use any online resources to create this algorithm, make sure you cite them in the comments of your code. 
* The cash drawer contains limited amounts of each denomination. So, when making change, you may find that you don't have enough of a particular denomination. If that is the case, deduct one from the next largest available denomination and use that to refill this denomination. We will assume that you are able to freely convert one denomination to another using an external source. 

{{% notice note %}}

Thankfully, the monetary system in the United States will always guarantee that change will be made with the fewest possible coins by following the naive algorithm described above. So, that greatly simplifies this process.

In addition, since the cash drawer will only accept deposits, we never have to worry about running out of cash. Simply make sure that the cash received from the customer is added to the drawer before removing the change. If needed, you can exchange the denominations provided from the customer to other denominations as part of your algorithm to make change. 

Finally, consider multiplying all values by 100 to work with whole integers instead of floating-point values. There is a great risk of [floating-point error](https://en.wikipedia.org/wiki/Floating-point_arithmetic#Accuracy_problems) when working with cash values in this way. 

{{% /notice %}}

When the transaction is completed successfully, the application may proceed to print the receipt (see the description below).

##### Printing a Receipt

Once a transaction has been completed successfully, the system should print a receipt containing the details of the transaction. The `ReceiptPrinter` class in the external library is used to print a receipt. 

The receipt should include the following information:

* The order number
* The date and time of the transaction
* A list of all items in the order, including price and special instructions. 
* The subtotal
* The tax amount
* The total amount
* The payment method (credit/debit or cash)
* If paid by cash, the amount received and the change given.

The receipt can only be printed one line at a time using the appropriate method in the `ReceiptPrinter` class, and each line is limited to **no more than 40 characters**. You are encouraged to make use of simple formatting, ASCII art, and short indentions to make the receipt more readable. There are methods provided in the `ReceiptPrinter` class to start and end a receipt.

The `ReceiptPrinter` class will print the receipt to a file named `receipt.txt` in the project folder. By default, the `ReceiptPrinter` will append new receipts to the end of that file. You may wish to empty this file regularly as part of testing, and should not commit it to GitHub. 

##### Unit Tests

Your application should include **unit tests** to test any functionality provided by your application. Specifically, you should test the following:

* When a cash transaction is finalized, the customer must have provided an amount of money equal to or greater than the transaction amount.
* When a cash transaction is completed, your application makes the correct change - both the amount and the denominations returned.
* When making change, the application will correctly handle the situation when not enough of a denomination is present. 
* When a receipt is printed, it includes all of the information in an order. 

You **do not** have to verify that the external library functions correctly. It already contains a complete set of unit tests. You are encouraged to review the source code of the unit tests contained in the external library for examples of how to test your own code!

Instead, you are encouraged to write wrapper classes around the classes in the external library using the **adapter pattern** and test those wrapper classes that contain your logic. 

For example:

* Write a method in your `CashDrawer` wrapper that accepts a transaction amount and a description of the cash denominations provided by the user, and then computes the correct change and returns a description of the denominations and amounts to be given as change. If the user did not provide enough cash, it could throw an exception or some other error.
* Write a method in your `CashDrawer` wrapper that accepts a description of the cash provided by the user, and a description of the change to be given. The method should compute the updated contents of the drawer using its existing contents, making substitutions when needed to handle situations where not enough of a denomination are present, and then return a description of those changes.
  * Your wrapper would also include a separate method to actually send those changes to the cash drawer, but that method **does not** need to be unit tested for correctness and shouldn't be directly called by the method above. That would technically be an _integration test_, which we aren't worrying about for now.
* Write a method in your `ReceiptPrinter` wrapper that accepts an `Order` object and returns a list of strings that represent the receipt to be printed. Verify that the contents of that list fully reflect the `Order` given to it.
  * Your wrapper would also include a separate method to actually print a list of strings to a receipt, but that method **does not** need to be unit tested for correctness and shouldn't be directly called by the method above.

{{% notice tip %}}

Review the source code of the `CashDrawer` class in the external library to see how it uses a hash map or dictionary to keep track of its contents. This is a good model for describing "cash" amounts made up of several denominations and amounts in these methods. 

{{% /notice %}}

If done correctly, you **should not** have to create a test double for any of the classes in the external library. While not an unbreakable rule, it is generally considered a bad practice to [mock a type you don't own](https://github.com/mockito/mockito/wiki/How-to-write-good-tests#dont-mock-a-type-you-dont-own), as that can lead to issues if the external library's API changes in the future. The mock version of the library will continue to function as before, meaning tests will pass that would otherwise fail when executed on the real library.

## Time Requirements

Completing this project is estimated to require **5 - 10** hours.

{{% notice tip %}}

_A rough estimate for this milestone would be around 1500-2000 lines of new or updated code. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* Part 1 - 50%
  * Combo Buttons on Order Panel - 5%
  * Combo Interface for selecting/editing items - 25%
  * Sidebar Handles Combos - 10%
  * Unit Tests - 10%
* Part 2 - 50%
  * Credit Card - 5%
  * Cash Interface - 5%
  * Makes Change - 15%
  * Prints Receipt - 15%
  * Unit Tests - 10%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.

---
---
---

#### Sample Combo Customization GUI

![Combo Window](/images/410_m7_gui.svg)

#### Sample Cash Transaction GUI

You may wish to review the [Spinner](https://docs.oracle.com/javase/tutorial/uiswing/components/spinner.html) (Java) or [Spinbox](https://tkdocs.com/tutorial/morewidgets.html#spinbox) (Python) GUI elements.

![Cash Window](/images/410_m7_gui_cash.svg)
