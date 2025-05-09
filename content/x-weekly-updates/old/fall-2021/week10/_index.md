---
title: "Fall '21 Week 10"
pre: "10. "
weight: 100
date: 2021-03-01T00:53:26-05:00
---

{{< youtube 1-3ApvbB4SY   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week 10 Announcements video for CC 410 in Fall 2021. So this week you're working on milestone seven, which is the checkout milestone, you'll have two weeks to work on that. This week, you're also doing an example on external libraries, which is really interesting. And then next week, you'll work on actually creating a packaged and installable release of your software. 

Milestone seven is actually best split into two parts. And so you can work on both parts kind of independently, I recommend on working them in order just to make everything work. The first part is editing the graphical user interface so that you can edit combos. You'll need to probably go through and update a lot of other GUI panels. But hopefully, a lot of this should be just wiring stuff together copy pasting code to build the combo GUI and getting some of the dropdowns figured out. Hopefully, it's pretty simple, especially with some of the examples I show. But if you need any help with that, let me know this is one of the trickier parts. 

The second part is to use the external library I give you to build a checkout system. So there's a library that mimics a cash register that you can either do a cash exchange or do a credit card. The credit card is very simple actually show you how to do that in the examples. So that should be pretty easy to build. The cash part is a little tricky, there's a lot of different ways you could build the cash user interface. And then of course, you have to handle how to make change. And make sure you read this very carefully, the library should only be instantiated once. And so making change, you'll have to make sure that if you run out of a particular coin, you can borrow them from the next highest, you can take $1 and get four quarters, for example. And so as long as the amount in the change drawer stays the same, you can make change however you need. And then finally, you'll print out a receipt. And so there's a little library that you'll have to read. The library has good documentation, the code is open source, so you can read the code as well. So take a look at that library, see if you can understand how I built it and how it works. And then use it within your program yourself. 

So beyond that, after this, this milestone we'll start working on the web. So maybe not in five minutes, but in a couple of weeks will switch over to do web frameworks. Also, bear in mind that we're getting toward the end of the semester, you got a little over a month and a half to work on your final projects. So now's the time to start thinking about getting code written for your final project. After this milestone the restaurant milestones will be a lot smaller for the last four. So that shouldn't be so bad. But make sure you keep in mind you got to start working on your final project soon so you have enough time to get it working. You should also have a final project meeting with be here in the next couple of weeks. So as always, if you have any questions, let me know otherwise. Good luck this week and next week on milestone seven and I look forward to hearing from you soon 

