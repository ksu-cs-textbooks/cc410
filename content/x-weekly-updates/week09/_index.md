---
title: "Fall '21 Week 9"
pre: "9. "
weight: 90
date: 2021-03-01T00:53:26-05:00
---

{{< youtube 1EuozvzMOjY >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week nine announcements video for CC 410 in Fall 2021. So we're on week nine, I apologize for missing the last couple of weeks. I was on vacation two weeks ago. And then last week, I was busy getting caught up with everything, but we're back on track and you should see announcements videos for most of the rest of the semester. 

So we've taken a couple of milestones and split them over two weeks. So this week, you should be finishing up the sixth milestone on the restaurant project. This one is all about design patterns and using mock objects in your unit tests. You should also have your third final project milestone meeting with me sometime this week or next week. This is the point in the semester where you should start working on your final project. So make sure you get that started soon. We're about halfway through that. Well, we're over halfway through the semester at this point. So for your final project, if you haven't already, load up that Codio project, get the base project built in there just like we did for the hello real world project. And then you can start working on code for your final project and get going there.

 So next week, we've got another split milestone over the following week. So next week, we'll introduce external libraries, and you'll start learning how to use those. And then the following week after that, we'll talk about releases. And you'll be working on the seventh milestone, which is the checkout milestone. Checkout is one of the other trickier milestones in this semester. So I gave two weeks for that one, make sure you use your time very wisely. And then after that milestone will start doing some stuff with web interfaces. And you'll have a lot more time to work on your final project as we get further into November. 
 
 So the milestone you're working on today, milestone six is all about orders and combos, we've added those new classes to our code. And then we're using some design patterns such as the factory method, builder pattern, singleton pattern and the iterator pattern. To use those design patterns to make orders and combos work really well in your system. We're also writing unit tests with test doubles or mock objects in there. So that'll be something really cool that you haven't used. But there shouldn't be very many GUI changes this week, the only real GUI changes are to handle the combos themselves. And it should be pretty minimal compared to what you've done in the past. But hopefully you start to see the use of design patterns in your code and how it's really useful to reuse these common structures so that other people can understand your code quickly and easily. 
 
 The other thing we've run into with this milestone is the testing issues. Running tests, especially with these large objects and large GUI things really can take a lot of time. And Codio boxes have limited memory, I believe Codio right now limits them to 512 megabytes. And because of that every once in a while the tests will crash in Codio. There are a couple of ways to fix this. In Java. If your tests crash and you need to stop a running Gradle project you can do "gradle --stop" on the terminal that will stop any running Gradle instances, then in Codio you go to the project menu and choose restart box that will restart the code your box your code is running on. And then once that's done, you refresh your browser page. And then you should be able to run the tests again, that should work. So if you ever have trouble with Gradle hanging on any of your tests, that's the way to fix it. In Python, we're simply going to run the tests in batches. And so in the code, I give you some examples of how you can change your tox configuration to run those tests in batches You may have to tweak it just a little bit to make sure that it fits with your unique setup. But that should work for that. 
 
 So looking ahead after the next few weeks, we're going to switch to doing some stuff with web interfaces. those milestones are meant to be a little bit smaller, a little bit more straightforward. And that will give you some more project time to work on the project over the last four weeks of the class. So keep that in mind. We're almost over the difficult part of the class and into some of the easier stuff toward the end. 
 
 So as you can tell week nine we're finally over the halfway mark on the semester. So you've only got about seven weeks worth of content left. So make sure you keep plugging away at it that you're doing well if you have any questions, let me know and otherwise I will see you next week. 

