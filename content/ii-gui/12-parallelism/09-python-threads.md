---
title: "Python Threads"
weight: 45
pre: "9. "
---
Python includes several methods for creating threads. The simplest and most flexible is to create a new `Thread` object using the [threading](https://docs.python.org/3/library/threading.html) library. When that object is created, we can give it a function to use as a starting point for the thread.  

Here's a quick example of threads in Python:

```python
import threading
import time
import sys


class MyThread:

    def __init__(self, name):
        """Constructor.
        
        Args:
            name: the name of the thread
        """
        self.__name = name

    def run(self):
        """Thread method."""
        for i in range(0, 3):
            print("{} : iteration {}".format(self.__name, i))
            # tell the OS to wake this thread up after at least 1 second
            time.sleep(1)
            
    @staticmethod
    def main(args):
        # create threads
        t1_object = MyThread("Thread 1")
        thread1 = threading.Thread(target=t1_object.run)
        t2_object = MyThread("Thread 2")
        thread2 = threading.Thread(target=t2_object.run)
        t3_object = MyThread("Thread 3")
        thread3 = threading.Thread(target=t3_object.run)
        
        # start threads
        print("main: starting threads")
        thread1.start()
        thread2.start()
        thread3.start()
        
        # wait until all threads have terminated
        print("main: joining threads")
        thread1.join()
        thread2.join()
        thread3.join()
        print("main: all threads terminated")
                  
                  
# main guard
if __name__ == "__main__":
    MyThread.main(sys.argv)

```

Let's look at this code piece by piece so we fully understand how it works.

#### Imports

```python
import threading
import time
import sys
```

We import both the `threading` library, which allows us to create threads, as well as the `time` library to put threads to sleep. We'll also need the `sys` library to access command-line arguments, if any are used. 

#### Class Declaration

```python
class MyThread:

    def __init__(self, name):
        self.__name = name
```

The class is very simple. Inside of the constructor, we are simply setting a `name` attribute so we can tell our threads apart.

#### Run Method

```python
    def run(self):
        for i in range(0, 3):
            print("{} : iteration {}".format(self.__name, i))
            # tell the OS to wake this thread up after at least 1 second
            time.sleep(1)
```

The `run()` method is the method we'll use to start our threads. This method is pretty short - it simply iterates 3 times and prints the value of the iteration along with the thread's name, and then it uses the `time.sleep(1)` method call. This tells the operating system to put this thread into a waiting state, and to not wake it up until at least 1 second has elapsed. Of course, we can't guarantee that the operating system won't make this thread wait even longer than that, but typically it will happen so fast that we won't be able to tell the difference. 

#### Main Method

```python
    @staticmethod
    def main(args):
        # create threads
        t1_object = MyThread("Thread 1")
        thread1 = threading.Thread(target=t1_object.run)
        t2_object = MyThread("Thread 2")
        thread2 = threading.Thread(target=t2_object.run)
        t3_object = MyThread("Thread 3")
        thread3 = threading.Thread(target=t3_object.run)
        
        # start threads
        print("main: starting threads")
        thread1.start()
        thread2.start()
        thread3.start()
        
        # wait until all threads have terminated
        print("main: joining threads")
        thread1.join()
        thread2.join()
        thread3.join()
        print("main: all threads terminated")
```

Finally, the `main()` method will create three instances of the `threading.Thread` class, and provide an instance of our `MyThread` class as the `target` argument to the constructor. In effect, we are _wrapping_ our runnable class in a thread. 

Then, we call the `start()` method on the thread, which will actually create the thread through the operating system and start it running. Notice that we **do not** call the `run()` method directly - that is called for us once the thread is created in the `start()` method. 

Finally, we call the `join()` method on each thread. The `join()` method will block this thread until the thread we called it on has terminated. So, by calling the `join()` method on each of the three threads, we are making sure that they have all finished their work before the main thread continues.

That's all there is to this example!

#### Execution

When we execute this example, we can see many different outputs, depending on how the threads are scheduled with the operating system. Below are a few that were observed when this program was executed during testing.

![Python Threads](/images/10/python_thread.png)

If you look closely at these four lists, no two of them are exactly the same. This is because of how the operating system schedules threads - we cannot predict how it will work, and because of this a multithreaded program could run differently each time it is executed!
