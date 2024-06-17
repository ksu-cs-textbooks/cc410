---
title: "Event Binding"
pre: "1. "
weight: 10
date: 2020-02-20T00:53:26-05:00
hidden: true
---

{{< youtube ze031YvdTr8   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

In this chapter, we're going to learn about how we can use the concepts in the event-driven programming paradigm to update our GUI-based programs to respond to events. To begin, let's look at what those events are and where they come from. When the user interacts with any GUI-based program, the operating system sends events back to our application based on what the user does. There are many different types of events that the operating system can tell us about, as we'll see shortly. In our application's code, we can choose a particular event type that is associated with an element in our GUI and **bind** that event to a specific object or function, known as an **event handler**. So, when our program receives an event of that type from the selected GUI element, our program will call the associated event handler and let it know that the event occurred. In this way, we can write programs that will quickly respond to any user interactions on our GUI.

There are many different events that we can bind to in our code. This is a short list of some of the most common events we may be concerned with. First of all, we can easily track the mouse as it moves across our program's GUI, which is very helpful for some tasks such as drawing or interacting in a video game. There are events for when a key on the keyboard is both pressed and released, allowing our program to track which keys are being used on both the keyboard and mouse. In addition, several elements have their own events, such as a button's clicked event or the text changed event that is present on most text entry elements. Most elements also have events that fire when the element is given focus, or when a user exits that element and it loses focus. Consider a form with several text entry elements, and the user is able to use the TAB key on the keyboard to move between elements. When the user presses TAB to go to the next element, that element is now the one that has focus. When the user presses TAB again to leave the element, it loses focus. Finally, there are events that are generated each time the GUI itself is resized, allowing us to modify our program's structure or layout as needed, though many times this is handled by our layout manager instead.

Both Java Swing and Python tkinter have methods that allow us to bind a particular event to an event handler. In Swing, we must create an object that implements an interface for the type of event it should handle, and then we register an instance of that object as an event listener for the event. When the event occurs, our program will call the listener registered for that event, if one exists. In Python, we can use the `bind` method to bind events to callback functions. In addition, many elements include a `command` argument that we can populate when they are created with the default event for that element, such as the click event for a button. Then, when the event occurs, our program will call the associated callback function. So, even though the structure and terminology is a bit different, both Java and Python handle GUI events in a similar way.

In both cases, they rely on a special method called an **event handler** to actually handle the event. Java typically calls these listeners, while Python and tkinter uses the term callback function. They contain the code that is executed when a particular event is received from the operating system. Most events will include additional data about the event, such as the location of the mouse or the particular key or button that was pressed that caused the event. Inside of the event handlers, we typically will update the GUI or perform some other action based on the event we receive. However, we must be very careful and make sure that our event handlers are efficient - if they take too long to complete, it could make our GUI appear to "lag" and slow down, which is definitely not something we want. So, if a particular action requires a large amount of work, we might want to spawn a new thread or use some other technique from parallel programming to do the work on a different thread. 

That covers the basic idea of how events cna be handled by our GUIs. In the next video, we'll go through the entire process of handling and event step-by-step. 