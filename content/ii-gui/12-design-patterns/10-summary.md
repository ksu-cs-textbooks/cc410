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
