---
title: "Event Loop"
weight: 25
pre: "5. "
---

{{< youtube jUodljf8V30  >}}

[Video Materials]({{% relref "./video" %}})

Most GUI frameworks, such as Java Swing and tkinter, handle user interactions through the use of a **loop**, which runs within the GUI thread and listens for events generated by the user.

![Event Loop](/images/11/eventloop.png)[^1]

[^1]: https://tkdocs.com/tutorial/eventloop.html

When an event is generated by the user, it is first placed in an **event queue**, which is a queue-based data structure used to keep track of events generated by the user. The events are placed there by a thread in the program, usually part of the GUI framework, that is connected and "listening" for events from the operating system. We use a queue to keep track of events, just in case the user generates events more quickly than our program can handle them.

Then, in the GUI thread of our program, there is a loop of code that is constantly checking if the event queue contains any elements. We typically refer to this code as the **event loop**. If it does, it will take the first element from the queue and examine it. If that event is **bound** with a known **event handler** somewhere in our code, then the event loop will call the event handler, shown in the diagram above as a "callback" function. 

Once the event handler has returned, the event loop will take the next event from the queue and act upon it, and it will continue to do so until there are no events left in the queue.

In some GUI frameworks, the event loop is also responsible for updating the GUI on the screen itself, as shown in the diagram above. So, while the event handlers are executing, the GUI screen itself cannot be updated and the application will appear to "freeze." 

So, it is _very important_ for our event handlers to be very short and execute quickly, or else the user might notice that our application is not responsive. If the event requires a large amount of calculation, we may want to create a separate thread to handle that operation. Thankfully, most simple GUI programs will not require this, but it is always something to be aware of in case our application starts running slowly. 

On the next two pages, we'll briefly discuss the event loop for both Java Swing and Python tkinter. As always, you may skip to the language you are learning, but it may be helpful to see how both languages perform a similar task.
