---
title: "Language Evolution"
pre: "2. "
weight: 20
date: 2020-12-28T00:53:26-05:00
hidden: true
---

{{< youtube O8rBA0ccGj8 >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

To understand how programming languages have evolved over the years, let's look at a few examples. On this slide is a small snippet of Fortran code from the EPIC model that is linked in the textbook. Take a minute to look through the code and see if you can determine what it does.

It's really difficult code to read, isn't it? We might recognize a few of the keywords like "do" and "if" but for the most part the variables don't mean anything at all. In addition, there are no spaces in much of the code, so it can be very hard to follow. Of course, there are some reasons for this - short variable names were easy to store in memory on older computers, and there may not have been coding style standards that focused on making readable code. So, while this program is very efficient, and is still used to this day, the code itself could make it very difficult to maintain or improve. 

In fact, a lot of early computing code looked something like this example from the BASIC language. Can you read it and figure out what it does? Effectively, this program will print the square of all numbers from 1 to 100. However, instead of using a loop or if statements, it uses the `GOTO` statement. The `GOTO` statement allows a program to jump from one part of the code to any other part of the code quickly and easily. On the surface, that makes sense, right? Even today, the assembly code that computers actually execute is fully of "jump" instructions just like this. So, why don't we use it more often in our code? Basically, overuse of the `GOTO` statement leads to a problem called "spaghetti code." Spaghetti code lacks any internal structure, making it very hard to trace and determine what is happening. We could try to build a flowchart based on that code, but even that could get complicated very quickly. 

So, in 1968, Edsger Dijkstra published a paper titled "Go To Statement Considered Harmful" where he basically argued that the use of the `GOTO` statement should be avoided at all costs. Instead, programmers should strive to restructure their programs in a logical way, making it easier to follow the program's flow and quickly understand what it actually does. So, while using a `GOTO` statement in your code may not summon velociraptors, as it does in this XKCD comic, it should still be avoided. In fact, many modern languages don't include the `GOTO` statement at all for that very reason. 

Instead, most modern programming languages follow the Structured Programming Paradigm. In that paradigm, any program consists of combinations of just three structures - sequences,selection, and iteration. I also like to add a fourth to this list - subroutines. Let's take a look at each of them.

First, we have linear sequences of code, sometimes referred to as blocks of statements. This is the simplest form of code, without any branching paths or loops. These sequences could be the only code within a function, or they could be the code that exists within another structure. 

Then, we have selection statements, also known as conditionals or "if" statements. This structure allows us to branch the program flow and select between two different sequences or blocks. Here, each sequence just consists of a single statement, outputting either "even" or "odd", but we can easily add additional statements to either sequence to make it more complex.

We can also have iteration statements, also known as loops. In a simple iteration structure, we can repeat a sequence of statements while a particular boolean value is true, or in more advanced structures we would repeat a certain number of times or across a list of values. If our language supports subroutines, as most languages do, then the iteration structure also encompasses the concept of recursion, where we call a subroutine from within itself. 

Finally, we have the subroutine structure. While this isn't one of the "big three" of structured programming, I think it is important to include it here since most languages support it. In effect, a subroutine allows us to take a "chunk" of code, give it a name, and then execute that chunk multiple times and from multiple places. It isn't required for structured programming, but it helps simplify our code by reducing the amount of repeated code. 

So, let's go back and look at that program in BASIC, rewritten to use structured code. As we can see, this program now clearly uses an iteration structure to iterate from 1 to 100, so it is much easier for us to understand how it works. This is the power that the structured programming paradigm brings to our programs - by using a small, standardized set of structures to build our programs, they are easier for other programmers to follow and digest quickly.

Another major change in programming languages was the introduction of the object-oriented programming paradigm. Early programs were organized in a very ad-hoc way, without much structure or reason behind how the different parts of the program were represented in code. In the object-oriented paradigm, programs are organized into "objects" or "classes" which typically represent real world or theoretical items that serve a particular purpose. The code within that object is then used to represent everything that object stores and all the actions it can perform. All core object-oriented languages include three properties - encapsulation, which allows attributes to be stored as data within objects; message passing, which allows external code to call methods that are stored within the object, and the use of dynamic dispatch, which allows the object to choose what code to execute when it receives a given message or method call. We'll dig deeper into these three properties later in this course as we work on our projects. 

So, here is an example of some object-oriented code written in Java to perform the same task as the BASIC program we saw earlier. As we can see here, the code is now contained within a class and a method, and the method accepts a parameter that gives the limit of the computation. So, when we want to execute this code, we would _instantiate_ an instance of the object, then call the `printSquares` method, effectively passing a message to the object that asks it to perform a task. The object then uses dynamic dispatch to look up the implementation of the method in its code and executes it, returning the result. It's a very effective way to structure large, complex programs like the ones we'll be building in this course.

So, we will only use object-oriented and structured code in this course. For Java developers, this isn't really a change. However, for Python, this enforces a few limitations that aren't necessarily required in the Python language. However, by writing exclusively object-oriented code, we'll see that it is very easy to structure and maintain our programs as they slowly get larger and more complex. 