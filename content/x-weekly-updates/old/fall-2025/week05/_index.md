---
title: "Fall '25 Week 5"
pre: "5. "
weight: 50
---

{{< youtube 0SAcbbkWemA >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week five announcements video for CC410 in fall 2025. This week you should be wrapping up a module on inheritance and polymorphism and playing around with an example on inheritance. Also in this week, we've got a start, stop, continue survey, which I think is one of the really important things I want you to get through in this class. So please take a little bit to work on that. That just gives me some quick feedback on how things are going. And hopefully you've got a little time to work on the final project because we're working on a two-week module. There's going to be a little bit of gap in there. So hopefully you can start working on some final project time as well. 

This week we're going to have a module that introduces debugging and logging. There's going to be a small example around that. We're also going to introduce Lambda expressions, which are really cool. We're going to use Lambda expressions a little bit in our unit testing, and then they come up again when we start building some of our user interface. So you'll do a quick example around that. And then you should be working on your third restaurant milestone as well as scheduling your second final project meeting for sometime toward the end of this month. Yes, we're already there as promised. We're meeting again at the end of September. It happens pretty quickly. 

So big things to keep in mind for milestone three. This is the first milestone where I will enforce all general requirements. That means I expect your code to fully pass a MyPy type check, to have unit testing with a very high level of code coverage, to have Flake 8 with a very low number of style problems, especially in your source folder. The test folder, I'm not so worried about, but the source folder, I definitely want that to pass a flake style check. You need to have unit tests for most everything. You need to have documentation for everything in the source folder at least. And so all of those things are going to bear into account. Ideally, when I run talks on your program, it should get all the way to the end and have a little green message that says everything passed. You'll also be updating your UML diagrams. So there's a lot of stuff going on outside of coding in this one. The actual code for this is only about 1500 lines of code, new or changed. So it's not so much difficult with the code, but it's more the theory and rearranging things to make it work. And then of course, as always, feedback is welcome if you have any questions. 

So like I said last week, big hints for Milestone 3, try and work in small chunks. Commit to GitHub early, commit often. That way, if you screw something up or make a mistake or want to roll back to a previous state, you can do that. You can consider trying test-driven development this time. Write your unit tests before you try and implement them. And my big hint, of course, is it's not clear in the milestone, but make sure you inherit the item abstract class on the base classes. So Entree, Drink, and Side should inherit that item interface, and then all the other classes should inherit from Entree, side, and drink, which will then also inherit item, but you don't have to explicitly do that because of the transitive inheritance. And then, of course, don't be afraid to ask questions on syntax if you have any questions there. 

Looking ahead after this module, we're going to get to module six and seven, which are design patterns and test doubles. Those are, I think, two of the most important modules in this class. So I really want you to pay attention to those. Then we'll switch over and start teaching a little bit of desktop GUI, and eventually we're going to get to some web GUI as well. 

So hopefully you're doing pretty well. I know right now the weather does not feel very cold out, but I'm hoping that soon we will get to the wonderful part of winter where it's nice and cold and snowy. And so instead of enjoying how hot it is outside, we can enjoy how cold it is outside. But hopefully things are going well. As a quick side note for people that watch these videos, I am trying some new microphone settings this week. So if my microphone sounds better or worse, let me know. Hopefully things sound a little bit better. I'm trying some different things to make my mic sound not quite as sharp as it had. So if you have any feedback on that, let me know. I'm constantly playing around trying to get the settings right on this new mic. But if you have any questions, let me know. Otherwise, best of luck and I will see you again next week. 
