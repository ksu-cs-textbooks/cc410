---
title: "Event Loop"
pre: "2. "
weight: 20
date: 2020-02-20T00:53:26-05:00
hidden: true
---

{{< youtube jUodljf8V30   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

Let's briefly go through the steps of starting a GUI program, the event loop, and handling an event. I hope this process will help clarify exactly what's going on behind the scenes in our GUI-based programs when an event occurs. First, let's set the stage. Here, we have our application to the right, and it contains some code that gives the overall structure and layout of the GUI.

When we load the program, we begin by calling the event loop. This is the thread that will continually run and keep the GUI updated on the screen, and it also handles all incoming events, as we'll see shortly.

The event loop will start by sending the instructions for painting the GUI to the operating system. The operating system will, in turn, send those commands to the monitor...

which will then display our application!

In addition, we can include code in our application to listen for several events. Each one of those will bind an event to a particular event handler. 

If we want to listen for more than one event or type of event, we'll need to add multiple handlers. 

In this example, we'll have three different event handlers, each one bound to a particular event in our application. The third event handler is bound to the "click" event from the button showing in our GUI.

Finally, our program will also have access to an event queue. This is the place where the operating system can send incoming events to our application, and then the event loop will be able to receive that event and act upon it.

So, let's say the user clicks on the button in our GUI. What happens then?

First, the click is received by the operating system by interpreting the information from the mouse, it's position on the screen relative to our GUI, and a whole bunch of other factors. 

Since the operating system is able to determine that this event should be sent to our application, it will place the event in the event queue for our application, like so.

Meanwhile, our application's event loop is constantly checking the event queue for new events. As soon as one appears, it will act upon it. First, it will examine the event to determine what type of event it is and which GUI element it is associated with. Then, it will look through all of the event bindings and determine which event handler, if any, is bound to this event. 

In this case, event handler 3 is bound to the click event on our GUI button...

so we'll send the event to that handler by calling the handler's method. 

Let's say that event handler is responsible for updating the GUI based on the button click. So, it will modify the associated GUI code and then return. 

As we've discussed before, we try to keep our event handlers very efficient so that they don't make our GUI appear to "lag" and be unresponsive to the user. So, it returns quickly. Notice that the screen hasn't been updated yet. This is because that process is actually handled within the event loop. So, once the event handler is done, the event loop continues running, and eventually it gets back to the point where it must update the screen.

At that time, it will send the new GUI instructions to the operating system...

which will then update the GUI that is displayed to the user! Of course, this happens so quickly that it appears to be instantaneous to the user, but as we've seen there are actually several steps involved. 

Hopefully this helps you better understand event-driven programming and what is going on behind the scenes when we bind an event handler to a particular event in our GUI. In the example project, we'll see how we can build some event handlers to make our GUIs actually useable. Good luck!

