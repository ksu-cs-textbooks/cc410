---
title: "Final Project"
pre: "A. "
weight: 5
date: 2021-08-17T00:53:26-05:00
---

This page lists the milestone requirements for the **Final Project** in CC 410. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

This assignment allow students to exercise their programming skills by building a project of their own design. Ideally, the project will be something related to the student's personal interests or area of study. All the requirements listed below are considered flexible and can be adapted to fit the individual project and student. 

## General Requirements

{{% expand "All projects must follow the professional coding standards listed here (click to expand):" %}}

{{% include-local "./_includes/a-requirements.md" %}}

{{% /expand %}}

## Assignment Requirements

A complete final project should include the following features:

#### Structural Requirements

* Satisfy **all general requirements** listed above.
* Include several **object-oriented data/object classes**, separated across at least two **packages**.
  * This does not include packages used for enums, base classes, or GUIs - there must be at least two distinct packages of instantiable data classes.
  * It is recommended, but not required, that applications follow the [Model-View-Controller](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) or MVC architecture.
* Demonstration of **inheritance** between classes.
  * This should include the use of both direct subclassing and interfaces. 
* A **user interface** with multiple panels/views/pages/operations.
  * This could be a graphical user interface (GUI), or a web-based interface.
* The use of an **external library** or **web API**.
  * The external library or API should be integrated directly into the application in some way.
* Proper **documentation comments** in code.
* A complete set of **UML Class Diagrams**.

#### Functional Requirements

  * Sufficient demonstration of **functionality** beyond just creating and storing data.
    * This means that there should be several functions that _do_ something with the data, such as perform an algorithm or compute a result. 
  * **Unit tests** to adequately test that the code works properly.
    * This should test the structure, defaults, and functionality of all data objects as well as any additional functionality. Basically, anything that is the demonstration of functionality described above should have associated tests.
    * A high level of code coverage should be achieved.
    * Some user interface code may be omitted from unit testing if it is impractical to test.

#### Other Requirements

* At least **one cool feature** above and beyond the requirements listed above. This is at your discretion, but as part of your project presentation you should clearly state the cool feature and why it is included. 

## Time Requirements

Completing this project is estimated to require 25-50 hours depending on familiarity with the tools involved. Spread across the entire semester, this equates to roughly 1-3 hours of work each week. This project should be roughly 1/4 to 1/3 the size and scope of the semester-long restaurant project.

## Milestones

The final project in this course will consist of several different milestones. Each milestone will require students to schedule a short meeting with the instructor or GTA to review the project as it stands and get feedback. The milestones are meant to roughly correspond to content being covered in this class. 

* Milestone 1 (Week 1) - Review project description and answer questions. Discuss possible topics.
* Milestone 2 (Week 5) - Discuss possible project topics and class structures.
* Milestone 3 (Week 9) - Discuss classes and inheritance, review existing unit tests and documentation. Discuss possible user interfaces.
* Milestone 4 (Week 13) - Discuss user interfaces, review existing code against requirements. Discuss possible external libraries or APIs. Review existing code against requirements. Discuss final steps and presentation.
* Milestone 5 (Week 16) - Present project to class, submit final code for review. 

## Deliverables

1. **Create a Release Tag on GitHub** - Your final submission to Canvas should include a release tag on GitHub to the final version of your project. Ensure that it meets the requirements listed above. All project deliverables should be included in the final GitHub release.
2. **Presentation** - Please include any presentation materials (slides, etc.) in your git repository and make sure they are uploaded to GitHub as part of your release tag. 
3. **Code Documentation** - Your code should include full documentation comments that can be used to generate developer documentation. Optionally, you may choose to deploy that documentation to GitHub pages. 
4. **Packaged Release** (_optional_) - You are encouraged to create a packaged release for your project that can be easily downloaded and installed.
5. **README File** (_optional_) - You are encouraged to create a `README` file that describes your project, including how to compile and run it. 
6. **User Documentation** (_optional_) - You may also include some user documentation describing how to use the project from a user's perspective. This may be included as part of your `README` file as well.

## Suggested Presentation Outline

* **Introduction** - Introduce yourself and the project
* **Background** - Give information on the project's inspiration and any related work to be aware of
* **Implementation** - Discuss how the project was designed and developed (_should be the bulk of the presentation_)
* **Evaluation** - Briefly evaluate how well your project met the original goal and how it compares to similar projects, if applicable
* **Future Work** - Share ways you would improve this project if given the opportunity to continue working on it
* **Conclusion** - Summarize what you learned
* **Demo** - Open your application and show us how it works, especially any cool features, and also open the source code and share interesting portions of it as well

## Grading Rubric

This assignment will be graded following the concept of **criterion grading**, an approach that **only** assigns points for completing the full requirements. However, the requirements will be brief and straightforward, and will be treated as such. Projects that meet the requirements listed above will, at a minimum, earn a passing grade of 60%. 

Projects that go above and beyond the requirements in various ways will be graded higher. In general, the goal of this project is to build a program that is interesting and engaging to the user, but also demonstrates the student's ability to develop professional code. So, projects that are easy to use, interesting, demonstrate good design and coding standards, and fit well within the student's defined interests are likely to earn additional points. 

Throughout the semester, students will have a chance to work with an instructor or GTA to get feedback on the project while it is being developed. These meetings allow the student to get information about which requirements have been met and which ones have not, as well as general overview of the project from the reviewer. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.