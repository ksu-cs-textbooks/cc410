---
title: "Java Synchronization"
weight: 40
pre: "8. "
---
Next, let's look at a quick example of a race condition in Java, just so we can see how it could occur in our code.

## Poorly Designed Multithreading

First, let's consider this example:

```java
public class MyData {
    
    public int x;
    
}
```

```java
import java.lang.Runnable;
import java.lang.Thread;
import java.lang.InterruptedException;

public class MyThread implements Runnable {

    private String name;
    private static MyData data;

    /**
     * Constructor.
     * 
     * @param name the name of the thread
     */
    public MyThread(String name) {
        this.name = name;
    }
    
    /**
     * Thread method.
     * 
     * <p>This is called when the thread is started.
     */
    @Override
    public void run() {
        for (int i = 0; i < 3; i++) {
            int y = data.x;
            // tell the OS it is ok to switch to another thread here
            Thread.yield();
            data.x = y + 1;
            System.out.println(this.name + " : data.x = " + data.x);
        }
    }
    
    /**
     * Main Method.
     */
    public static void main(String[] args) {
        // create data
        data = new MyData();
        
        // create threads
        Thread thread1 = new Thread(new MyThread("Thread 1"));
        Thread thread2 = new Thread(new MyThread("Thread 2"));
        Thread thread3 = new Thread(new MyThread("Thread 3"));
        
        // start threads
        System.out.println("main: starting threads");
        thread1.start();
        thread2.start();
        thread3.start();
        
        // wait until all threads have terminated
        System.out.println("main: joining threads");
        try {
            thread1.join();
            thread2.join();
            thread3.join();
        } catch (InterruptedException e){
            System.out.println("main thread was interrupted");
        }
        System.out.println("main: all threads terminated");
        System.out.println("main: data.x = " + data.x);
    }
}
```

#### Explanation

In this example, we are creating a `static` instance of the `MyData` class, which can act as a shared memory object for this example. Then, in each of the threads, we are performing this three-step process:

```java
int y = data.x;
// tell the OS it is ok to switch to another thread here
Thread.yield();
data.x = y + 1;
```

Just as we saw in the earlier example, we are reading the current value stored in `data.x` into a variable `y`. Then, we are using the `Thread.yield()` method to tell the operating system that it is allowed to switch away from this thread at this point. In practice, we typically wouldn't use this method at all, but it is helpful for testing. In fact, `Thread.yield()` is effectively the same as calling `Thread.sleep(0)` - we are telling the operating system to put this thread to sleep, but then immediately add it back to the list of threads to be scheduled on the processor. Finally, we update the value stored in `data.x` to be one larger than the value we saved earlier. 

In effect, this is essentially the Java code needed to reproduce the example we saw earlier in this class.

#### Execution

So, what happens when we run this code? As it turns out, sometimes we'll see it get a different result than the one we expect:

![Race Condition in Java](/cc410/images/10/java_race.png)

Uh oh! This is exactly what a race condition looks like in practice. In the screenshot on the right, we see that two threads set the same value into `data.x`, which means that they were running at the same time. 

## Java Synchronized Blocks

To fix this, Java includes couple of special methods for dealing with synchronization. First, we can use the `synchronized` statement, which is simply a wrapper around a block of code that we'd like to be **atomic**. An atomic block is one that shouldn't be broken apart and interrupted by other threads accessing the same object. In effect, the `synchronized` statement will handle acquiring and releasing a lock for us, based on the item used in the statement.

So, in this example, we can update the `run()` method to use a `synchronized` statement:

```java
    @Override
    public void run() {
        for (int i = 0; i < 3; i++) {
            synchronized(data) {
                int y = data.x;
                Thread.yield();
                data.x = y + 1;
                System.out.println(this.name + " : data.x = " + data.x);
            }
            Thread.yield();
        }
    }
```

Here, the `synchronized` statement creates a **lock** that is associated with the `data` object in memory. Only one thread can hold that lock at a time, and by associating it with an object, we can easily keep track of which thread is able to access that object. 

Now, when we execute that program, we'll always get the correct answer!

![Synchronized in Java](/cc410/images/10/java_synch.png)

{{% notice info info-1 "Not Always Random?" %}}

In fact, to get the threads interleaved as shown in this screenshot, we had to add additional `Thread.sleep()` statements to the code! Otherwise, the program always seemed to schedule the threads in the same order on Codio. We cannot guarantee it will always happen like that, but it is an interesting quirk you can observe in multithreaded code. In practice, sometimes race conditions may only happen once in a million operations, making them extremely difficult to debug when they happen.

{{% / notice %}}

