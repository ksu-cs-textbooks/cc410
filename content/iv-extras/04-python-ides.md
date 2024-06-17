---
title: "Python IDEs"
pre: "4. "
weight: 20
date: 2022-02-25T00:53:26-05:00
---

{{< youtube 10NhTZHd5SI   >}}

#### Resources

* [Download PyCharm](https://www.jetbrains.com/pycharm/download/#section=windows)
* [Download Visual Studio Code](https://code.visualstudio.com/)
* [Python in Visual Studio Code](https://code.visualstudio.com/docs/languages/python)

#### Video Script

Now let's look at a couple of common IDEs for Python and see how we can use those with the projects that we've already configured. For this example, I'm going to install both PyCharm and Visual Studio Code. So to do that, I'm going to begin by installing both of those IDEs. When you're installing PyCharm, it does present you with a quite a few options that you can choose from. Depending on your particular setup, you may wish to check mark things such as updating your PATH variable, updating your Windows context menu, and associating the .py file extension with this tool. 

When installing Visual Studio Code, you may also want to check out some options to add different menu items to your Windows Explorer context menu.

Let's first take a look at PyCharm and see what it takes to open this project in that IDE. Once PyCharm is open, we can click the Open button to open the folder containing our project inside of the IDE. In the dialog, I'll select the folder containing our project. This is the same one that we downloaded using Git earlier. We'll also choose to trust the project, which will allow it to actually run the code that it contains. 

When PyCharm first loads a project, it has to go through and scan and configure a lot of different things. So just be patient and watch the bar at the bottom of the screen as PyCharm gets everything set up for the first time. As PyCharm scans the project, it may find the virtual environment and set that as the Python interpreter. You can see that down here at the bottom of the screen, where it shows the Python version and the location of the interpreter. You can hold your mouse over to confirm that it's working in the .venv folder, which is what we want. By selecting this interpreter, this will tell PyCharm to use that virtual environment and install all of the packages there. 

Once PyCharm is done configuring, we'll need to add a run configuration so that knows how to run our projects. To do that, we'll go to the Run menu, and then choose Edit Configurations. Then we'll hit plus and choose Python. And then here in the dialog, instead of a script path, I wanted to run a module. So I'll click this drop down choose Module Name, enter source or src for the module, to match the name of our module in our Python project. And I'll also set the working directory to the default, which is just the package directory itself. Then we can click OK. And now if we want to run the project, we can go to the Run menu and choose Run src and it will run that Python module directly from within Python. We can also choose the debug option to debug this, which is a really powerful tool that we can use directly in PyCharm. 

PyCharm also includes a terminal that will load the default PowerShell terminal in Windows. However, it will not by default load the virtual environment. So we'll have to remember to type `.venv/Scripts/activate.ps1` to load the virtual environment before we run any Python commands directly within the terminal. That's a quick update on how to use PyCharm with this project. There are many many more things that we can do in PyCharm, including configuring it to work with tox. However, we won't cover those things in this video, but you can find lots of good documentation online. 

Now let's quickly look how we can open this project in Visual Studio Code. To do that, I'll go to our Start menu and load Visual Studio Code. In Visual Studio Code, the easiest way to open a project is to go to the File menu and then choose Open folder. Here we'll select our project folder, and it will open it in Visual Studio Code. Visual Studio Code will ask us to confirm that we trust the authors of this project so that it can run the code directly inside of it. 

Once the project is loaded, we can go open one of our Python files, and that will cause Visual Studio Code to prompt us to install a few additional extensions. I'm just going to click the button that says Install to install the recommended extensions for Python. Once the Python extension is installed, you'll need to allow it to select a Python interpreter. So I'm going to click that option and choose Select Python interpreter. Thankfully, Visual Studio code is smart enough to immediately detect our virtual environment. So I'm going to choose that as our interpreter for this project. Once I've done that, I can go back to my files and I should be able to see them using Python. Notice down here at the bottom, it will tell us which interpreter it's running just like we saw in PyCharm. 

To run this project, we'll need to add a configuration, and we're going to choose a Python module and enter the module src as the name of our module. That will create a launch configuration that looks like this, which gets stored in a JSON file. Once that's been done, we can go to the Run menu and choose Start Run without debugging to actually run our Python project. And there we go. We see Visual Studio can now run our Python project. One other neat feature of Visual Studio Code is then when we open a terminal with the Python extension turned on, it will automatically know to activate our virtual environment. So it will take care of that for us. It's a really neat feature that it has. 

So there we go. There's a quick overview of how to load both PyCharm and Visual Studio Code IDEs with these Python projects. If you have any questions, please feel free to let us know.
