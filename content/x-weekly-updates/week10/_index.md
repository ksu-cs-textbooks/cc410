---
title: "Fall '26 Week 10"
pre: "10. "
weight: 100
---

{{< youtube AeoP7Fly3oU >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript

[00:00]
Hello and welcome to the week 10 announcements video for CC410 in fall 2026. So this week you should be working on an example around external libraries where we're going to bring in a cash register library that I actually wrote to simulate a cash register for a project. And then you're going to integrate that into the restaurant milestone for milestone eight.

[00:24]
We also have another chance to fill out a start-stop-continue survey for this class. As a quick reminder, that's just a very low-barrier-to-entry eval. If you have any feedback for me on things you want me to start doing, stop doing, or continue doing, totally anonymous. It's collected through Qualtrics. I can't see any information about you, but it gives me a quick opportunity to get some feedback from you if there's anything in this class you want me to change.

[00:46]
So for milestone eight, you're going to update the sidebar in your user interface for orders to handle things such as combos. You're going to add combos to your user interface as well, as well as some basic unit testing for some of those. And you're also going to build the factory method. This allows you to actually have a factory method class that will create the different UI panels based on button clicks in your UI. It makes your UI code a little bit cleaner and a little bit more repetitive.

[01:10]
So hopefully this milestone works out. This is adding some of the complexity to the user interface. Generally, students do OK on this milestone. But big thing is make sure you're testing it in your UI, actually clicking the buttons, going through the process, making sure that it all makes logical sense as you work on this milestone. Another quick thing that's going on is not this week, but next week, the example has to do with creating a release. So to do that, we're going to create one more GitHub repository for you for releases. So watch your email for the invite for this GitHub repo. I'm going to send that out very shortly today. Make sure you accept that. If you don't accept it, I have to resend it after seven days. It's not a big deal. You just have to email me.

[01:53]
But for this example, the starter code is still going to live in Codio. The repo will be blank. What you'll do is complete the work in Codeo and then push that to GitHub. And then in GitHub, you'll make a GitHub release and make the documentation available and some other steps like that. So you can actually play around with creating a real release in GitHub.

[02:10]
So other big thing to remember, most everybody has figured this out at this point. But if you're having any trouble with the user interface, make sure that you're on port 3050. Just look at your web browser address. If it says 300, change it to 3050. I believe I have updated that most places that it needs to be updated. The other big thing is you have to open that GUI viewer in Codio before you can start your program. Basically in Codio, it does not launch the user interface parts, all the libraries in the background until you load that viewer program. And so you have to load the viewer before you start your program. And then the third thing you'll need to do is run the command `xhost +` in your terminal one time every time you start Codio before you can run any tests. That just allows talks to access your user interface as well.

[02:54]
And so as we go into building unit tests for our user interfaces, we'll run into some problems with the limited memory in Codio. If your Codio ever acts like it's crashed or is acting really slow, you can go to the project menu and hit restart box that will restart the underlying Codeo instance that you're connected to. And then just hit the refresh button in your browser to clear out your browser cache. That generally helps. For Python, what we're going to do is we're going to run our tests in batches. And so I show you how to make an update to the tox file to run multiple sets of tests individually, and then conglomerate all those together into a single result.

[03:24]
Other big things, just like I said in the previous one, if you're running tests, make sure you run `xhost +` at least once in your terminal before you run tox. And you'll also need to make sure you have the GUI viewer open in the background in another browser tab before you can run tox as well so that those tests will actually run.

[03:42]
Looking ahead after that, we've got a couple more modules on graphical user interfaces. We'll talk about building a release and building the checkout process very soon. And then we're going to switch over and talk about web user interfaces. And so once we get to module 12, that's where the restaurant milestones will become a lot smaller. And so you'll have more time to work on your final project. Bear in mind, we're on week 10 of 17 in the week, if you include the Thanksgiving week. Otherwise, there's 16 weeks in the semester. So we've got about six or seven weeks left. Now is the time to start thinking about working on your final project and getting up to speed on that so you're ready to go.

[04:18]
Other than that, hopefully things are going well. We're getting to the point where you can actually do a full restaurant simulation with our project. It should be fun. As always, if you have any questions, let me know. Otherwise, good luck, and I will see you again next week.