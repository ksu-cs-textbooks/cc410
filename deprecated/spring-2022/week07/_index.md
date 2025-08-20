---
title: "Spring '22 Week 7"
pre: "7. "
weight: 70
date: 2022-02-28T00:53:26-05:00
---

{{< youtube D8IjQlb6XWk   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week seven announcements video for CC 410 in spring 2022. So this week, we'll be doing the second module on GUI programming, which is all about event driven programming. And so in this module, you'll actually have two smaller examples covering both parallel programming and event driven programming. And then you'll work on the fifth restaurant milestone, which is all about making your GUI reactive to button clicks and things like that. 

So again, in this milestone, you'll be working on your events in your GUI, we're going to refine the structure of the GUI a little bit to change a couple of things. But the big thing you're going to do is add the button click handlers for your GUI. So by the end of this milestone, you should have a mostly functional GUI, there's a few things that we'll leave out, but we'll get to over the next couple of milestones. You'll also be writing a few unit tests for this project. And the big thing I will tell you is look at the milestone and read the hints. There are a lot of hints on coding style and some different things you may want to change in this milestone. So make sure you read the hints that I give you and try and follow those as best you can. 

So one thing that comes up with this milestone, as we start doing unit tests with graphical interfaces is we run into the problem that the Codio boxes have a very limited memory on the internet itself, most of them have only 512 megabytes of memory. And when we're running unit tests, we keep spawning a lot of instances of the user interface and that can cause problems. So on Java, what will happen is Gradle will lock up so you'll just have to open the terminal and do gradle --stop to stop any running Gradle processes. And then go to the Project menu and hit restart box to restart the Codio box. And then you can refresh your browser and try again. In Python in tox, what we do is we run the tests in batches. And so I give you an a skeleton of an updated tox file, you may have to tweak it just a little bit to match your previous talks files. But this allows you to run things in batches. The other thing you can do, I just released a set of videos for how to set up either Visual Studio Code or PyCharm or IntelliJ outside of code to to work on these projects. And so another option is you could download your projects to your computer, get those things set up and then run Gradle or tox outside of Codio to do the testing. It's up to you. I've been able to get everything to work in Codio but sometimes I have to start with restarting the box and then running Gradle immediately after that, or being careful in Python about how I break out my tests so that they will all actually run. So read up on that if you run into trouble, please let me know. And I'd be happy to help you out. 

So looking ahead, The next module is all about design patterns and combos. Like I said earlier design patterns, I think is probably the most important thing to take away from this class other than the object oriented concepts we've already covered. So you'll have that module you'll have all through spring break to work on that milestone. And then after that, we're going to do module nine and 10, which is external libraries and releases. And so week nine and 10, after you get back from spring break are also going to be the same milestone. So after this milestone, you have to double week milestones. So you've got plenty of time to work on those. And these are two of the last really big milestones before we switch over and work on web development. And so after that on week 11 and going forward, we'll switch over to web API's. 

So we're getting close to spring break. Hopefully everybody's keeping up your motivation and then keeping up with this course. As always, if you have any questions, please let me know and otherwise, I hope you have a great week. 




