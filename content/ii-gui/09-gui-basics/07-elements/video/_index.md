---
title: "Elements"
pre: "3. "
weight: 30
date: 2020-02-08T00:53:26-05:00
hidden: true
---

{{< youtube GTkJYwpw4vQ >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

Now let's look at the various common elements that we can use to build our graphical user interfaces for our application. This window show some of the most common elements used in GUIs today, but of course there are others we can choose from that are built into our GUI frameworks, and we can also create our own elements as well. In this diagram, we see many different items annotated, most of which we will discuss separately on later slides in this video. I do want to call your attention to the first few callouts at the top of the graphic. We see the overall window itself, which is created by the GUI toolkit by interacting with the host operating system that our application is running on. Within the window, we can set the window title at the top of the screen, and then we also see the window's content area, usually represented as a panel in our framework, where we can actually place our content. In most cases, we cannot configure much of the window itself outside of the content area beyond setting the window's title. The rest is left to the operating system itself.

So, within our window, we always have a default container, which is usually an instance of the panel element for the GUI framework we are using. Within that panel itself, we can add elements, including other panels as shown here. A panel is just a default container that can store other elements, but it's also important to remember that layout managers are typically attached to individual panels within our GUI. So, a GUI that contains two internal panels as shown here could end up using 3 different layout managers, one for the window's content panel, and two more for each nested panel.

Now that we've covered containers, let's look at the other elements we can use in our GUI. First is the label element, which is simply a piece of text we'd like to display on our GUI, but one that shouldn't be editable or interactable by the user. In this example, we have a few different labels, each one showing a piece of information to the user. Of course, we can change the text that a label displays within our code itself, so it isn't unchangeable, it is just not meant to be edited by the end user of our software. 

To allow users to enter or edit text in our application, we have a couple of options - the single line text input, sometimes called the text box, and a multi line text input, sometimes called the text area. These two elements allow users to work with text in our GUIs, and with a bit of extra coding we can add features such as spell checking and autocomplete to most of these text input elements.

Another major part of any GUI are the buttons. A button is simply an element that the user can interact with, usually by clicking or touching it, that will cause our application to perform an action. This could be saving a file, loading data, or switching the GUI to a different screen. Here, we see simple buttons, as well as button bars and a special type of button called a toggle button, which can represent two states, similar to the checkbox.

A checkbox is another simple element, which is used to represent Boolean values. So, each checkbox typically only has two states - on, when the box is checked, which usually represents true, and off when the box is unchecked, representing false. In some GUI frameworks, checkboxes can also represent a 3rd state by shading in the box, usually meant to represent some undefined or mixed state. This is usually done when checkboxes are combined with a tree structure in the application.

Another element is the radio button and radio button group. A radio button looks similar to at checkbox, but it is typically round instead of square. Within a radio button group, only one of the buttons can be selected, similar to the old style analog radios from many decades ago. Radio buttons are useful when your user must clearly select just one of a very short and static list of options. One important thing to notice here is the use of subtle, consistent design cues throughout most modern computer interfaces. If we are familiar with computers, we have learned that square boxes are checkboxes, whereas these round one are radio buttons, and even if we didn't know their names, we probably understood how to use them. This is the power that comes from using these standard GUI elements - by providing a consistent experience across applications, and even across operating systems, we can make computers easier for our users to interact with and understand. Basically, we should always focus on using elements our users would already be familiar with if we can.

The next element is the list box, which is simply a list of items that the user can select. We can even configure out list box to allow the user to select one element, multiple sequential elements, or even multiple non-sequential elements. On a computer, we typically use the SHIFT and CTRL keys for this, but there are ways to do this with a touch interface or by adding checkboxes to the elements in the list. Once those items are selected, we typically include one or more buttons that the user can use to interact with that selection. In fact, you are probably used to using list boxes all the time, even if you didn't realize it. Most operating systems today include a file browser that is based on the list box element, including our Codio IDE.

The last element we'll cover in this video is the combo box, which is just a combination of a text input field and a list box. To select an item, users can click the drop-down arrow to open the list, and choose an item from the list. They can also usually type in the box to search for an item, and the field can even be configured to accept typed input that is not in the list. Combo boxes are really great when the list of items that the user can select from is large, or needs to be programmatically generated from a list that can change over time. This is in contrast to a radio button group, which is better suited to a short list of options that doesn't change.

Put all together, we can build a pretty cool GUI for our program out of just these few simple elements. In the next videos, we'll go through the process of creating a quick "Hello World" GUI in both Java Swing and Python tkinter.