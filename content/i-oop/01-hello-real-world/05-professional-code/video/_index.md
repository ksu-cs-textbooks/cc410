---
title: "Writing Professional Code"
pre: "3. "
weight: 30
date: 2020-12-28T00:53:26-05:00
hidden: true
---

{{< youtube qIvM_uGgSoE >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

In this course, we're going to focus on learning to write professional code. To do that, we're going to introduce a lot of new topics, tools, and techniques to help improve our code. Of course, this can be very difficult, as satirized by this XKCD comic - we can focus on writing code quickly or writing it correctly, but in both cases we can run into issues. If we code quickly, our code quickly becomes unmanageable, but if we focus on doing everything perfectly it could take so long that the requirements have changed before we complete the code. So, we'll have to strike a balance between writing perfect code and writing code quickly. 

So, how do we write professional code? Here are several things that we'll focus on in this course.

First, as we saw earlier, we'll use the structured programming paradigm to build programs using simple and standard building blocks to make them easier to understand. This makes our code more readable and maintainable by other developers.

We'll also use the object-oriented programming paradigm to separate our program into a set of classes and objects that represent individual parts of the program. By leveraging things such as inheritance, we can build programs that are easy to diagram so we can understand how the large parts all interact with each other.

In addition, we'll learn how to develop and use unit tests to ensure that our code is working the way it should. This will also help us as we make changes to our code later on - if a unit test fails after an update, we'll know we introduced a bug that needs fixed.

Along with our unit tests, we can also make sure our tests are achieving a high level of code coverage. If we have written enough tests to check every possible line of code, we know that we're at least covering the basics. Of Course, that's just a first step, but it is a good baseline to start.

We'll focus on writing good comments and documentation into our code, allowing us to explain how our code functions to other developers and our future selves. This is really important if we have to come back to a project in the future and make changes, since it helps us quickly get back up to speed.

Finally, we'll use some static code analysis tools to help us determine if the code is correctly structured and following a proscribed coding style. Those tools will help us make sure our code doesn't contain type errors, and is easy to read for any other developer since it follows the same style.

To learn all of this, we're going to work on a project I'm calling "Hello Real World." The concept here is to rebuild the standard "Hello World" project that all programmers learn, but this time we'll focus on building it like a professional developer would. 

So, we'll make sure that our code uses the object-oriented paradigm and is fully type checked. For Java developers, this is already covered by the Java language standard and the Java compiler, but for Python developers we'll have to introduce a few new concepts and tools to cover these two requirements. 

Then, we'll make sure that our program includes a complete set of unit tests that achieve 100% code coverage. This will make sure that our "Hello World" program actually prints the correct message, allowing us to detect if we make an error or typo somewhere. 

Finally, we'll make sure that our program is fully commented using the proper documentation standard, and that the whole thing follows a proper coding style. This makes sure our code is easily understandable and readable for anyone who must look at it in the future. 

Once we've done that, then we can use a another tool to generate documentation based on those code comments. And, at long last, we'll save our code to a code repository, making it easy to keep track of all the changes we've made. 

In the next part of this module, you'll work through a guided example to build this new "Hello Real World" program and explore all of the tools and techniques that professional software developers use in their development process. After that, we'll spend the next few modules diving deeper into object-oriented programming while building the first few milestones of the restaurant project in this course. Good luck!




