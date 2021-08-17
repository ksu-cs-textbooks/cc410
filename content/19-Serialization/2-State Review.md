---
title: "State Review"
weight: 10
pre: "2. "
---
First, let's quickly review the state of a program. Recall from an earlier chapter that the **state** of a program consists of all of the variables and objects stored in memory. So, any time we create a new variable or instantiate a new object in our code, that adds to the overall state of the program.

![State Oracle](../../images/19/state1.gif)^[https://docs.oracle.com/javase/tutorial/java/concepts/object.html]

In the diagram above, we can visualize an object in object-oriented programming as the state, with a set of variables in the center, and the behaviors around those variables defining how we can use, interact with, and modify that state. For example, we could represent a bicycle's state and behavior as shown below:

![State Oracle 2](../../images/19/state2.gif)^[https://docs.oracle.com/javase/tutorial/java/concepts/object.html]

In this diagram, we see that the bicycle is traveling at 18 miles per hour (MPH) and the wheels are rotating at 90 revolutions per minute (RPM). The bicycle itself is in 5th gear. 

However, in most programs, the only things we are really concerned with are the objects stored in memory that represent the core data that the program is using. Consider the example of a word processing program, such as Microsoft Word or Google Docs. In this program, we might consider the document itself as the core part of the program's state that we are really concerned with saving. 

Other items in memory, such as the list of recent changes that can be used to "undo" those changes, and the various view settings such as the current page and the "zoom" of the document, are all still part of the **state** of the program, but we might choose to not serialize that part of the state when saving the document. 

In effect, it is an important design decision to make when developing an application - what parts of the state should be serialized as "persistent state", and which parts are "ephemeral state" that can be easily reconstructed by the user as needed.

Going back to the bicycle example, perhaps we consider the fact that the bicycle is in 5th gear as persistent state that we need to store, but perhaps we don't need to store the current speed.
