---
title: "Race Conditions"
weight: 25
pre: "5. "
---

{{% youtube PasqRhMjmcI %}}

[Video Materials]({{<relref "./video">}})

Unfortunately, the big takeaways we saw on the previous page have very important consequences for our multithreaded programs. One of the most common errors, and also one of the notoriously most difficult errors to debug, is a race condition.

## Race Condition

A [**race condition**](https://en.wikipedia.org/wiki/Race_condition) occurs when two threads in a program are trying to update the same value at the same time. If the operating system decides to interrupt one thread at just the wrong time, then a race condition occurs and the value could be given an incorrect value.

Let's look at the simplest form of a race condition. Consider the case where we'd like to read a value from a variable, and then add 1 to that value. In code, it might look something like this:

```python
y = data.x
data.x = y + 1
```

Here, we have some `data` object stored in memory, which includes an attribute of `x`. Notice that we are not just adding 1 to the value of `x` and immediately updating it. Instead, we read the value of `x` into `y`, then use `y` to increase the value of `x` by 1. This is a very arbitrary example, but it is reflective of code that we might actually use in our applications. For example, we might read the `x` coordinate position of a sprite in a video game, perform some calculation on that position, and then update the position. It follows a pattern very similar to this. 

So, if we run this code in two separate threads, one way the program could execute is shown below:

![No Race Condition Threading](/images/10/thread_norace.svg)

In this case, both pieces of code work like we expect. The spawned thread goes first, and reads the value 0 from `data.x`. Then, it computes the new value 1 and stores that back in `data.x`. After that, the main thread is scheduled on the other processor, and it reads 1 from `data.x`, computers the new value 2, and stores it back in place. So far, so good, right?

What if the threads get interrupted during the computation? In that case, the program could instead execute like this:

![Race Condition](/images/10/thread_race.svg)

In this case, the spawned thread reads the value 0 from `data.x`, then stores it in `y`. Then, it is interrupted on its CPU, while the main thread is scheduled to execute on the other CPU. So, that main thread will also read the value 0 from `data.x` and store it in `y`. After that, the spawned thread will run, updating the value in `data.x` to 1. Finally, the main thread will execute updating the value in `data.x` to 1 again, even though it was already 1. 

So, as we can see, we've run the same program, and it has produced two different results, depending on how the threads themselves are scheduled to run on the system. This is the essence of a race condition in our code.

What if both threads are scheduled to run simultaneously on two different processors, as in this example:

![Simultaneous Threads](/images/10/thread_simul.svg)

In this case, the main thread is trying to read the value of `data.x` at the exact same instant that the spawned thread is trying to save that value. In that case, what will the main thread think is stored in `data.x`? As it turns out, _we have no way of predicting_ what it will read. It could read 0, or 1, or maybe even some intermediate value the CPU uses while it stores the data.

Thankfully, there is a way to deal with this situation, as we'll learn on the next page. 
