---
title: "Creating Threads"
weight: 20
pre: "4. "
---

{{% youtube CmbtJtrAOH8 %}}

[Video Materials]({{<relref "./video">}})

Now that we've learned about threads, let's discuss how we can work with them in our programs. Writing a multithreaded program can be significantly more difficult than a single threaded program, but with the extra difficulty comes the ability to write programs that are much more flexible and powerful. 

## Creating a Thread

Creating a thread is very simple in many modern programming languages. Both Java and Python include libraries for dealing with threads, and to create a new thread, each one simply requires some sort of function or method to serve as the starting point for the new thread. In a way, this is just like the `main()` method that is the starting point of most programs - we're just defining a new method to serve as the starting point for a new thread.

Once we've created the thread, it is given to the operating system for scheduling. Our main thread can continue to work, and the newly created thread will also start to run as well. So, the theoretical model might look something like this:

![Thread Model](/images/10/thread1.svg)

Here, it appears that both threads are running simultaneously. However, as we discussed earlier in this chapter, that isn't really the case. For example, if the system only has one processor core, and these are the only two threads running on the system, then the threads might be interleaved on that processor like this:

![Single Core](/images/10/thread2.svg)

If we expand that to two processor cores, then they might actually run simultaneously, like this:

![Dual Core](/images/10/thread3.svg)

Of course, this is a _very_ simplified view of this process. In practice, there will be many processes and threads that are competing for access across several cores, so the actual model could look something like this:

![Threading Model](/images/10/thread4.svg)

As we can see, the processors are always executing some code, but many times they are executing code in a thread from some other application. Our application's code will be scheduled by the operating system in between the other threads, but we cannot guarantee when it will be scheduled or for how long. Also, while this diagram makes it appear that each thread will only be scheduled on one processor, in fact the thread could be scheduled on ANY processor that is available. On a modern personal computer today, there may be as many as 16 or 32 individual threads available, sometimes multiple threads per CPU core, in the processor!

So, the big takeaways here:

1. Our application can create threads, which start by running code in a function specified when the thread is created.
2. The operating system will schedule our threads across the available cores in the CPU.
3. We cannot predict or control when the threads will be scheduled to run.
4. We cannot predict or control how long the threads will run. 
5. We cannot predict or control when the threads will be interrupted by another thread.
