---
title: "Java Swing"
pre: "4.J. "
weight: 40
date: 2020-02-08T00:53:26-05:00
hidden: true
---

{{< youtube hVQuB2upXqQ >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

In this video, we'll learn how to create our first GUI using the Java Swing GUI toolkit.

First, a bit about Swing. Java Swing was developed in the late 1990s as a replacement and upgrade to the existing Abstract Window Toolkit, or AWT, which at the time was the standard way to create graphical user interfaces in Java. Swing improved on AWT by adding several new elements, and allowing the elements to change their look and feel to match the underlying operating system or a variety of themes. In addition, Java Swing is built in an object-oriented way, so we can easily extend existing elements to create our own versions. Finally, just like Java, Swing is meant to be cross-platform, allowing us to create a single GUI that will work on many different operating systems.

So, let's go through building our first GUI using Swing. To start, we need to import a few libraries. I've just listed the main library packages here using a wildcard import, which is a quick and easy way to build our GUIs. However, to pass the Java checkstyle linter using the Google style guide, you'll have to replace these with explicit imports for each class used in the GUI. I'll leave that as an exercise for you to do as part of the example project and milestone in this module.

Next, we're going to create a class that contains three things - a constructor, a method for handling actions performed by the user, and a main method to load our application. At the top, notice that our class is inheriting from the `JFrame` class, which is the default panel element in Java Swing. We're also implementing the `ActionPerformed` interface, which allows this class to listen for and receive actions from our GUI as the user interacts with it. We'll discuss that in just a bit.

First, let's look at the constructor, which is used to create and lay out the GUI within this frame. At the beginning, I'm setting the size of this window to be 200 pixels by 100 pixels, which is pretty small but works well for this simple application. Next, I'm setting the default close operation to exit our application. By doing so, when our user clicks the close button at the top right of the window, the application will terminate. Without this line, it is possible for the user to close this window but the application itself will keep running in the background, which can be useful in some instances but not for this sample application. Finally, we're going to set the layout manager to be a `GridBagLayout`, which is one of the more flexible and easy to use layout managers available for Java Swing. As part of that, we need to create an instance of the `GridBagConstraints` class, which we will use to further customize the layout of each element on the screen.

Java's `GridBagLayout` manager allows us to create GUIs based on a grid system, as shown here.

This image includes the row and column grid that is used to align controls on the application. In this case, it uses three rows and three columns. We can also see that controls can span across multiple rows and columns, depending on how we'd like them to work.

In addition, as we resize the window, we can have the controls automatically resize themselves to fit the larger space, based on options we configure in the `GridBagConstraints` object assigned to each element. 

Now, let's add a label to the screen. This is pretty simple. First, we'll configure the `GridBagConstraints` object to set the element on the 0th row and 0th column, and we'll allow it to expand in the horizontal direction to fill the space available. This will, in effect, center the label horizontally in the space. Then, we use the `add()` method that is part of our `JFrame` class to add a new `JLabel` element to the frame, using the `GridBagConstraints` object as the second parameter to the `add()` method. 

Adding a button is similar, but there are a couple of extra steps. As before, we'll configure the `GridBagConstraints` to place this button on the 1st row of the 0th column, and it will still be allowed to fill the horizontal space as configured previously. Then, we create a new instance of the `JButton` class to represent our button itself. Once the button is created, we set the action command associated with the button, which allows us to easily identify the button later on when it is clicked, and we also configure the button to use the current instance of our `MainWindow` class as its action listener. This basically tells Java that, whenever this button is clicked, it should call the `actionPerformed()` method in this class to handle that event. Finally, we use the `add()` method once again to add the button to the GUI.

With all of that code in place, we'll end up with a GUI that looks something like this. It includes the label on the 0th row, and a close button below that one the first row. 

So, how can we tell our application to do something when the button is clicked? For that, we must look at the `actionPerformed()` method. This method is defined in the `ActionListener` interface that we are implementing, so we must provide an implementation of that method in our class. This method is called whenever an element on the GUI that uses this class as it's action listener is interacted with, and it sends along an `ActionEvent` object that helps us determine what event happened. In this case, we can examine the action command associated with the event. If it is the "close" command we configured earlier on our button, then we can tell the application to terminate using the `System.exit()` method. As we add more buttons to our GUI, we can make sure that each one uses a different action command, and then add additional if statements to this method to handle each one.

Finally, let's look at the code used to launch this application in the main method. This code is a bit complex, but is listed in the Java Swing documentation as the recommended way to launch an application written in Java Swing. In effect, we are scheduling a thread using the `SwingUtilities.invokeLater()` method, and providing it a new instance of an anonymous class that implements the `Runnable` interface. In that anonymous class, we provide an implementation of the `run()` method, which creates a new instance of our `MainWindow` class and sets it to be visible once it has been constructed. It looks complex, but basically we are telling Java to create an instance of our `MainWindow` and make it appear, but to do it in a different thread. We'll discuss threads and why this is important in a later chapter in this course.

There we go! We've written our first GUI in Java Swing. In the example project for this module, we'll build upon this simple application to build parts of a GUI that will be very useful as we continue to work on our larger project in this course. 