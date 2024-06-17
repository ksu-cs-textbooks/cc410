---
title: "State & Behavior"
pre: "2. "
weight: 20
date: 2020-01-25T00:53:26-05:00
hidden: true
---

{{< youtube ooxRxPAodRw   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>
#### Video Script

Throughout this course, we've continually talked about objects in our programs consisting of two parts - state and behavior. So, it only makes sense for us to realize that there are really only two possible sources of bugs in our program - the state of the program, or the behavior.

Put another way, the bug is either in the data we are using, or the code that is running. Of course, this is a bit oversimplified, since the bug may actually involve both incorrect code and incorrect data, but this really gives us two solid places to look for the bug. 

Let's consider the state of our program first. Recall that state consists of all the data stored in our class attributes. In addition, we might want to consider any input files that our program uses, as well as individual arguments that are passed to a particular method. Any one of those could be the source of an error in our code. 

So, how can we examine the state of our program? To be honest, one of the simplest ways to do so it simply using the humble print statement. At any point in our program, we can print the value stored in any variable and examine the output to make sure it is correct. We can even include some conditional statements so we only print the output if it meets a certain criteria, making it even easier to find an error. Beyond print statements, we can make sure of logging or interactive debuggers, which we'll cover later in this chapter. 

In addition, as part of our testing we may want to force the program to have a particular state to see if that causes the problem. In most cases, the easiest way to do this is via unit tests - we can simply call the method we want with the inputs we desire and see what happens. Beyond that, we could develop some sample inputs and see how our program handles them. For example, if we are writing an image editor, we could use a small black or white image as input and see how it treats that input. Finally, as a last resort, we could also hard code a few values in our program when we test it. However, I always warn students to do this with extreme caution, as it is VERY easy to accidentally leave this code in your final product. There are simply too many examples of professional software being released today with hard-coded test credentials or insecure backdoors, and all of that is due to sloppy coding practices. So, we must be very careful if we choose to do this for testing. 

What if the data isn't the culprit, but the code itself? In that case, we have a few tools at our disposal to try and spot the bug. One of the most powerful ways to examine code behavior is through the use of the call stack. For example, if our program throws an exception from a particular function, how can we tell where in our code that function was called from? The answer will be in the call stack, which lists all of the currently executing functions, all the way back up to our program's main function at the very bottom of the stack. Beyond that, we can also use debuggers to interactively step through our code and examine the call stack, as we'll see later. Another clever use of print statements is to surround a piece of code with a few print statements, and see which ones of them print before the program dies. That can help us quickly narrow down the location of the bug, especially if we aren't exactly sure where it is. We can also combine those print statements with loggers get even better output from our program. Finally, unit tests are a great way to examine the behaviors in our program. A good set of unit tests should exercise each piece of code and provide several different inputs, so working within a particular set of unit tests is a great way to verify a smaller piece of our overall program.

So, as you continue to develop larger and more complex programs, hopefully you can use some of these tips and ideas to improve your debugging skill. As with any other art, it is one that you'll get better at with practice, so I encourage you to spend some time learning to debug your code. Maybe have another developer change one line of your program to something different, and see if it crashes your program. If so, can you work backwards to discover what changed? Exercises like that, along with just writing lots of code, can be great ways for developers to build their debugging skills. 