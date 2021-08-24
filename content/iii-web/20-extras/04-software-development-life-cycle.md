---
title: "Software Development Life Cycles"
weight: 20
pre: "4. "
---

One major topic that this course doesn't cover is [software engineering](https://en.wikipedia.org/wiki/Software_engineering). Software engineering is all about applying practices from the field of engineering to the development of software. So, while it also includes things such as program architecture, programming paradigms, and design patterns, which we do cover in this course, software engineering also includes many other topics related to the **process** of developing, operating, testing, and maintaining software. 

One of the major topics in software engineering is the [Software Development Life Cycle](https://en.wikipedia.org/wiki/Systems_development_life_cycle), sometimes abbreviated as SDLC or referred to as the [Software Development Process](https://en.wikipedia.org/wiki/Software_development_process). This is all about how we actually design and build software, going from the initial idea, all the way through design, development, testing, maintenance, updates, and more. There are entire courses and books dedicated to this topic, and it is an area of constant study and improvement for software developers of all skill levels.

On this page, we'll give a brief overview of the major concepts and how they all fit together.

## Steps

![Software Development Life Cycle Steps](/cc410/images/20/sdlc_wiki.gif)[^1]

[^1]: https://commons.wikimedia.org/w/index.php?title=File:Systems_Development_Life_Cycle.gif&oldid=534019806
_Right-click and open image in new tab for larger version_

The software development life cycle consists of many steps, and each of the methodologies discussed below may use a slightly different list of steps, adding or omitting them as needed. However, they generally fit into a few major groupings:

### Requirements

The first step is generally to determine the requirements of the piece of software. At this step, a developer might ask questions about who the software is for, what it should do, how it will store and access data, and what type of hardware it will be running on. All of these questions help build the list of **requirements** for the software. Throughout most of your academic career, this is usually provided to you as the description of the programming project. It clearly states what the finished product should do and how it should work. 

### Design

Once the requirements are determined, developers will start working on the overall **design** of the application. This usually involves creating some UML diagrams to help describe the structure of the application itself, and it may also include discussions of external libraries to be used, software design patterns to apply, and more. Again, this is usually given to you as part of the assignment description, though in this class you were tasked to develop your own software design as part of your final project. 

### Development

This step is the obvious one - it involves actually **developing** the software! In this step, developers refer back to the design documents and original requirements list to make sure the code being developed meets those needs. In your academic career, this is the step that most classes, up to this point, have focused on teaching you. As a programmer in a large organization, or working on your own personal project, this is really the core step of the process that you'll work with. However, throughout your career you may find yourself branching out a bit and working more on gathering requirements and designing software that others will help you build. 

### Testing

Once the software is developed, it needs to be tested. In this course, we introduced unit testing, which makes up the bulk of software testing. As we discussed before, this could also include items such as regression tests, integration tests, and more. In fact, the **test-driven development** paradigm turns this around by requiring tests to be developed before the software itself, effectively combining both the testing and development steps into a single step. 

### Deployment & Maintenance 

When the software is ready to be released, the last step in its life cycle is to be deployed to the end-users. However, once they have access to the software, they are bound to find bugs to be fixed. So, many software projects also must include some maintenance steps here to fix bugs and provide updates to the program even after it is released. 

#### References

* [Software Development Life Cycle](https://en.wikipedia.org/wiki/Systems_development_life_cycle) on Wikipedia
* [Software Development Process](https://en.wikipedia.org/wiki/Software_development_process) on Wikipedia

## Methodologies

Another core concept of software engineering are the **software development methodologies**, which are different ways of moving through the steps of the software development life cycle listed above. Each methodology follows its own unique pattern through those steps, and may add additional constraints or processes as needed. There are many different methodologies in use today, but let's look at a few of the more common ones that you might come across.

### Waterfall

![Waterfall Model](/cc410/images/20/waterfall.svg)[^2]
[^2]: https://commons.wikimedia.org/w/index.php?title=File:Waterfall_model.svg&oldid=453496509

The [Waterfall Model](https://en.wikipedia.org/wiki/Waterfall_model) is a software development methodology that basically works through the software development lifecycle one step at a time. So, in the waterfall model, developers cannot start working on code until both the requirements and design steps are fully complete. And, at any time, if the developers realize that the design is not feasible, development must be paused while the design is reconsidered. 

The waterfall model is seen as a more traditional model, since it has its roots in the early days of software development in the 1950s and 1960s. Many large corporations and government projects still follow this model today. However, there are many drawbacks to this model, such as the fact that it can be very rigid and inflexible, especially as the requirements and design of a software project may change over time. 

### Iterative and Incremental Development

![Iterative and Incremental Development Model](/cc410/images/20/iter_wiki.svg)[^3]

[^3]: https://commons.wikimedia.org/w/index.php?title=File:Iterative_development_model.svg&oldid=484829875]

The [Iterative and Incremental Development](https://en.wikipedia.org/wiki/Iterative_and_incremental_development) model builds upon the waterfall model by using the same basic steps, but repeated over and over again. Instead of developing the project all at once, this model focuses on building a small part of the project first, and then slowly adding to it (incremental). That process is repeated multiple times (iterative), until the full project is complete. Through this model, it is much easier to build small prototypes of the software, get feedback, and continually adapt the design and requirements as more information is acquired. 

This model has been used successfully in a variety of contexts, including as part of the Mercury and Space Shuttle programs at NASA.^[https://www.computer.org/csdl/magazine/co/2003/06/r6047/13rRUxBJhpL]

### Spiral Model

![Spiral Model](/cc410/images/20/spiral.svg)[^4]

[^4]: https://commons.wikimedia.org/w/index.php?title=File:Spiral_model_(Boehm,_1988).svg&oldid=480509142]

Closely related to the iterative and incremental development model, the [Spiral Model](https://en.wikipedia.org/wiki/Spiral_model) also focuses on a repeated set of steps that start with a small concept and prototype, working outwards toward a final project. In a spiral model, however, developers and teams analyze the "risk" that comes with any change to the software or new concept to be added, and aims to minimize that risk as much as possible. For example, if the team decides to add a new feature to a project, but they are worried that it may not be well received by users, they may decide to only spend a little bit of time working on that feature before getting feedback from the users. If it is well received, the next cycle may devote more time to that feature. If the users don't like it, they will have saved themselves lots of wasted time by not spending too much time on it in the first place.

### Agile Software Development 

[Agile Software Development](https://en.wikipedia.org/wiki/Agile_software_development) is one of the newer and most popular software development methodologies today. Agile software development actually comes in many forms, but they all focus on rapid prototyping, continual improvement, and quickly responding to changes in requirements and design. It all started with the publication of the [Manifesto for Agile Software Development](http://agilemanifesto.org/), which contains the statements:

> ... we have come to value:
> Individuals and interactions over processes and tools
> Working software over comprehensive documentation
> Customer collaboration over contract negotiation
> Responding to change over following a plan

Therefore, most implementations of the agile software development methodology involve very short development cycles, commonly measured by days or even hours instead of weeks or months. In addition, there is a large focus on automation at all levels, such as [continuous integration](https://en.wikipedia.org/wiki/Continuous_integration) and automated unit testing, and many developers are encouraged to use standard structures and techniques such as software design patterns and clean code to make their code easy to understand and maintain.

There are lots of great resources for learning more about agile software development on line, including many free courses. For developers considering working in the industry, we highly recommend learning more about agile due to its popularity in all levels of the industry today. 
