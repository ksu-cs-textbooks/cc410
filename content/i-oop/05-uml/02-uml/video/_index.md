---
title: "Overview"
pre: "1. "
weight: 10
date: 2020-01-15T00:53:26-05:00
hidden: true
---

{{< youtube Pk4U6GE8jnI   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

In this chapter, we're going to discuss the Unified Modeling Language, or UML. UML gives us a standard way that we can represent the structure and behavior of a software system in a set of easy to understand diagrams. Because UML is somewhat standardized in the industry, it makes it easy for a developer to review documentation on any project, even if it is one they haven't seen before. 

The UML standard actually describes many different types of diagrams that could be created. They are roughly divided into two groups - structural diagrams and behavioral diagrams. From there, each type of diagram can show one particular aspect of the finished software system, ranging from the classes it contains to how a particular operation is performed, and even more. 

Probably the most common UML diagram is the class diagram. A UML class diagram is used to show one or more classes in an object-oriented program. Those classes are represented as boxes which contain information about the attributes and methods within the class. Then, those classes can be connect to one another using arrows which represent associations between the classes themselves. We'll discuss class diagrams in more depth later in this chapter.

Another common UML diagram type is the sequence diagram. A sequence diagram is used to show the set of steps used to perform a particular task, typically represented as individual method calls and the classes containing those methods. For example, this diagram shows the `checkEmail` task, which is broken down into several individual steps, or method calls, that are made between the computer and the server. Remember that we can also think of method calls as messages being passed between classes, which can help make this diagram more understandable. 

At the high level, the design of many software systems begins with the Use Case diagram. A Use Case diagram gives an overview of what the software should be able to do, typically from the viewpoint of the user. Use Case diagrams are a great way to work with non-technical clients who have a particular project in mind, but aren't sure how to design it. This diagram shows a very simplified overview of how a restaurant might operate. 

So, as we discuss UML in this chapter, there are a few important things to keep in mind. First, remember that UML is simply a way to visualize structure and behavior of software. UML itself isn't a particular diagram or process, but a defined way to represent various aspects of a piece of software. 

Because UML is meant to be flexible, that means that there is no "one right way" to represent a piece of software in a UML diagram. Basically, each person asked to create a UML diagram may do it slightly differently, based on their expertise and what they think is important to include in the diagram and what can be omitted.

To that end, one of the major variations between different UML diagrams is the level of detail they contain. One class diagram could show just the basic attributes and operations to help an architect see the bigger picture, while another diagram for the same classes could include language-specific details, accessor methods, and more, to help the developers actually write the software. 

Finally, the UML standard includes an element known as a stereotype, which can be used to include language-specific information in a diagram. The UML standard itself doesn't include many provisions for how stereotypes should be used, so it is up to a particular software development team to come up with internal standards. 

I hope this is a helpful overview of UML and how it can be used. There are entire college courses that cover just this one topic, and we're going to just barely scratch the surface here. I encourage you to check out the plethora of online resources available for UML, and look up other UML diagrams online to see how they are used in practice. 
