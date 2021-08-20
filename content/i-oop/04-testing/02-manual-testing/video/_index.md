---
title: "Overview"
pre: "1. "
weight: 10
date: 2020-01-14T00:53:26-05:00
hidden: true
---

{{< youtube mFLBP2hW154 >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

In this chapter, we're discussing the many different ways we can test our code. Before we dive deeply into the test frameworks we're going to be using, let's step back and look at the big picture of software testing. There are two major categories of methods we can use to test our code. The first category is informal testing. For most of us, this is the type of testing we do naturally as we learn to program. We simply run our program, pick some random inputs that may or may not work, and then observe the results. If the output is different than we expect, we go back to our code to try and figure out why that is. Maybe our assumptions were bad, or maybe our code was incorrect. In either case, we can fix the error and try again. Informal testing is quick and easy, and doesn't require much additional work to perform. However, informal testing is not very good, and can easily lead to errors in the code that are not properly caught and fixed. Believe me, after reviewing code from many students over the years, I am sure that informal testing is not at all adequate!

The other category of testing is formal testing. When we are doing formal testing, we start by developing a test plan. That plan will list the inputs and expected outputs we want to observe, and we want to focus on providing a wide range of inputs that will help us properly test edge cases and achieve a high level of code coverage. Then, we can execute those tests following our plan and observe the results. The biggest difference is that we're now planning ahead and trying to use the same inputs over and over again, and we're making sure that we choose a challenging set of inputs that will properly test our entire program. And, of course, once we have a test plan developed, we can look at ways to automate that testing. We'll come back to that in just a minute.

First, let's look at the traditional model of software development. This is the model used in the early days, probably up through the end of the 20th century. We start by gathering requirements for the software, and using that to develop a formal design specification. Then, once we've build the specification, we implement it in code. After all the implementation is complete, then, and only then, do we start formally verifying that the code works properly, without any bugs. Can you spot the problem here? As you have hopefully learned in your programming career so far, waiting until the end of a project to start testing things is a very poor idea, as it can be extremely difficult to narrow down the location of a single bug when a bad output might be caused by several different bugs. Now, that's not to say that you can't start developing test plans and thinking about testing earlier in the process, but for a long time that simply wasn't how most software development projects were structured. More recently, with the advent of Agile software development methodologies, we are more likely to see testing as an integral part of the entire development process. This, of course, is aided by the creation of automated test frameworks.

So, in short, if there is one big takeaway from this discussion, it is this statement. Test early, and test often.

The easiest way to facilitate that is through the use of automated testing tools. The most common form of automated testing are unit tests, which are small pieces of code that are meant to check and verify that individual units of the program, usually at the function or class level, are working properly. By developing a good set of unit tests, we can help make sure our code is working properly. We'll focus on creating and running unit tests in this course. 

There are a couple other forms of automated testing that we should discuss here. One is integration testing, which involves testing how many pieces of the software work together. One major downside of unit testing is that it focuses on testing individual units of the program, but not how those pieces interact. So, an integration test involves making sure each module provides the correct API, and that they can all work together to produce the desired user output. 

The other type of automation testing is system testing. This involves testing the entire application as a whole, and is usually done either through GUI automation tools such as Selenium or by actually asking real users to perform specific tasks. System tests help verify that the software indeed works for the eventual end users. 

That's a quick overview of software testing, mainly to help us understand how unit tests fit into the broader picture. Next, we'll review how to develop unit tests using the test framework available in our language. 
