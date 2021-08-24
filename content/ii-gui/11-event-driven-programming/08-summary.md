---
title: "Summary"
weight: 40
pre: "8. "
---

In this chapter, we learned about **event-driven programming** and how to configure our GUI-based programs to respond to actions taken by the user. 

When the user interacts with our GUI, an **event** is created by the operating system and placed in the **event queue**. Then, our program uses an **event loop** to check the queue for incoming events, and respond to them. When an event is found, our program determines if that event has been **bound** to a particular **event handler**, also known as a **listener** or **callback**. If so, it calls the appropriate function handle that event.

The **event loop** is typically run in a separate thread in our program, and we must make sure that any operations performed on that thread are quick enough to prevent any lag in our GUI. 

In the example project for this chapter, we'll explore how to add some event handlers to our GUIs. 
