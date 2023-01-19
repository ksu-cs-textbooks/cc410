---
title: "tkinter Main Loop"
weight: 35
pre: "7. "
---

In Python tkinter, we have an event loop that runs in the background, handling all of the GUI updates as well as responding to any events in the event queue by calling the appropriate callback function. 

## Starting the Thread

In all of our examples so far, we have observed a unique piece of code in the `main()` method that is used to actually launch our GUI-based programs:

```python
MainWindow().mainloop()
```

The `tk.Tk.mainloop()` method is used to start the event loop attached to the top-level `tk.Tk` object in our GUI. This is a **blocking** function, meaning that it will not return as long as the GUI is running, even when it isn't visible to the user. So, in effect, any code after this in our `main()` method that is after this function call will not be executed. Instead, that thread is constantly working to update the GUI on the screen and making sure that events are handled quickly.

Therefore, if we need to create an additional thread for our application, we typically will do so before calling this `mainloop()` method in our `main()` method. We can also create new threads from within the event loop thread as needed.

## Handling Events

The other important task performed by the event loop is actually responding to events from the operating system. So, when it isn't actively running a callback, the event loop is the thread that is constantly checking the event queue for any new events. 

When an event is received, it looks up the event's associated GUI element, and then checks to see if any callbacks are registered with that object for that type of event. If so, then it calls the callback function for that event. 

As discussed earlier, we need to make sure our event handlers do not take too long to complete. Otherwise, we'll end up slowing down the event loop and making it respond more slowly to events. In addition, this will make our entire GUI appear to "lag" for the user, which is definitely something we want to avoid.

##### References

* [Event Loop](https://tkdocs.com/tutorial/eventloop.html) from Tkdocs
