---
title: "Spring '22 Week 9"
pre: "9. "
weight: 90
date: 2022-03-21T00:53:26-05:00
---

{{< youtube 6ThLHVt-FKE >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week nine announcements video for CC 410 in spring 2022. So we're just getting back from spring break, and you're still working on the same module as before. So this week, you'll be working on design patterns and test doubles. And you'll also have an example around using patterns and test doubles or mocks in your projects. And then you'll start working on milestone six, you have two weeks to work on milestone six. So it's not due until the end of next week, which is March 28. And then by the start of the next week, on April 1, you should meet with me again for your third final project check in. 

So remember, milestone six is all about adding orders and combos to the restaurant project. An order is a way to keep track of all of the things that the user has ordered. Right now we're putting those in the sidebar in our GUI, but we're not actually keeping track of those in an object. So now we'll make an object for that, we're also going to have the ability to create a combo where they can have an entree side and the drink all put together with a discount. And we're going to do that to test out a lot of design patterns. And so in your project, you'll get to use the factory method pattern, the builder pattern, the singleton pattern and the iterator pattern. And then you'll also write unit tests for those new projects. And you're going to use test doubles, so mock objects, fake objects, things like that, to work along with these patterns. To go along with all of that there's very few changes in your user interface itself, just mainly adding these different parts onto it. But this adds a lot of the remaining functionality to your project except for the checkout process, which we'll do in milestone seven. 

So some big tips for milestone six, there are a bunch of different things you're doing. And I really recommend trying to tackle one piece at a time in to get that working before you try and move on to the next, it's probably easiest to add orders first. So that's doing things like the singleton pattern. And then once you get orders done, then you'll add combos. Oh, and the orders also does the iterator pattern as well combos, then you'll be adding the builder patterns and adding combos to your menu. And then you'll add the panel factory doing the factory method pattern third. And so if you get each one of those working in turn before you start the next one, it should work really well. I encourage you to make unit tests as you go, you can even try some test driven development by writing tests before you work on your code. And then once your tests pass, you know your code is working the way you intend it. And it's also a really good chance to practice documenting your code and fixing style as you go. It's much much easier to do that a little bit at a time as you go, instead of having to spend a few hours at the end of the milestone doing all your documentation and style fixing all at the same time. 

Also, this project, you might run into some testing issues. So this is due to the limited memory of Codio boxes where they're limited to about 512 megabytes of RAM. In Java, if your Gradle ever crashes, you can hit CTRL+C to stop it and then do Gradle --stop in a new terminal and that will stop Gradle running, then you can go to Project and restart the box and then refresh your web browser to clean things up. In Python in tox, the easiest way to fix this is to simply run the tests in batches that seems to work really well. And of course, you can always develop things outside of Codio and I've just released some videos a couple weeks ago on how to install a local IDE and get these projects working. They're focused on Windows, you can probably do something very similar on Mac or Linux. If you're on either of those systems, let me know and I'd be glad to help you out to figure that out. 

So looking ahead after this week, once we get done with this module, you'll have a couple more modules on libraries and releases. And then milestone seven. We'll cover some of that. And then once we get past that, then we'll start working on web API's and other things. This week is a two week milestone. The next milestone is also a two week milestone. And then after that things will really ramp down and you'll have some more time to work on your final project. 

So here we are. It's the Monday after spring break. So hopefully didn't hit you too hard. But now it's time to get back to work and start working on the rest of the semester. As always, if you have any questions, let me know and I will look forward to seeing you again next week. 

