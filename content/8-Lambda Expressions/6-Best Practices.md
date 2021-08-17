---
title: "Best Practices"
weight: 30
pre: "6. "
---
Lambda expressions are a very powerful tool that has been added to many different programming languages, including the ones we are studying in this course. However, there are some caveats that we should be aware of, and some best practices to follow. 

## Readability

For starters, lambda expressions can affect the readability of code. Even though lambda expressions are included in both Java and Python, and have been for quite a while at this point, many developers still have not learned how to use them. This is mainly due to the fact that lambda expressions are closely related to functional programming, which is a completely different programming paradigm than what most programmers are used to. 

In addition, pretty much anything that can be done with a lambda expression can be achieved through strictly procedural code, so there is really nothing to be gained through the use of lambda expressions in terms of functionality or performance.

Instead, the use of lambda expressions in Java and Python really comes down to readability, and for that reason, many developers tend to avoid them. From a certain point of view, lambda expressions don't really do anything except make the code harder to read for some developers, but possibly easier to read for others. 

## Scale

If we do choose to use a lambda expression, it is best to keep them as short and concise as possible. In effect, a lambda expression should be thought of as a single operation or expression. In Python, this is required, but Java allows lambda expressions to include multiple statements. 

If we need to write more complex code, it is probably best to do so using procedural code and traditional functions instead of lambda expressions.

## Summary

In general, while lambda expressions are very powerful and can be used in many different places in our code, in this course we'll generally avoid their use in places where they are not required. However, as a developer, you are welcome to use your better judgment - if you feel that a piece of code is better expressed as a lambda expression instead of procedural code, you are welcome to do so. When you do, keep in mind that this may make your code more difficult to understand for novice programmers who are not experienced with lambdas, so you may wish to thoroughly document your code to explain how it works. 
