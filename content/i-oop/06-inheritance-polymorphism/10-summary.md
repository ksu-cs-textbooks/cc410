---
title: "Summary"
weight: 50
pre: "10. "
---
In this chapter, we explored the concept of types and discussed how variables are specific types that can be explicitly or implicitly declared.  We saw how in a statically-typed language (like Java), variables are not allowed to change types, though they can do so in a dynamically-typed language like Python.  We also discussed how casting can convert a value stored in a variable into a different type.  Implicit casts can happen automatically, but explicit casts must be indicated by the programmer using a cast operator, as the cast could result in loss of precision or the throwing of an exception.

We explored how class declarations and interface declarations create new types.  We saw how polymorphic mechanisms like interface implementation and inheritance allow object to be treated as (and cast to) different types.  We also introduced a few casting operators, which can be used to cast or test the ability to cast.  

Finally, we explored how messages are dispatched when polymorphism is involved. We saw that the method invoked depends on what type the object was created as, not the type it is currently stored within.

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

# Polymorphism

**Polymorphism** is best described by what literal meaning?

1. [X] Many forms
1. [ ] Type shift
1. [ ] From many, one
1. [ ] Change into

# Type

A **type** is described in this chapter as giving what information about a variable?

1. [X] How it is represented and what operations can be performed on it
1. [ ] Whether it can be accessed by other objects
1. [ ] The location in the code where it is first created
1. [ ] Whether it is abstract or inheritable

# User-Defined Types

Which construct from object-oriented programming best represents a **user-defined type**?

1. [X] Class
1. [ ] Attribute
1. [ ] Method
1. [ ] Exception

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

# Message Passing

In object-oriented programming, we can think of **message passing** as another way to represent what action?

1. [X] A method call
1. [ ] Instantiation of an object
1. [ ] Storing a value in a variable
1. [ ] Clearing unused memory

# Interface

An **interface** for a class, such as an API described in that class's documentation, is essentially a list of what?

1. [X] Public methods
1. [ ] Private methods
1. [ ] Public attributes
1. [ ] Private attributes

# OOP Interface

In object-oriented programming, an **interface** is a special type of class that performs what function?

1. [X] Defines the methods required in subclasses of the interface
1. [ ] Combines two classes into a single object
1. [ ] Converts private attributes to public accessor methods
1. [ ] Protects data in a superclass

# Interface Association

When a class implements an interface, we would describe that as what type of association in UML?

1. [X] Weak is-a
1. [ ] Strong is-a
1. [ ] Weak has-a
1. [ ] Strong has-a

# Multiple Inheritance

True or false: in most object-oriented programming languages, a class may implement, or inherit from, multiple interfaces?

1. [X] True
1. [ ] False

# Shared Types

True or false: in object-oriented programming, two objects created from classes that implement the same interface can be treated as having the same type?

1. [X] True
1. [ ] False

# Inheritance

In object-oriented programming, **inheritance** is best described by what statement?

1. [X] Driving part of a class definition from an existing class
1. [ ] Storing a value in multiple variables
1. [ ] Creating an interface for each method
1. [ ] Separating state and behavior in a class

# Interface Association

When a class inherits from another class, we would describe that as what type of association in UML?

1. [ ] Weak is-a
1. [X] Strong is-a
1. [ ] Weak has-a
1. [ ] Strong has-a

# Protected

In object-oriented programming, a **protected** attribute is best described by what statement?

1. [X] Only accessible to the declaring class and derived classes
1. [ ] Read-only outside the declaring class
1. [ ] Not shown in UML diagrams
1. [ ] Cannot be inherited by derived classes

# Abstract

In object-oriented programming, an **abstract class** is best described by which statement?

1. [X] A class that exists only to be derived from, not instantiated
1. [ ] A class containing only attributes, but no methods
1. [ ] A class containing only methods, but no attributes
1. [ ] A class that does not implement any interfaces

# Casting

**Casting** in object-oriented programming is best described by which statement?

1. [X] Transforming a value from one data type to another
1. [ ] Storing an element in a list of similar elements
1. [ ] Expanding a variable's value into an attribute
1. [ ] Inheriting a single method from an interface

# Duck Typing

In Python, the term **duck typing** is used to describe what aspect of the language?

1. [X] Python allows developers to treat objects as any compatible type without casting
1. [ ] Python does not know what type is stored in a variable at any given time
1. [ ] Python only allows single inheritance
1. [ ] Python classes must include an explicit "duck type" for inheritance purposes

# Checking Types

True or false: both Java and Python include a special method for determining if a particular object is compatible with a given type?

1. [X] True
1. [ ] False

# Message Dispatching

In object-oriented programming, **message dispatching** is best described by what statement?

1. [X] How a language decides which implementation of an inherited method to invoke at runtime
1. [ ] How a derived class updates an attribute in the base class
1. [ ] How to determine the type of an object after instantiation
1. [ ] How a base class can update attributes in all derived classes

# Method Overriding

Which of the following is an example of **method overriding** in object-oriented programming?

1. [X] A method in a derived class that replaces a method of the same name in the base class
1. [ ] Two methods in the same class with the same name that accept different parameters
1. [ ] Replacing a static method with a non-static method of the same name
1. [ ] Converting a method that doesn't return a value into a method that does return a value

# Method Overloading

Which of the following is an example of **method overloading** in object-oriented programming?

1. [ ] A method in a derived class that replaces a method of the same name in the base class
1. [X] Two methods in the same class with the same name that accept different parameters
1. [ ] Replacing a static method with a non-static method of the same name
1. [ ] Converting a method that doesn't return a value into a method that does return a value

{{< /quizdown >}}