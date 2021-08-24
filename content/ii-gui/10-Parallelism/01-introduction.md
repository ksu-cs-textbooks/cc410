---
title: "Introduction"
weight: 5
pre: "1. "
---

Up to this point, we've only been dealing with programs that run within a single [**thread**](https://en.wikipedia.org/wiki/Thread_(computing)) of execution. That means that we can follow a single path through the code, all the way from the start of the program when it calls the `main()` method all the way to the end. Unfortunately, while this allows us to create many useful programs, we aren't able to take advantage of the power of modern computers with [multi-core processors](https://en.wikipedia.org/wiki/Multi-core_processor), which can handle multiple tasks simultaneously. 

In addition, if our application needs to perform multiple tasks at once, such as computing a complex value while also handling user interactions with a GUI, we need a way to develop a program that can have multiple simultaneous paths executing at the same time. Without this, our GUI will appear to freeze anytime the application needs to compute something, frustrating our users and making it very slow to use. 

In this chapter, we'll introduce the concept of [multithreaded computing](https://en.wikipedia.org/wiki/Multithreading_(computer_architecture)), which involves creating a single program that can perform multiple simultaneous tasks within **threads**, itself a subset of the larger concept of [parallel computing](https://en.wikipedia.org/wiki/Parallel_computing) that involves running multiple **processess** simultaneously, sometimes spread across large [supercomputers](https://en.wikipedia.org/wiki/Supercomputer). 

Some key terms we'll cover in this chapter:

* Thread
* Process
* Multithreading
* Scheduling
* Parallel
* Thread safety
* Shared memory
* Race Condition

We'll also explore a short example multithreaded program to see how it works in each of our programming languages. 
