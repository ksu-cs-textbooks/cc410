---
title: "Requirements Elicitation"
weight: 25
pre: "5. "
---

On the previous page, we discussed the software development life cycle. One of the most important, and often overlooked, steps in those processes is [requirements elicitation](https://en.wikipedia.org/wiki/Requirements_elicitation). Requirements elicitation is all about determining what the users or customers want from a piece of software that is being developed. While this might sound simple, it can actually be one of the most difficult steps in the whole process. In addition, since it is generally the first step in any new software development task, getting this step right can make everything work smoothly, whereas even a small problem at this step can cause the entire project to fail. 

## The Difficulty

One of the major issues with gathering requirements is that many times the users or customers themselves are not well trained in technology or programming themselves, and therefore they don't have a good idea of what is possible, impossible, or even impractical, when developing a new piece of software. Likewise, they may not be able to fully articulate exactly what they want from a new piece of software, or they might ask for something that they think is achievable without discussing the actual problem they'd like to solve.

This problem is well summed up by the following XKCD comic:

![XKCD 1425: Tasks](/images/20/tasks.png)[^1]

[^1]: https://xkcd.com/1425/

Here, we see a user asking for two things that seem similar - when the user takes a picture using a mobile application, can we determine where it was taken and what is in the picture? Sounds simple, right? 

However, to a programmer, those two questions are actually asking for vastly different things. On the one hand, most phones today support GPS, so the mobile app can simply capture the user's current GPS coordinates when the picture is taken, and then check to see if those GPS coordinates lie within a defined national part boundary. So, this can be easily done with just a little bit of work.

On the other hand, how can we determine if there is a bird in a picture? This is a computer vision problem, and is definitely still an unsolved problem as of 2021. There are some very advanced algorithms available today that can perform facial recognition on people, but they require massive amounts of data for training and testing, and even then they aren't perfect. Our ability to recognize other objects is even more limited, but it is slowly getting better. Projects such as [Google Lens](https://lens.google.com/) demonstrate what can be done currently in this field. So, expecting a mobile app to perform this task is not really feasible at the current time, but perhaps in the future it could be done.

## Approaches

There are many ways to approach the process of gathering requirements for a project. This could involve brainstorming ideas, holding focus groups, collecting surveys and user feedback, producing prototypes and allowing users to interact with them, and more. Once again, the topic of requirements elicitation is large enough for an entire course in itself.

So, if you do find yourself in a position where you need to gather requirements from users or customers, it is worth doing a bit of reading to discover the various approaches and methods that you may be able to put to use. Below are a few resources you may find helpful.

#### Resources

* [Requirements Elicitation](https://en.wikipedia.org/wiki/Requirements_elicitation) on Wikipedia
* [An Overview of Requirements Elicitation](https://www.modernanalyst.com/Resources/Articles/tabid/115/ID/1427/An-Overview-of-Requirements-Elicitation.aspx) from Modern Analyst
* [Software Engineering - Requirements Elicitation](https://www.geeksforgeeks.org/software-engineering-requirements-elicitation/) from GeeksforGeeks
* [Eliciting, Collecting, and Developing Requirements](https://www.mitre.org/publications/systems-engineering-guide/se-lifecycle-building-blocks/requirements-engineering/eliciting-collecting-and-developing-requirements) from MITRE
