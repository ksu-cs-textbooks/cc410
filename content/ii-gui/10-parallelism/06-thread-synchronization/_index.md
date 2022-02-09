---
title: "Thread Synchronization"
weight: 30
pre: "6. "
---

{{% youtube zJRpJxICl-s %}}

[Video Materials}({{<relref "./video">}})

To deal with race conditions, we have to somehow synchronize our threads so that only one is able to update the value of a shared variable at once. There are many ways to do this, and they all fit under the banner of **thread synchronization**.

## Locks

The simplest way to do this is via a special programming construct called a **lock**. A [lock](https://en.wikipedia.org/wiki/Lock_(computer_science)) can be thought of as a single object in memory that, when a thread has **acquired** the lock, it can access the shared memory protected by the lock. Once it is done, then it can **release** the lock, allowing another thread to acquire it.

A great way to think about this passing a ball around a circle of people, but only the person with the ball can speak. So, if you want to speak, you try to acquire the ball. Once you've acquired it, you can speak and everyone else must listen. Then, when you are done, you can release the ball and let someone else acquire it.

Of course, if someone decides to hold on to the ball the entire time and not release it, then nobody else is allowed to speak. When that happens, we call that situation **deadlock**. The same thing can happen with a multithreaded program. 

So, let's update our program to use a lock. In this case, we'll assume that `data` includes another attribute `lock` which contains a lock that is used to control access to `data`:

```python
data.lock.acquire()
y = data.x
data.x = y + 1
data.lock.release()
```

Now, let's look at our two possible situations and see how they change when we include a lock in our code. First, we have the situation where the programs are properly interleaved:

![Thread No Race with Lock](/images/10/thread_norace_lock.svg)

In this case, the spawned thread is able to acquire the lock when needed, perform its computation, and then release the lock before the other thread needs it. So, the lock really didn't change anything here. 

However, in the next case, where they are interleaved, we'll see a difference:

![Thread Race With Lock](/images/10/thread_race_lock.svg)

Here, the spawned thread immediately acquires the lock and reads the value of `data.x` into `y`, but then it is interrupted. At that same time, the main thread wakes up and starts running, and tries to acquire the lock. When this happens, the operating system will **block** the main thread until the lock has been released. So, instead of waiting, the main thread will be blocked, and the spawned thread will continue to do its work. However, once the spawned thread releases the lock, the operating system will wake up the main thread and allow it to acquire the lock itself. Then, the main thread can perform its computation and update the value in `data.x`. As we can see, we now get the same value that we had previously. This is good! This means that we've come up with a way to defeat the inherent unpredictability in multithreaded programs. 

The same holds for the third example on the previous page, when both threads run simultaneously. If both threads try to acquire the lock at the same time, the operating system will determine which thread gets it, and block any other threads trying to access the lock until it is released. 

Of course, this introduces another interesting concept - if our threads must share data in this way, then is this any better than just having a single thread? If we look at this example, it seems that the threads can only run sequentially because of the lock, and that is true here. So, to make our multithreaded programs effective, each thread must be able to perform work that is independent of the other threads and any shared memory. Otherwise, the program will be even more inefficient than if we'd just written it as a single thread!

On the next pages, we'll explore the basics of creating and using threads in both Java and Python. As always, feel free to skip ahead to the language you are learning, but you may wish to review both languages to see how they compare.
