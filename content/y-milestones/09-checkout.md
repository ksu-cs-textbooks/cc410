---
title: "Checkout"
pre: "9. "
weight: 90
---

This page lists the milestone requirements for **Milestone 9** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Game Grub_, offering food of all kinds to celebrate our love of games of all kinds. 

The ninth milestone involves finalizing the GUI for creating orders and combos, and handling the steps to check out and pay for an order, including printing a receipt. The purpose is to continue to learn how to use and modify an existing GUI and interface with an external library. 

{{% notice warning %}}

Fewer hints will be given as to the overall structure of your implementation for this milestone. Therefore, you will have to make some decisions about how you feel this milestone should be best achieved and the overall structure of your code!

When in doubt, feel free to contact the course instructor to discuss possible ideas. You may also choose to write small "demo" implementations either in this project or one of the related example projects before committing to a particular solution.

{{% /notice %}}

## General Requirements

{{< expand "All projects must follow the professional coding standards listed here (click to expand):" >}}

{{< include-local "../_includes/a-requirements.md" >}}

{{< /expand >}}

## Assignment Requirements

Implement the following features into your existing project.

#### Checkout

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

The `CashDrawer` class in the external library is used to keep track of the available amount of each denomination in the drawer and to balance transactions. Each transaction begins by opening the drawer and providing the expected amount to be deposited. Then, while the drawer is open, cash denominations are added to the drawer from the customer and any change given back is deducted from the drawer. When the drawer is closed, the amount it contains must equal the previous amount plus the expected transaction amount. In addition, the total value in the drawer and the count of each denomination in the drawer may only be accessed when the drawer is closed. 

{{% notice warning %}}

Your project must only instantiate a `CashDrawer` instance once, when the project is first launched. It should use that same `CashDrawer` instance for all transactions, updating it as needed, until the application is closed.

{{% /notice %}}

Cash denominations are listed in the `CashDenomination` enum, which includes both the name and value of each denomination. 

If the customer has not provided enough money to pay for the transaction, your application should not allow it to be finalized. Your application should also handle making appropriate change from the cash drawer when finalizing a transaction. This includes determining the count of each denomination to be given back to the customer. Some tips for completing this portion of the project:

* The contents of the drawer cannot be queried while the drawer is open, nor can the contents of the drawer be updated while it is closed. The external library will throw exceptions if this rule is violated.
* To make change, find the amount to be given back and work from the highest denomination to the lowest. Make use of division and modulo arithmetic. (This is exactly backwards to how you were most likely taught to do this in your head!) If you use any online resources to create this algorithm, make sure you cite them in the comments of your code. 
* The cash drawer contains limited amounts of each denomination. So, when making change, you may find that you don't have enough of a particular denomination. If that is the case, deduct one from the next largest available denomination and use that to refill this denomination. We will assume that you are able to freely convert one denomination to another using an external source. **This is more difficult than it may seem. Make sure the rest of the process works before worrying about this edge case - it is not worth very many points!**

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

The receipt can only be printed one line at a time using the appropriate method in the `ReceiptPrinter` class, and each line is limited to **no more than 40 characters**. You are encouraged to make use of simple formatting, ASCII art, and short indentations to make the receipt more readable. There are methods provided in the `ReceiptPrinter` class to start and end a receipt.

The `ReceiptPrinter` class will print the receipt to a file named `receipt.txt` in the project folder. By default, the `ReceiptPrinter` will append new receipts to the end of that file. You may wish to empty this file regularly as part of testing, and should not commit it to GitHub. 

##### Documentation Comments

All new and updated classes in this milestone should contain full documentation comments. **All methods must be fully documented!**

##### Unit Tests

Your application should include **unit tests** to test any functionality provided by your application. Specifically, you should test the following:

* When a cash transaction is finalized, the customer must have provided an amount of money equal to or greater than the transaction amount.
* When a cash transaction is completed, your application makes the correct change - both the amount and the denominations returned.
* When making change, the application will correctly handle the situation when not enough of a denomination is present. 
* When a receipt is printed, it includes all of the information in an order. 

You **do not** have to verify that the external library functions correctly. It already contains a complete set of unit tests. You are encouraged to review the source code of the unit tests contained in the external library for examples of how to test your own code!

Instead, you are **highly** encouraged to write wrapper classes around the classes in the external library using the **adapter pattern** and test those wrapper classes that contain your logic. 

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

* Credit Card - 10%
* Cash Interface - 10%
* Makes Change - 30%
* Prints Receipt - 30%
* Unit Tests - 20%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.

---
---
---


#### Sample Cash Transaction GUI

You may wish to review the [Spinner](https://docs.oracle.com/javase/tutorial/uiswing/components/spinner.html) (Java) or [Spinbox](https://tkdocs.com/tutorial/morewidgets.html#spinbox) (Python) GUI elements.

![Cash Window](/images/m7/410_m7_gui_cash.svg)
