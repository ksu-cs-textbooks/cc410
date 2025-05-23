---
title: "Summary"
weight: 35
pre: "7. "
---
In this chapter, we discussed some steps we can take when debugging our applications. When we find a bug, we should try to figure out how to replicate it first, then focus on isolating the bug, and finally fix the bug. While we do so, we can write additional unit tests to reproduce the bug that will help us confirm that we've fixed it, and we can perform some regression testing to make sure we didn't introduce any new errors.

We discussed ways we can inspect the state and behavior of our application. We learned that we can create a call stack or stack trace from our code, giving us insight into exactly what lines of code are being executed at any given time.

We explored the use of debuggers, and saw that Codio has a built-in debugger that we can use in our projects.

Finally, we learned about the logging capabilities that are present in both Java and Python, and how we can convert our simple print statements to logging statements that can easily be turned on, off, or configured as needed.

## Review Quiz

Check your understanding of the new content introduced in this chapter below - this quiz is not graded and you can retake it as many times as you want.

{{< quizdown >}}

---
primaryColor: '#512888'
secondaryColor: '#cccccc'
textColor: black
shuffleQuestions: true
shuffleAnswers: true
locale: en
---

# Hello World

According to a common programming joke relevant to this chapter, the **Hello World** program is also what?

1. [X] The only bug-free program you'll write
1. [ ] The hardest program to debug
1. [ ] A great example of object-oriented programming
1. [ ] The most difficult program to write

# Cost of Bugs

We've already seen that the cost of fixing software bugs is high. What is one method proposed to **reduce those costs**?

1. [X] Write fewer bugs
1. [ ] Increase inflation
1. [ ] Use a different programming language
1. [ ] Write code in a single function

# Fixing Bugs

Place the three steps for dealing with a bug below in the correct order. (Click and drag to reorder elements)

1. Reproduce the Bug
2. Find the Bug
3. Fix the Bug

# Regression Testing

When fixing a bug, why might we also want to perform **regression testing**?

1. [X] To make sure the fix didn't introduce new bugs
1. [ ] To fix older versions of the software
1. [ ] To deploy the software on older hardware
1. [ ] To look for related bugs in the software

# Inspecting State

Which of the following is proposed as one way to inspect the current **state** of the program?

1. [X] Print statements
1. [ ] Stack trace
1. [ ] Unit tests
1. [ ] Profiling

# Forcing State

Which of the following is proposed as one way to force a particular **state** within a program?

1. [ ] Print statements
1. [ ] Stack trace
1. [X] Unit tests
1. [ ] Profiling

# Inspecting Behavior

Which of the following is proposed as one way to inspect the current **behavior** of the program?

1. [ ] Print statements
1. [X] Stack trace
1. [ ] Unit tests
1. [ ] Profiling

# Debugger

A **debugger** is a special program to do what?

1. [X] Inspect another running program
1. [ ] Automatically remove common bugs
1. [ ] Mark bugs in source code
1. [ ] Run programs repeatedly to discover errors

# Breakpoint

In a debugger, we can set a **breakpoint** on a line of code to accomplish what task?

1. [X] Pause the program before executing that line of code
1. [ ] Automatically check if that line causes a bug
1. [ ] Terminate the program if it skips that line
1. [ ] Change the branch taken in a conditional statement

# Step Into

If a debugger is stopped on a line containing a function call, pressing the **step into** button will perform what action?

1. [X] Pause execution on the first line within the function being called
1. [ ] Move execution to the next line in the current function unless it reaches a breakpoint
1. [ ] Continue executing the program until another breakpoint is reached
1. [ ] Finish executing the current function and move to the function it was called from

# Step Over

If a debugger is stopped on a line containing a function call, pressing the **step over** button will perform what action?

1. [ ] Pause execution on the first line within the function being called
1. [X] Move execution to the next line in the current function unless it reaches a breakpoint
1. [ ] Continue executing the program until another breakpoint is reached
1. [ ] Finish executing the current function and move to the function it was called from

# Step Out

If a debugger is stopped on a line containing a function call, pressing the **step out** button will perform what action?

1. [ ] Pause execution on the first line within the function being called
1. [ ] Move execution to the next line in the current function unless it reaches a breakpoint
1. [ ] Continue executing the program until another breakpoint is reached
1. [X] Finish executing the current function and move to the function it was called from

# Resume

If a debugger is stopped on a line containing a function call, pressing the **resume** button will perform what action?

1. [ ] Pause execution on the first line within the function being called
1. [ ] Move execution to the next line in the current function unless it reaches a breakpoint
1. [X] Continue executing the program until another breakpoint is reached
1. [ ] Finish executing the current function and move to the function it was called from

# Logger

In programming, a **logger** is a tool that performs what action?

1. [X] Collects debugging information while a program is running
1. [ ] Pauses execution of a running program
1. [ ] Removes any unnecessary branches of a program
1. [ ] Detects and eliminates bugs in the code

{{< /quizdown >}}