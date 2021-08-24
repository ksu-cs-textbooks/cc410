---
title: "Summary"
weight: 55
pre: "11. "
---
In this chapter, we learned about **processes** and **threads**. A process is an instance of an application running on our computer, and it can be broken up into multiple **threads** of execution. 

Creating threads is very simple - in most cases, we just need to define a function that is used as the starting point for the thread. However, in multithreaded programs, dealing with shared memory can be tricky, and if done incorrectly we can run into **race conditions** which cause our programs to possibly lose data.

To combat this, programming languages and our operating system provide methods for **thread synchronization**, namely **locks** that prevent multiple threads from running at the same time. 

Then, we saw some quick examples for how to create threads in both Java and Python, and how to handle basic race conditions through the use of locks in each language.

In the next chapter, we'll introduce **event-driven programming**, which depends on multiple threads to make our GUI responsive to the user even while our application is doing work in the background.
