---
title: "Validation & Serialization"
pre: "11. "
weight: 110
date: 2021-04-21T00:53:26-05:00
hidden: true
---

This page lists the milestone requirements for **Milestone 11** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Game Grub_, offering food of all kinds to celebrate our love of games of all kinds. 

The eleventh milestone involves adding form validation and serialization to the existing project, specifically targeted at custom menu items.

## General Requirements

{{< expand "All projects must follow the professional coding standards listed here (click to expand):" >}}

{{< include-local "../_includes/a-requirements.md" >}}

{{< /expand >}}

## Assignment Requirements

This milestone consists of two portions: adding form validation to the forms for creating and editing custom items, and serializing those custom items to a file.

#### Form Validation

Update the forms for creating and editing custom menu items to perform server-side validation. This should use the built-in features of either Java Spring or Python Flask, as demonstrated in the example video. The following validation rules should be enforced:

* The `name` of the custom menu item should not be null, and have at least 4 characters.
* The `price` of the custom menu item must be greater than or equal to 1.50, and support no more than 2 decimal places. You may either use a validator for this or implement rounding in the setter for this item.
* The `calories` of the custom menu item must be an integer greater than or equal to 250.

When validation fails, the user should be taken back to the form, where the entered values are still present and the validation errors are clearly displayed. 

{{% notice tip %}}

Java developers will need to change the `price` attribute to use the `BigDecimal` class ([Javadoc](https://docs.oracle.com/javase/8/docs/api/java/math/BigDecimal.html)) in order to enforce a limit on the number of digits using a validator. I recommend maintaining the existing getter and setters for `price` (adapting them to use the value in the new `BigDecimal` class) and then adding new getters and setters for this attribute. Likewise, in the HTML form, you'll use the new `BigDecimal` attribute instead of the existing `price`. See the example video for details.

{{% /notice %}}

#### Serialization

Update the application to use serialization to store and load the list of custom items. You may choose any file format (XML, JSON, or binary, or another of your choosing). See the serialization examples on GitHub ([Java](https://github.com/K-State-Computational-Core/serialization-examples-java) or [Python](https://github.com/K-State-Computational-Core/serialization-examples-python)) as well as the textbook for code you can use.

* The custom menu items should be loaded into memory when the singleton instance of the `CustomItemList` class is created. In Java, this would most likely be the `getInstance()` method, while in Python it would be in the `__new__()` method. So, when the user first visits the `/custom` page, the previously saved custom items should appear.
* The `CustomItemList` class should implement a new method called `save` that will serialize the current contents of the custom item list to a file.
* The application should add a new HTTP POST route to the `CustomController` with the path `/custom/save` that will save the existing custom items list to file by calling the new `save` method. 
* Add an HTML form to the `/custom` index page containing a button to save the custom items by sending a POST request to the new route. This form will be very similar to the one used on the page for deleting items.

The code should include proper exception handling when reading and writing files, as well as ensuring the file is properly closed. In Java, a [try with resources](https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html) statement is recommended. In Python, a [with inside a try](https://realpython.com/python-exceptions/) structure is recommended. You may simply catch the generic exception and print it to the terminal instead of handling multiple exception types.

As proof of working serialization, create the following custom menu item and serialize it to a file, then ensure that file is committed to your Git repository when committing this project.

* **Name**: The Katharine Hepburn
* **Price**: 12.50
* **Calories**: 1907

#### Documentation & Testing

* All new classes and methods must include full documentation comments.
* HTML templates do not require documentation, but inline comments are recommended if they are useful.
* No new unit tests are required for this milestone.

## Time Requirements

Completing this project is estimated to require **2 - 5** hours.

{{% notice tip %}}

_A rough estimate for this milestone would be around 100 lines of new or updated code.-Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* Validation: 30%
  * Name: 10%
  * Price: 10%
  * Calories: 10%
* Serialization: 70%
  * Save: 30%
  * Load: 30%
  * Preloaded Entry: 10%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.
* Any portion of the project which does not meet the general requirements listed above will have a commensurate amount of points deducted.
* Points will be deducted if pages do not contain valid HTML5 with all tags properly closed. 

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

{{% notice note "Code Review" %}}

_As part of the grading of all assignments in this course, I will be doing a deep dive into a few classes in your code. This will include leaving detailed comments on code style and format in GitHub. I will usually choose various classes to review at random, and any issues found in that class will be verified in other classes of the same type. For any GUI and Web portions, I'll also be testing the functionality of the UI for each class under review. - Russ_

{{% /notice %}}

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.