---
title: "Processes"
weight: 10
pre: "2. "
---

{{< youtube aDJMUyneWKY  >}}

[Video Materials]({{% relref "./video" %}})

First, let's review how modern computers actually handle running multiple applications at once, and what that means for our own programs.

## Process

![HTOP](/images/10/htop.png)[^1]

[^1]: https://commons.wikimedia.org/w/index.php?title=File:Htop.png&oldid=528715283

When a program is executed on a computer, the operating system loads its code into memory and creates a [**process**](https://en.wikipedia.org/wiki/Process_(computing)) to handle running that program. A process is simply an instance of a computer program that is running, just like an object is an instance of a class. Some programs, such as a web browser, allow us to create multiple processes of the same program, usually represented by multiple windows or tabs. The image above shows the `htop` command in Linux, which lists all of the processes running on the system. In Codio, we can use the `top` command in the Terminal to see the running processes - go ahead and try it!

At some point during your experience working with a computer, you may have been told that a computer can only do one thing at a time, and that it appears to run multiple programs at the same time by quickly switching between them. That's mostly true, though in actuality there is a bit more nuance to it, which we'll discuss a bit later. For modern computer with multi-core processors, we can typically have one process running per core. 

In practice, an operating system may have tens or even hundreds of processes running at any given time. However, the computer it is running on may only have four or eight processor cores available. So, the operating system includes a **scheduler** that determines which processes should be executed at any given time, and most operating systems will switch between running processes thousands of times per second, making it appear to a user that all running processes are executing at the same time. This process of swapping between running processes is known as **context switching**.

![Process States](/images/10/process_states.svg)[^2]

[^2]: https://commons.wikimedia.org/w/index.php?title=File:Process_states.svg&oldid=508079226

The diagram above shows the various states a process can be placed in by the scheduler in the operating system. When the process is able to execute, it is in the **running** state. When the scheduler is ready to pause it, it is placed into the **waiting** state. However, when it is trying to load a file or waiting on another task, it is instead in the **blocked** state until that operation has completed. 

When a process is **waiting** or **blocked**, the operating system could also decide that it needs to reclaim the memory used by this process. In that case, it can be **swapped** out of the processor's cache in place of another process. Of course, all of this happens at the microsecond level in modern processors, so a process can be running, waiting, blocked, swapped out of memory, and swapped back in memory, all within a single second.

So, in the simplest version, each program we want to run is loaded into a process by the operating system, which handles scheduling that process to run on one of the cores of our processor. That's what we need to know for now, as we introduce the next concept, **threads**.




