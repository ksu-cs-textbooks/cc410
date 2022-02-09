---
title: "Encapsulation"
pre: "1. "
weight: 10
date: 2020-12-31T00:53:26-05:00
hidden: true
---

{{< youtube UmAOkkJtAZ8 >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

In this chapter, we're going to dive a bit deeper into the object-oriented programming paradigm, and explore some of the reasons and history behind the design decisions that led us to where we are today. As you'll recall, the original idea for object-oriented programming, as proposed by Alan Kay, involved these three elements - encapsulation, message passing, and dynamic binding. First, let's look at encapsulation.

Think back to the code for the EPIC simulation program we looked at in an earlier chapter. That code is a great example of what early software looked like - it was largely unstructured, and most of the variables were stored _globally_, meaning that they could be changed by any part of the program. Part of the beauty of this structure was in its simplicity - developers really didn't have to think much about the structure. New variables were just declared globally, and they could write any code they needed just about anywhere, without thinking about how it all should fit together as a system. So, a high level overview of that code would look something like this diagram, where all the variables governing the crops, weather, soil, and use of fertilizer were stored in one global area. Likewise, there would be a large pile of code that handles all of the updates and modifications to those variables, but the code itself really isn't organized beyond being separated into a few separate files.

So, in 1972, David Parnas wrote a paper titled "On the Criteria To Be Used in Decomposing Systems into Modules" where he described a better way of organizing code. He proposed that code should be divided into **modules**, where each module contained both a data structure to represent the data controlled by that module, as well as methods for accessing and updating that data. Given what we already know about object-oriented programming and classes, we can see how this would set the stage for classes we know today. However, let's look at the steps it took to get there.

Early programming languages, such as C, supported the creation of custom data types through the use of **structs**, which represent a structure in memory consisting of multiple primitive variables combined together. This struct could be used to group variables together into a single unit, which made organization easier. Likewise, those languages supported the use of multiple files, so each file of code could be thought of as a **module** which contained functions that were related to the struct defined in that file. So, in a way, each code file defined both a data structure and a set of methods that work on that data structure. This greatly improved the organization of code. 

So, thought of in another way, we can say that the code consists of several modules that looks like this, each one **encapsulating** both the methods and the data for that module. While this makes perfect sense to us today, its important to remember that even simple structures like this really changed how early software was developed, and helped pave the way for even better and more complex structures and patterns that we'll learn about later in this course.