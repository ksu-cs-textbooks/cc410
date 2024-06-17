---
title: "Locks"
pre: "4. "
weight: 40
date: 2020-02-16T00:53:26-05:00
hidden: true
---

{{< youtube zJRpJxICl-s   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

In the previous video, we saw how two threads could cause issues if they tried to modify a shared variable at the same time. In this video, we'll explore how we can modify our code to use locks, preventing the two threads from conflicting with each other. First, we'll start with the same setup as always - our main thread will start, and then it will create a new thread and start it.

So, we'll see our new thread get scheduled to execute by the operating system.

When that thread starts running, the first thing it will do is try to acquire the shared lock protecting the `data` object in memory. Meanwhile, the main thread was interrupted, so it is in the waiting state.

Since no other threads have acquired the lock, our spawned thread will be able to acquire and hold the lock. We'll show that in this diagram with the green square. When a thread holds that lock, it is the only thread that is able to access and modify the `data` object. 

So, our thread can quickly read the value in `data.x` and then update it with the new value. 

Finally, once our thread is done working with `data`, it can release the lock. That will allow another thread to access that value if needed. Its always important to remember to release a lock as soon as we are done with it - if we don't, we could possibly cause our program to lock up due to **deadlock**. 

Now, in the main thread, we can also acquire the lock. 

Since it is not currently being held by any thread, we are able to acquire it. 

Like before, our main thread can quickly read the value in `data.x` and update it without worrying about any other thread interrupting it. 

Finally, once the main thread is done working with the `data` object, it can also release the lock. So, as we can see, adding the lock really doesn't change anything when the two threads don't try to run at the same time.

Now, let's look at the situation where the threads to actually execute at the same time. Like before, we'll start by creating our second thread.

That thread will try to acquire the lock. Since it is not held by any other thread...

the spawned thread will acquire the lock. 

Next, it will read the value from `data.x` and store it in `y`. We're doing good so far.

Now, what if the main thread is scheduled to execute on another CPU at the same time? In that case, the first thing it will do is try to acquire the lock. Unfortunately, that lock is currently held by the other thread...

So the operating system will block the main thread until the lock is released! This means our lock is working as intended - the main thread is now unable to be scheduled again until the lock is released by the spawned thread.

So, back in the spawned thread, it can complete its work and store a new value in `data.x`. 

And then it can release the lock.

As soon as it does, the operating system will switch the main thread back to the waiting state, and allow it to be scheduled again. When the main thread is scheduled, it will try to acquire the lock again, and this time it is able to get it. So, the main thread now holds the lock.

At that point, the main thread can perform its computation and store the updated result in `data.x`. As we can see , it gets the correct value! 

Finally, the main thread can release the lock, and our program can continue running like normal.

So, as we've seen, using a lock to synchronize access to a shared data object between two threads works really simply. First, the thread must acquire the lock for the object it wishes to modify. Once it does, it can perform work on the object. If any other thread tries to acquire the same lock while it is held, that thread will be blocked until the lock is released. Finally, once the thread is done, it can release the lock and allow another thread to access the shared object. 

Of course, as we warned earlier, it is very important for threads to release locks as soon as they are done - otherwise, we could reach a situation where **deadlock** occurs. This happens when all of our threads are blocked from running, and our whole program freezes up. 

I hope this quick introduction to parallel programming was interesting. In the next chapter, we'll learn how to use multiple threads in our GUI-based programs to make them responsive while the rest of the application is still running in the background. This is a core idea behind event-driven programming, a common paradigm used with graphical programs. 