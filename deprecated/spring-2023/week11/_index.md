---
title: "Spring '23 Week 11"
pre: "11. "
weight: 110
---

{{< youtube seQaCv9hzWI   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week 11 Announcements video for CC 410 in spring 2023. My apologies for being a little bit behind this week, but I'm going to get this video out on Thursday. This week, you're going to be looking at releases, we're going to talk a little bit about how we can actually build a releasable version of our project. So we'll do a quick example around that. And then we're going to do the ninth restaurant milestone where we're adding the features to actually check out and pay for our order. 

So the ninth milestone, like I mentioned is checkout, we're going to include an external library that represents an actual cash register, that cash register allows you to pay by cash or credit card, the credit card part is pretty easy. That's what we do in the example project. But then if we want to pay by cash, we have to figure out how to make change. And then in either case, we also have to figure out how to print a receipt. Thankfully, the external library has functions to handle all of this. But we'll need to figure out how to use that library and how to adapt our data and what our application is doing to actually fit the requirements of that library. So some quick hands for milestone nine. First and foremost, making change is hard. The actual calculation isn't that bad. But when you have to take into account the limited amount of denominations in the cash register, that can be very, very difficult. One hint that a lot of people mess up is that you should only instantiate the cash register once when you start your application, not each time you make a new order. And so you'll have to watch for that. The receipts, each line has a limited length, I think it's 40 characters or something. So you'll have to figure out how to truncate or limit the size of your receipts and do some text formatting. So three seats look nice. 

I really recommend in either case, using the adapter pattern so that you can adapt the library and have your own wrapper around it and call those functions. And I encourage you to look at the source code for the library that I provided you it's all open source, including the unit tests, the unit tests will give you a good idea of some things you can do to actually test your code and make it a little bit better. The other thing that will really tell you I'm making change, don't worry about the edge cases, first, just get it making change without worrying about if you run out of pennies, or nickels or something, get that base case working and get it tested before you try and add the other cases. The other cases are not worth that many points. So don't worry about it too much if you don't get there. Looking ahead after this milestone, we're going to switch gears and start talking about a web interface. The web interface milestones there's about three or four of them, they're going to be a lot smaller milestones about half the size of the current restaurant project milestones, and it's meant to give you more final project time. So from here on out, we've got about five weeks left. Hopefully you starting to spend more time working on your final project and getting that up and running. 

So hopefully everything goes well like the target lady, you get really excited every time the coupon matches of the credit card swipes properly. Hopefully things are going well in the restaurant project. I know a couple of you are a little bit behind but you're getting caught up pretty quickly. As always, if you have any questions, let me know and I look forward to seeing you again next week. 

