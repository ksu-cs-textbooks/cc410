---
title: "Summary"
weight: 60
pre: "12. "
---
In this chapter we learned about testing, both manually using test plans and automatically using a testing framework. We saw how the cost of fixing errors rises exponentially with how long they go undiscovered. We discussed how writing automated tests during the programming phase can help uncover these errors earlier, and how regression testing can help us find new errors introduced while adding to our programs.

We learned a bit more about the testing frameworks we have available to us in our chosen programming language and how to use them. And finally, we discussed some more advanced topics related to software testing. 

{{< quizdown >}}

---
primaryColor: '#512888'
secondaryColor: '#cccccc'
textColor: black
shuffleQuestions: true
shuffleAnswers: true
locale: en
---

# Informal Testing

**Informal testing** is best described as what process?

1. [X] Manually running programs with various input and seeing what happens
1. [ ] Structured testing following a written procedure
1. [ ] Testing small parts of a program individually
1. [ ] Testing an entire program all at once

# Formal Testing

**Formal testing** is best described as what process?

1. [ ] Manually running programs with various input and seeing what happens
1. [X] Structured testing following a written procedure
1. [ ] Testing small parts of a program individually
1. [ ] Testing an entire program all at once

# Test Plan

A **test plan** includes which of the following? **Choose all that are correct.**

- [X] What inputs to supply
- [X] What results to expect for each input
- [ ] The structure of the software to be tested
- [ ] The edit history of the program

# Waterfall Model

The **waterfall model** of software development is best described by what statement?

1. [X] Each task depends on the one before it
1. [ ] Start with a small prototype and expand from there
1. [ ] Develop features in short sprints of work
1. [ ] Just write code and fix it later

# Unit Test

A **unit test** is best described by which statement?

1. [X] A test on a single piece of code in isolation
1. [ ] A test of interactions between various parts of a program
1. [ ] A test of an entire program's behavior
1. [ ] A test that is expected to fail

# Integration Test

An **integration test** is best described by which statement?

1. [ ] A test on a single piece of code in isolation
1. [X] A test of interactions between various parts of a program
1. [ ] A test of an entire program's behavior
1. [ ] A test that is expected to fail

# System Test

A **system test** is best described by which statement?

1. [ ] A test on a single piece of code in isolation
1. [ ] A test of interactions between various parts of a program
1. [X] A test of an entire program's behavior
1. [ ] A test that is expected to fail

# Code Coverage

The **code coverage** of a set of unit tests is best described as a measure of what value?

1. [X] The amount of code in a program executed by those tests
1. [ ] The range of values provided as inputs in those tests
1. [ ] The likelihood of an error being discovered by those tests
1. [ ] The number of tests that are expected to fail

# Parameterized Test

A **parameterized test** is a special type of unit test that is best described by which statement?

1. [X] A test that is executed multiple times with different input values
1. [ ] A test that checks only edge cases
1. [ ] A test that calls the same method multiple times in rapid succession
1. [ ] A test that purposefully breaks a system to see how it fails

# Edge Case

An **edge case** is best described by which statement?

1. [X] An input value near a boundary between two possible ways the function could execute
1. [ ] An input value that cannot be provided by the user
1. [ ] An input value that causes the function to perform differently each time
1. [ ] An input value that is safe for the function to process

# Assertion

In a unit test, an **assertion** is used for what purpose?

1. [X] To determine if the actual results match the expected results
1. [ ] To prevent another part of the program from executing
1. [ ] To provide various input values to the function being tested
1. [ ] To execute multiple tests at the same time

# Hamcrest

**Hamcrest** is a cross-platform library that includes additional versions of what type of statement used in unit tests?

1. [X] Assertions
1. [ ] Conditionals
1. [ ] Exceptions
1. [ ] Lambdas

# Syntactic Sugar

**Syntactic sugar** is best described by which statement?

1. [X] A language feature that doesn't add any new functionality but makes code more easily readable
1. [ ] A process for reducing the number of function calls in a method
1. [ ] A shortened form of a longer method name
1. [ ] A kinder way to state an exception

# Test Runner

A **test runner** is used to perform what task?

1. [X] Discover and execute unit tests in a project
1. [ ] Examine the running time of a function
1. [ ] Determine the number of times a function is called
1. [ ] Automatically create unit test for a project

# Regression Testing

**Regression testing** is best described by which statement?

1. [X] Running all previously passed tests anytime a change is made
1. [ ] Testing older versions of a program with new tests
1. [ ] Executing tests on older hardware
1. [ ] Running tests on purposely broken versions of the software

# White Box Testing

**White box testing** is a testing approach that is best described by which statement?

1. [X] The test developer has full access to the source code
1. [ ] The test developer does not have access to the source code
1. [ ] The tests are determined by the eventual end user of the program
1. [ ] The tests are written before the code being tested is written

# Black Box Testing

**Black box testing** is a testing approach that is best described by which statement?

1. [ ] The test developer has full access to the source code
1. [X] The test developer does not have access to the source code
1. [ ] The tests are determined by the eventual end user of the program
1. [ ] The tests are written before the code being tested is written

# Acceptance Testing

**Acceptance testing** is a testing approach that is best described by which statement?

1. [ ] The test developer has full access to the source code
1. [ ] The test developer does not have access to the source code
1. [X] The tests are determined by the eventual end user of the program
1. [ ] The tests are written before the code being tested is written

# Test-Driven Development

**Test-driven development** is a testing approach that is best described by which statement?

1. [ ] The test developer has full access to the source code
1. [ ] The test developer does not have access to the source code
1. [ ] The tests are determined by the eventual end user of the program
1. [X] The tests are written before the code being tested is written

{{< /quizdown >}}