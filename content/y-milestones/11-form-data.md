---
title: "Form Data"
pre: "11. "
weight: 110
---

This page lists the milestone requirements for **Milestone 11** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Game Grub_, offering food of all kinds to celebrate our love of games of all kinds. 

The eleventh milestone involves augmenting the menu display from the previous project by adding search and filtering functionality via an HTML form.

## General Requirements

{{< expand "All projects must follow the professional coding standards listed here (click to expand):" >}}

{{< include-local "../_includes/a-requirements.md" >}}

{{< /expand >}}

## Assignment Requirements

This milestone adds several pieces of functionality to your existing website, mostly based around searching and retrieving menu items.

#### Simple Search via Keywords

Your website should implement a simple search functionality via keywords, which allows the user to enter one or more words, separated by spaces, in a text input field, and then any menu items containing any of those keywords anywhere in the name of the item should be displayed on a results page. 

You should also handle the case where keyword searches will return a combo if it contains an item that matches the search term. For example, a search for "chess" should not only return that entree, but also any combos that include that item. 

Your search page should be accessible via the `search` route/URL. If you used a template layout that includes a search box, such as the [Bootstrap Sticky Footer with Navbar](https://getbootstrap.com/docs/4.6/examples/sticky-footer-navbar/), you may implement this search functionality using the search box in the default layout. Make sure that you specify the `action` of the form to point to the correct URL, since it will be available on all pages. The form should use the HTTP `POST` method.

You may choose to use the same template for both the search page and the results, or different templates. Also, don't forget to add a link to the `search` URL in your site's navigation in the layout template.

#### Advanced Search and Filter

Your website should also implement an advanced search and filter feature. This page will allow the user to find menu items based on the following criteria:
* Keywords (same as the simple search above)
* Type (entree, side, drink, combo)
* Price Range (minimum & maximum)
* Calories Range (minimum & maximum)

Your advanced search page should include HTML form elements for each of the items given above, arranged to make it clear to the user how to use the form. Try to make it as functional as possible based on the user's intent. For example, if the user doesn't enter any keywords, assume that they wish to find all menu items. Likewise, if the user inputs a maximum price but not a minimum, you should show all items that are less than the maximum price given. When submitted, the form should use the HTTP `POST` method. If any inputs are invalid or cannot be parsed, you should substitute them with reasonable default values.

Your advanced search page should be accessible via the `advancedsearch` route/URL. You should add a link to this URL to your site's navigation.

You **must** use the same template for both the search form and displaying results. If the search form has been completed and submitted, the submitted values should be present in the form where the results are displayed. Likewise, if the form has not been completed or no results are present, the site should clearly present that information to the user. 

#### Search Functions in Menu

The functions required to search and filter the menu should be implemented in the existing `Menu` class as static methods. You **should not** perform any searching in the web application controller itself - it should simply call these methods as needed.

Some recommended functions you may wish to implement:

* `filterKeywords(Iterable<Item> items, String keywords) - returns Iterable<Item>`
* `filterTypes(Iterable<Item> items, boolean entree, boolean side, boolean drink, boolean combo) - returns Iterable<Item>`
  * Alternatively, you could call the appropriate existing methods to collect these types initially before filtering
* `filterPrice(Iterable<Item> items, float min, float max) - returns Iterable<Item>`
* `filterCalories(Iterable<Item> items, int min, int max) - returns Iterable<Item>`

Each new method added to `Menu` should include proper unit tests. You are encouraged to use test doubles (mocks, etc.) to test these methods rather than using actual menu items. 

{{% notice note "Iterable Class" %}}

_In the method signature above, the `Iterable` class is simply an interface. In Java, you can use a `List` subtype such as `LinkedList` that supports that interface. In Python, the base `List` type will also work. - Russ_

{{% /notice %}}

#### Documentation & Testing

* All new classes and methods must include full documentation comments.
* HTML templates do not require documentation, but inline comments are recommended if they are useful.
* Any methods added to the `Menu` class require unit tests to achieve 100% coverage. You should use test doubles in these unit tests, and make sure you are testing all possible outcomes. 

## Time Requirements

Completing this project is estimated to require **2 - 5** hours.

{{% notice tip %}}

_A rough estimate for this milestone would be around 750 lines of new or updated code, the majority of which is HTML and unit tests. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* Simple Search: 30%
  * Keyword Search: 15%
  * Results: 15%
* Advanced Search: 50%
  * Types: 10%
  * Price: 10%
  * Calories: 10%
  * Results: 20%
* Unit Tests: 20%

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