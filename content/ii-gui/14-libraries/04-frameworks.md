---
title: "Frameworks"
weight: 20
pre: "4. "
---
One question that comes up frequently when discussing software libraries is the difference between a library and a **framework**, as many times the terms are used interchangeably. So, let's briefly explore the difference between the two and how they interact with each other.

![Framework vs. Library](/cc410/images/14/framework-vs-library.png)[^1]

[^1]: https://www.geeksforgeeks.org/software-framework-vs-library/

## Software Library

As discussed on the previous page, a **library** is a reusable software component that has an API that we can make use of in our code. So, our code will call methods in the API to perform the desired actions, and we'll typically import the library's code into our own code files.

Structurally, we can think of our code as a _wrapper_ around the library. We're using the library in our application, so we are _in control_ of what it does.

## Software Framework

On the other hand, a framework is a piece of software written to perform a specific task or be used in a specific way. However, the framework includes places where a developer can customize the code to change the actions performed by the framework. Many frameworks can be used without any customization at all, but in most cases the framework will not do anything useful without additional code added by a developer.

Some great examples of a framework are the Python [Flask](https://flask.palletsprojects.com/en/1.1.x/) and Java [Spring](https://spring.io/) frameworks, which are both designed to create web applications. They provide the overall structure for a web application, including the routing, page templates, receiving requests from a browser and creating a response, and more. Then, the developer can customize the web application by providing code to add individual web pages, API endpoints, and databases to store data. All of the customization to make the application meet the needs of the user is handled by the developer, but the framework itself is responsible for the overall structure and operation of the application.

Put another way, a framework is a _wrapper_ around our code. The framework is _in control_ of what the application does, and it calls our code as needed to create the desired pages and send the correct output back to the user. 

A key concept of a software framework is this _inversion of control_, where the program's overall structure and operation are determined by the framework itself and not our code. As shown in the diagram above, a framework calls our code, and then our code calls code stored in libraries. That is the easiest way to spot the difference between a framework and a library.

Frameworks also make extensive use of the **template method pattern** that we learned about in an earlier chapter. Our code will implement parts of the template method, such as a template method for sending a web page to a web browser. We'll provide one part of the content, and we can override other methods to customize it as needed, but the framework itself will use the template method to actually send the web page to the browser. 

In a later chapter in this course, we'll explore the Python [Flask](https://flask.palletsprojects.com/en/1.1.x/) and Java [Spring](https://spring.io/) frameworks a bit deeper, and see how we can use them in our ongoing software project in this course to make them available via the internet.

### References

* [Software Framework](https://en.wikipedia.org/wiki/Software_framework) on Wikipedia
* [Software Framework vs. Library](https://www.geeksforgeeks.org/software-framework-vs-library/) from Geeks for Geeks
* [Creating software with a framework vs library: what tech recruiters need to know](https://devskiller.com/framework-vs-library/) from DevSkiller
