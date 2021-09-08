---
title: "Assignment Requirements"
weight: 10
pre: "1. "
---

This page lists the example project requirements for **Example 4** in CC 410. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

This example will cover adapting an existing project to use inheritance and interfaces

## General Requirements

{{% notice warning %}}

This project is the first that requires **ALL** general requirements introduced in the "Hello Real World" project. Read this section carefully to see what is required for this particular milestone.

{{% /notice %}}

{{% expand "All projects must follow the professional coding standards listed here (click to expand):" %}}

{{% include-local "../../_includes/a-requirements.md" %}}

{{% /expand %}}

## Assignment Requirements

This milestone should include the following features:

* Update all fruit classes to directly inherit from the `Fruit` abstract class.
  * The `Fruit` class should include an abstract getter for the `name` attribute that returns the name of the fruit.
* Add an `IBlendable` interface that defines a `blend()` method, and all classes that include the `blend()` method should implement that interface.
* Add a new `Apple` class that properly inherits the `Fruit` superclass and the `IBlendable` interface.
* Update the `main()` method in the `Main` class to do the following:
  * Create a list containing an instance of each class implementing the `IBlendable` interface. The list should have the `IBlendable` data type.
  * Iterate through the list and call the `blend` method on each object.
  * If the object is a subclass of `Fruit`, print the name of the fruit before calling `blend`.
  
## Time Requirements

Completing this project is estimated to require 1 hour.

## Grading Rubric

This assignment will be graded based on the rubric below:

* `Fruit` abstract class - 30%
* Fruit classes properly inherit `Fruit` - 10%
* `IBlendable` interface - 30%
* Blendable classes properly implement `IBlendable` - 10%
* Main method code - 20%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.