---
title: "Data Types"
pre: "1. "
weight: 10
date: 2020-01-25T00:53:26-05:00
hidden: true
---

{{< youtube 6X3xXxPNguo >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

In this chapter, we're going to cover inheritance and polymorphism in object-oriented programming languages. This is a topic that comes up many times, and you may have already learned about it in the past. In this course, we're going to dive a bit deeper into how it works and some of the theory behind it. Before we can do that, we should spend a little time talking about data types and how that relates to inheritance. Recall that most programming languages store data using a few primitive data types. For example, both Java and Python have a type called `int` that is used to store integers. There are other primitive data types for storing floating-point numbers, boolean values, and text data. Here, we're referring to the Java `String` type as a primitive, even though it really is a class itself. But, in theory, we can treat it as a primitive for this use.

Data types are important because they help the computer determine how to handle different values. Consider this example, which I have written in both Java and Python. We have an integer, a floating point value, and a boolean value, as well as a string. Each one is stored using a different data type in both languages. Then, at the bottom, we are attempting to use the plus operator along with an integer and a string. So, what should happen?

Curiously, each programming language handles this situation a bit differently. In Java, the language will treat the plus operator as the concatenate operation when applied to a string and any other type. So, in Java, we will see the message "5Hello" printed.

What about Python? Python is a bit more strict in this particular instance, because it doesn't allow us to use the plus operator with an integer and a string. So, Python will instead raise a `TypeError` when we try to execute this code. 

So, as we can see, the data type is used to determine how variables are treated by the program. 

Likewise, different data types may support different operations, and it may vary between programming languages. As we saw, Java supports the plus operation between a string and an integer, but Python does not. If we apply the plus operator to other data types, we will get other results.

How does this relate to inheritance? Well, it is important for us to understand that we can create our own data types. One way to create a new data type is by creating an enumeration, or enum type. This was supported way back in the early days of the C programming language, and predates object-oriented programming. A enum is a type that simply creates a list of possible values. Those values are named, but behind the scenes they are usually stored as integer values. The Python example explicitly names those values, whereas Java does it automatically. So, in both of these examples, we are creating a new data type called `Grade` that can store 5 possible values: A, B, C, D, and F. 

So, once we've created our enum, it becomes a new data type and we can use it just like any other data type. We can create variables that store values of that data type, and we can use it within methods and anywhere else in our code.

When object-oriented programming was introduced, we could use our newly created classed to define other data types. Instead of being a list of possible values, a class can create a composite data type that contains many other attributes. Put another way, a class is simply a new data type that is composed of variables of many other data types. 

To use the terminology we've already learned in this class, the _state_ of an object built from this class is an instance of the new data type. So, we can store it in a variable with the data type of the class, and treat it just like any other data type. This is one of the powerful concepts of object-oriented programming - objects are first-class citizens in our language, and we can treat them just like any other variables.

Finally, let's just briefly review how both Java and Python handle types. As we saw earlier in this course, both Java and Python are strongly-typed languages, meaning that they always keep track of the data type stored in a particular variable. Java uses static typing, meaning that a variable can only store one type of data throughout its entire life in the program, while Python uses dynamic typing. In that way, the same variable may store multiple different data types while the program runs. 

However, we are using the Mypy type checking tool with Python, along with type annotations. So, even though Python itself is dynamically typed, we are treating it more like a statically typed language. We do this mainly to make it a bit easier to work with as our programs get larger, and also to give us a better grasp of how data types are handled in Python itself. So, with this background in mind, we can now dive deeper into inheritance!