---
title: "The Gang of Four"
weight: 10
pre: "2. "
---

{{% youtube DX4RqiA871I %}}

[Video Materials]({{<relref "./video">}})

![Design Patterns Cover](/images/12/design_patterns.jpg)[^1]

[^1]: https://www.journaldev.com/7229/best-design-patterns-book

While the first discussions of patterns in software architecture occurred much earlier, the concept was popularized in 1994 with the publication of [_Design Patterns: Elements of Reusable Object-Oriented Software_](https://en.wikipedia.org/wiki/Design_Patterns) by Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides. Collectively, the four authors of this book have been referred to as the "Gang of Four" or "GoF" within the software development community, so it is common to see references to that name when discussing the particular software design patterns discussed in the book.

In their book, the authors give their thoughts on how to build software following the object-oriented programming paradigm. This includes focusing on the use of interfaces to design how classes should appear to function to an outside observer, while leaving the actual implementation details hidden within the class. Likewise, they favor the use of object composition over inheritance - instead of inheriting functionality from another class, simply store an internal instance of that class and use the public methods it contains. 

The entire first chapter of the book is a really great look at one way to view object-oriented programming, and many of the items discussed by the authors have been implemented by software developers as standard practice. In fact, it is still one of the best selling books on software architecture and design, even decades after its release!

Of course, it isn't without criticism. One major complaint of this particular book is that it was developed to address several things that cannot be easily done in C++, which have been better handled in newer programming languages. In addition, the reliance on reusable software design patterns may feel a bit like making the problem fit the solution instead of building a new solution to fit the problem. 

##### References

* Gamma, Erich, et al. _Design Patterns: Elements of Reusable Object-Oriented Software._ Addison-Wesley, 1995. 
* [Design Patterns](https://en.wikipedia.org/wiki/Design_Patterns) on Wikipedia
* [Software Design Patterns](https://en.wikipedia.org/wiki/Software_design_pattern) on Wikipedia
