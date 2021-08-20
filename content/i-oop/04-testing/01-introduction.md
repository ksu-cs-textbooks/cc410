---
title: "Introduction"
weight: 5
pre: "1. "
---

{{% notice info info-1 "content note" %}}

Much of the content in this chapter was adapted from Nathan Bean's [CIS 400](https://textbooks.cs.ksu.edu/cis400/1-object-orientation/04-testing/) course at K-State, with the author's permission. That content is licensed under a [Creative Commons BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.

{{% / notice %}}

A critical part of the software development process is _ensuring the software works!_  We mentioned earlier that it is possible to logically prove that software works by constructing a state transition table for the program, but once a program reaches a certain size, this strategy becomes less feasible.  Similarly, it is possible to model a program mathematically and construct a theorem that _proves_ it will perform as intended.  But in practice, most software is validated through some form of _testing_.  This chapter will discuss the process of testing object-oriented systems.

## Key Terms

Some key terms to learn in this chapter are:

* Informal Testing
* Formal Testing
* Test Plan
* Test Framework
* Automated Testing
* Assertions
* Unit Tests
* Testing Code Coverage
* Regression Testing

## Key Skills

The key skill to learn in this chapter is how to write unit tests in our chosen language. For Java, we'll be using [JUnit 5](https://junit.org/junit5/docs/current/user-guide/) to write our tests, and in Python we'll use [pytest](https://docs.pytest.org/en/stable/) as our test framework. We will also explore using the [Hamcrest](http://hamcrest.org/) assertion library for both [Java](https://github.com/hamcrest/JavaHamcrest) and [Python](https://github.com/hamcrest/PyHamcrest). 
