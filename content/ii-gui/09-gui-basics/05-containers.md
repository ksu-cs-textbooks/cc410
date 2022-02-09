---
title: "Containers"
weight: 25
pre: "5. "
---

To begin building our own GUIs, let's start at the top and work our way down into the details of each individual element that our applications include. At the top of that list is the window.

## Window

A **window** is the top most level of the user interface for most programs. Basically, the GUI for each application is contained within one or more windows, that are then displayed on the screen and managed by the operating system. Each time we open an application, a new window appears that contains the application.

We see windows all the time when we work with modern computer interfaces. The [window metaphor](https://en.wikipedia.org/wiki/Windowing_system) is the most dominant interface metaphor in use today, used by nearly all operating systems designed for personal computers. 

![Window Metaphor](/images/9/window.png)[^1]

[^1]: https://commons.wikimedia.org/w/index.php?title=File:Window_(windowing_system).svg&oldid=518575036

Most windowing systems use a design similar to the one shown above, containing many common elements such as a title bar, menu bar, scroll bars, and more. In fact, look at the web browser you are most likely using to read this content - how many of those elements are present in your browser? Some of them may be there, but others may have been removed or hidden over time. 

If you are familiar with web development, you can think of the overall window as the `<body>` tag in a web page. It is the container that displays all of the content to the user. 

## Panel

Inside of the window itself is a global container that contains all of the elements of our GUI. We typically call this container a **panel**, but it can also be called a **pane** or a **frame**, depending on the GUI toolkit we are using. 

A panel typically doesn't appear on the GUI itself, but it is simply a container or grouping of other display elements. The panel may use a **layout manager** to determine how the elements are arranged within its space, or the elements can be placed statically using **x-y coordinates**. 

In web development, we might think of a panel like a `<div>` tag. The `<div>` tag itself doesn't appear on the screen, but it can be used to group similar items together, arrange them within the container, and then the container itself can be placed within a larger container on the screen.

