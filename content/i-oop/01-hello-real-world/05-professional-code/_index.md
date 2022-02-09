---
title: "Writing Professional Code"
weight: 25
pre: "5. "
---
{{% youtube qIvM_uGgSoE %}}

[Video Materials]({{<relref "./video">}})

As we saw earlier in this module, the software development industry adopted many new processes and ideas to help combat the issues that arose during the software crisis. One of the major things they focused on was how to write code that is easy to understand, easy to maintain, and works as intended with a minimal amount of bugs. Let's review a few of the concepts that came from those efforts, which we'll learn more about throughout this semester.

### Object-Oriented Programming

The use of object-oriented programming languages was one major outcome of the software crisis. An object-oriented language allows developers to build code that represents real-world concepts and ideas, making it easier to reason about large software programs. In addition, the concept of encapsulation helped ensure data stored and manipulated by one part of the program wasn't inadvertently changed by a bug in another part. Finally, through message passing and dynamic binding, we could write more advanced functions that allowed our code to be very modularized, flexible, and highly reusable. We'll spend the next several modules in this course covering object-oriented programming in much greater detail.

### Unit Testing

Another major movement in the software industry was toward the use of automated testing frameworks and the use of **unit testing**. [Unit testing](https://en.wikipedia.org/wiki/Unit_testing) involves writing detailed tests for small units of a program's source code, often individual functions, that exercise the expected functionality of the code as well as checking for any edge cases or expected errors. 

In theory, if the unit tests are properly written and perform all possible operations that the code should perform, than any code passing the tests should be considered complete and ready for use. Of course, coming up with a set of unit tests that can account for all possible scenarios is just as impossible as writing software that doesn't contain any bugs, but it can be a great step toward writing better software.

A common software development methodology today is **test-driven development** or *TDD*. In [test-driven development](https://en.wikipedia.org/wiki/Test-driven_development), the unit tests are developed first, based on the software specification, before the source code is ever written. In that way, it is easy to know if the software actually does what the requirements says it should, instead of the test simply being written to match the code that exists. (It is shockingly common for unit tests to be written based on the code it should test, which is equivalent of looking at the answers when doing a word scramble - you'll find what you expect to find, but won't actually learn anything useful from it.)

Another useful feature of unit tests is the ability to re-run tests on the program after an update has been developed, which is known as **regression testing**. If the program previously passed all available unit tests, then failed some of those tests after an update, we know that we introduced some unintended bugs in the code that can be repaired before publishing an update. In that way, we can avoid sending out an update that ends up making things even worse. 

### Code Coverage

Along with unit testing, another useful technique is calculating the **code coverage** of a set of tests. Ideally, you'd like to make sure that each and every line of code in the program is executed by at least one test - otherwise, how can you really say that that line does what it should? This is especially difficult in programs that contain multiple conditional statements and loops, or any code that checks for and handles exceptions. 

There are various ways to measure [code coverage](https://en.wikipedia.org/wiki/Code_coverage), including this list from Wikipedia:

* Function coverage - has every function been called?
* Statement coverage - has every statement been executed?
* Edge coverage - has every edge in the control flow graph been executed?
* Branch coverage - has every branch in each control structure been executed?
* Condition coverage - has every boolean expression been evaluated to both `true` and `false`?

There are various different ways to measure code coverage that we'll discuss later in this course, but for now we'll just look at statement coverage. Thankfully, there are some great tools for computing the code coverage of a set of unit tests. Our goal is always to get as close to 100% coverage as possible. 

### Documentation

Another major focus among professional coders is the inclusion of **documentation** directly in the source code itself. Many languages, such as Java, Python, and C#, include standards for documenting what various pieces of the code are for. This includes each individual source code file, classes, functions, attributes, and more. In many cases, this is done by including specially structured [code comments](https://en.wikipedia.org/wiki/Comment_(computer_programming)) in various places throughout the source code. 

To make those comments easier to read and understand, many languages also include tools to automatically create developer documents based on those comments. A prime example of this is the [Java API Documentation](https://docs.oracle.com/javase/8/docs/api/), which is nearly entirely generated directly from comments in the Java source code. In fact, you can compare the source code for the [ArrayList](http://hg.openjdk.java.net/jdk8/jdk8/jdk/file/tip/src/share/classes/java/util/ArrayList.java) class and the [ArrayList Documentation](https://docs.oracle.com/javase/8/docs/api/) in the Java API to get an idea of how this works.

### Static Code Analysis

Finally, there are many tools available today that can perform **static code analysis** of source code, helping developers find and fix errors without ever even compiling and running the code. Some [static code analysis](https://en.wikipedia.org/wiki/Static_program_analysis) tools are quite powerful, able to find logic errors or completely validate that the software meets a specification. These tools are commonly used in the development of critical software components, such as medical devices and avionics for aircraft, but they are also quite difficult to use. 

In this course, we're going to focus on a simpler form of static code analysis that will help us maintain good coding style. These tools are sometimes commonly referred to as "linters," named for the old Unix 'lint' tool that performed this task for code written in the C programming language. Of course, the use of the term "lint" is a reference to the tiny bits of fiber and fuzz that are shed by clothing, with the idea that by removing the "lint" that makes our code messy, we can have code that is cleaner and easier to read and maintain.

In fact, you may have already encountered these tools in your programming experience. Development environments such as the one used by Codio, as well as other integrated development environments (IDEs) such as Visual Studio Code, PyCharm, IntelliJ, and others all include support for static code analysis. Usually it takes the form of helpful error messages that show simple syntax and usage errors.

In this course, we'll learn how to use some more powerful static code analysis tools to enforce a standard coding style across all of our source code. A [coding style] can be thought of as roughly equivalent to a dialect of a spoken or written language - it deals with common conventions and usage, beyond just the simple definitions and syntax rules of the language itself. By following a standardized style, our code will be easier to read and maintain for any developer who is familiar with that style. 
