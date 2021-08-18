---
title: "RESTful Architecture"
pre: "10. "
weight: 100
date: 2021-04-12T00:53:26-05:00
---

This page lists the milestone requirements for **Milestone 10** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Starfleet Subs_, based in the [Star Trek](https://en.wikipedia.org/wiki/Star_Trek) universe. 

The tenth milestone involves building a RESTful web application that could be used to manage custom menu items.

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
  * **All HTML must conform to the HTML5 standard.** Use the [W3C Validator](https://validator.w3.org/) to check your rendered pages if desired.
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).

## Assignment Requirements

This milestone adds several pieces of functionality to your existing website, focused on managing custom menu items. First, you'll need to add new classes to represent and store the custom items. Then, you'll create a new web controller that follows a RESTful architecture to manage these custom items. While doing so, you'll also create several templates to display the custom items on the web. Finally, you'll update the UML diagram for your application to include the new web application classes.

### New Classes

#### CustomItem Class

Create a class `starfleetsubs.data.menu.CustomItem` that can represent a custom menu item. It should implement the `OrderItem` interface, and should include both getters and setters for all required attributes. The class itself should only store the name, price, and calories of the item. It may simply return an empty list for special instructions. You may add additional utility methods as desired. You do not have to create any unit tests for this class.

#### CustomItemList Class

Create a class `starfleetsubs.data.menu.CustomItemList` that represents a list of custom menu items. This class should implement both the **Iterator** design pattern (using the `Iterable<CustomItem>` type), as well as the **Singleton** design pattern. This class is designed to keep a single list of custom items in memory for the entire application. We are using the singleton pattern so that it can be instantiated in the web controllers as needed, and it will always refer to the same list.

This class should maintain a list of `CustomItem` objects, and provide methods for adding, retrieving, updating, and deleting those items. You may add additional utility methods as desired. You do not have to create any unit tests for this class.

{{% notice tip %}}

In Java, you may wish to refer to the methods commonly used in the [List](https://docs.oracle.com/javase/8/docs/api/java/util/List.html) interface. In Python, you may wish to refer to the methods in the [MutableSequence](https://docs.python.org/3/library/collections.abc.html) abstract base class, which includes "dunder" methods `__getitem__`, `__setitem__` and `__delitem__`, among others. 

{{% /notice %}}

In the next milestone, we will add serialization capabilities to this class, which will allow us to maintain a list of custom items across many application executions.

### Web Controller

Create a new web controller named `CustomItemController` to handle these custom items. It should follow a RESTful architectural style. Specifically, it should include the following URL routes:

| HTTP Method | URL Path | Description | CRUD Method |
|:-----------:|----------|-------------|:-----------:|
| GET | `/customitems` | Display all custom items. | Read All |
| GET | `/customitems/new` | Display a form to create a new item. | N/A |
| POST | `/customitems` | Create a new custom item | Create |
| GET | `/customitems/{id}` | Display a single custom item | Read One |
| GET | `/customitems/{id}/edit` | Display a form to edit the custom item | N/A |
| POST | `/customitems/{id}` | Update the custom item | Update |
| GET | `/customitems/{id}/delete` | Display a warning page before deleting an item | N/A |
| POST | `/customitems/{id}/delete` | Delete the custom item | Destroy |

More details about each page is included below. In these URLs, assume the `{id}` is the index of the custom menu item in the `CustomItemList` data structure.

{{% notice warning %}}

Unlike an actual RESTful application, this application will **NOT** maintain the same identifier for an item indefinitely. For example, if there are three items in the list, and the second item is removed, the identifier for the third item will now be changed. This is because it is now at a different index in the `CustomItemList` data structure, and because of this the URL to access that item will also change. However, since we are not using a relational database to store our data, this is a reasonable compromise that allows us to explore a RESTful architecture without the extra complexity of a database.

Since our application should also be following the [HATEOAS](https://en.wikipedia.org/wiki/HATEOAS) model, the links on the index page should be updated as soon as it is reloaded in the browser. So, we'll still be able to interact with our application, but it will only work well with just a single tab open. Otherwise, any deletions might cause unintended consequences.

Likewise, since browsers only natively support the HTTP GET and POST methods, we won't be using PUT or DELETE here. Using those methods requires client-side JavaScript code, which is outside of the scope of this class.

{{% /notice %}}

#### Base Layout

Add a link to the `/customitems` route to the navigation section of your site's base layout template.

#### All Items

You are encouraged to reuse the content from your existing template for displaying all menu items here. Each menu item should include a link to the `/customitems/{id}` route for that item. 

#### Single Item

This is a new page, but it can also reuse content from the existing template for menu items - just remove the loop! This page should include links to the `/customitems/{id}/edit` and `/customitems/{id}/delete` routes, as well as a link to the main `/customitems` route. 

#### New Item / Edit Item

You'll need to create a form that can be used for creating new items or editing existing items. Much of the template code is reused, and there are ways to use the same template for both routes. You may include additional HTML attributes on the HTML form to add limits to the numerical values. However, your web application may assume that data submitted matches the expected format. We will handle validation of form data in the next milestone.

{{% notice tip %}}

Python users are encouraged to use [Flask-WTF](https://flask-wtf.readthedocs.io/en/stable/) to create a special class for representing the form, as demonstrated in the example video. This will make the next milestone much simpler. 

Unfortunately, there is not something similar for Java users, but the Spring framework already includes parts that make the next milestone very simple with the existing code, only with slight modifications.

{{% /notice %}}

#### Delete Item

This page is a copy of the single item page, but with additional warnings about deleting the item. This page should have a form that uses the HTTP POST method to submit to the same URL. When submitted, it should delete the item from the list. 

For the user, the process to delete an item should follow this pattern:
1. `/customitems` - find the item to delete and click the link to see details.
2. `/customitems/{id}` - click the delete link to delete the item.
3. `/customitems/{id}/delete` - see a warning page about deleting, and click the delete link again. 
4. `/customitems/{id}/delete` - browser sends a POST request to this URL to delete the item (this is invisible to the user)
5. `/customitems` - browser is redirected back to the main page

### Update UML Diagram

At the end of this project, you should **update the UML diagram** for the project to include the new web application classes. You may choose to make multiple diagrams showing more detail within each package, and a summary diagram showing the relationships between the packages.

## Time Requirements

Completing this project is estimated to require **2 - 5** hours.

{{% notice tip %}}

_A rough estimate for this milestone would be around 500 lines of new or updated code. The new controller and new classes are under 100 lines each. However, the small amount of code required involves some complexity to make everything function properly. There are many moving pieces to this milestone, but they are all pretty simple to put together. Try to reuse existing template resources whenever possible, and get a small portion working before starting on the next. It is simplest to start with creating a new custom item, displaying the entire list, and displaying a single item. From there, most of those parts can be reused to build the rest of the application. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* `CustomItem` class - 10%
* `CustomItemList` class - 20%
* REST Controller & Templates - 60%
  * Create New - 15%
  * Read All - 10%
  * Read One - 10%
  * Update - 15%
  * Destroy - 10%
* UML Diagram Updates - 10%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.