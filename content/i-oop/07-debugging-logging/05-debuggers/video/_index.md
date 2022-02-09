---
title: "Debuggers & Loggers"
pre: "3. "
weight: 30
date: 2020-01-25T00:53:26-05:00
hidden: true
---

{{< youtube oVKZPiGAd4c >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>
#### Video Script

Finally in this chapter, let's briefly discuss both debuggers and loggers and how we can use them to help us find and fix error in our code. First, we can talk about debuggers. Debuggers are special programs that we can use to interactively examine our program while it is running. Both Java and Python have a debugger we can use, as do most programming languages and integrated development environments, or IDEs, including Codio. We'll see how to use the Codio debugger as part of the example project in this module. In short, a debugger allows us to examine both the state and behavior of our program. We can see the values stored in variables while our program executes, and we can pause the program at a particular line of code and run it line-by-line until we find the error. Learning how to use a debugger effectively is a very powerful skill for developers to develop!

This is a quick example of the Codio debugger in action. Here, we have a short python program that is being examined, and the execution of the program is stopped at the line highlighted in red. Next to that line, we see a small red dot, which is a **breakpoint** that was added to our code through the Codio interface. When we run the debugger, the program will run until it reaches a breakpoint. At that point it will pause our program, and we can examine the state. To the right, we see the debugger panel that lists the call stack and variables in our program at that point. 

Once our program has been paused by the debugger, we can interactively step through it using the buttons at the top. Most debuggers support these actions: Resume will let our program run until it reaches the next break point. Stop will stop our program completely so we can start it again. Step Over will run the program until it reaches the next line in the current method. If the line we are stopped on is a method call, it will call that method and let it completely finish before pausing on the next line. The other two options are Step Into and Step Out. If our current line is a method call, Step Into allows us to move execution to the code contained in that method, and it will pause at the first line of that method's code. Effectively, we'll add one more layer to the call stack and step into that method's code. Similarly, Step Out will finish executing the current method, and take us down one layer in the call stack, pausing after the line that called the current method. So, using the Step Into and Step Out buttons allow us to somewhat traverse the call stack itself. Pretty handy!

The other helpful tool we can include in our programs is a logger. A logger is a special tool that allows our program to record helpful debugging information in a more useful way, instead of just printing it to the terminal. Loggers can include very complex formatting and handling code, making it easy to explore the logged information later. We can even define different levels of detail, and enable or disable various logging information as needed. So, in this way, we can leave the logging code in our program and just disable it when we are done debugging, instead of having to remember to remove all of our print statements later on. Finally, loggers can integrate with more complex data collection systems, and many large professional software programs include robust logging so companies can keep track of what their users are doing. The textbook includes quick examples for how to include a logger in both Java and Python, as well as links to documentation for both languages. I encourage you to try including a logger in your own code, just to see how it works!