---
title: "Spring '22 Week 11"
pre: "11. "
weight: 110
date: 2022-04-048T00:53:26-05:00
---

{{< youtube Xo1j_PZWKEs >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week 11 Announcements video in CC 410 in spring 2022. So this week, you should be finishing up milestone seven, which is all about checkout. And you'll also be doing a quick example on building a release of your project. This is a really great opportunity to learn how to package your software up in a way that other people can use it. And I'm hoping later this semester, I can give you some pointers about adding some automation and GitHub actions with your releases as well. I'm prepping that for another class, but I'm going to try and share it here. But either way, this is really useful information for you as you get out into industry. 

Don't forget, for milestone seven, it really comes in two parts, you have the first part, which is adding all the GUI options to add an edit combos to your order, you'll need to update some of your other GUI panels. But hopefully you can reuse a lot of the code that you've got, it's just about rewiring it in a different way to work with combos instead of just single items for your orders. Then the second part is adding the checkout functionality to your project, we went through an example of doing the credit card parts of this. So hopefully that should work. And then you're going to add the cash part and the making a receipt part. Make sure you focus on getting this to work as best you can, it doesn't have to cover all of the edge cases, because there's not a ton of points there. I also really encourage you to use the adapter pattern, it's in the book of patterns that you can look at, you can also just Google it online. But basically you make a wrapper around the library that I provide and the new call functions in your wrapper that call functions in my library. And then in between there, you can do your own logic. And that's the stuff that you can unit test. So hopefully you can get that working. If you have any trouble, please let me know. 

But like I said, focus on the basic ideas first, and then dive into the little nitpicky edge cases and things like that. So I went through a lot of these hints. Remember making changes hard receipts have limited length, do your best to use the adapter pattern and read through the library's code and the unit tests that will give you a lot of good ideas of how to complete milestone seven. So after this milestone starting next week, we're going to shift over and do some milestones around web interfaces. Thankfully, these milestones do not depend a whole lot on milestone six, and seven. So as long as you are good up through about milestone five, the Web Interface kind of picks up from that point. So don't worry too much if you have little bits and things that don't work so well in milestone six and seven. That's pretty common in this course, because we'll shift over the web. Also, you'll have smaller, smaller milestones from here on out, which gives you some more time to work on your final project. We're getting to the point where you have about five weeks left in the class. So make sure you're starting to schedule time to work on the final project and ramping up on that, especially after this week. 

So hopefully that works for this week. You've got any questions you can let me know. I always like this gift because as you're testing your credit card thing, it gets kind of frustrating that it doesn't work all the time. So hopefully you get really excited when it's a match and the credit card is approved and you're testing and as always if you have any questions, let me know 