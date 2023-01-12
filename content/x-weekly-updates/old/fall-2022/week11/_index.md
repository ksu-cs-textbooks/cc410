---
title: "Fall '22 Week 11"
pre: "11. "
weight: 110
---

{{< youtube U77My4NJZCA >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week 11 Announcements video for CC 410 in fall 2022, this week you should be working on milestone seven. And you'll also have a short example on creating a release. Those are really the only big topics for this week, you also should be finishing up the external libraries example from last week if you haven't done that already. But mostly this week is just getting through the checkout milestone, it's the biggest milestone in this class really, it's generally the most difficult one. And so hopefully, you've got enough time this week to spend on that and get that taken care of. 

So milestone seven that you've been working on really comes in two parts. The first part is updating the user interface to handle combos. So you'll have a GUI to actually edit and create the combos and you'll need to make some updates to the other GUI handles so that they will actually work with the combos that we created in milestone six. The second part is checkout, we're going to add a checkout feature where you'll have an external library representing a cash register that has a receipt printer, it will be able to check out using credit card or cash. In the example I'll show you how to use the credit card for this, but you'll have to work on the cash part yourself with the cash part, you'll also be making change. And then finally, you'll be printing a receipt into a text file. So all of these things that you'll need to do some big hints for the combo GUIs, make sure you reuse your existing panels. One of the nice thing is all of the panels that you've created, have a parent or a master that you can give it and so when you're putting them inside of the combo, you just use that frame as the master instead of the parents window. It's pretty cool. So take a look at the example project, I give you some pretty good code for how to do this. 

On the checkout side, making change is hard. And so I always tell students get it to work in the initial case, don't chase all of the edge cases first, just get it making change. If you run out of coins in the cash register in a crashes, that's fine. Get it working first and then try and work on those edge cases if you have time. Likewise, with receipts, remember that each line can be a limited length, so you may have to add some string parsing in there to make sure that those lines are not too long. And so a great way to do this is to use the adapter pattern where you can actually write a wrapper around the cash register classes. And then you can use your functions to do all of this work and then call the functions inside of the cash register. With that adapted data. If you want to learn how to unit test all of this stuff, you can read the unit tests in the library, all of the code for that library, including the unit tests is open source, so you can take a look at it. So feel free to read some of the unit tests that I've written to see how you might try and unit test your adapters as well. Bear in mind, you only have to test your functionality, you do not have to test the functionality of the cash register itself, you can assume that it works. 

So looking ahead after this one, once you turn in milestone seven next week, we're going to shift gears and talk about web interfaces. The next four milestones in this class are much smaller and easier to do, they shouldn't take a lot less time than these last two milestones have. And so the idea here is to give you more time to work on your final project. So after this week, I encourage you to get started on your final project and contact me and schedule a time to meet if you have any questions or aren't sure where to go from here. So hopefully everything's going well. Hopefully you get really excited the first time your project works. You can actually do a checkout with a credit card and you get a match and it works. As always if you have any questions, let me know otherwise, I will see you next week.

