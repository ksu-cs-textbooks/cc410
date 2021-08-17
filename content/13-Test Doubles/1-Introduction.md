---
title: "Introduction"
weight: 5
pre: "1. "
---
Earlier in this course, we learned about unit testing and how we can write code to help us verify that parts of our program are performing as intended. However, what if the portion of our program we'd like to test depends on other parts working correctly? In that case, any errors in our tests might be due to our code having a bug, but it could also be due to a bug in another part of the program that our code depends on.

So, we need some way to test parts of our code _in isolation_ from the rest of the program. In that way, we can make sure our code is working as intended, even if the parts it depends on to function aren't working.

Enter **test doubles** - items such as **stubs**, **fakes** and **mocks** - which are temporary objects we can include in our unit tests to mimic, or "double," the functionality of another part in our program. In that way, we can write our test as if the other portion is working, regardless of whether it is or not. 

In this chapter, we'll learn about the following key terms and ideas:

* Test Doubles
* Stub Methods, or Stubs
* Fake Objects, or Fakes
* Mock Objects, or Mocks
* Arrange, Act, Assert

We'll also see a brief example for how to create and use some of these items in our chosen programming language. After reviewing this content, we should be able to use some test doubles in our own unit test code.
