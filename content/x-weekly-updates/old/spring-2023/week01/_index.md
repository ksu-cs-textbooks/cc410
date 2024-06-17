---
title: "Spring '23 Week 1"
pre: "1. "
weight: 10
---

{{< youtube iq55Ll2fU4M   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week one Announcements video for CC 410 in Spring 2023, my name is Russell Feldhausen. And I'll be your instructor this semester. My contact information is here on the slide, you can email me anytime you can also contact me, I generally work remotely, I usually am at home in Shawnee, Kansas near Kansas City. But I'm usually on campus on Mondays. So most of the time you're working with me I'll be remote, we can meet via zoom anytime we want. If you want to meet with me in person, you can do that usually on Mondays when I'm on campus.

 So the big picture for cc 410 is all about building up your skills in object oriented programming. We're going to spend a lot of time learning how to structure large programs, with a lot of classes and a lot of different things going on, we're going to learn about testing specifically unit testing, we're going to learn some design patterns that are very common in software. Then we'll shift gears a little bit and spend some time learning about graphical user interfaces or GUIs. We'll learn a bit about web interfaces. And we'll spend some time on serialization and some other topics. The way this class is taught is each week or each module will have some sort of textbook section followed by a quiz, then we'll have an interactive example. Generally the example you'll just follow along with me, I work through the example in a video that takes about an hour or so. And then when you get done with the example we'll have a long form restaurant project that consists of multiple milestones. And throughout the semester, we'll build up that project one milestone at a time until we get a fully working restaurant point of sale. At the same time throughout the semester, you'll be working on an independent final project. We'll talk more about the final project when we meet in person a little bit later. But for right now, don't worry too much about the final project, just be aware that there's one out there that's coming towards the end of the semester. 
 
 So in this class, we're going to introduce you to a lot of new technologies you haven't used before. First and foremost, you'll be using Git and GitHub classroom to store all of your code. This is one of the tools that you use in professional software development. And it's really important for you to get comfortable with it. So you'll learn how to use Git and GitHub classroom will also use an automated build tool for Java, you'll be using Gradle, which is one of the more common tools for Python, we're going to use tox, which I think is a pretty good tool for Python for that. For Python, specifically, we'll also introduce you to formal type checking in Python, it's something you haven't had to do a whole lot of right now, Java developers, you're already pretty used to type checking, so you don't have to worry about that too much. Unit testing is going to be brand new, it's how you can write software to actually test the software that you're writing. We'll also spend some time talking about programming style and doing style checking, and also writing documentation comments in your code. 
 
 So like I said, the final project, you get to choose the topic for the final project, the goal is to have it aligned with your interests in some way, and use the new skills that you learned in this class to actually demonstrate that you've really learned how to build some software on your own. You'll meet with me a few times throughout the semester, for the different milestone check ins via zoom, we'll discuss the scope and I'll kind of give you some pointers on exactly where you can go. And then at the end of the semester, you'll deliver a presentation as part of your final project. 
 
 So this is week one week one is mostly administrivia. Just going over the basics of the class, you'll also go through the Hello real world example where we'll build up some of our development environment for this class. You'll also be able to schedule the first final project meeting for either this week or next week, where we can meet one on one to discuss final project ideas. Don't be afraid to to look at the office hours. I don't have any formal office hours for this class, but you can schedule a one on one meeting with me using Calendly. Anytime. Since there's only three people in this class, I think that will work out much better than trying to have a formal Office Hours period. We also have a lot of discussion platforms that you can use my primary platform for this class is discord. So you'll have a chance to introduce yourself on Discord and say hi, you can also chat with me via email anytime. I'm also on the K State instance of Microsoft Teams. So if you use teams, you can also DM me there whatever works for you. But Discord is a great place for having whole class discussions. 
 
 After that, you'll shift into week two, you'll spend some time writing a class library and object oriented formatted for the restaurant project. That project is about 2000 to 2500 lines of code, which is already several times larger than the largest project you've probably done so far in the computational core program. A lot of it, however, is boilerplate code. So once you get one class built, you should be able to copy and reuse a lot of that code. But you have to be a little bit thoughtful about how you copy paste and be really careful and make sure that you get everything changed and updated. Because being careful now makes next week a lot easier. 
 
 The week after that on week three, you'll spend some time learning about unit testing and documentation. You'll add full unit tests to all of your class library, you'll also add full documentation comments. So depending on where you're at, that could be 3000 to 4000 additional lines of code. My model solution from a couple of semesters ago took 423 unit tests. However, a lot of those unit tests again are repeats. So you can copy paste and reuse a lot of the code and it's a really good chance to catch errors. One reason that we're doing projects this big is part of the point of this class is to get you used to working on large code bases. And so one of the things we have to do is have you write a large amount of code so that you learn some of those tools and techniques for how to manage large code, code bases, how to carefully copy paste how to reuse things, and how to really build stuff in an object oriented way. Then we'll shift to week four, and five will add some inheritance and polymorphism to our class library, you'll also develop the UML diagram to represent it. This is about 1000 lines of code, and a lot of it is just refactoring old code and simplifying the structure. In fact, sometimes you may even remove about as many lines of code as you add. 
 
 And then on week four, and five, we'll actually have our second final project milestone where we'll talk a bit more about what the final project will look like now that you've seen a few of the milestones in the class. So that takes us all the way through the end of February. After that, you're going to learn about graphical user interfaces, libraries, web serialization, and a bunch more throughout this class. 
 
 So this semester, I'm making some big changes and some small changes to the class. The Big changes are I'm trying to split some of the larger milestones into smaller milestones. Previously, in the last couple of semesters when we got to the GUI part, I had two really large two week milestones, and I'm going to split those into four smaller one week milestones. Hopefully that helps you stay on task a little bit better. I'm also doing that to move some of the content around I'm going to try and pull the stuff on more advanced unit testing and undesigned patterns, I want to pull that forward. Before we start talking about GUIs. I'm hoping by doing so the class will be a little bit more streamlined. However, there might be some hiccups as I get everything figured out, we might have some examples that I have to rerecord things like that. So please bear in mind that I'm doing some changes in this class, but I'll work with you to make it as painless as possible. And a lot of this will start with module six, which is the module you'll start on at the end of February 1 of March. 
 
 There's also some small updates behind the scenes. In Code yo, I've updated the stack that we're using. So now in your load, your Codio box will be running on Ubuntu 22. With Java 11, and python 3.10. It shouldn't really change anything. What you've been learning in computational core program is compatible with all of this. But it does mean that some of the versions are a little bit different than what you're used to. This also implicates all of the examples. The examples have some hard coded stuff in there that is relative to a particular language, I'm going to go through and test and update those, but it may take me a little bit. For example, my goal today is to work on the Hello real world project. So there may be some updates that ASU for that very quickly this week as I get some of those fixed. So bear in mind, there's some changes, I'm working through all of the code to make sure that it's up to date. 
 
 So some advice for this class. This is a four credit hour class, which means you're expected to work around 12 hours each week on the class. That's four credit hours of actually in class time of watching lectures watching examples reading the textbook, plus another eight hours of working on the projects, I've tried to build the project milestones, so I expect any student can complete them in about eight hours. Most of the project milestones I can code through in about an hour to an hour and a half. So I figured that that gives you plenty of time to work through it. However, because it's a four credit hour class, and it is a programming class, it might feel very heavy, it's a bit a bit larger than classes that you're used to. So I really encourage you to take the time now and schedule your time wisely. To help with that I've added a time management sheet in into the files and into the modules for this class. Basically, you can fill out a sample week for you and make sure that you've got 12 hours of time to devote to this class. And then on the backside, there's a whole semester calendar that you can fill out so that you have an idea of what your due dates are, what the requirements are, you can fill that out through Week Five right now that's already posted. And you'll be able to fill the rest of that out as I post the rest of the modules. As far as each individual module, I really encourage you to start early and leave time for questions. Most everything in this class is due on Mondays. And so you'll basically have all week to work on it the weekend to work on it and then you'll have a chance on Monday to get questions answered. But if you wait until Friday to start and you get stuck very early on, you may not have time on Monday after I answer your questions to really get going. I will try and answer emails over the weekend as I can, but I don't guarantee it always there are some times when I'm out of town over the weekend. I do guarantee email responses within one business day. So if you email me after hours on Friday, it might be Monday before I can get back to it. I will try and do better than that. But that's what I can guarantee. Another piece of advice I can give you is to copy paste carefully. There are a lot of instances where you can either copy paste example code or copy paste your existing code and adapt it to a new class. However, you have to be very careful when you do that. Make sure you get your variables updated your class names updated. Sometimes debugging a pile of copy pasted code can be more frustrating than just rewriting it from scratch. Another tool that you can use is Git will show you how to use Git to store your code. One thing that programmers learned sometimes the hard way is to commit to get frequently anytime you have something working anytime you have a file finished, you know multiple times throughout a milestone you should be able to save and commit your code to get that way as you continue to work. on future stuff, if you break something, you just roll back to that commit, no big deal. So programmers will tell you that you should commit to get, you know, about every 30 minutes to every hour, whenever you get something working you should be committing to get. The last thing you can do in this class is used and cite online resources. There are a lot of resources out there for learning more advanced forms of code, I encourage you to go read through those. And then if you do use any code from those, you should cite those, again, the same rules apply. Don't copy paste code, that is the point of the assignment. So if I'm asking you to write a bunch of unit tests, do not copy a whole unit test suite in there. That's plagiarism. I don't want to see that. But if you can't remember how to reverse a list, or you want to know something, that's you know, a little thing that you can find on StackOverflow go look that up, learn how to do it, and then cite the resource that you use to learn that that's a very common thing you'll see an industry and I want to encourage you to do it here. 
 
 So that's really all I got, um, beyond that you can keep in touch with me via discord. If you haven't signed up for discord already, please do you can go to discord bot.cs.ksu.edu. To register your eID with the discord system, it will match those two things up so you can get into the discord. There's a channel there already for CC 410 that you get to post a little introduction in as part of the first assignments. Another good way to keep in touch with me is tea time office hours. We're bringing that back this semester. So every Tuesday at 330. And every Friday at 1130 will open the Zoom Room for an hour. So it'll be me and David Invirgo one of the CS advisors will also have some other CS faculty and staff hanging out and we encourage students to come hang out. It's a great time to just hang out chat, get to know your fellow students ask questions about life, the universe and everything, whatever we can do to help. And then of course, you can schedule a one on one office hours with me anytime using Calendly that you can find either on the syllabus or on the homepage of Canvas. That's all I've got. For this first video. I'm rooting for you. I hope things go well this semester. I look forward to meeting each of you one on one via zoom when we have our first final project meeting later this week or next week. In the meantime, feel free to get started on the coding, introduction and hello real world example. A lot of that is due either this Friday or the coming Monday. So make sure you watch those due dates. Those come up very, very quickly. If you have any questions, comments or concerns, feel free to email me anytime. And otherwise Watch this space for a new announcements video probably every Tuesday morning throughout the semester. I'll try and be pretty good about getting those posted sometime before noon. So I look forward to working with you and I will see you all next week.