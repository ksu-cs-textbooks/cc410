---
title: "Java IDEs"
pre: "5. "
weight: 25
date: 2022-02-25T00:53:26-05:00
---

{{< youtube y5nrS9dnbxI >}}

#### Resources

* [Download IntelliJ](https://www.jetbrains.com/idea/download/#section=windows)
* [Download Visual Studio Code](https://code.visualstudio.com/)
* [Java in Visual Studio Code](https://code.visualstudio.com/docs/languages/java)
* [Java Build Tools in VS Code](https://code.visualstudio.com/docs/java/java-build)

#### Video Script

In this video, I'm going to discuss how to install and configure two popular IDEs for Java to work with our projects. Those IDEs are IntelliJ and VS Code. First, let's look at installing those two IDEs. I've already downloaded the installers, and so now I'm going to install both the IntelliJ IDE, and Visual Studio code. When installing IntelliJ, it gives you many different options that you may want to enable depending on how you're using the tool. I'm going to enable adding it to the PATH, adding open folders project and associating the .java file extension. 

When installing Visual Studio code, you may also want to check mark some options to add different menu items to your Windows Explorer context menu. 

At this point, we can open up IntelliJ and configure it to work with our project. So I'm going to find IntelliJ on my start menu, and click it to open it. When you first load IntelliJ, it will ask you if you want to import any settings, I'm just going to choose do not import settings and click OK. Once IntelliJ is loaded, I'll click the Open button to open our projects folder as a project in IntelliJ. In the dialog, I'll select our project that we downloaded directly from Git. The first time we load the project IntelliJ will ask us if we trust the authors. I'm going to click trust projects so that it can actually execute it properly. Once we select that project, IntelliJ will go through and configure everything it needs for the project. This may take a few minutes, so just hang tight while it does this work. 

Once IntelliJ has done indexing, we can add a run configuration so we can actually run our project. In the configurations, we're going to choose the option for a Gradle configuration. And then we can put in the Gradle task that we want to run. A very simple gradle run task we can type run here. But we can also create additional run configurations for check, and for test, and for any other Gradle tasks that we want to run. With that in place, we can run our project using that run configuration. If everything works correctly, we should see our project appear on the screen. IntelliJ also includes the Gradle tab, which gives us direct access to a lot of our Gradle tasks and configurations here. That's just a quick overview of how we can use IntelliJ with this project. There are many many more features available, but you can find out more about that by reading the documentation for IntelliJ.

Now let's look at how we can use Visual Studio Code to load this project in java. To load Visual Studio Code. I'll simply find it on the start menu and click it to open it. The easiest way to open a project in Visual Studio Code is to go to the File menu and then choose Open Folder. We'll select our project folder, and click select folder to open it. When we first open a project in Visual Studio, it will ask us if we trust the authors. Since we wrote this project, we'll go ahead and click yes so that we can fully work with this project. 

Once we've opened the project, we can go to one of our Java source files to get Visual Studio to prompt us to install all of the extensions we need to work with Java. So we'll click this install button to install all the recommended extensions for Java. Once the extension pack is finished installing, we can go back to our project. Once the extensions are installed, it will eventually scan through and find all of the Java Development Kit and initialize the workspace. As Visual Studio Code builds the project, it will give you a prompt to upgrade Gradle. Go ahead and click that because that will upgrade the Gradle that is bundled with this extension. If everything works correctly, eventually Visual Studio will be done building the project. 

There's one more extension we can install, which is the Gradle extension. The Gradle extension from Microsoft allows us to interface directly with Gradle in our code. When the Gradle extension installs, you may have to allow a few things through the firewall. With the Gradle extension installed, we can choose that option from the options over on the left and watch it as it goes through and parses our Gradle project and eventually presents us with all of our tasks. Once it's done configuring, we should be able to expand the Tasks list for our different apps, and we'll be able to see all of the different Gradle tasks that we can run. This is a great way to explore how Gradle works in your project. 

Finally, we can also add a launch configuration directly to VS Code to run our Java code directly outside of Gradle. A launch configuration will look something like this with the main class put in here. You can configure these by going to the Run menu and choosing Add Configuration. That's a quick overview of how to work with Java in Visual Studio Code. If you have any questions with any of this feel free to let us know 
