---
title: "Threads"
weight: 15
pre: "3. "
---
![Thread](/images/10/thread.svg)[^1]

[^1]: https://commons.wikimedia.org/w/index.php?title=File:Multithreaded_process.svg&oldid=515934464

In most modern operating systems, a process can be further divided into **threads**, which are individual sequences of instructions that the program can follow. A great way to think of a thread is an individual line of code that you can trace through your program, starting at the beginning and going all the way to the end. Up to this point, we've only written programs that contain a single thread, so you should only be able to trace a single line of code all the way through the program. 

However, it is possible for our program to create multiple threads, and then have them appear to run simultaneously. Of course, as we said before, they may not actually run simultaneously, especially on a computer with only a single processing core. It is all left up to the scheduler in the operating system to determine how these threads are actually scheduled and executed. 

{{% notice info note-1 "Complexity" %}}

This description leaves out some of the complexity of how threads and processes work within modern operating systems on modern hardware. In the real world, it is possible for a process to consist of multiple threads, and those threads can be scheduled to run at any time on any processor in any order by the operating system.

In addition, many newer processors support running multiple threads simultaneously on a single core, so threads could be running at the exact same time, maybe even on the same processor core itself.

We won't worry about any of these details in this course, since much of this is handled for us by our programming language and operating system. However, if you plan to develop truly high-performance applications that use threads, you'll need to learn how to properly deal with the complexity that comes from using modern computer hardware.

{{% / notice %}}

Thankfully, because of this, we can write programs that use multiple threads to perform different tasks at (nearly) the same time. To the user, it appears that our program is doing multiple things at once!

For our use, there are two major reasons why we would want to use multiple threads:

1. If our program is running on a system that truly has multiple cores, we can split large calculations into multiple threads which can run simultaneously, making the calculation take less time overall.
2. If our program includes a GUI that the user is interacting with, we can run the GUI in one thread and perform calculations in other threads. In that way, the GUI won't appear to freeze when a calculation is occurring. 

In this chapter, we're going to learn about both uses, but going forward we're most concerned about the second use, making our GUI appear to be responsive even while our program is performing other tasks. In a later chapter, we'll learn about **event-driven programming**, which relies on splitting a program into multiple threads as well.
