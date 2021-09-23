---
title: "Summary"
weight: 35
pre: "7. "
---
{{% notice info info-1 "Content Note" %}}

Portions of the content on this page were adapted from Nathan Bean's [CIS 400](https://textbooks.cs.ksu.edu/cis400/1-object-orientation/00-introduction/02-the-growth-of-computing/) course at K-State, with the author's permission. That content is licensed under a [Creative Commons BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.

{{% / notice %}}

In this chapter, we've discussed the environment in which object-orientation emerged.  Early computers were limited in their computational power, and languages and programming techniques had to work around these limitations. Similarly, these computers were very expensive, so their purchasers were very concerned about getting the largest possible return on their investment.  In the words of Niklaus Wirth:

<blockquote>
Tricks were necessary at this time, simply because machines were built with limitations imposed by a technology in its early development stage, and because even problems that would be termed "simple" nowadays could not be handled in a straightforward way.  It was the programmers' very task to push computers to their limits by whatever means available.
</blockquote>

As computers became more powerful and less expensive, the demand for programs (and therefore programmers) grew faster than universities could train new programmers.  Unskilled programmers, unwieldy programming languages, and programming approaches developed to address the problems of older technology led to what became known as the "software crisis" where many projects failed or floundered.

This led to the development of new programming techniques, languages, and paradigms to make the process of programming easier and less error-prone. Among the many new programming paradigms was structured programming paradigm, which introduced control-flow structures into programming languages to help programmers reason about the order of program execution in a clear and consistent manner.  Also developed during this time was the object-oriented paradigm, which we will be studying in this course.

## Programming Today

Today, many software developers have adopted techniques designed to produce high quality code. These include the use of automated unit testing and test-driven development, as well as standardized use of code comments and linters to maintain good coding style and ample documentation for future developers. In the project for this module, we'll explore what this looks like by building a simple "Hello World" program that uses all of these techniques. 

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

# Software Crisis

What was the primary cause of the **software crisis**?

1. [X] Machines becoming more powerful, requiring more software
1. [ ] Software becoming too expensive for anyone to afford
1. [ ] The unavailability of software for a particular task
1. [ ] All common software was compromised and hacked

# Structured Programming

What is the major feature of the **structured programming** paradigm?

1. [X] Control-flow structures like conditionals, loops, and switch statements
1. [ ] Structures to represent real-world objects
1. [ ] Functions as first-class citizens in the code
1. [ ] Statements only executed in the order listed in the code

# 3 Key Properties

**Encapsulation**, **message passing**, and **dynamic binding** are three key properties of a programming language that follows what paradigm?

1. [X] Object-oriented programming
1. [ ] Structured programming
1. [ ] Functional programming
1. [ ] Imperative programming

# Unit Testing

**Unit testing** is best described by what statement?

1. [X] Detailed tests for small parts of a program, usually individual functions
1. [ ] Verifying the result of a mathematical computation has the correct unit
1. [ ] Recruiting users to test a new piece of software under observation
1. [ ] Automatically testing the whole program together at once

# Test-Driven Development

**Test-driven development** is a process for software development that creates the items below in what order? (Click and drag to reorder elements)

1. Software specification
2. Unit tests
3. Source code

# Regression Testing

**Regression testing** is best described by what statement?

1. [X] Re-running previously passed unit tests after an update to catch new bugs
1. [ ] Testing older versions of software for new bugs
1. [ ] Providing invalid data to a program to make sure it doesn't crash
1. [ ] Running new software on old hardware

# Code Coverage

The **code coverage** of a set of unit tests is a measure of what?

1. [X] The percentage of source code that is executed during testing
1. [ ] How many possible inputs are handled properly by a function
1. [ ] How many different keywords are used in a program's code
1. [ ] The number of different developers who have reviewed the code

# Documentation

**Documentation** in programming typically refers to what?

1. [X] Including code comments that describe how a program works
1. [ ] Keeping track of the number of hours required to develop a program
1. [ ] Instructions for ways to compromise the system once it is deployed
1. [ ] A list of all developers of a piece of software

# Messy Code

Tools that help clean up messy code by making sure it follows good style are examples of what type of tool?

1. [X] Static code analysis
1. [ ] Automated testers
1. [ ] Code mutators
1. [ ] Source control

# First Program

What is the common name for the simple program that most programmers learn first when learning a new language? 

1. [X] Hello World
1. [ ] Count to Three
1. [ ] EPIC
1. [ ] Tic-Tac-Toe

{{< /quizdown >}}