---
title: "Introduction"
pre: "1. "
weight: 10
date: 2020-02-28T00:53:26-05:00
hidden: true
---

{{< youtube mJIS9K260_o   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

In this chapter, we're going to learn about how we can use test doubles in our unit tests to make it easier to test classes in our program that rely heavily on other classes working properly, something which we cannot always guarantee to be the case. First, however, let's take a step back and look at the overall structure of a large software system like the one we are building in the ongoing project in this course. Hopefully at this point you've recognized why we started by putting our various classes into packages, as shown in this diagram. By grouping classes together based on their common uses and structures, we can create a program that consists of a few larger subsystems instead of several smaller classes and components. 

Going forward, we can start to look at those subsystems as independent parts of the program, hiding all of the underlying classes and data and instead only looking at the publicly available methods, or the API, or the subsystem when we are working with it. So, from within one particular subsystem, we can ignore most of the internal details of an external subsystem when we are writing our code, and we want to be able to do the same when we are testing our code. That means that we need to have some way to guarantee that the external subsystem works properly, but that's really outside of what we want to deal with. Instead, what if we just replace that subsystem with another one, one that we know will at least look like it works, even if it actually doesn't work. Would that be enough?

As it turns out, most of the time the answer is YES! That's where test doubles come in. A test double, sometimes referred to as a mock, fake, or stub, is an object that we create as part of a unit test that mimics another part of the program, usually one that is outside of our control. So, instead of relying on that portion to function correctly within our test, we simply pretend that it is working correctly by writing a test double that looks and acts the same. It will return plausible results, but many times those results will be hard-coded based on the API of the external part we are mimicking. By doing so, we can verify that our code is working and interacting properly without relying on the external code, making it easier to test individual parts of the program without the entire program actually working or even being completed yet. This really is one of the core ideas of true unit testing - we should be able to test each unit of the code individually, completely independent from the rest of the application. Think back to what we learned about preconditions and postconditions in a prior class. As long as we can guarantee that the preconditions are met, sometimes by using test doubles to mimic other parts of the program, our unit tests should be able to verify that the postconditions are also met once the code is executed.

In the next video, we'll briefly explore three common types of test doubles and see how they can be used in our code. 