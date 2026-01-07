---
title: "Fall '25 Week 11"
pre: "11. "
weight: 110
---

{{< youtube -29XMW85KYU >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week 11 announcements video for CC410 in fall 2025. So, this week we're going to work on another project all about building a release version of our software. This is a packaged version of our software that we can provide to other people that aren't programmers and allow them to use it as quickly and easily within their own projects as we would in ourselves. So we're going to use a quick example of releases and then we're going to update our restaurant project by adding a checkout library to help us actually finalize the sales process of our point of sale system. 

So for Milestone 9, we're going to insert an external library. We're not going to build a release version ourselves, but we're going to insert a library that is a release version of a Python library. It's going to simulate allowing you to pay with cash your credit card. Obviously, with cash, you need to do some work to make change. And then, of course, it also has a library for printing a receipt. So we're going to build all of those things into our project. 

Some big hints for this milestone, making change is hard. The algorithm for making change can be a little complicated, especially when you're dealing with the real world situation where the cash drawer has a limited number of each digit. So what I encourage you to do is make change, assuming you have infinite numbers of each denomination of currency, and then only if you have time and get that working should you try and do the thing where you actually deal with the case where you might be out of ones and have to substitute a five for five ones and things like that. The other thing you'll need to do with your receipts is each line on the receipt has a limited width. It's in the documentation, so make sure you think about that. You can truncate your code or have it wrap down to the next line. 

In both of those cases, I encourage you to use the adapter pattern that we learned earlier this semester in our discussion on design patterns to wrap the change drawer and the receipt printer in an adapter of your own code. And then, of course, you can write unit tests against your adapter functions and then just have an untested function at the end that actually does those changes on the change drawer. So for example, you have an adapter function that figures out all the changes to be made and returns a dictionary of all the things to be updated in the cache drawer. You can unit test that code and then have a separate function that just applies those changes to the cache drawer. Same thing with the receipt is have a function that generates a list of strings that will be printed to the receipt and then have a separate function that actually prints those strings to the receipt, but you can test the first one. You can read the unit test for the library that I provide. It gives you some insight in how I do some testing for these things, might give you some ideas for what you want to do in your code. 

So after this module, once you get this done, we're going to switch over to doing web interface. So those next milestones are going to be much smaller and give you more time to work on your final project as we get toward the end of the semester. So hopefully everything's going well. Hopefully you're able to get your credit cards and cash checkouts to work and are just as happy as the Target Lady. As always, if you have any questions, let me know. Otherwise, best of luck this week and I will see you again next week. 