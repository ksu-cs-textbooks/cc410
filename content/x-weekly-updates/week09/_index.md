---
title: "Fall '25 Week 9"
pre: "9. "
weight: 90
---

{{< youtube 1RKMCuK6ccY >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript

Hello, and welcome to the week nine announcements video for CC410 in fall 2025. This week you're going to be working on some parallel programming examples to give you an idea of how we work in multi-threaded environments. We're also going to do another example on event-driven programming, which is how we actually add interactability to our user interfaces. And then finally, you're going to do a restaurant milestone where we're going to take the user interface that you built last milestone, and we're going to add some event-driven programming to it so that the button clicks actually work and it actually starts doing what we want it to do. 

So, one thing you might run into in this particular milestone is issues with testing. The biggest problem we run into is the Kodio boxes have limited memory. A lot of them only have 512 megabytes of RAM available. Because of that, we can't just spawn off a whole bunch of tests and expect it to work. For Python, the biggest thing that we're going to do is run our tests in batches. And so I show a little bit of how to do that in the project and in the milestone. Basically, it just involves adding more unique commands to your tox file so that you run the tests in individual batches instead of trying to run them all in one shot. If you have any trouble getting your unit tests to run nicely in Kodio, just let me know. I'd be happy to help you with that. 

So looking ahead after this, the next couple of modules, we'll finish up our user interface by adding in some external libraries and building a release version of our app. And then after that, we're going to switch over and start working on web APIs and some other information as we get toward the end of the class. And those modules are also designed to be a little bit smaller to give you more time to work on your final project. So we're close. We're getting there. We're slowly getting toward the end of the semester. We're at week nine right now. So hopefully things are going well. As always, if you have any questions, let me know. Otherwise, best of luck. And I will see you again next week. 

