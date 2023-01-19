---
title: "Summary"
weight: 40
pre: "8. "
---

In this chapter, we learned about **event-driven programming** and how to configure our GUI-based programs to respond to actions taken by the user. 

When the user interacts with our GUI, an **event** is created by the operating system and placed in the **event queue**. Then, our program uses an **event loop** to check the queue for incoming events, and respond to them. When an event is found, our program determines if that event has been **bound** to a particular **event handler**, also known as a **listener** or **callback**. If so, it calls the appropriate function handle that event.

The **event loop** is typically run in a separate thread in our program, and we must make sure that any operations performed on that thread are quick enough to prevent any lag in our GUI. 

In the example project for this chapter, we'll explore how to add some event handlers to our GUIs. 

## Review Quiz

Check your understanding of the new content introduced in this chapter below - this quiz is not graded and you can retake it as many times as you want.

{{< quizdown >}}

---
primaryColor: '#512888'
secondaryColor: '#cccccc'
textColor: black
shuffleQuestions: true
shuffleAnswers: true
locale: en
---

# Event-driven Programming

The **event-driven programming** paradigm is best described by which statement?

1. [X] A program's execution order is determined by events
1. [ ] A program's execution follows linearly through the code
1. [ ] A program is constructed of logical rules converting inputs to outputs
1. [ ] A program is constructed of smaller parts like conditionals and iterative structures

# Event Handler

In event-driven programming, what is the purpose of an **event handler**? 

1. [X] Receives incoming events and determines which action to perform
1. [ ] Prevents the user from generating events until the current one is finished
1. [ ] Automatically generates events corresponding to GUI elements
1. [ ] Tells the operating system which events to generate

# Event Loop

Many event-driven programs use an **event loop**, which is responsible for what task?

1. [X] Continually checking for new events to be processed
1. [ ] Making sure the program has not hit deadlock
1. [ ] Sending a heartbeat message to the operating system
1. [ ] Executing the same event repeatedly

# Connecting

The act of connecting an event in the GUI to an event handler is known by what term?

1. [X] Binding
1. [ ] Linking
1. [ ] Attaching
1. [ ] Glueing

# Events

When a user interacts with a button on a GUI, what is the most likely event that will be generated?

1. [X] `Clicked`
1. [ ] `Resize`
1. [ ] `Key Released`
1. [ ] `Get Focus`

# Java Handlers

In Java Swing, we typically refer to event handlers by what name?

1. [X] Listeners
1. [ ] Callbacks
1. [ ] Integrators
1. [ ] Executors

# Python Handlers

In Python tkinter, we typically refer to event handlers by what name?

1. [ ] Listeners
1. [X] Callbacks
1. [ ] Integrators
1. [ ] Executors

# Event Queue

An **event queue** in event-driven programming is used for what purpose?

1. [X] To store events as they are generated until they can be handled
1. [ ] To keep track of any possible events supported by the GUI
1. [ ] To maintain a list of events that have been handled
1. [ ] To remember what the program was doing when an event is generated.

# Short Events

In the text, what reason is given for making sure that event handlers are short and execute quickly?

1. [X] The GUI screen cannot update while an event handler is running
1. [ ] Event handlers consume a large amount of memory
1. [ ] Event handlers must complete within 1/60th of a second or they will be terminated
1. [ ] The program might crash while waiting on input from the user

# Starting a Program

Both Java Swing and Python tkinter have a special way to start a GUI based program, which involves performing what task in our code?

1. [X] Starting the event loop
1. [ ] Clearing the screen
1. [ ] Registering the user
1. [ ] Handling the `Program Start` event

{{< /quizdown >}}