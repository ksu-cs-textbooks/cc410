---
title: "Fall '22 Week 3"
pre: "3. "
weight: 30
---

{{< youtube heHNjm6WPeU   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week three announcements video for CC 410 in fall 2022. This week you should be wrapping up module two, which is all about object oriented programming. You've also got a quick example on object oriented programming. And you're also going to be diving deep into the first restaurant milestone. Hopefully all of that is going well. But if you have any questions or concerns, feel free to let me know. I'll be grading those over the next few days this week and leaving lots of comments both in Canvas for the grading and in GitHub on your code. So make sure you check both of those places to see all of my feedback from milestone one on the restaurant project, you'll have a chance to make some of those updates as part of milestones two and three, as we go ahead. 

So this week, we're going to dive into some other topics related to programming. Specifically, we're going to focus on documentation and testing, we're also going to do a quick review of the Unified Modeling Language or UML, which is a great way that you can document the structure of your program. We're also going to do a quick example on adding documentation and doing some unit testing for an example project. And then you're also going to start working on the second restaurant milestone, which is Milestone Two. So hopefully that goes well. 

Milestone Two is all about adding unit tests and documentation to the code. My estimation is there anywhere from 300 to 400. Unit tests, maybe even a few more than 400 unit tests that you'll add to your project. You'll also add documentation comments to every method, every class, every file, you'll have class diagrams that you'll add. This milestone I estimate, once again takes about three to eight hours depending on your comfort level and familiarity with the content. In this one is very large, there can be anywhere from 3500 to 4000, lines of code that you touch. Some of those lines are obviously just comments, a lot of those are unit tests that you can copy, paste and tweak. And so try and think ahead, one of the things I really recommend doing for this milestone is picking one of the large entree classes writing all the unit tests for that one. And in most of those tests, you can copy and paste and tweak a little bit for the other entrees. The same goes for the drinks on the side. So it's a lot of repeated code with little tweaks. So make sure you think about how you can do that in a more intelligent way instead of just writing the code by hand in every class. 

So some other big hints for Milestone Two. First and foremost, do not look at your source code, I really want you to write these unit tests based on the specification that was in Milestone One, not by looking at your source code. What happens if you look at your source code is you ended up testing what you wrote, instead of what you should have written. For example, making sure that the prices are correct making sure that the calories are correct making sure that things are spelled correctly, you want to go back to that original source document and write the tests based on that not based on the code that you wrote. Another thing you can do is you can use Global attributes, I'll show an example of that on the next slide, you can try and generalize some of your tests a little bit. But don't try and generalize the individual ingredients in the entrees that's really difficult. And also you can look at using parameterised tests across the enums. So we have a few enums that we're going to use in our object oriented programming. And you can parameterize a test so that it tries it with each possible enum value to make sure that it works. 

So this gives you a quick idea of what a generalized test would look like this is from a few semesters ago. But in this case, we have a menu item that has a price and a calories. And then we have tests that will check to see that the price is correct, and checks to see if the calories are correct. And so instead of embedding the price and the calories in the unit test itself, I've made those global variables in the test class at the top. And so what I can do is I can copy paste this entire piece of code into another class and just change those variables. And then we'll be able to reuse a lot of the code without having to tweak each individual line of code to do the same test. So this gives you a quick idea of one way that you can restructure your code to make it a bit easier. 

So looking ahead from here, and the next few milestones will cover inheritance next time, we'll have a module on debugging. And then at that point, we'll be at the end of September, and we'll be working on about the second final project milestone, then we'll shift over and we'll start talking about graphical user interfaces and event driven programming, and lots of things to go down the road from there. So hopefully, this unit testing module gives you a lot of experience working with unit tests and how you can actually write code to test that your code works properly. It's a really important concept in software development. And it's one of the things that I really encourage you to learn. Writing good unit tests will help make your code better because you know how to make good testable code. As always, if you have any questions, let me know and I look forward to seeing you again next week.
