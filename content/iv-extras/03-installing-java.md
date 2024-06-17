---
title: "Installing Java"
pre: "3. "
weight: 15
date: 2022-02-25T00:53:26-05:00
---

{{< youtube q48b8OFSJ50   >}}

#### Resources

* [Java JDK Installers](https://www.oracle.com/java/technologies/downloads/)
* [Gradle Downloads](https://gradle.org/install/)

#### Video Script

In this video, I'm going to go over installing Java and Gradle on Windows. So I've already downloaded the Java Development Kit directly from the Oracle website. So I'm going to briefly double click to install that. 

I'll also install Gradle. However, Gradle does not come with an installer, it just has a ZIP file. So to install Gradle, we're going to extract this ZIP file, and we're going to extract it to the folder C:\Gradle. Once I've extracted the Gradle files, I'll open up the Gradle folder, and then the bin folder. And I'm going to click up here in the address bar and copy that path. We need to add this path to our Windows path so that we can actually access these files in the search bar. If I start typing environments, it should give me an option to edit my system environment variables. So I'll choose that option, then click environment variables. And then under system variables, I'll find the path variable and choose Edit. And then I'm going to create a new entry and paste in that path. 

Now that we've installed both Java and Gradle, we can actually run this project. To do that, I'm going to start by opening PowerShell. And then in PowerShell, I'm going to change directory to our project folder. Once here, I can type java -version to confirm the version of Java, and gradle -version to confirm the version of Gradle. If everything looks correct, I should be able to run Gradle run to actually build and run my project using Gradle. If everything works correctly, we should see our application pop up on our screen. 

That's all it takes to get Java and Gradle running on Windows. In the next video I'll talk about how we can configure two popular IDEs, IntelliJ and Visual Studio Code, to work with this project. 
