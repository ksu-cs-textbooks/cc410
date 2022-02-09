---
title: "Inspecting State"
weight: 15
pre: "3. "
---

{{% youtube ooxRxPAodRw %}}

[Video Materials}({{<relref "./video">}})

Object in our object-oriented programs can really be thought of as two different parts - the **state** and **behavior** of the object. When debugging, we may need to consider both parts of the object to determine what is really going on behind the scenes. So, let's look at some ways we can explore the state of our program.

## Print Statement Debugging

The quickest and easiest way to explore the state of our program at any particular point during its execution is to simply add a print statement that prints the value of any variables we are interested in. 

Many times we are dealing with objects that we've created, and printing them directly may not be very useful. So, it is very important for us to develop useful string representations of our objects that we can use when debugging. In Java, we can override the default `toString()` method for this. In Python, we have both the `__str__()` method that is used when printing, as well as the more complex `__repr__()` method that typically gives more information. 

When printing this information, it is helpful to include additional information along with the value of the variable, such as the function and even the line of code where the statement is located:

```
TestCode:5 - a=5 b=6 c=7
```

As we'll see later in this chapter, we can also do this automatically when we use a **logger** along with our program.

## Triggering A Print Statement

Sometimes, we may only want to print our program's state when a particular situation occurs. In that case, we can simply wrap our print statements in a conditional statement, or if statement, that checks for the desired condition. This helps minimize the amount of data we have to sort through to pinpoint our error.

While this may seem pretty obvious, its important to remember that we can use the same simple tools we use when building a program to debug that program as well. 

## Forcing State

As a last resort, we may wish to force our program to have a particular state to help us isolate a bug. This is best accomplished through a unit test, since we can call individual functions with the exact values we need.

Later in this chapter, we'll learn about one more tool we can use to inspect state - a **debugger**!
