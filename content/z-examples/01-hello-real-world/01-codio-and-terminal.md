---
title: "Codio and Terminal"
weight: 10
pre: "1. "
---

{{% youtube 1sWLEF_awoM %}}

One thing you'll quickly notice is that the source code files are no longer created for you in this course. Instead, in most cases you'll be responsible for creating the source code files and folders used by your program. 

So, let's cover some basics of using the Codio interface and the terminal. 

## Codio Interface

![File Tree](/images/e1/1file.png)

To the left, you should see the Codio file tree interface. If you don't see it for some reason, you can always show it by going to the **View** menu and selecting **File Tree**. 

This is where you can manipulate files and folders within your project. You can right-click most things in the file tree to get a context menu like the one shown above, which can be used to create, delete, and rename files. You can also drag and drop elements in the file tree to move them between folders. 

The Codio main interface supports panels and tabs, so you can create your own layouts as desired. The standard layout includes having this guide to the right and your code in a single panel to the left, but you may change that layout anytime. You can even minimize or close this guide if you need more space!

Codio has some great documentation for its IDE interface. A few of the more useful pages are linked below:

* [Basic IDE Features](https://docs.codio.com/project/ide/navigation/)
* [Panels and Tabs](https://docs.codio.com/project/ide/panels/)

Feel free to play around with the Codio environment and editor, and find the settings that work best for you.

{{% notice note "Java & Python Folders" %}}

We recommend placing all of your code and contents in either the **`java`** or **`python`** folder, whichever matches the programming language you are using. Those folders are already created for you in most assignments. The assignments in this course are designed to cover both languages, but to keep the files separate we use these folders. This also makes working with tools such as Gradle, Tox and Git much simpler later on.

The example videos will model this behavior. Make sure you pay special attention to the specific locations in the file tree where new contents are placed.

{{% /notice %}}

## Linux Terminal

![Linux Terminal](/images/e1/2terminal.png)

You'll also need to use the Linux terminal from time to time in this course. This is how you can compile and execute your programs, run your tests, and more. Codio includes several ways to open the terminal:

1. Selecting the **Tools** menu, then choosing the **Terminal** option
1. Pressing SHIFT + ALT + T in any Codio window (you can customize this shortcut in your Codio user preferences)
1. Pressing the **Open Terminal** icon in the file tree

For the most part, you'll learn all the commands you need to know by watching the videos we provide in these example assignments. However, this will only scratch the surface of what can be done via the Linux terminal. To learn more about Linux and using the Linux terminal, here are a couple of additional resources you may want to review:

1. Command Line Interface Tutorials from Codio - available in the CC 410 Modules List on Canvas (look at the bottom of the page)
2. [Beginners Guide to the Bash Terminal](https://www.youtube.com/watch?v=oxuRxtrO2Ag) by Joe Collins on YouTube
3. [Ubuntu Terminal](https://cis527.russfeld.me/1-secure-workstations/13-ubuntu-terminal/) from CIS 527 at K-State

### Working with Directories

One important thing to keep in mind when working through the Linux terminal and the Codio interface is the path of the current directory. Many times we will either create or edit files from a certain directory location, or we'll need to make sure the working directory of our Linux terminal matches the example given. 

In any of the videos and screenshots, you can determine the current working directory of the Linux terminal by looking closely at the prompt. It will be shown between the colon `:` and dollar sign `$` characters, as shown in the image below:

![Path Terminal](/images/e1/3path.png)

The path `~/workspace` corresponds to the top level of the Codio file tree. So, the full path `~/workspace/java/directory1/directory2` corresponds to the directory highlighted in the image below: 

![Path Directory](/images/e1/4path.png)

Make sure you watch the videos and read the content closely to get the directories correct! The projects in this course are much more complex than previous courses, and include multiple different folders full of files, sometimes with identical names!

{{% notice info "Directory vs. Folder" %}}

Computer programmers tend to use the terms "directory" and "folder" interchangeably when talking about a file system. Most Linux tools use the term "directory," but many other operating systems refer to them colloquially as "folders" since that is the icon most commonly used to represent them. Rest assured that both generally mean the same thing - a location where other files or directories/folders can be stored in a hierarchical file system.

{{% /notice %}}
That should cover the basics! On the next few pages, we'll dive into creating our new "Hello Real World" project!