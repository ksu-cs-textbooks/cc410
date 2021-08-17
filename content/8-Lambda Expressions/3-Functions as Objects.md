---
title: "Functions as Objects"
weight: 15
pre: "3. "
---
One of the major concepts from functional programming is that functions are now treated as [first-class citizens](https://en.wikipedia.org/wiki/First-class_citizen) within a programming language. A first-class citizen is an element of a programming language that can be treated like any other element - it can be stored in a variable, provided as an argument to another function, returned from a function, and even modified by other code. 

This can be a very strange concept to reason about - we are used to thinking of _state_ and _behavior_ as two separate parts of an object-oriented program. However, functional programming allows us to store a _behavior_ as _state_, and then use that _behavior_ as input to other parts of the code. 

## Lambda Expressions

In both Java and Python, one of the most common ways to create a behavior that can be stored as state is to use a **lambda expression**. Lambda expressions are sometimes known as **anonymous functions** since they are effectively functions that are not given a name, though some languages like Python allow us to assign names to lambda expressions as well.

As we saw in the example on the previous page, JavaScript allows us to quickly create lambda expressions that perform a particular task, such as determining if a value meets a given criteria that was used with `filter`, converting a value to a new value as used with `map`, or taking two values and reducing them to a single value as used in the `reduce` function.

In that example, `filter`, `map`, and `reduce` are examples of [higher-order functions](https://en.wikipedia.org/wiki/Higher-order_function) that accept other functions as input. Those higher-order functions can then use the function provided as input to perform their work. In the case of `filter`, it uses the provided function to determine if each value in the array should be included in the result or not. 

We've already seen a couple of examples of lambda expressions, or at least something similar, in our programs:

* **Java** - in our unit tests, we saw a lambda expression `() -> new GameLogic()` used as part of a unit test. That lambda is used to create a new object, and is used by the `assertThrows` assertion, itself a higher-order function, to determine if the code in the lambda expression results in an exception. In effect, that function executes the lambda and observes the result to determine if the exception is thrown.
* **Python** - one major feature of Python is list comprehension, such as `square_list = [x**2 for x in range(0, 10)]`. While list comprehension isn't exactly the same as a lambda expression, it is very similar in concept. We are effectively creating a small anonymous function that is used to populate a list. In fact, we could do the same thing with a lambda expression: `square_list = list(map(lambda x: x**2, range(0, 10)))`

On the next pages, we'll discuss the specifics of creating and using lambda expressions in both Java and Python. Feel free to read the page for the language you are studying, but it may be very informative to review how both languages handle the same concept. 
