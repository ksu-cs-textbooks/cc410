---
title: "Screens"
weight: 10
pre: "2. "
---

{{% youtube jOfzarqaQKM %}}

[Video Materials]({{<relref "./video">}})

Java Swing and Python tkinter are libraries and toolkits for creating Graphical User Interfaces - a user interface that is presented as a combination of interactive graphical and text elements, commonly including buttons, menus, and various flavors of editors and inputs.  GUIs represent a major step forward in usability from earlier programs that were interacted with by typing commands into a text-based terminal (the EPIC software we looked at in the beginning of this textbook is an example of this earlier form of user interface).

The availability of GUIs and the tools used for creating them have changed over the years, especially as the display technologies themselves have evolved. 

### Screen Resolution and Aspect Ratio

No doubt you are used to having a wide variety of screen resolutions available across a plethora of devices.  But this was not always the case.  Computer monitors once came in very specific, standardized resolutions, and only gradually were these replaced by newer, higher-resolution monitors.  The table below summarizes this time, indicating the approximate period each resolution dominated the market.

<table>
  <tr>
    <th>Standard</th>
    <th>Size</th>
    <th>Peak Years</th>
  </tr>
  <tr>
    <td>VGA</td>
    <td>640x480</td>
    <td>1987-1990</td>
  </tr>
  <tr>
    <td>SVGA</td>
    <td>800x600</td>
    <td>1990-2003</td>
  </tr>
  <tr>
    <td>XGA</td>
    <td>1024x768</td>
    <td>2007-2015</td>
  </tr>
</table>

Many of these libraries were introduced in the early 2000s, at a time where the most popular screen resolution in the United States was transitioning from SVGA to XGA, and screen resolutions (especially for business computers running Windows) had remained remarkably consistent for long periods.  Moreover, these resolutions were all using the 4:3 aspect ratio (the ratio of width to height of the screen). Contrast that with trends since that time:

![Screen Resolutions in US from 2009-2020](/images/9/sizes.png)[^1]

[^1]: https://gs.statcounter.com/screen-resolution-stats

There is no longer a clearly dominating resolution, nor even an aspect ratio! Thus, it has become increasingly important for applications to adapt to different screen resolutions. Altering these values in response to different screen resolution requires significant calculations to resize and reposition the elements, and the code to perform these calculations must be written by the programmer. To deal with this, many graphics libraries added additional features and methods for laying out controls on the screen, automatically positioning them much like a web browser will lay out content on a webpage to fit the screen. With careful design, the need for writing code to position and size elements is eliminated, and the resulting GUIs adapt well to the wide range of available screen sizes.

For more information, check out the [History of the Graphical User Interface](https://en.wikipedia.org/wiki/History_of_the_graphical_user_interface) article on Wikipedia for a deep dive into this topic!

### Customizable Styling and Template System

Many modern graphics libraries also leverage controls built around graphical representations provided directly by the hosting operating system.  This helped keep applications looking and feeling like the operating system they were deployed on, but limits the customizability of the controls.  A commonly attempted feature - placing an image on a button - can become an onerous task within some systems.  Attempting to customize controls often required the programmer to take over the rendering work entirely, providing the commands to render the raw shapes of the control directly onto the control's canvas.  Unsurprisingly, an entire secondary market for pre-developed custom controls emerged to help counter this issue.

In addition, many graphics libraries include the ability to "skin" or change the overall look and feel of the entire user interface quickly. We won't get too far into the design aspects of a good GUI in this course, but students are welcome to play around with the tools they find and see what works best for them.
