---
title: "Fall '24 Week 9"
pre: "9. "
weight: 90
---

{{< youtube c7d5TZwVLdE >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Edited Transcript

Hello and welcome to the week 9 announcements video for CC 410 in fall 2024. I'm coming to you this week from my office on campus because I'm on the road a little bit so hopefully the quality of the video is not too bad and I can at least get the point across. So this week you should be working on a module all about parallel programming and doing an example of doing parallel programming in either language that you're working on and then we'll shift over and do some work with event driven programming which is the paradigm that we use a lot in graphical user interfaces. You'll do an example around that and then you'll be working on the seventh milestone in the restaurant project which adds some interactivity to your user interface that you built in the previous milestone. 

So with this we actually run into some testing issues. The biggest thing we run into is that the Codio boxes by default only have 512 megabytes of RAM which is not an awful lot when you start running unit tests with a graphical user interface. So there are a few things that you can do to actually get around this. In Java if you find that you run into issues you might try the Gradle dash dash stop command to make sure there are no Gradle projects running in the background or you can also go to the project menu and choose the restart box option which will restart the underlying Codio box and then refresh your browser once that is done and then it should clear out any memory that you're using in Java. In Python we can get around this by running our tox tests in batches. I show a couple of examples of how to do this in the example projects and I believe I also have some documentation in the textbook that gives you an example tox file that you can base your work off of If you have any trouble getting that to work or you're not sure feel free to ask me and I will happily help you set this up so we can get around this. Of course the other thing you can do is if you're set up to do this class on your local machine you can actually get around this without any issues itself but when I run the tests in Codio for grading I'll kind of look for this or I'll configure it real quick so it should work. So if you have any questions for this just let me know. 

So looking ahead from here in modules 10 and 11 we'll finally refine our user interface to add a few more features to it around combos and orders and getting everything such as the checkout process included. So module 10 we're going to integrate an external library that mimics a cache register and then in module 11 we'll actually learn how to build a release of our project and get it available before we shift gears and start talking about web APIs and things like that toward the end of the semester. So we're getting close to the end of the semester we're starting to get to the downhill slope so hopefully things are going well. As always if you have any questions or concerns let me know. As I hinted earlier in this video I am on the road a little bit this week so my availability is less than normal. Feel free to check my calendar to see what times I'm available or email me or email the help address and let me know you'd like to meet and I will try and find some time that I can meet with you while I'm on the road. So if you have any questions let me know otherwise good luck and I will see you again next week. 
