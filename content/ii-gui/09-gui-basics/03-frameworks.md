---
title: "Frameworks"
weight: 15
pre: "3. "
---

There are many different graphics frameworks available today. Some are limited to a specific language, such as [Java Swing](https://docs.oracle.com/javase/tutorial/uiswing/), whereas others are cross platform, such as the [tkinter](https://docs.python.org/3/library/tkinter.html) library in Python which is based on the [Tk GUI framework](https://www.tcl.tk/). Finally, others are limited to particular operating systems, such as the [Windows Presentation Framework](https://docs.microsoft.com/en-us/dotnet/desktop/wpf/introduction-to-wpf?view=netframeworkdesktop-4.8). Let's review the two frameworks we'll be using: Java Swing and Python tkinter.

## Java Swing

![Java Swing](/cc410/images/9/swing.png)[^1]

[^1]: https://commons.wikimedia.org/w/index.php?title=File:Gui-widgets.png&oldid=458387263

Swing is a graphical user interface toolkit for Java that was originally created in 1996 by Netscape, but it was later integrated into the core of Java in 1997. It was meant to be an upgrade to the existing [Abstract Window Toolkit](https://en.wikipedia.org/wiki/Abstract_Window_Toolkit) that was used to create graphical programs in Java at the time, though even today we still use some classes from the `awt` package along with the newer `swing` components.

One major benefit of Java Swing is the ability to quickly change the "look and feel" of the application using various different components. In addition, it is cross platform, and applications displayed on Windows will look nearly identical to those displayed on Linux or Mac as well. 

In addition, developers can easily customize many components of the Java Swing toolkit using inheritance. We simply must extend an existing component in Swing, such as the `JFrame` container, and we can provide additional functionality directly in that class. 

## Python tkinter

![Tk](/cc410/images/9/tk.png)[^2]

[^2]: https://commons.wikimedia.org/w/index.php?title=File:Tk-Demo_using_Tk_8.6.6_on_Windows_10,_November_2016.png&oldid=475248301

Python includes a library called `tkinter` (short for "Tk Interface"), which is a wrapper around the [Tk GUI framework](https://www.tcl.tk/). Tk is a cross platform toolkit for building GUIs that was developed in the early 1990s, but is still used today in many different programs. Tk includes a large range of elements, called "widgets," including buttons, text boxes, and more, that can be used to build interactive GUIs.

In more recent versions of Python, a new "themed Tk" style was introduced, allowing Tk widgets to match the look and feel of programs natively built for the operating system. This helps programs written in Tk "fit in" with other applications running on the same operating system. 

Like Java Swing, tkinter allows us to build GUIs by inheriting from the default components such as the `Frame` widget that can act as a container for other widgets. We can even nest `Frame` widgets inside other `Frame` widgets to build more complex layouts. 

On the next few pages, we'll discuss the basic features each of these frameworks has in common, before diving a bit deeper into each one and what makes it unique.

{{% notice info info-1 "Other Frameworks" %}}

There are many other frameworks available for both of these languages, but there are a few specific reasons we chose to focus on Java Swing and Python tkinter. 

In Java, the newer [JavaFX](https://openjfx.io/) platform has been available since the mid 2000's, but unfortunately it is difficult to use Java FX in Codio since we are reliant on the OpenJDK platform instead of the Oracle JDK due to licensing issues and ease of use. In addition, JavaFX is much more oriented toward web applications than other traditional GUI frameworks like Tk. So, to simplify things and keep the two languages in sync, we choose to use the older Java Swing framework. 

For Python, recently many Python developers have been using [PySimpleGUI](https://pysimplegui.readthedocs.io/en/latest/) as a simpler wrapper for the tkinter library. It also is compatible with other GUI frameworks such as Qt and WxPython, and in many cases is easier to use than tkinter itself. Unfortunately, as of this writing we felt that PySimpleGUI wasn't quite mature enough for us to include in this curriculum. So, we chose to continue to use the built-in tkinter library in Python for now.

{{% / notice %}}
