---
title: "Fall '24 Week 11"
pre: "11. "
weight: 110
---

{{< youtube 7dFaBri0rr8 >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript

Hello and welcome to the week 11 announcements video for CC 410 in fall 2024. This week you're going to be working on an example around releases. We're going to talk about how we can actually build a releasable version of our code that others can easily use. You'll do a small example around building a release and then you'll switch over to the restaurant project where you're going to add an external library to help us actually go through the checkout process. 

So for this milestone, we're using a library that I have developed that simulates a cash register and a receipt printer and it allows you to add checkout functionality to your project while also learning how to interface with an external library that has code that you don't control. The cash register itself handles either cash or credit card. It has a credit card machine that will basically tell you whether the card was approved or not. It also has a cash drawer that you can interact with that you have to read the documentation on a little bit to figure out how it works. Basically the cash drawer you can only count it while it's closed, but you can only modify it when it's open. And so you have to do your calculations in advance to make your change. The last thing that you'll do is you'll actually print a receipt using a receipt printer. Bear in mind that a receipt printer has a limited line length and so you'll have to deal with that as well.

So some hints for this milestone. First and foremost, making change is hard, especially when you have a limited amount of money in the cash drawer. Generally, I would advise you to write the making change algorithm first without worrying about that limited amount of cash in the cash drawer. Just assume you have everything available and then only if you feel like it, go in and add the extra a little bit to deal with the fact that you might be out of ones and you'll have to exchange a five for some ones and another cash drawer. So read that part of the assignment very closely. It's only worth about five or 10% to actually get the change fully working. So get a bare minimum working and then move on and then come back to it if you have time. Likewise, printing receipts. You have to remember that the receipts have a limited length of characters that you can put on each line. So you may have to truncate or line wrap some of your stuff. You can also use some ASCII characters to do formatting on the receipts to make it look really nice. I've seen some really cool receipts. I've even seen some students do ask you out on the receipts. So feel free to be creative there. 

The other thing I really recommend that you do is use the adapter pattern on this assignment. The adapter pattern allows you to take my library and then wrap it in your own code so that it's more easy to unit test and it's easier to work with inside of your own code. And finally, the source code for the library that I'm giving you is open so that you can check out both the source code for the cash register library as well as the unit tests that I wrote for it that may be useful in helping you write unit tests to test your change making assignment as well. 

So looking ahead after this milestone, we're gonna switch over and start working on some web interfaces. This is where we're going to build a simple web interface for our project that keeps track of the menu and allows us to add custom menu items. After this one, there's going to be smaller milestones. There'll be a lot less actual code in the milestone. So it should take you quite a bit less time to do those milestones and the idea is it gives you more time to be working on your final project as we shift over into November and December and get close to finals week. 

So hopefully things are going well. I hope you get excited the first time that you get the credit card swiper to work in the cash register so that you have the full checkout process going all the way through a point of sale system. That's really the goal that we're trying to get to at the end of this restaurant project. As always, if you have a question, let me know. Otherwise, happy Halloween and I will see you again next week. 
