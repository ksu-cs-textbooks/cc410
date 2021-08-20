---
title: "The Art of Debugging"
pre: "1. "
weight: 10
date: 2020-01-25T00:53:26-05:00
hidden: true
---

{{< youtube 7C4_tgqClkw >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

In this chapter, we're going to take a short detour and cover a couple of topics that might of interest as we start to develop our own larger programs. One major task that most developers must do from time to time is find and fix bugs in a program. This becomes even more difficult to do in large scale software projects, and most professionals would tell you that there is an art to it. So, in this chapter, we're going to discuss a bit of the art of debugging and some tips we can use in our projects to help quickly find and fix bugs. Before I begin, I want to give credit to Remy Sharp, a developer and public speaker who inspired the content of this section. 

At some point, someone will tell us that a program we wrote has a bug in it. It might be a user, a fellow developer, or it might even be a bug we ourselves realize is in our code. When that happens, there are three basic steps we can follow to take care of the bug. First, and foremost, we must try to reproduce the bug. Sometimes this is really easy to do - for example, our program could crash when we try to open a particular file. Other times, the bug can be harder to reproduce. For example, what if our program doesn't handle leap years correctly? In that case, we might only see the bug on one day every 4 years! In either case, as a developer, we want to think logically about the cause of the bug and how it can be caused. Ideally, we'd like to come up with a minimal set of steps that, when performed, will cause the bug. Once the bug can be reproduced successfully, we can start fixing it.

The next step is to find the bug in our code itself. At this point, we should be able to reproduce the bug, so we can start digging through the code and figuring out where the problem is. At this step, we may wish to rely on some common debugging tools such as print statements, logging systems, or even interactive debuggers. We'll learn more about those later in this chapter. Hopefully, we'll be able to figure out exactly what method and inputs cause the bug in our code. Once we do, it is always a good idea to try and write a unit test that causes the bug. In that way, we can quickly know if we've solved it later on, and make sure it doesn't come back.

Finally, once we've narrowed down the source of the bug in our code, we can start to fix it. In many cases, this involves reviewing the code, understanding how it works and why the bug occurs, and then carefully modifying the code to remove the bug. Once we think we have it solved, we should test our code and make sure we can no longer reproduce the code. In addition, we may wish to perform regression testing and make sure our fix didn't break something else. We might also consider the case where there are other related bugs that we can also fix at the same time. Finally, once we are confident in our solution, we can update our code and deploy the new version. 

While this may seem straightforward, I find it very helpful to think through these three steps whenever I'm faced with a particularly difficult bug in my code. First, I try to reproduce it. Then, I isolate it in the code, and finally I work on fixing it and testing my new version. If all goes well, my problem will be solved!