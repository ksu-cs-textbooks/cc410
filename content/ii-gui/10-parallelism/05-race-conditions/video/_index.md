---
title: "Race Conditions"
pre: "3. "
weight: 30
date: 2020-02-16T00:53:26-05:00
hidden: true
---

{{< youtube PasqRhMjmcI >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

Let's take a look at a situation where two threads are trying to modify the same data structure and see how this could possibly lead to one of the major pitfalls of parallel programming - a race condition. Here, we are continuing our diagrams from the previous example, but now we've added a box in the middle to represent the shared `data` object, which is contained in the shared memory of the process that our application is running under. So, our main thread stars by creating the shared `data` object, and then creating and starting a new thread.

So, we'll place our second thread on the second CPU in this diagram. Of course, as I've explained a few times already, this is oversimplifying things a bit - our threads could be scheduled on any processor at all, but this diagram just shows that they could be scheduled on any arbitrary processor. 

In this diagram, we'll assume that the main thread is interrupted on CPU 1, so it is placed in the waiting state. At the same time, our spawned thread on CPU 2 will start performing its computation. So, it will read the value from `data.x` and store it in the local variable `y`. Then, it will store the result of adding 1 to the value in `y` back in `data.x`. We do this in a two step process to allow it to be interrupted by the operating system, as we'll see later.

Next, the spawned thread is interrupted, and the main thread is scheduled to execute. So, it will also perform its computation, eventually storing the value `2` in `data.x`. That's the expected output for this program, so we should see that result no matter how it executes.

Let's look at another example. It starts the same way, with the main thread.

Then, it spawns a second thread. 

And, once again, the spawned thread starts to execute by storing the value `0` from `data.x` in the variable `y`. 

However, as soon as it had completed that operation, the operating system could decide to interrupt that thread and place it in the "waiting" status. Meanwhile, the main thread could be scheduled to execute, and it will start its work by reading the value `0` from `data.x` and storing it in its own local variable `y`. 

Unfortunately, once again the operating system jumps in and interrupts the main thread, but allows the spawned thread to start working again. So, it will read the value `0` stored in `y`, add `1` to it, and then storing that value back in `data.x`. So, `data.x` now stores the value 1. 

After that, when the main thread starts again, it still has the value `0` stored in `y`. So, it will also write the value `1` to `data.x`. Uh oh! This is a problem, because now our program has run the exact same code, but achieved the wrong answer. This is because our program is written in a way that each thread could be interrupted between when it reads a value from the shared memory and when it is able to write it. While this example may seem a bit contrived, as we could just read and update the value in a single line of code, there are many instances where we'll read a value, perform some computation on it, and then write that value a bit later. So, if we aren't careful, we could run into a situation where two threads accidentally store the wrong value.

There is an even bigger problem we'll have to consider. What if the threads are truly executing at the same time? In that case, we'll start like before.

Then create our second thread.

And then that thread will read the value `0` from `data.x` and store it to `y`. 

Next, that thread will store the updated value `1` in `data.x`. 

Meanwhile, on CPU 1, the operating system might schedule our main thread to run at the exact same time. So, while our spawned thread is writing the value `1` to `data.x`, our main thread is trying to read that same value at the same time. So, what would happen in that case? Honestly, there is no way of knowing. Most likely, our main thread will either read `0` or `1`, but if our CPU decides to write any intermediate values to `data.x` while updating it, we could read one of those values instead. So, we really cannot predict what would happen in this case.

Of course, that means that, when the main thread updates the value in `data.x`, we have no way of predicting what value will be stored. 

So, the core essence of a race condition is the fact that we cannot really predict what value will be stored in our shared variable when two threads execute simultaneously. Because those threads can be executed in any order, when they try to update the shared value, they could easily conflict with each other and produce an incorrect result. So, to truly be able to write multi-threaded programs, we need a way to prevent multiple threads from accessing the same variables at the same time. In the next video, we'll discuss one way to do that, through the use of locks. 

