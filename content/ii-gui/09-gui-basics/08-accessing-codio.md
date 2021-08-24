---
title: "Accessing GUI in Codio"
weight: 40
pre: "8. "
---

Before we can learn to write our own GUI programs, we should discuss exactly how to access a graphical program in Codio. Thankfully, there is an easy way to do this, but let's look at the technology behind the scenes that makes this possible.

## X Window System

The **X Window System** (sometimes referred to as **X11** or simply **X**) is a windowing system that is used on many Linux-based operating systems, including the Ubuntu system that Codio uses in the background. X handles drawing windows on the screen and passing user input back to the application, but that's about it. Most of the look and feel of the application is handled by the application itself, though different window managers bundled with various operating systems can also provide various themes for applications that are rendered using X.

![X Client Server](/cc410/images/9/x_example.svg)[^1]

[^1]: https://commons.wikimedia.org/w/index.php?title=File:X_client_server_example.svg&oldid=485453207

One of the very powerful features of X is the ability to display graphical programs on a remote system across the network. In this way, programs can be launched on one system and then viewed remotely on another system, providing a rudimentary remote interface similar to Remote Desktop or VNC tools today.

Codio uses this technology to display a graphical program directly in the Codio interface. So, all we have to do is open the Codio X viewer when we run our application, and it will display the output for us. The details for how to do this are covered in the [Codio Documentation](https://docs.codio.com/project/ide/boxes/#gui-based-output)

There are a few ways to do this:

1. At the top of the Codio interface, there is a **Preview** menu that lists several options (it's between the Run menu and the Debugger). There may be options already configured in there for **Box URL** or **Viewer** - in that case, you can click those options to open the viewer.
2. If the option is not present in the Preview menu, you can add it by adding `"Viewer": "https://{{domain3000}}/"` to the `.codio` file present in the root of the project. Here's an example of what it might look like:

```js
{
// Configure your Run and Preview buttons here.

// Run button configuration
  // other data here

// Preview button configuration
  "preview": {
        "Viewer": "https://{{domain3000}}/"
  }
}
```

3. You can load the viewer in any other browser tab using the url `https://box-name-3000.codio.io/`, where you replace `box-name` with the two word domain name. It can be found in the **Project** menu under **Box Info**. It also appears on the terminal:

![Box Name](/cc410/images/9/boxname.png)

In this case, the box name is `field-memo`. Once you load the viewer, you should see a window similar to this:

![Viewer](/cc410/images/9/viewer.png)

Then, when you launch any program that has a GUI, it will appear in this window. 

On the next pages, we'll discuss a simple "Hello World" style program for both Java Swing and Python tkinter. As always, you are welcome to just read the pages that correspond to your chosen language, but it may be beneficial to see both languages to learn a bit more how each of them work in different ways.
