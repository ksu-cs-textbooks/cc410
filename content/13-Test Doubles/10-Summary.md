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
