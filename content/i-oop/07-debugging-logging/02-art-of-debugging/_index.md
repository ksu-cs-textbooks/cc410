---
title: "Art of Debugging"
weight: 10
pre: "2. "
---

{{% youtube 7C4_tgqClkw %}}

[Video Materials]({{<relref "./video">}})

First, let's briefly discuss the art of debugging. Finding and fixing bugs in a complex piece of software is indeed an art, meaning that it something that takes a great amount of skill that comes with practice. So, how can we get better at this? Here are some tips. Much of this content was inspired by the talk [The Art of Debugging](https://remysharp.com/2015/10/14/the-art-of-debugging) by Remy Sharp. 

## Write Fewer Bugs

This seems pretty obvious, but as we've discussed several times in this course, software bugs can be very costly to fix, and the longer they remain in the source code, the harder they can be to fix. So, as a developer, it is important for us to always focus on writing code that is free of any obvious bugs and errors.

If we take the time to think clearly about our code, trace it out on paper or in our head, and maybe even write small little test programs to make sure the code behaves the way we expect it to, we can greatly reduce the amount of simple bugs that get included in our programs. Even simple logic errors such as the classic "off by one" error (where we forget to properly handle the last item in an array) or more complex issues such as floating-point errors can be discovered and dealt with quickly by a programmer who is consciously thinking about how the code will be used and how it might fail. 

Unfortunately, if a bug is introduced, we can follow a three step process to find and fix the bug.

## 1 - Reproduce The Bug

The first step in debugging is figuring out how to consistently reproduce the bug. For example, say a customer complains that our point of sale application crashes once every few days. There could be all sorts of reasons why that might happen, and based on that information, it can be really difficult to tell what is going on.

However, with a bit more digging, we might find out that the customer only sells hot dogs on Fridays, and those are the days that the application crashes. That might give us a clue that something related to hot dogs might be the culprit.

So, we can start working with our program and figuring out exactly what causes the application to crash. Hopefully, we'll be able to figure out a minimum set of steps or a short piece of sample code that can trigger the exact bug we are looking for. Once we are in a position to effectively reproduce the bug, we can start fixing it.

## 2 - Find The Bug

At this point, we know how to cause the bug, but we still may not know exactly why the bug is occurring, nor what piece of code is causing it. So, we'll need to continually reproduce the bug while inspecting our program to determine the root cause. At this point, we can use several tools such as **debuggers** and **stack traces** to see exactly what is going on when the program crashes. We can also examine **logs** of data created by our program.

Finally, one of the simplest but surprisingly powerful methods of isolating a bug is to add some additional debugging code to our program, and then engage in a virtual "binary search" process to determine where the bug is. If the code reaches our debugging code before it crashes, we know that the bug occurs after that point in our program. While it may seem rudimentary, it can be a very powerful technique. 

## 3 - Fix the Bug

Once we have identified the location of bug, we can work on fixing it. At this point, one of the most powerful things we can do is write a unit test that causes the bug. We can use special methods in our unit test to assert that the code should or should not throw an exception, depending on how it should operate.

Then, once we are sure our unit test will cause the bug, we can set about trying to fix it. This could involve some careful coding to either catch the specific case that causes the bug, or we may have to more generally refactor or restructure our code a bit to deal with larger errors.

Once we believe we've fixed the bug, we can run our unit test to confirm that it is no longer present in our code. At that point, we may also want to run all of our unit tests as a form of **regression testing** to make sure that our fix for this bug didn't introduce any new bugs as well. 

If everything looks good, then we can work on deploying the new version of our application, hopefully with at least one fewer bug!
