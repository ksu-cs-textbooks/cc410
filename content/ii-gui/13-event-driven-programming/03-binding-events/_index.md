---
title: "Binding Events"
weight: 15
pre: "3. "
---

{{< youtube ze031YvdTr8  >}}

[Video Materials]({{% relref "./video" %}})

The first step in building a program using event-driven programming is actually creating the events that you'd like to respond to. For a GUI-based program, this is actually handled by the GUI framework itself. It includes a large number of events that are already available for us to use. Instead, we have to **bind** those events to special functions, called **event handlers**, within our code. Then, when those events occur, the GUI framework will call the **event handler** associated with that event.

## GUI Events

Most GUI frameworks include a large number of events that we can bind our event handlers to. There are some obvious ones, such as the **clicked** event for a button, or the **value changed** event for checkboxes, but there are actually many events that are generated by our GUI that we might not have thought of. Here are just a few events we can typically find in our GUI framework:

* **Mouse Moved** - happens whenever the cursor is moved across our window. We can typically find the `x` and `y` coordinates of the cursor at any time through this event.
* **Key Pressed** - happens whenever a key is depressed on the keyboard. This could also include the buttons on the mouse, though many times they are listed as separate events.
* **Key Released** - happens whenever a key is released on the keyboard. By tracking both when keys are pressed and released, we can react differently if they user presses and holds a button like one would when playing a game, vs. individual presses used to type text in a text entry field.
* **Text Changed** - happens anytime the text in a text entry field is edited
* **Get Focus / Enter** - happens when the user selects a particular element in the GUI. That element is said to be in **focus** at that point. This is usually helpful when working with forms that have multiple text entry elements. 
* **Lose Focus / Leave** - happens when the user's selection moves to a different element in the GUI. The element left is said to have **lost focus** at that point. 
* **Resize** - happens whenever the window or an individual GUI element is resized. Many times this event is handled by our layout manager, but we can also bind our own functions to it as well.

Each GUI framework can handle many different events. You can find a list of some of them at the following resources:

* [java.swing.event](https://docs.oracle.com/javase/8/docs/api/javax/swing/event/package-summary.html) Package
* [Event Handling](https://tkdocs.com/tutorial/concepts.html#events) from Tkdocs

## Binding to Events

Both Java Swing and Python tkinter include simple ways to bind an event to a function. In fact, we've already seen a bit of how to do that in a previous example - we created a few buttons that called a function when clicked! That is a great example of binding the **clicked** event to a function in our code.

Here's a more general example in both Java and Python, this time binding the **mouse moved** event:

{{< tabs >}}

{{% tab title="Java" %}}

_Excerpted in part from [How to Write a Mouse-Motion Listener](https://docs.oracle.com/javase/tutorial/uiswing/events/mousemotionlistener.html) from Oracle._

```java
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class MouseDemo extends JFrame implements MouseMotionListener {

    public MouseDemo() {
        this.setMinimumSize(new Dimension(800, 600));
        // ------------------------------
        // This is the **bind** action
        this.addMouseMotionListener(this);
        // ------------------------------
    }
    
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
    
    private void output(String event, MouseEvent e) {
        System.out.println(event + " : " + e.getX() + "," + e.getY());
    }
    
    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                new MouseDemo().setVisible(true);
            }
        });
    }
}
```

{{% /tab %}}

{{% tab title="Python" %}}
```python
import sys
import tkinter as tk
from typing import List


class MouseDemo(tk.Tk):

    def __init__(self) -> None:
        """Initializer for GUI."""
        tk.Tk.__init__(self)
        self.minsize(width=800, height=600)
        # --------------------------------
        # This is the **bind** action
        self.bind('<Motion>', motion)
        # --------------------------------

    def action_performed(self, event) -> None:
        """Event handler for GUI events."""
        print("Mouse Moved : {},{}".format(event.x, event.y))

    @staticmethod
    def main(args: List[str]) -> None:
        """Main method."""
        MouseDemo().mainloop()


# Main Guard
if __name__ == "__main__":
    MouseDemo.main(sys.argv)
```

{{% /tab %}}

{{< /tabs >}}

In both of these examples, we see how to bind an event to a function. In Java Swing, we need to add a specific type of "listener" to the object, which is an event handler in Java Swing terminology. We then implement the associated interface, which defines the function(s) we must include to react to those events. In this case, we implement the `MouseMotionListener` interface. 

In Python tkinter, we literally use a method called `bind` along with the name of the event we'd like to bind and the function we'd like to call. This is much more straightforward, but we don't have the benefit of a compiler and type checker making sure that our events are bound correctly, nor that we'll get the correct data out of them. So, we have to be a bit more careful as well.

On the next page, we'll go a bit deeper into **event handlers**, the functions that are called when the events occur. 
