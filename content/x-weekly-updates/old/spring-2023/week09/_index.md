---
title: "Spring '23 Week 9"
pre: "9. "
weight: 90
---

{{< youtube _F06a93mMQc   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week nine Announcements video for CC 410 In spring 2023. This week we're going to go through a couple of different examples. The first one is about parallel programming, which is an important concept for us to learn when working with user interfaces. We'll also do an example around event driven programming, which allows us to make our interfaces interactive. And then finally, we'll have another milestone for the restaurant project. This week, we'll do milestone seven, where we're going to add events to our user interface, we'll refine our structure a little bit for our user interface to add a tree to keep track of our menus. But the big thing is, we're going to add our button click handlers. By the end of this milestone we should having mostly functional user interface, we'll still be needing to add some things. And we're also going to add some unit tests as well. One big thing I really encourage you to do with this milestone is to read the hints very carefully, I give you some hints about structure and some code that you may want to use, both in your user interface and in the unit tests. 

So one of the things you run into when we're doing unit tests with GUIs is we need to use a lot of RAM because we're constantly creating and destroying our GUI. This can cause issues on Codio. Because Codio boxes, by default have a very limited memory of only 512 gigabyte megabytes. So if you run into issues where something breaks, for example, Gradle will hang up or your system will run out of memory. In Java, you can open up another terminal and try and do gradle --stop to stop any running Gradle projects. Otherwise, you can go to the Project menu and Codio click restart box to restart the underlying Codio box. And then once that's done, you can refresh your browser. For Python, we're just going to run our tests in batches. And so you'll see some new tox files that I include that will help you with that. But if you have any questions or any issues with testing issues, just let me know. 

Looking ahead after this, we'll have a couple more modules working with traditional user interfaces. These modules will mostly cover additional concepts like working with libraries and working with releases while we finish up our user interface itself. And then we'll switch over to start talking about web API's and web interfaces from there on out. So we're over halfway we're past spring break, which means we're closing in on the end of the semester. Hopefully you're enjoying this class and getting a lot out of it. As always if you have any questions, feel free to let me know and I look forward to seeing you again next week. 



