---
title: "Summary"
weight: 60
pre: "12. "
---

In this chapter, we looked at how object-orientation adopted the concept of **encapsulation** to combine related **state and behavior** within a single unit of code, known as a **class**.  We further explored how **objects are instances of a class** created through invoking a **constructor** method.  

We also discussed several different ways of looking at and reasoning about objects - as a **state machine**, and as **structured data stored in memory**.  We discussed how a **method is really a form of message passing** that provides an **interface** to interact with objects safely.

Finally, we explored how all of these concepts are implemented in both the Java and Python programming languages.

## Review Quiz

Check your understanding of the new content introduced in this chapter below - this quiz is not graded and you can retake it as many times as you want.

{{< quizdown >}}

---
primaryColor: '#512888'
secondaryColor: '#cccccc'
textColor: black
shuffleQuestions: true
shuffleAnswers: true
locale: en
---

# Encapsulation

The term **encapsulation** refers to what part of object-oriented programming?

1. [X] Organizing code into units that handle state and behavior
1. [ ] Communication between various units in a program
1. [ ] Determining which code to run based on messages received
1. [ ] Converting data from one format to another

# Scope

**Scope** refers to what concept in programming?

1. [X] Which code can access a particular variable
1. [ ] The amount of memory used in an application
1. [ ] Cleaning dirty data from a database
1. [ ] Using multiple variables for the same data

# Information Hiding

**Information hiding** is a practice from programming used for what outcome?

1. [X] Protecting data from accidental changes by other parts of the program
1. [ ] Encrypting source code to prevent reverse engineering
1. [ ] Adding unused variables to confuse other developers
1. [ ] Preventing memory leaks by only using certain data types

# Package

A **package** is used in programming languages for what purpose?

1. [X] To group similar code and prevent name collisions
1. [ ] To make programs easier to install
1. [ ] To prevent developers from using external libraries
1. [ ] To send messages between various units of code

# Data Types

Rearrange the following data types below to match the order of the descriptions given below. (Click and drag to reorder elements) <br>
<br>
Whole numbers <br>
Numbers with fractional/decimal values <br>
`True` or `False` values <br>
List of characters <br>

1. `int`
2. `float` or `double`
3. `boolean` or `bool`
4. `String` or `str`

# Package

A **package** is used in programming languages for what purpose?

1. [X] To group similar code and prevent name collisions
1. [ ] To make programs easier to install
1. [ ] To prevent developers from using external libraries
1. [ ] To send messages between various units of code

# Static Typing

A **statically-typed** language has what property?

1. [X] The data type of a variable type is set when it is declared
1. [ ] The data type of a variable depends on what it contains
1. [ ] The data type of a variable can always be determined
1. [ ] The data type of a variable cannot always be determined

# Dynamic Typing

A **dynamically-typed** language has what property?

1. [ ] The data type of a variable type is set when it is declared
1. [X] The data type of a variable depends on what it contains
1. [ ] The data type of a variable can always be determined
1. [ ] The data type of a variable cannot always be determined

# Strong Typing

A **strongly-typed** language has what property?

1. [ ] The data type of a variable type is set when it is declared
1. [ ] The data type of a variable depends on what it contains
1. [X] The data type of a variable can always be determined
1. [ ] The data type of a variable cannot always be determined

# Weak Typing

A **weakly-typed** language has what property?

1. [ ] The data type of a variable type is set when it is declared
1. [ ] The data type of a variable depends on what it contains
1. [ ] The data type of a variable can always be determined
1. [X] The data type of a variable cannot always be determined

# Type Annotations

**Type annotations** can be added to Python to convert it to what type of language?

1. [X] Statically typed
1. [ ] Dynamically typed
1. [ ] Strongly typed
1. [ ] Weakly typed

# Struct

A **struct** from C++ is best described as what?

1. [X] A compound data type
1. [ ] A binary value
1. [ ] An exception handler
1. [ ] A function

# Module

Parnas describes a **module** as containing what items (choose all that are correct):

- [X] Data structure
- [X] Accessing procedures
- [X] Modifying procedures
- [ ] Documentation

# State

The **state** of a program is best described by which statement?

1. [X] The data stored at any given moment
1. [ ] Whether the program is running or not
1. [ ] The system the program is executing on
1. [ ] The most recent output of the program

# Behavior

The **behavior** of a program is best described by which statement?

1. [X] The code that changes the program state
1. [ ] The graphical user interface of an app
1. [ ] The registry entries installed by a program
1. [ ] The memory layout of the data in a program

# Class

A **class** is best described by what analogy?

1. [X] The "blueprint" of an object
1. [ ] The "contents" of a variable
1. [ ] The "instance" of a package
1. [ ] The "behavior" of a library

# Object

An **object** in object-oriented programming refers to what concept?

1. [X] A discrete instance of a class
1. [ ] A compound data type
1. [ ] A memory location
1. [ ] A block of code

# Private

The `private` modifier in Java has what effect when applied to a variable? (The use of a double underscore `__` prefix in Python is meant to confer the same idea, but it is not enforced by the system.)

1. [X] Prevents access or modification outside the class
1. [ ] Encrypts the data stored in the variable
1. [ ] Protects the variable from invalid values
1. [ ] Sets a variable to `null` or `None` when created

# Constructor

The **constructor** is a special method in a class that performs what task?

1. [X] Creates a new instance of the class as an object
1. [ ] Defines a new method within the class
1. [ ] Deletes the memory used by an object
1. [ ] Launches a new thread for an object

# Access Modifier

Which of the following keywords are examples of **access modifiers** in Java? Choose all that are correct.

- [X] `private`
- [X] `public`
- [ ] `static`
- [ ] `void`

# Static

The `static` keyword has what effect when applied to a field or method in a class?

1. [X] Indicates that the item exists only in one memory location
1. [ ] Indicates that the value cannot be changed
1. [ ] Doubles the amount of memory allocated
1. [ ] Launches a new thread for an object

# Message Passing

Which of the following is the best example of **message passing** in object-oriented programming?

1. [X] Calling a method
1. [ ] Constructing an object
1. [ ] Deleting an object
1. [ ] Directly updating a variable

{{< /quizdown >}}