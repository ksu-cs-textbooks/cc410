---
title: "Event Handlers"
weight: 20
pre: "4. "
---
At its core, an **event handler** is simply a piece of code that is called when a particular event happens within the GUI. The function typically receives additional information about the event, such as the source of the event and any relevant details. In some languages, we also refer to event handlers as **callbacks**.

## Java Listeners

In Java, most events are handled by special interfaces called "listeners" that we can implement within our code. When we bind to an event in Java Swing, we specify an object that is instantiated from a class that implements the appropriate listener for that event. Then, when the event happens, behind the scenes Java will find the associated object and call the correct method defined as part of the interface. Here's the example from the previous page:

```java
// ----------------------------------------------
// These functions are the **event handlers**
// This is when the mouse is moved but not clicked
public void mouseMoved(MouseEvent e) {
    this.output("Mouse Moved", e);
}

// This is when the mouse is moved while being clicked
public void mouseDragged(MouseEvent e) {
    // this.output("Mouse Dragged", e);
}
// ----------------------------------------------
```

These two methods are defined in the [MouseMotionListener](https://docs.oracle.com/javase/8/docs/api/java/awt/event/MouseMotionListener.html) interface. When the event happens, it sends along an instance of the [MouseEvent](https://docs.oracle.com/javase/8/docs/api/java/awt/event/MouseEvent.html) class that contains the information about the event, such as the location of the mouse and any buttons that are pressed. 

## Python Callbacks

In Python, events are typically sent directly to a function that is sometimes referred to as a "callback" function. So, when we bind to an event in Python tkinter, we simply specify the function that'd like to be called when the event happens. If we want to capture some additional data along with the function, we can do that using a lambda expression, which we saw in the earlier GUI example project.

Here's the example callback function from the previous page:

```python
def action_performed(self, event) -> None:
    """Event handler for GUI events."""
    print("Mouse Moved : {},{}".format(event.x, event.y))
```

When the `'<Motion>'` event occurs, Python will call this function and pass along a second parameter, which we've named `event` in this example. The `event` object contains the `x` and `y` coordinates of the mouse, but may also contain different information based on the event that was generated. Unfortunately, there isn't a good source of documentation for all of these events and what information they contain, so you may have to do a bit of digging to figure out what you can expect from each type of event. 

