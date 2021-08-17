---
title: "Hello Real World"
weight: 30
pre: "6. "
---

[Example Videos](video)

Based on the previous page, it sounds like writing professional code can be quite difficult. There are so many tools and concepts to keep track of, and, in fact, you may end up spending just as much time working with everything else around your code as you do writing the code itself. The benefit of all of this work comes later, when you have to update or maintain the code. If you've done a good job writing unit tests, checking for coverage, documenting and styling your code, you'll end up with fewer bugs overall, and hopefully it will be easier to patch and update the code over the long term that it is in use.

Thankfully, in this course, we're going to start small in this module with a new project we're calling "Hello Real World."

## Hello Real World

Most programmers can recall the simple "Hello World" program they wrote when learning to program. For many of us, it is the first program we learned to write, and usually the first thing we write when learning a new language. It is almost a sacred tradition!

We're going to build upon that in this module by learning to write a "Hello World" program of our own, but one that meets the following requirements:

1. It must be fully object-oriented, with the code placed within a method that is inside of a class, which is part of a package.
2. The code must include unit tests that fully verify that the code works properly in all cases.
3. The unit tests must achieve 100% code coverage of the source code.
4. The source code must contain full documentation for each file, class, and method, as defined by the language's standard for in-code documentation.
5. The source code must pass all checks enforced through static code analysis based on a common coding style for the language.
6. The entire process should be easily executable at-will from the terminal, while providing opportunities for future full automation.
7. The resulting code should be stored in a version control software system. 

That's quite a tall order, but this is really how a professional software developer would approach writing good and maintainable code. In some languages, such as Java, a few parts of this process are pretty straightforward - Java is already fully object-oriented by default, and Java uses a common standard for creating in-code documentation. Other languages, such as Python, end up becoming more complex to work with as more requirements are added. For Python developers, a simple "Hello World" program is a single line of code, whereas this set of requirements requires multiple files to properly create a Python package. In addition, the Python language itself does not define a common standard for in-code documentation, so we must rely on external resources to determine what coding style we should follow. 

Thankfully, we'll go through this entire process step by step in the example portion of this module, and you'll be able to follow along and build your own version of "Hello Real World."
