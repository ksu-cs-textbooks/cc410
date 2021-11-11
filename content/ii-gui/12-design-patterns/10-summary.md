---
title: "Summary"
weight: 50
pre: "10. "
---

In this chapter, we explored several **software design patterns** introduced by the "Gang of Four" in their 1994 book: _Design Patterns: Elements of Reusable Object-Oriented Software_. Design patterns are a great way to build our code using reusable, standard structures that can solve a particular problem or perform a particular task. By using structures that are familiar to other developers, it makes it easier for them to understand our code.

Software design patterns are loosely grouped into three categories:
* **Creational Patterns**
* **Structural Patterns**
* **Behavioral Patterns**

We studied 5 different design patterns. The first three were **creational patterns**:
* **Builder Pattern** is useful for building complex objects by offloading the work to a special builder class, letting other classes reference the builder as needed.
* **Factory Method Pattern** is used to construct objects based on a given parameter, making it easy to get the object you need without needing to even explicitly know the exact type. 
* **Singleton Pattern** allows us to make sure only a single instance of a class is present on a system at any given time.

We also studied a **structural pattern**:
* **Adapter Pattern** is helpful when we need to make an existing class's interface match a different desired interface

Finally, we looked at two **behavioral patterns**:
* **Iterator Pattern** allows us to walk through a collection of items, and makes use of the **enhanced for** or **for each** loops present in our language.
* **Template Method Pattern** allows us to build the internal structure of a method, but then delegate some of the actual computation to methods that can be overridden by subclasses. 

In the future, we can use these patterns in our code to solve specific problems and hopefully make our program's structure easier for other developers to understand.

{{< quizdown >}}

---
primaryColor: '#512888'
secondaryColor: '#cccccc'
textColor: black
shuffleQuestions: true
shuffleAnswers: true
locale: en
---

# Authors

Collectively, the authors of the book _Design Patterns: Elements of Reusable Object-Oriented Software_ are known by what name?

1. [X] The Gang of Four
1. [ ] The Group of Founders
1. [ ] The Design Pattern Developers
1. [ ] The Collective of Designers

# Criticism

Which of the following statements is one criticism that is discussed regarding the _Design Patterns_ book?

1. [X] It is focused on C++ and many issues have been fixed in newer languages
1. [ ] It does not contain patterns for web enabled applications
1. [ ] It uses imperative programming instead of object-oriented programming
1. [ ] It assumes that the reader is familiar with algorithm analysis

# Software Design Pattern

Which statement best explains what a **software design pattern** is?

1. [X] A reusable structure or solution to a common problem in software development
1. [ ] A class that includes reused elements from another class
1. [ ] A method for developing software quickly using sprints and scrums
1. [ ] A library that can be added to any software project

# Creational Patterns

**Creational patterns** are best described by which statement?

1. [X] Patterns to construct instances of objects programmatically
1. [ ] Patterns to build individual classes using inheritance
1. [ ] Patterns to determine how objects act and interact
1. [ ] Patterns to make programs run faster on old hardware

# Structural Patterns

**Structural patterns** are best described by which statement?

1. [X] Patterns to construct instances of objects programmatically
1. [ ] Patterns to build individual classes using inheritance
1. [ ] Patterns to determine how objects act and interact
1. [ ] Patterns to make programs run faster on old hardware

# Behavioral Patterns

**Behavioral patterns** are best described by which statement?

1. [X] Patterns to construct instances of objects programmatically
1. [ ] Patterns to build individual classes using inheritance
1. [ ] Patterns to determine how objects act and interact
1. [ ] Patterns to make programs run faster on old hardware

# Creational Patterns List

Which of the following design patterns are **creational patterns**? **Choose all that are correct.**

- [X] Builder Pattern
- [X] Factory Method Pattern
- [X] Singleton Pattern
- [ ] Iterator Pattern
- [ ] Template Method Pattern
- [ ] Adapter Pattern

# Structural Patterns List

Which of the following design patterns are **structural patterns**? **Choose all that are correct.**

- [ ] Builder Pattern
- [ ] Factory Method Pattern
- [ ] Singleton Pattern
- [ ] Iterator Pattern
- [ ] Template Method Pattern
- [X] Adapter Pattern

# Behavioral Patterns List

Which of the following design patterns are **behavioral patterns**? **Choose all that are correct.**

- [ ] Builder Pattern
- [ ] Factory Method Pattern
- [ ] Singleton Pattern
- [X] Iterator Pattern
- [X] Template Method Pattern
- [ ] Adapter Pattern

# Builder Pattern

The **builder pattern** is best described by which statement?

1. [X] Pattern to simplify creation of complex objects
1. [ ] Pattern to create multiple identical objects quickly
1. [ ] Pattern to fill an array with sample data
1. [ ] Pattern to construct an object without knowing the explicit type

# Factory Method Pattern

The **factory method pattern** is best described by which statement?

1. [X] Pattern to construct an object without knowing the explicit type
1. [ ] Pattern to simplify creation of complex objects
1. [ ] Pattern to fill an array with sample data
1. [ ] Pattern to create multiple identical objects quickly

# Singleton Pattern

The **singleton pattern** is best described by which statement?

1. [X] Pattern to ensure only one instance of a class exists
1. [ ] Pattern to prevent multiple variables storing the same value
1. [ ] Pattern to fill an array with sample data
1. [ ] Pattern to prevent multiple users from accessing data

# Iterator Pattern

The **iterator pattern** is best described by which statement?

1. [X] Pattern to traverse the elements in a collection
1. [ ] Pattern to repeat a method multiple times
1. [ ] Pattern to fill an array with sample data
1. [ ] Pattern to build a graph from a tree

# Adapter Pattern

The **adapter pattern** is best described by which statement?

1. [X] Pattern to fit an existing interface into a new interface
1. [ ] Pattern to store one data type in a different data type
1. [ ] Pattern to construct an object using an abstract class
1. [ ] Pattern to rebuild a program for different hardware

# Template Method Pattern

The **template method pattern** is best described by which statement?

1. [X] Pattern to define a skeleton for a method to be implemented later
1. [ ] Pattern to reuse a method in multiple classes
1. [ ] Pattern to build multiple objects using the same data
1. [ ] Pattern to write multiple methods with the same name

{{< /quizdown >}}