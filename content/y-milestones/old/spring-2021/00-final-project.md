---
title: "Final Project"
pre: "A. "
weight: 5
date: 2021-01-23T00:53:26-05:00
---

This page lists the milestone requirements for the **Final Project** in CC 410. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

This assignment allow students to exercise their programming skills by building a project of their own design. Ideally, the project will be something related to the student's personal interests or area of study. All the requirements listed below are considered flexible and can be adapted to fit the individual project and student. 

## General Requirements

All projects must follow these professional coding standards:

* **All code must be object-oriented.**
  * All executable code must be within a class
    * Python package files such as `__init__.py` and `__main__.py` are exempt.
  * Classes must be organized into packages based on common usage.
* **All projects must include automation for testing, style checking, and documentation generation.**
  * Java: Use Gradle with the `application`, `jacoco`, and `checkstyle` plugins.
  * Python: Use tox configured to use Python 3.6 and a requirements file to install libraries.
* **All code must properly compile and be executable.**
  * Java: It must compile and execute using Gradle.
  * Python: It must execute using Python 3.6. Where specified, type hints should be included in the code, and all code should pass a strict Mypy type check.
* **All code submitted must be free of style errors.** We will be using the [Google Style Guide](https://google.github.io/styleguide/) for each language. 
  * Java: Use Checkstyle 8.38+ and the [Google Style Configuration](https://raw.githubusercontent.com/checkstyle/checkstyle/checkstyle-8.38/src/main/resources/google_checks.xml). 
    * You may modify the configuration to allow 4 space indentations instead of 2 space indentations.
  * Python: Use Flake8 with the `flake8-docstrings` and `pep8-naming` plugins. Code should conform to PEP 8 style with Google style docstrings. 
* **Where specified, code should contain appropriate unit tests that achieve the specified level of code coverage.**
  * Java: Use JUnit 5. You may choose to use Hamcrest for assertions.
  * Python: Use pytest. You may choose to use Hamcrest for assertions.
* **Where specified, code should contain appropriate documentation comments following the language's style guide.**
  * Java: Use javadoc to generate documentation.
  * Python: Use pdoc3 to generate documentation.
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).

## Assignment Requirements

A complete final project should include the following features:

* Satisfy **all general requirements** listed above.
* Several **object-oriented classes**, separated across at least two **packages**.
  * It is recommended, but not required, that applications follow the [Model-View-Controller](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) or MVC architecture.
* Some use of **inheritance** between classes.
  * This could be done direct subclassing or the use of interfaces. 
* A **user interface**.
  * This could be a graphical user interface (GUI), the text console, or a web-based interface.
* The use of an **external library** or **web API**.
* **Unit tests** to adequately test that the code works properly.
  * A high level of code coverage should be achieved.
  * Some user interface code may be omitted from unit testing if it is impractical to test.
* Proper **documentation comments** in code.
* A complete **UML Class Diagram**.
* At least **one cool feature** not listed above.

{{% notice warning %}}

_As of January 2021, this list is subject to change as the course progresses, depending on how far into the content we get. - Russ_

{{% /notice %}}
  
## Time Requirements

Completing this project is estimated to require 25-50 hours depending on familiarity with the tools involved. Spread across the entire semester, this equates to roughly 1-3 hours of work each week. 

## Milestones

The final project in this course will consist of several different milestones. Each milestone will require students to schedule a short meeting with the instructor or GTA to review the project as it stands and get feedback. The milestones are meant to roughly correspond to content being covered in this class. 

* Milestone 1 (Week 1) - Discuss possible project topics and class structures.
* Milestone 2 (Week 5) - Discuss classes and inheritance, review existing unit tests and documentation. Discuss possible user interfaces.
* Milestone 3 (Week 10) - Discuss user interfaces, review existing code against requirements. Discuss possible external libraries or APIs.
* Milestone 4 (Week 14) - Discuss use of external library or API, review existing code against requirements. Discuss final steps and presentation.
* Milestone 5 (Week 16) - Present project to class, submit final code for review. 

## Deliverables

1. **Create a Release Tag on GitHub** - Your final submission to Canvas should include a release tag on GitHub to the final version of your project. Ensure that it meets the requirements listed above, including a full **UML Class Diagram**.
2. **Code Documentation** - Your code should include full documentation comments that can be used to generate developer documentation. Optionally, you may choose to deploy that documentation to GitHub pages. 
3. **README File** (_optional_) - You are encouraged to create a `README` file that describes your project, including how to compile and run it. 
4. **User Documentation** (_optional_) - You may also include some user documentation describing how to use the project from a user's perspective. This may be included as part of your `README` file as well.
5. **Presentation** - Please include any presentation materials (slides, etc.) in your git repository and make sure they are uploaded to GitHub as part of your release tag. 

## Suggested Presentation Outline

* **Introduction** - Introduce yourself and the project
* **Background** - Give information on the project's inspiration and any related work to be aware of
* **Implementation** - Discuss how the project was designed and developed (_should be the bulk of the presentation_)
* **Evaluation** - Briefly evaluate how well your project met the original goal and how it compares to similar projects, if applicable
* **Future Work** - Share ways you would improve this project if given the opportunity to continue working on it
* **Conclusion** - Summarize what you learned
* **Demo** - Open your application and show us how it works, and also open the source code and share interesting portions of it as well

## Grading Rubric

This assignment will be graded following the concept of **criterion grading**, an approach that **only** assigns points for completing the full requirements. However, the requirements will be brief and straightforward, and will be treated as such. Projects that meet the requirements listed above will, at a minimum, earn a passing grade of 70%. 

Projects that go above and beyond the requirements in various ways will be graded higher. In general, the goal of this project is to build a program that is interesting and engaging to the user, but also demonstrates the student's ability to develop professional code. So, projects that are easy to use, interesting, demonstrate good design and coding standards, and fit well within the student's defined interests are likely to earn additional points. 

Throughout the semester, students will have a chance to work with an instructor or GTA to get feedback on the project while it is being developed. These meetings allow the student to get information about which requirements have been met and which ones have not, as well as general overview of the project from the reviewer. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.