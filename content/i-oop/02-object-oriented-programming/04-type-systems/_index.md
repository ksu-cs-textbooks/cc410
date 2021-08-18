---
title: "Type Systems"
weight: 20
pre: "4. "
---

{{% youtube wHvgrz1Nts0 %}}

[Video Materials](video)

Before we go further into some object-oriented concepts, let's briefly review one important concept in programming - data types and type systems.

## Primitive Data Types

Most programming languages include several **primitive data types**, which are the fundamental units of data that can be stored and represented by that programming language. Here's a short list of those primitive data types for each language:

| Data | Java | Python | 
|:----:|:----:|:------:|
| Whole Numbers | `int` (`byte`, `short`, `long`) | `int` |
| Floating-point Numbers | `double` (`float`) | `float` | 
| Boolean Values | `boolean` | `bool` |
| Single Character | `char` | `str`^[A string of length 1] |
| String of Characters | `String`^[This is not a primitive, but the [String](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html) class. However, it is so ubiquitous that we'll include it here.] | `str`|

Any data that is stored by our program must fit into one of these data types. That is an important fundamental rule to remember - no matter how complex our code gets, **everything** is stored in primitive data types. That's simply all there is.

## Complex Data

What if we want to store more complex data, such as information about a person? Well, we could easily create an integer that stores the person's age, and perhaps a string for the person's name. Those are still just primitive data types, so we're good there. 

However, as you probably already know, we can group those items together into **classes**. However, before we can really understand classes and how they relate to encapsulation, we must look at a precursor to classes first. We'll cover that later in this module.

## Type Systems

The way that programming languages handle these data types is known as the **type system** of the language. Let's look at two different ways to categorize type systems to see how they differ.

### Static Typing vs. Dynamic Typing

In programming, there are two common ways that programming languages deal with data types. The first is called **static typing**, where each variable has a particular data type associated with it as soon as it is declared, and that variable can _only_ store items of that data type. Because of this, we can use tools like the Java compiler to analyze our code before we ever execute it, making sure that we always are storing the correct type of data in each variable.

Java is a **statically typed** language. When we create variables in Java, we must assign data types to them, as in this example:

###### Java 

```java
int x = 5;
double y = 5.5;
String name = "CC 410";
```

Similarly, when we create methods in Java, we must declare the types of all parameters, as well as the return type of the method.

Python, on the other hand, is a **dynamically typed** language. That means that variables in Python do not have a particular data type assigned to them, and they can store multiple different types of data throughout the course of the program. Here's an example:

###### Python

```python
x = 5
x = 5.5
x = "CC 410"
```

This is a perfectly valid program in Python, and will execute just fine. However, as we'll soon learn, this could lead to some preventable errors, and we'll see how to resolve them.

### Strong Typing vs. Weak Typing

Programming languages can also be classified based on their use of type systems in one other way. A **strongly typed** language always knows what data type is stored in a variable at any given time during the program's execution. In statically typed languages such as Java, this is trivial - if the program compiles, then we know that the _only_ possible data type that could be stored in a variable is the type listed in that variable's declaration. It's pretty straightforward.

However, what about Python? Python is dynamically typed, which means that each variable could store multiple different data types during a single program's execution, and each time the program executes it could be different. However, at any given instant during the execution of the program, the Python interpreter knows exactly what type of data is being stored in each of the variables in the program. We can use methods such as `isinstance()` to confirm this. So, Python is also a **strongly typed** language. 

So, what is a **weakly typed** language? A great example is code written in an assembly language. The computer will simply execute whatever is written, and has no way of keeping track of the types of data stored in each variable. Instead, it depends on the compiler or developer to make sure there are no type errors in the assembly code. 

### Making Python Statically Typed

As we learned in the "Hello Real World" project, we can add **type annotations** to Python code to convert Python into a statically typed language. Then, we can use tools such as Mypy to make sure there are no type errors in our code, much like the Java compiler does for Java code. So, here's a rewritten example of Python code that is statically typed:

###### Python

```python
x: int = 5
y: float = 5.5
name: str = "CC 410"
```

By adding these type annotations, we can tell Mypy what type of data we expect to be stored in each of these variables, and it can perform the same type checking process that the Java compiler uses. In this class, we're going to focus on using statically typed Python code as much as we can. 

## Why This Matters

We're spending a little time reviewing types and type systems now because it will help us understand the new concepts being introduced in the next few pages. Before the introduction of object-oriented programming, programmers had to use other tools to build more complex data types than the primitives we've discussed here. 
