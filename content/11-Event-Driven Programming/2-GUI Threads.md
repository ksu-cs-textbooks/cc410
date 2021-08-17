---
title: "GUI Threads"
weight: 10
pre: "2. "
---
Up to this point, we've only created applications that use a single thread. However, now that we are writing applications that include a GUI, we must start to build applications that use multiple threads to manage its work. Otherwise, if the application is busy working on a particular task while the user clicks a button in the GUI, the GUI won't respond to the user until our task is complete.

To resolve this, we typically build our GUI applications in a way that the GUI runs in a separate thread from the rest of our application. In that way, the GUI is always responsive to the user, and our application can continue to do whatever it needs in additional threads. Those threads won't impact the responsiveness of our GUI, at least if they are constructed properly.

## Event-Driven Programming

![Event Loop](../../images/11/event_loop.jpg)^[https://commons.wikimedia.org/w/index.php?title=File:Event_driven_programming_Simply_Explained.jpg&oldid=462525602]

This leads to a new programming paradigm called [**event-driven programming**](https://en.wikipedia.org/wiki/Event-driven_programming). Event-driven programming can be thought of as an alternative to [imperative programming](https://en.wikipedia.org/wiki/Imperative_programming), though in practice both paradigms are used within the same program. In imperative programming, the program follows a set sequence of steps to perform an action, directly as defined in the program's source code. In event-driven programming, the steps a program takes are determined by an external factor that generates **events** within the system. The program will receive those events, and then use the event received to decide what steps, if any, to perform. Of course, the process of waiting for events, receiving them, and acting upon them, is usually all done through imperative code. 

Consider the diagram above. In it, a user interacts with a button in an application, which is an event. That event triggers some piece of code, which is typically called an **event handler**, to react to that event. The event handler examines the event, and performs the requested action. 

Behind the scenes, there is another piece of code, called the **event loop**, that is actually watching for these events and calling the appropriate event handlers for us.

On the next few pages, we'll dive into each of these steps in building a responsive GUI using event-driven programming.
