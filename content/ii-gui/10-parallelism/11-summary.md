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

{{< quizdown >}}

---
primaryColor: '#512888'
secondaryColor: '#cccccc'
textColor: black
shuffleQuestions: true
shuffleAnswers: true
locale: en
---

# Process

In a computer, a **process** is best described as what?

1. [X] An instance of a computer program that is running
1. [ ] A sequence of instructions in a program
1. [ ] The memory stored in a running process
1. [ ] A method for synchronizing running programs

# Scheduler

A **scheduler** in an operating system is responsible for what task?

1. [X] Determining which processes to execute at any given time
1. [ ] Choosing when to turn off the computer 
1. [ ] Automatically updating the computer
1. [ ] Keeping track of which program was installed most recently

# Context Switching

**Context switching** on a computer is the process of performing what task?

1. [X] Swapping between running processes
1. [ ] Switching between open windows
1. [ ] Changing the currently logged-in user
1. [ ] Using two versions of the same software

# Thread

In a computer, a **thread** is best described as what?

1. [ ] An instance of a computer program that is running
1. [X] A sequence of instructions in a program
1. [ ] The memory stored in a running process
1. [ ] A method for synchronizing running programs

# Containment

Which of the following statements regarding threads and processes in a computer is the most accurate?

1. [X] A process can contain multiple threads
1. [ ] A thread can contain multiple processes
1. [ ] A thread can belong to multiple processes
1. [ ] A process can belong to multiple threads

# Multiple Threads

Which of the following reasons is given for why we would want to run multiple threads in a GUI-based program?

1. [X] The GUI runs in one thread and the program does work in another
1. [ ] Multiple users can use the program simultaneously
1. [ ] The GUI can only talk to a single thread
1. [ ] A single thread doesn't have enough memory for a GUI to operate

# Running Threads

Which of the following statements regarding threads is the most accurate?

1. [X] We cannot control when a thread will be interrupted by another thread
1. [ ] We can control exactly when a thread will run on a system
1. [ ] We can predict exactly how long a thread will run on a system
1. [ ] A program's threads must all run on the same processor core

# Race Condition

Which of the following statements best describes a **race condition** in parallel programming?

1. [X] Two threads try to update the same value at the same time
1. [ ] One program finishes before another one starts
1. [ ] Two programs try to read the same file at the same time
1. [ ] Two variables contain the same exact value

# Lock

A **lock** in parallel programming is used to perform what task?

1. [X] Prevent two threads from accessing the same data
1. [ ] Protect a file from unwanted changes
1. [ ] Encrypt secure passwords in a vault
1. [ ] Make sure the assembly code is not overwritten

# Deadlock

What is the primary cause of **deadlock** in a computer program?

1. [X] A thread acquires a lock and does not release it
1. [ ] Threads not using locks to access data
1. [ ] Processes that contain a single thread
1. [ ] A thread acquires and quickly releases a lock repeatedly

{{< /quizdown >}}