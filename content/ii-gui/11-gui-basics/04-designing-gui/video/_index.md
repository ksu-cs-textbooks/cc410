---
title: "GUI Design"
pre: "2. "
weight: 20
date: 2020-02-08T00:53:26-05:00
hidden: true
---

{{< youtube wqeJO6S5lJE   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

Let's talk a bit about how to design user interfaces in our programs. First and foremost, I want to make it clear that this class is NOT a user interface design class, nor am I a particular expert on good user interface design. Instead, we are mainly focused on learning how to build the interfaces and make them functional, with design left as a extra topic that you are welcome to explore as your time allows. Simply put, we could spend an entire semester just learning all of the intricate ways we can add design and style to modern GUIs, but we really want to focus on the code and functionality behind the scenes as much as possible. When in doubt, try to make your GUIs as simple and straightforward as possible, and learn from your users as they give you feedback. 

So, how do we begin designing a new GUI for a program? As it turns out, the simplest tool is usually the best, and in this case we'll want to draw a sketch of our application. So, I'm going to walk through designing a fictional screen that looks similar to something we might use in one of our projects in this course. 

First, we'll need to start with a window. This is the outermost part of our application, and the Window itself is usually created by the operating system. Inside of that window is where we'll be able to place our content.

For this application, I'm going to use a couple of different panels. The main panel to the left will contain most of the content, but I'm also creating a sidebar to the right that will serve as a persistent area to keep track of a few items. By dividing our application into panels, we can swap out the content stored in these panels without completely redoing the application window itself. 

Once I've built the basic structure of my application, it's time to add the individual elements. In this case, I'm developing a possible point of sale system for a restaurant, so I've added buttons to the main content panel for each item on the menu, and a sidebar that will list the items in the order. This is a very simple GUI, but it helps us get an idea for what it might look like in practice.

Next, we can go through and annotate our sketch, pointing out which types of element we intend to use. We might also add additional information such as the layout that each panel should have. Here, we see that we are creating one button per menu item in the main panel, which will use a grid layout to arrange all of the buttons. In the sidebar, we have some labels, a list box, and a button that keep track of the current order itself. So, now we can start to visualize in our mind what our application will look like and how it will function before we've ever started building it. In fact, it took me probably 15 minutes to develop this prototype, and it is already something I could share with my users to get feedback on how useful they'd find this design, long before I spend any time trying to develop it in code.

Here is a great example of how I can reuse elements of my previous design. In this case, I play to switch to other screens in my application by replacing the content of the leftmost panel with different content, while leaving the sidebar as-is. In this way, we can display different information to the user based on their actions, without ever leaving the main window of our application. Of course, this is just one way we could structure our application, but I believe it makes sense for this particular use.

Finally, we should consider how we'd like the elements in each panel arranged. For that, we'll often rely on a layout manager. A layout manager is a piece of code that handles automatically arranging and resizing elements in our GUI. This helps us avoid lots of repeated code for dealing with screen resolutions and handling instances where the user resizes the screen. Instead of manually creating this code, we can simply tell the layout manager how we'd like the window to be structured, and it will handle making everything fit in place correctly. If you've ever done web development and worked with complex CSS and HTML DIV tags, you're probably familiar with this style of design - instead of defining exactly the position and size of our elements, we instead design the layout in terms of the relative position and sizes of each element, and let the display manager compute the actual values.

Here's a quick example. Let's say we wanted to build this GUI but only use a static layout. That means each of the buttons would be assigned a specific x and y coordinate within the window. It might look really good for a window that is exactly the size we want, but what if the user wishes to resize the window?

In that case, without some complex math to resize each of our elements and reset the coordinates, our GUI would look something like this. Notice how the buttons are located in the same places, but since the window is now larger, our controls have not relocated or resized themselves to fit. This ends up making the application very difficult to use when it is any size other than what the developer originally intended.

Instead, what if we use a grid-based layout manager? In that case, we would assign each button to a particular row and column within the panel as shown here. 

Then, as the GUI grows, the layout manager would automatically resize and relocate the controls to fit the larger space, following the rules defined by the layout manager and configured by the developer. In this way, the application is much more flexible and will look correct when resized to just about any reasonable window size. 

Finally, it is worth noting that we can use panels to create nested layouts, which each one using a different layout manager. For example, consider the application itself. If we set the window's topmost panel to a grid layout, then we can arrange our two internal panels in columns 0 and 1 as shown here. Then, within the panel, we can use a new layout manager to arrange those controls. In that way, we can independently control each part of our application. Again, if you are familiar with web development, some of these ideas will feel very familiar to you. So, as we've seen, we can easily use different GUI frameworks and their built-in layout managers to create and arrange elements within our program's graphical user interface. 

