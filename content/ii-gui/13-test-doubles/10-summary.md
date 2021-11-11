---
title: "Summary"
weight: 50
pre: "10. "
---

In this chapter, we learned about **test doubles** and how they can use them in our unit tests to mimic functionality from other parts of our program. In short, there are three different common types of test doubles:

* stubs - methods that mimic actual methods
* fakes - objects that mimic actual objects
* mocks - objects that record operations performed on it

We also explored how we can use these in our code both Java and Python. Finally, we learned about **dependency injection** and how we can use that technique to place our test doubles directly in our classes. Now, we'll be able to update the unit tests in our ongoing project to help separate the classes being tested from other classes that it depends on.

{{< quizdown >}}

---
primaryColor: '#512888'
secondaryColor: '#cccccc'
textColor: black
shuffleQuestions: true
shuffleAnswers: true
locale: en
---

# Test Doubles

**Test doubles** are best described by which of the following statements?

1. [X] Temporary objects in unit tests to mimic functionality
1. [ ] Duplicate unit tests used to confirm results
1. [ ] Floating-point values used to test arithmetic methods
1. [ ] Abstract methods with no actual implementation

# Separation of Concerns

The design principle **separation of concerns** is best described by which statement?

1. [X] Breaking a larger system into distinct sections for a particular task
1. [ ] Preventing the user from editing system data in an application
1. [ ] Sandboxing user interface elements from the underlying program
1. [ ] Writing and debugging one part of a program at a time

# Reason for Test Doubles

Which of the following is a major reason to use test doubles in unit tests? 

1. [X] To replace other methods with versions that will always work 
1. [ ] To reduce the amount of code in our unit tests
1. [ ] To repeatedly test other parts of the application
1. [ ] To ensure a test never fails

# Uses of Test Doubles

Which of the following was **not** given as a possible use of test doubles?

1. [X] Measure how long an operation takes to perform
1. [ ] Verify a method is called from our code
1. [ ] Produce fake data that our code can operate on
1. [ ] Enure our code updates data in another module
1. [ ] Observe how many times our code builds a particular object

# Unit Test Pattern

Place the steps of the common unit test structure below in the correct order. (Click and drag to reorder elements)

1. Arrange
2. Act
3. Assert

# Behavior-Driven Development

Place the steps of the **behavior-driven development** structure below in the correct order. (Click and drag to reorder elements)

1. Given
2. When
3. Then

# Stub

According to the text, a **stub** is best described by which statement?

1. [X] An object that returns predefined data when its methods are called
1. [ ] An object that implements all public methods but may use shortcuts to produce results
1. [ ] An object used to listen for incoming method calls
1. [ ] An object that contains several abstract variables

# Fake

According to the text, a **fake** is best described by which statement?

1. [ ] An object that returns predefined data when its methods are called
1. [X] An object that implements all public methods but may use shortcuts to produce results
1. [ ] An object used to listen for incoming method calls
1. [ ] An object that contains several abstract variables

# Mock

According to the text, a **mock object** is best described by which statement?

1. [ ] An object that returns predefined data when its methods are called
1. [ ] An object that implements all public methods but may use shortcuts to produce results
1. [X] An object used to listen for incoming method calls
1. [ ] An object that contains several abstract variables

# Naming

True or false: the names **stub**, **mock** and **fake** are used consistently across languages and frameworks?

1. [ ] True
1. [X] False

# Dependency Injection

The concept of **dependency injection** is best described by which statement?

1. [X] Building a class so that external objects can be added from outside
1. [ ] Ensuring that all variables and methods are public
1. [ ] Designing a class to construct its own external objects as needed
1. [ ] Only using external libraries from reputable sources

{{< /quizdown >}}