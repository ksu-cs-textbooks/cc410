---
title: "Scheduling"
pre: "2. "
weight: 20
date: 2020-02-16T00:53:26-05:00
hidden: true
---

{{< youtube CmbtJtrAOH8   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

Let's look a bit deeper at how the operating system handles scheduling multiple threads within a process and what impacts that might have on our code. First, let's start with the theoretical process model shown here. This is a very simplistic view of how two processes might run in parallel, but it hides many of the important details regarding how these two processes might execute on a computer. First, we see our process's main thread begin with the `main()` method. Then, inside of the main method, we create a new thread, and call it's `start()` method to cause that thread to be placed in the "waiting" state, ready for the operating system to schedule it to run. Once it does, then both threads can work independently and in parallel, hence the term "parallel programming." 

Now, let's see what this theoretical model might look like on a computer that has just a single CPU core. While this might seem unrealistic, remember that there are still many small devices such as watches that only have a single processor, and even today many of the shared systems in the cloud only give users access to a single processing core at a time. So, this model may actually make sense for those systems. In this diagram, we start at the top, and then time moves forward as we move down the diagram, just like before. However, now we are representing the CPU as the box down the middle, and each thread is allowed to execute on the CPU when its box overlaps with the CPU box. Starting at the top, we load our application and start in the `main()` method, which will create and start a new thread. In this example, the operating system immediately decides to switch to that new thread, so the main thread is put into the "waiting" state and the spawned thread is scheduled to run. It will compute for a while, but eventually the operating system will decide to interrupt it and switch back to the main thread. On most modern systems, the spawned thread will only run for a few microseconds, but that might cover thousands or more individual CPU cycles. So, the operating system will switch back and forth between these two threads until they are both finished. 

The model becomes a bit more complex when we expand it to cover multiple CPUs. Here, we are showing two different CPUs, and that each thread only runs on its own CPU core. However, in practice, threads may switch between any of the available CPU cores at any time, so even this is leaving out a few details. However, such a diagram would be overly complex for our needs in this course, so we'll leave that part out. Here, we can see that the main thread starts on CPU 1, and as soon as it spawns a second thread, that threads can execute on CPU 2. This is the power of multithreaded, or parallel, programming. By taking advantage of multiple CPU cores, our application can perform multiple computations simultaneously, making the entire application appear to run much faster. And, in practice, parallel programming done correctly can indeed result in programs that run much faster on modern computer systems. 

Of course, there is one other thing we have to keep in mind. On most computer systems, there are potentially hundreds or thousands of threads that all need access to just a few CPU cores. So, our threads aren't the only ones that are being scheduled to run on the CPUs. Here, we can see how our threads can be constantly interrupted by other threads that are scheduled by the operating system. And, our threads may be moved between processors as well, though again we are just focusing on this simple 2 CPU model for now. As we see here, our threads still run in parallel, but there is no real guarantee that they will not be interrupted while performing their work. They will still appear to run faster to the user, but they are not running 100% of the time. 

So, what is the big takeaway from all of this. In short, we must always remember that the operating system is in control, not the programmer. Because of that, we can neither predict, nor control, when our threads are executed, which core they are executed on, how long they will run, or when they will be interrupted. This means that we really don't know much of ANYTHING about how our threads may actually execute, so instead we'll have to write our code in a way that will guarantee success no matter what happens. The rest of this chapter will introduce the classic form of an error in parallel programming, the race condition, and give us one possible way to solve it. 

