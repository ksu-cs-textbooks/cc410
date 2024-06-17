---
title: "Fall '23 Week 12"
pre: "12. "
weight: 120
---

{{< youtube sSK6fkM5aTo   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript


Hello and welcome to the week 12 announcements video for CC410 in fall 2023. As you can tell, I've been a little bit under the weather, so apologize for the voice. But hopefully we can get through this pretty quickly. This week you should be working on learning about releases. We'll do a quick example on actually creating a release out of a project that we've created so far. And then in the restaurant milestone, you'll start working on an external library where we're adding features to actually do the checkout process at the restaurant. It's really cool. So milestone nine is all about adding a checkout. You're going to work with an external library that I've written that simulates a cash register and a receipt printer. You'll be able to check out using cash or credit card. You're going to write the algorithm for making change and being able to pop up how much change to give. And you're going to print a nice friendly receipt for the customer as well. 

So milestone nine, there's a few hints. First big hint is making changes hard, especially because the cash drawer has a limited amount of each denomination in it. In general, don't worry about that right now. Write the basic making change algorithm. If it crashes after a few times, that's fine. Only try and build in the part where you can make substitutions for different denominations if you have time. For example, if the cash drawer runs out of pennies and you need to turn a nickel into five pennies, you can do that. But be careful. It's really, really tricky. So don't worry about that. It's not worth many points. But if you want to attempt that, you can likewise with the receipts. Remember, the receipts have a limited length of the line. So each line can only be a certain number of characters. So make sure you read the instructions for that and figure out the best way to represent your receipt. 

I really recommend using the adapter pattern for this. You can go back and look at the module on design patterns. So you can take the register library and then you can either wrap it in an adapter class or you can extend it. Either one of those works. I really like wrapping it in a wrapper class. That makes it really easy. And then you can also read the unit tests that I wrote for the library. All of the code is open source. You can find the code for the receipt, the restaurant register library out on GitHub. It's out there. You can see how I wrote my unit tests. That might be really helpful for you to understand how to interact with this library. you So looking ahead after this module the next one we're going to switch gears and we'll start working on web interfaces That's the start of a bunch of smaller milestones, which gives you more final project time I apologize. There are two milestones that are due right after Thanksgiving It's just because I left the gap in the schedule and I missed it until we got there But it shouldn't be a problem those milestones are very quick and easy to get through So hopefully everything works. Hopefully when you're scanning your credit card you get excited that it's a match If you have any questions or concerns, let me know otherwise best of luck this week And hopefully you can get through the next couple weeks and make it to Thanksgiving. Good luck 
