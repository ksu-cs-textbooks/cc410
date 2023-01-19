---
title: "Swing Event Dispatch Thread"
weight: 30
pre: "6. "
---

The Java Swing GUI toolkit uses a special thread called the [**Event Dispatch Thread**](https://docs.oracle.com/javase/tutorial/uiswing/concurrency/dispatch.html) (abbreviated EDT) to handle events. This thread is where most of the code that interacts with a GUI written in Swing actually runs, leaving the main application thread to do other tasks as needed.

## Starting the Thread

In all of our examples so far, we have observed a unique piece of code in the `main()` method that is used to actually launch our GUI-based programs:

```java
SwingUtilities.invokeLater(new Runnable() {
    public void run() {
        new MouseDemo().setVisible(true);
    }
});
```

The `SwingUtilities.invokeLater()` method is used within the application thread to run code within the EDT. So, when we launch our application, the first thing we do is construct a new anonymous class that implements the [Runnable](https://docs.oracle.com/javase/8/docs/api/java/lang/Runnable.html) interface, which defines an object that can be run as a thread. Inside of that class, we place the to code to construct our GUI and make it visible in the `run()` method.

In the background, the first time we call `SwingUtilities.invokeLater()`, Java will see that there is no EDT running and will spawn that thread. Once it is running, then at some time in the future the `run()` method of our anonymous class will be called, which actually loads the GUI within the EDT. 

## Handling Events

The other important task performed by the EDT is actually responding to events from the operating system. So, when it isn't actively running an event handler, the EDT is the thread that is constantly checking the event queue for any new events. 

When an event is received, it looks up the event's associated GUI element, and then checks to see if any listeners are registered with that object for that type of event. If so, then it finds the listener object and calls the appropriate method for that event. 

As discussed earlier, we need to make sure our event handlers do not take too long to complete. Otherwise, we'll end up slowing down the EDT and making it respond more slowly to events. In addition, this will make our entire GUI appear to "lag" for the user, which is definitely something we want to avoid. 

##### References

* [The Event Dispatch Thread](https://docs.oracle.com/javase/tutorial/uiswing/concurrency/dispatch.html) from Oracle
* [Event Dispatching Thread](https://en.wikipedia.org/wiki/Event_dispatching_thread) on Wikipedia
