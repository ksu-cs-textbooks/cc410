---
title: "Spring '25 Week 11"
pre: "11. "
weight: 110
---

{{< youtube Vo4ZLRo_JXs >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript

Hello and welcome to the week 11 announcements for CC 410 in spring 2025. So this week you should be working on a milestone on releases where we're going to actually take our project and build a release version of it that we can share out with others across the internet. This is kind of the last big wrap up part of this whole GUI process that we've been going through. And so for the ninth restaurant milestone, you'll be finishing the checkout process using the external cash register library that you've installed and also printing a receipt so that everything comes together and we have a fully working point of sale system for our project. 

So the checkout milestone, milestone nine, you're going to install an external library mimicking a cash register. This is a library that I have written that is open source so that you can read the source code for it, especially reading the source code might be useful when you're trying to figure out how to write some of your unit tests. It allows you to pay with cash or with credit card, and then you need to write the algorithm to make change and make sure that the cash balances in the register itself. It is a little bit frustrating because you can't count the cash in the register while it's open. And so you have to have the register close to count it. You open the register, you make all of the changes to the register values and close it, and it should have the same amount in the register plus or minus the sales amount. So it's a little bit tricky to make change. Don't worry about handling every single minor detail in that process. If you get it mostly working, that's what I'm shooting for. There's a definite long tail of diminishing returns as you try and get all of the edge cases for making change. I'm not so worried about that. I just want you to see the complexity in that process. And then finally, make sure that you spend some time printing the receipt and read the directions on that to get your receipt to format correctly. 

So like I said, making change is hard. So be aware of that. Don't go chasing all of the little bugs. Get it mostly working and you should be fine, but make sure it is working so that you can see that. For receipts, remember that each line on a receipt has a limited length, and so you may have to trim or adjust the layout of your receipt to make it read. maybe even look at some real world receipts that you've received and see how you can format your receipt to match that. I highly encourage you to use the adapter pattern that we've learned earlier in this class, taking my catch register library, my receipt library, making a wrapper or an adapter around it, because that's where you can write your unit tests. And then of course you can read the unit tests that I use for my library to kind of figure out how I interact with the library and how I test it. Remember, you don't have to test the functionality of my library, you have to test the functionality of how you're using it and make sure that you're calling the right functions and doing the right things in your adapters. 

So after that, this is the last week of the GUI milestone. So after this week, the milestones get a lot smaller as we start working on the web interface. The web interfaces is kind of a simple process, but I want you to at least see what it looks like and compare it to the GUI interface. So we have smaller milestones, it gives you a lot more time to work on your final project over the last four weeks of the semester. So hopefully everything's going well. Hopefully you get really excited the first time you're able to use the checkout and see that your credit card actually matches and it works. As always, if you have any questions, let me know. Otherwise, I will see you again next week. 
