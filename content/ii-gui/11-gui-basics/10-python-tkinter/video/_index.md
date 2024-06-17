---
title: "Python tkinter"
pre: "4.P. "
weight: 45
date: 2020-02-08T00:53:26-05:00
hidden: true
---

{{< youtube Xfb2VJ2dswM   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

In this video, we'll learn how to create our first GUI using the Python tkinter GUI toolkit.

First, a bit about tkinter. Python's tkinter library is a warpper around the Tk GUI framework, which was first developed in the early 1990s. Tk, like many other GUI frameworks, allows the elements to change their look and feel to match the underlying operating system or a variety of themes. In addition, tkinter is built in an object-oriented way, so we can easily extend existing elements to create our own versions. Finally, just like Python, tkinter is meant to be cross-platform, allowing us to create a single GUI that will work on many different operating systems.

So, let's go through building our first GUI using tkinter. To start, we need to import a few libraries. I've just listed the main library packages here using a package import, which works in most cases. If we want to use some of the newer elements, we may also have to import the ttk, or "Themed Tk" package as well. 

Next, we're going to create a class that contains three things - a constructor, a method for handling actions performed by the user, and a main method to load our application. At the top, notice that our class is inheriting from the `tk.Tk` class, which is the topmost container element in Tk that represents a window. 

First, let's look at the constructor, which is used to create and lay out the GUI within this frame. At the start, we need to initialize the parent `Tk` object, which can be done by calling it's `__init__()` method. Then, I'm setting the size of this window to be 200 pixels by 100 pixels, which is pretty small but works well for this simple application. Finally, I'm setting a few options that control how the grid geometry manager in tkinter will resize each row and column in our application. 

tkinter's grid geometry manager allows us to create GUIs based on a grid system, as shown here.

One of the powerful features of the grid system is the ability to attach the element in each cell to one or more sides of the cell suing the `sticky` option, allowing it to grow and shrink along with the rest of the application. If we don't do that, each element will just be centered within the cell. For this sample application, we'll just leave it like that. 

However, as we saw, each row or column can be given a `weight` attribute, which controls how the elements will behave when resized. If the columns and rows are all given a weight of 0, they will not grow at all, as shown here. 

If each column has the same weight, then they will grow and shrink at the same rate. Otherwise, the ratio of the weights will be used - for example, a column with weight 2 will grow twice as quickly as a column with weight 1. In this example, the column on the left has a larger weight than the column on the right, so it expanded more quickly as the window grew in size. Pretty nifty!

Now, let's add a label to the screen. This is pretty simple. First, we'll construct a new label, and set it's master attribute to be the instance of the `tk` window that we are configuring. The `master` argument tells the element which panel it should be contained within. We can also set the text of the label. Finally, we use the `grid()` method to attach it to the panel, providing the desired row and column as arguments. 

Adding a button is similar, but there are a couple of extra steps. As before, we'll set the `master` argument to `self`, attaching it to this window, and set the text displayed on the button. We'll also set the `command` argument, which tells Python what to do when this button is clicked. Here, we are using a lambda expression, which simply calls the `action_performed()` method within this object with a parameter of "close", which we can use to determine which button was clicked. Once we've configured the button, we can use the `grid()` method to attach it to our panel in the desired location.

With all of that code in place, we'll end up with a GUI that looks something like this. It includes the label on the 0th row, and a close button below that one the first row. 

So, how can we tell our application to do something when the button is clicked? For that, we must look at the `action_performed()` method. This is the method that we used in the lambda expression provided as the `command` argument when we created a button. We can use any function or lambda expression there, but I chose to use this model as it most closely matches how other GUI frameworks, such as Java Swing, handle events. So, when the `action_performed()` method is called, our lambda expression also provides the argument "close". So, in our code, we can simply check the value of the argument against the possible actions our GUI can perform. If it is the "close" argument we configured earlier on our button, then we can tell the application to terminate using the `sys.exit()` method. As we add more buttons to our GUI, we can make sure that each one uses a argument, and then add additional if statements to this method to handle each one.

Finally, let's look at the code used to launch this application in the main method. This code is pretty simple - all we do is construct a new instance of our `MainWindow` class, and then call the `mainloop()` function to start listening for events. However, it is important to note that this function call will not return until we close the window, so we are essentially blocked from doing anything else here. As another option, we could create additional threads before we launch our GUI, and use those threads to perform other actions while the GUI is running. We'll discuss threads and why this is important in a later chapter in this course.

There we go! We've written our first GUI in Python tkinter. In the example project for this module, we'll build upon this simple application to build parts of a GUI that will be very useful as we continue to work on our larger project in this course. 
