---
title: "Fall '22 Week 10"
pre: "10. "
weight: 100
---

{{< youtube 3oGsC4M3F1M   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week 10 Announcements video for CC 410 in fall 2022 This week and next week, you should still be working on the external libraries and releases examples. And then you also have a restaurant milestone all about checking out, which is what we're going to talk about today. 

So milestone seven, it really can be split into two parts. The first part is adding all of the GUI interfaces for dealing with combos, so you'll be able to add buttons to your menu to add a combo to the order, you'll also have a GUI where you can edit combos, including drop down lists, where you can add the wrap the side and a drink to the combo, you'll also need to update some other GUI panels to make all of that work. The biggest thing you can do is reuse a lot of the stuff you've been using and look at the example as we'll talk about in just a second. The second part of milestone seven is adding a library to handle checkout, I have written a custom library that simulates a cash register and a receipt printer that you'll download and install on your project, you'll basically be able to use cash to pay for the order or there's a simulated credit card reader, you'll also need to figure out how to make change out of the cash register, which is a little bit more difficult than it sounds. And then you should also print a receipt that will actually just get printed to a text file. And all of these have some limitations that you'll have to figure out. 

So for the hints for milestone seven, the first big thing for the combo GUIs is you can reuse all the existing panels, really take a look at the example project and see how we use a drop down to switch panels out in a larger window. That becomes the basis for the idea of the combo panel. However, instead of having one of those, you'll have three of those side by side by side. So you'll be able to switch out the wrap the side and the drink in the combo and save it that way. So really take a look at the code in the example projects and try and get that to work. The second big thing in this milestone is to deal with making change on the cash register. Making change can be kind of difficult, especially when you consider the fact that the cash register has limited amounts of each coin in it. My biggest hint for this, ignore that for now get change working without worrying about that requirement and then only try and implement that requirement. If you have taught. That's only about five points of this milestone. So if you get it working great. If not, don't sweat it, it's much much harder than it looks. But I put it out there as a neat little challenge that you'll have to deal with in real life when you're dealing with this. The other thing that you work on is receipts. The big thing about receipts, the receipt printer can only print lines of a limited length, I believe it's like 40 characters, so you may have to truncate some names of things. But you want to try and make your receipts easily readable so that you can see the item and all the special instructions as well as the subtotal and the total and how the item was paid for. So make sure you try and get all of that in using the receipts. For both the cash register and the receipt printer, you can use the adapter pattern where you actually make your own class, and then wrap it around my class that I wrote. And so that way, you can add your own logic to what's going on. Instead of calling directly into those methods, you kind of get to control everything with your adapter pattern.

The other big thing I recommend doing is reading all of the source code for the library and read the unit tests for the library. The unit tests especially give you some really good hints about how to test the cash register. And it gives you some really good examples of using test doubles to be able to do that. So read my code, read my unit tests and make sure you make use of that in your own code as well. So I've got a couple of questions for feedback for this class. It's been a couple of semesters since I built this class the way it is currently structured. And I'm leaning toward the idea of splitting milestones six and seven. Currently, they are big milestones that you spend two weeks on, I'm considering splitting them into four smaller milestones that you'll spend a week on each and then maybe adjusting the point values a little bit to match. So I'm curious about that. The other things I'm thinking about doing is moving the stuff on test pattern or on design patterns and test doubles. Moving that earlier in the semester. Before we have the GUI, I kind of found the parts of milestone six seemed a little bit out of place, because we weren't doing any GUI updates to add the order and the combo into the GUI. And so I wonder if maybe we should move those earlier to milestone four or five, and then shift all the GUI stuff a little bit later. So I'm curious about your feedback on this. If you have any input, you can use the start stop, continue survey link to send me some feedback. Let me know what you think about this. But just kind of letting you know I'm considering restructuring this class for future semesters. So any feedback you have is greatly appreciated.

So looking ahead, after we get done with milestone seven, you're going to move toward web interfaces working with milestone eight through 11. Those milestones are going to the smaller milestones that I have promised, so you'll have more time to work on your final project. So once you get done with milestone seven, you'll be scheduling your next final project meeting. And this is the one where I'm really going to talk to you about the specifics of your final project and really get you started coding on it. And then you'll have about a month or so to code on that as you work on these last few milestones in the class. The other big thing you can do in this class if you want to, you can forge ahead and get the last milestones done really quickly. They're all posted and available for you. If you get a milestone done and you want to graded before the deadline, all you have to do is send me an email, I will basically use that email as your submission time where you can't change it afterward. And then I will go in and grade it real quick so you can get some feedback. So if you want to just forge ahead and finish up the milestone content, and then leave the last part of the class for your final project, that's fine too. Feel free to do that if it fits in your schedule.

So that's all I've got for this week, you'll be working with cash registers. So hopefully, you'll be really excited to get your GUI up and running and actually have a fully fledged project where you can go from picking your order to getting it in the order of setting up your combos and finally being able to pay for the order and get your receipt. As always if you have any questions let me know and I look forward to seeing you again next week.