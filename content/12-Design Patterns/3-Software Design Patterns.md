---
title: "Software Design Patterns"
weight: 15
pre: "3. "
---
The most important part of the book by the "Gang of Four," as evidenced by the title, are the 23 software design patterns that are discussed within the book.

A **software design pattern** is a reusable structure or solution to a common problem or usage within software development. Throughout the course of developing many different programs in the object-oriented paradigm, developers may find that they are reusing similar ideas or code structures within applications with completely different uses, which leads to the idea of formalizing these ideas into reusable structures.

However, it is important to understand that a design pattern is not a finished piece of code that can simply be dropped into a program. Instead, a design pattern is a framework, structure, or template that can be used to achieve a particular result or solve a given problem. It is still up to the developer to actually determine if the design pattern can be used, and how to make it work.

The power of these design patterns lies in their common structure and the familiarity that other developers have with the pattern. For example, when building a program that requires a single global instance of class, there are many ways to do it. One way is the **singleton pattern**, which we'll explore later in this chapter. If we choose to use that pattern, we can then tell other developers "this uses the singleton pattern" and, hopefully, they'll be able to understand how it works as long as they are familiar with the pattern. If they aren't, then the usefulness of the pattern is greatly reduced. So, it is very helpful for developers to be familiar with commonly-used design patterns, while constantly being on the lookout for new and interesting patterns to learn about and add to their ever growing list of patterns that can be used. 

A great analogy is poetry. If we write a simple poem containing 5 lines, where the first, second, and fifth all end in a rhyming word and have the same number of syllables, and the third and fourth also rhyme and have fewer syllables, it could be very difficult to explain that structure to another writer. However, if we just say "I've written a [limerick](https://en.wikipedia.org/wiki/Limerick_(poetry))" to another writer, that writer might instantly understand what we mean, just based on their own familiarity with the format. However, if the writer is not familiar with a limerick, then referencing that pattern might not be helpful at all.

## Software Design Pattern Categories.

In _Design Patterns_, the "Gang of Four" introduced 23 patterns, which were grouped into three categories:

* **Creational Patterns** - these patterns are used to create instances objects, typically by doing so in a programmatic way instead of directly instantiating the object.
  * Abstract Factory Pattern
  * Builder Pattern
  * Factory Method Pattern
  * Prototype Pattern
  * Singleton Pattern
* **Structural Patterns** - these patterns are mainly used to structure individual classes or groups of classes using inheritance, interfaces, and composition.
  * Adapter Pattern
  * Bridge Pattern
  * Composite Pattern
  * Decorator Pattern
  * Facade Pattern
  * Flyweight Pattern
  * Proxy Pattern
* **Behavioral Patterns** - these patterns determine how objects act and interact, mainly by communicating between objects using message passing.
  * Chain of Responsibility Pattern
  * Command Pattern
  * Interpreter Pattern
  * Iterator Pattern
  * Mediator Pattern
  * Memento Pattern
  * Observer Pattern
  * State Pattern
  * Strategy Pattern
  * Template Method Pattern
  * Visitor Pattern

In addition, many modern references also include a fourth category: **Concurrency Patterns**, which are specifically related to building programs that run on multiple threads, multiple processes, or even across multiple systems within a supercomputer. We won't deal with those patterns in this course since they are greatly outside the scope of what we're going to cover. 

Instead, we're going to primarily focus on three creational patterns: **the builder pattern**, **the factory method pattern**, and **the singleton pattern**. Each one of these is commonly used in many object-oriented programs today, and we'll be able to make use of each of them in our ongoing course project.

We'll also look at a few of the structural and behavioral patterns: **the iterator pattern**, the **template method pattern**, and **the adapter pattern**.
