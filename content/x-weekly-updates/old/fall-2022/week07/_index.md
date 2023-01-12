---
title: "Fall '22 Week 7"
pre: "7. "
weight: 70
---

{{< youtube o6fxDW2JTS8 >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week seven announcements video for CC 410 in Fall 2022, this week, we're going to switch gears a little bit and spend some time working on both parallel programming and event driven programming, a couple of different paradigms that you've maybe seen before, but you haven't worked with a little bit. So this will be some really good examples that you can work through. And then we'll apply a lot of that to our restaurant milestone where we'll add some of the interactivity to our graphical user interface. 

So in milestone five, we're adding all the events to our GUI. When you click on buttons, it needs to be able to actually do something following event driven programming paradigms. We're also going to refine the structure a little bit by reformatting the sidebar as a tree, which will make it a little bit easier to manage down the road. By the end of this milestone, we should have a mostly functional user interface where we can do some things, we can actually take click buttons, we can get to different places, we can save items, we're also going to add some basic unit tests, mainly to check the sanity of our GUI forms so that when we give an item to the form, it formats it correctly. And then when we save an item from the form, the item it creates, is done correctly. It's not a very fully functional unit tests, but it gets some of the basic ideas across. The other big thing for milestone five, please make sure you take some time to read the hints. There's a lot of useful information in that milestone. So make sure you read the milestone carefully and get all of those nice little hints that I've included to help you get through it. 

So one of the things we run into with this project as we start making them more complex is we run into some issues with testing. Specifically, when we're running testing, using graphical user interfaces, it does use up a lot more memory. And you might run into trouble with Codio. having issues with that. If that happens if your Codio box locks up or anything, one of the things you can do if you're running in Java is you can refresh the page, then go back to the terminal and do gradle --stop that will stop any Gradle daemons running in the background and it should clear out some memory. Once you've done that, go to the Project menu in Codio and click restart box to restart the underlying box and refresh your browser that should get you past any issues if you run into them with Java. on the Python side of things, what we're going to do is we're going to run our unit tests in batches. And so I give some updated talks dot ini configuration. To help with that, you will have to shift those examples from Python 3.6 to 3.9. But other than that a lot of those examples should work really well. If you do run into issues running any of these unit tests, just let me know. And I'd be help happy to help you figure those out. 

So of course, looking ahead after this module, we're going to spend some time on design patterns and combos, then we'll bring in some information about external libraries and working through releases. And then we'll start shifting over to web API's and some other background as well. So keep an eye out for that. So we're pretty close to halfway through the semester. At this point. It's week seven out of 15 ish. It's technically a 16 week semester, but week 16 is final. So we're pretty much halfway through the semester. Hopefully things are going well for you. But as always, if you have any questions, let me know and I will look forward to seeing you again next week.

