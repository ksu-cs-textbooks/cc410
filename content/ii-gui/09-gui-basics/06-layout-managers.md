---
title: "Layout Managers"
weight: 30
pre: "6. "
---

Many different GUI elements can be placed within a frame. For more complex GUIs, there might be dozens of these elements, and each one will need to be positioned on the screen in such a way that the GUI is usable. In addition, if we want to build our GUI for multiple different window sizes and screen resolutions, we might need a way to automatically adjust the size and position of these elements within the frame to fit our screen. All of that can be very tedious and time consuming to do by hand. So, many GUI toolkits include special software called **layout managers** to help us with that task. Some tools, such as Tk, also refer to these as **geometry managers**.

## Layout Manager

A layout manager, put simply, is a piece of code that can automatically resize and position elements within a panel in a GUI. Web browsers make extensive use of layout managers to enable resizing of web pages. Try it yourself - see if you can resize this page, and then watch how the web browser and Codio interface adjust to fit the new screen size. How small of a screen can it handle? 

### Java Swing

As an example, the Java Swing toolkit includes several different layout managers, and each one can be used to achieve different outcomes. The best resource is [A Visual Guide to Layout Managers](https://docs.oracle.com/javase/tutorial/uiswing/layout/visual.html) on the Oracle website, as it shows graphically how each layout manager available in Java Swing operates. 

![Border Layout](/cc410/images/9/border.png)[^1]

[^1]: https://docs.oracle.com/javase/tutorial/uiswing/layout/visual.html

For example, the `BorderLayout` will attach controls to the borders of the screen, growing and shrinking them as the window is resized. 

![Grid Layout](/cc410/images/9/grid.png)[^1]

The `GridLayout` will arrange controls in a grid of rows and columns. 

### Python tkinter

The Python tkinter library includes three layout managers, `place`, `pack`, and `grid`. 

![Place Layout](/cc410/images/9/place.png)[^2]

[^2]: https://zetcode.com/tkinter/layout/

The `place` layout manager can be used to place elements on the screen at specific x-y coordinates. 

![Pack Layout](/cc410/images/9/pack.png)[^2]

The `pack` layout manager is used to fit controls to the screen, expanding them in various directions as needed to fill the available space.

![Grid Layout](/cc410/images/9/gridpy.png)[^2]

Finally, the `grid` layout manager works very similar to the `GridLayout` manager in Java, allowing us to create rows and columns of elements on our screen.

As we develop our GUIs, we'll be able to choose the layout manager we'd like to use. In the example project for this chapter, we'll explore how to use these layout managers to create a simple interface that contains a set of buttons and a few other elements.

#### References

* [A Visual Guide to Layout Managers](https://docs.oracle.com/javase/tutorial/uiswing/layout/visual.html) from Oracle
