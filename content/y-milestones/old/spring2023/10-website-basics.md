---
title: "Website Basics"
pre: "10. "
weight: 100
---

This page lists the milestone requirements for **Milestone 10** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Game Grub_, offering food of all kinds to celebrate our love of games of all kinds. 

The tenth milestone involves moving into the web by creating a data-driven website to display the menu and some other information about the restaurant.

## General Requirements

{{< expand "All projects must follow the professional coding standards listed here (click to expand):" >}}

{{< include-local "../../../_includes/a-requirements.md" >}}

{{< /expand >}}

## Assignment Requirements

###### Web Framework

Add a Web Framework to the existing project.

* **Java** - Install the [Spring](https://spring.io/) framework using the [Spring Initializr](https://start.spring.io/). It should include the Spring Boot DevTools, Spring Web, and Thymeleaf Template Engine as dependencies.
* **Python** - Install the [Flask](https://flask.palletsprojects.com/en/1.1.x/) framework and the [Flask-Classful](https://flask-classful.teracy.org/) extension. You may also wish to install `python-dotenv` to use a `.flaskenv` file. 

{{% notice warning %}}

**Java Users** - You will need to remove the `'org.junit.jupiter:junit-jupiter-api:5.6.2'` entry from the `testImplementation` section of the dependencies. It conflicts with the version provided by Spring.

**Python Users** - You may ignore any type errors from `flask_classful` by adding `#type: ignore` after the import line.

{{% /notice %}}

###### Web Code

* Create a new `gamegrub.web` package.
* Create a `gamegrub.web.MenuController` class to act as the controller. It should include the following routes:
  * `/` - a home page for the application.
  * `/about` - an about page with the text given at the bottom of the page. You may add additional text and items as desired
  * `/menu` - a page that includes the entire menu (all predefined combos, entrees, sides, and drinks). 
    * It should use the existing `Menu` class to collect these items. 
    * You may add additional methods (with requisite unit tests) to the `Menu` class as desired to make this work.
* Update the required files to launch the web application properly as shown in the example video.

###### Templates

Create a base layout file including the following:

* Valid HTML5 structure
* A &lt;title&gt; element including the page name, followed by ` - Game Grub`
* A &lt;body&gt; containing:
  * &lt;nav&gt; that contains links to all pages in the application
  * &lt;main&gt; containing all the content in the page
  * &lt;footer&gt; containing the following copyright notice: "&copy; 2023 Game Grub"
* It is recommended (but not required) to build upon an existing template. You may wish to review the [Bootstrap 4.6 Examples](https://getbootstrap.com/docs/4.6/examples/). 

Create the following template files to match the routes listed above:

* `index.html` contains an &lt;h1&gt; tag with the title "Homepage" and the following text in a paragraph (you may add additional text as desired):

> Welcome to Game Grub! Our motto: play fair, eat well!

* `about.html` contains an &lt;h1&gt; tag with the title "About Game Grub" and the following text in a paragraph (you may add additional text as desired):

> Game Grub was developed as part of the CC 410 course at Kansas State University by &lt;your name here&gt;.

* `menu.html` contains the following content:
  * an &lt;h1&gt; containing "Menu"
  * an &lt;h2&gt; for each of the four categories of menu items (entree, side, drink, combo)
  * Each menu item should be placed in a &lt;div&gt; with the class `menu-item`. It should include:
    * The name of the item
    * The price of the item
    * The calories of the item
    * _If the item comes in multiple sizes, the price and calories for each size should be listed somehow!_
    * _If the item is a combo, you may also include the contents of the combo!_
  * You may use additional HTML elements & CSS style to improve the readability of this page as you see fit! As with the GUI project, this is your chance to explore a bit. 
    * The model solution uses the [Card](https://getbootstrap.com/docs/4.6/components/card/) component and [Row Columns](https://getbootstrap.com/docs/4.6/layout/grid/#row-columns) in Bootstrap 4.6. 
  * Under the "Combo" heading, add a note that any entree, sides, and drink may be combined for a combo discount, and print the current combo discount value as well. (_Hint: you'll have to send this through the controller to the template somehow..._)

{{% notice tip %}}

You can format currency values directly in your templates! See [Formatting Currencies in Spring using Thymeleaf](https://www.baeldung.com/spring-thymeleaf-currencies) for Java or using the familiar Python [String.format()](https://realpython.com/python-formatted-output/) function as demonstrated in this [StackOverflow](https://stackoverflow.com/a/31158813) comment.

{{% /notice %}}

###### Documentation & Testing

* All new classes and methods must include full documentation comments.
* HTML templates do not require documentation, but inline comments are recommended if they are useful.
* No new unit tests are required. 

## Time Requirements

Completing this project is estimated to require **2 - 5** hours.

{{% notice tip %}}

_A rough estimate for this milestone would be around 500 lines of new or updated code, the majority of which is HTML. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* Web Framework Installation: 10%
* Web Code: 30%
  * Index & About Routes: 10%
  * Menu Route: 20%
* Templates: 60%
  * Layout Template: 20%
  * Index & About Templates: 10%
  * Menu Template: 30%

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

---
---
---

## Web Sketches

Below is a screenshot from a previous model solution for some web design inspiration.

![Main Window](/images/m8/410_m8_menu.png)