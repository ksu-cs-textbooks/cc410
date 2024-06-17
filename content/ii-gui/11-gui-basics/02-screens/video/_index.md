---
title: "Introduction"
pre: "1. "
weight: 10
date: 2020-02-08T00:53:26-05:00
hidden: true
---

{{< youtube jOfzarqaQKM   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

In this chapter, we're going to look at how we can create graphical user interfaces, or GUIs, for our programs. Thankfully, the technology and frameworks we have available today have greatly simplified this process, but it is still worth looking back at some historical information first, just to get a sense of how things have changed over the years. For example, this slide shows the various standard screen resolutions that have been used on computer systems over the years. In the textbook, we discuss how resolutions such as VGA, or 640 by 480 pixels, were popular in the late 1980s, up through XGA, or 1024 by 768 pixels, which was dominant up through the start of the 2010s. Today, there are a wide variety of resolutions that are commonly used, but it is also very common for users to no longer just use applications in "full screen" mode, so our applications really could be expected to work for a variety of screen sizes. 

Thankfully, much of this work can be offloaded to a GUI framework. A GUI framework is a code library that can interface directly with the operating system on our computer, and it handles all of the work to create and display windows on the screen. In addition, GUI frameworks include a number of common GUI elements, such as text boxes, checkboxes, and buttons, giving our programs the same basic interactivity that users are already familiar with. They also allow us to use a standardized look and feel across our applications, and in many cases we can make our application's look and feel match the one of the underlying operating system. Many of these frameworks are cross platform, allowing us to develop our applications once and use them on a variety of different operating systems. In addition, they make creating and modifying our GUIs quick and easy, and many of the more modern frameworks are built in an object-oriented style, making it easy for us to create our own custom elements quickly and reuse them throughout our code.

In this course, we'll look at two different frameworks, one for each language. In Java, we'll use the Java Swing framework, which has been a part of the Java programming language since the late 1990s. This screen shows a sample window that was developed using Java Swing with its default look and feel, which is available on multiple platforms. 

For Python, we'll use the tkinter library, which is a Python wrapper around the very popular Tk GUI toolkit. This is a Windows application written using Tk, and it was configured to use a Windows-like look and feel, so it looks almost like a native Windows application itself. Like Java Swing, Tk is available on multiple platforms, so we can use it on nearly any system that runs Python.

