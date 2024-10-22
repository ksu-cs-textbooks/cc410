---
title: "Fall '24 Week 10"
pre: "10. "
weight: 100
---

{{< youtube KpNHsIYIGJo >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week 10 announcements video for CC 410 in Fall 2024. This week we're working on parallel programming, so you'll do a short example around that. We'll also work a little bit on event -driven programming, and you'll do an example around that. And then you'll work on the seventh restaurant milestone. This is the milestone where you're going to add event -driven programming to your user interface so that you can actually switch between windows, you can save objects, and you can actually update the order itself. This is where we actually start building the real interactive part of the user interface by building these event -driven pieces of code into our GUI, and it hopefully really helps you understand a little bit better how we actually work in an event -driven scenario instead of an imperative scenario like you've worked at in the past. 

So like I said, this milestone is all about adding events to our user interface. We're going to refine our user interface structure a little bit by replacing the order list with a tree. That turns out to be a little bit better structure for keeping track of orders and combos in our sidebar, so we'll do that. The big thing is you're going to add button -click handlers for almost everything, so you'll end up with a mostly functional user interface by this point, and you'll start writing some unit tests. Remember the goal of the unit tests is just to make sure that the selections on the user interface actually represent the item to get saved, and vice versa, if you hand an item to a user interface, it actually represents it correctly in the UI. So definitely read the hints and look at the example project on that because that gives you an awful lot of hints of how to actually complete that. 

So, like I talked about last time, there are some testing issues with these larger projects, especially when we start testing the user interface. So remember that the Codio boxes have limited memory. In Java, everything should run okay, but if something crashes or something isn't working, you can try and stop Gradle using the Gradle dash dash stop command. Then you can restart the box by going through the project menu and then refresh your browser. And of course, in Python, we're just going to update our tox file to run the tests in individual batches. And I show some examples of how to do that in the lab. 

So, looking ahead after that, module 10, we're going to talk about external libraries and how we we can bring a cache register library into our code. We're also going to work a little bit on adding orders and combos to our sidebars so that we can deal with that part of our project. And that really gets us to a mostly fully functional user interface. We'll add a little bit more features on module 11 and actually build a release version of our project as well. And then we'll shift gears and in November, we'll start talking about web APIs and how to make a web interface for some of this as well. So at the end of this lab, you should be able to hopefully take an order and actually get the order to somewhat show up and use your interface between this lab and the next lab. We'll get most of that functionality up and running. As always, if you have any questions, let me know. Otherwise, good luck on this lab and I will see you again next week. 
