---
title: "pytest"
pre: "2.P. "
weight: 21
date: 2020-01-15T00:53:26-05:00
hidden: true
---

{{< youtube _5txXZHtFkw   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

For the Python programming language, we're going to use the pytest test framework to develop our unit tests. pytest is one of the most popular unit test frameworks for Python today, and it is very easy to use. On this slide, we have a simple pytest test that could be used to test the `Square` class we introduced in an earlier chapter. For pytest to find the test methods, we have to follow some specific naming standards. In general, our Python file must start with `test`, the class must have `Test` in the name, and then the test methods should also begin with `test`. Typically, we name our test methods with very descriptive names, as that method name is the first thing we'll see when a test fails. If the method name is descriptive enough, we'll know exactly what test failed. Then, inside the test, we execute our code, and use one or more assertion statements to verify that the output produced is correct. In this case, we are using the constructor to instantiate a new Square object, and then checking to make sure it sets the `length` attribute properly. While this may seem obvious, tests like this one are very important - if we aren't sure that the class sets its attributes correctly, then many of our later tests will also fail. 

We can also write a parameterized unit test as shown in this example. To create parameterized tests, we'll have to import the `pytest` library in our code. Then, before our test method, we'll use the `@pytest.mark.parametrize` decorator to tell pytest that it should treat this test as a parameterized test. Inside of that decorator, we can declare a single variable or a tuple of variables, followed by a list of values that we'd like to use. When our test is executed, this test method will be called multiple times, once for each entry in the list. That entry will be provided to the method as a parameter, and then we can use that parameter in our code. In this case, the code will construct multiple different `Square` objects and make sure that they all are constructed correctly.

pytest includes a few different assertions that we can use, some of which are listed here on this slide. The bulk of our assertions will simply use the default `assert` statement in Python, so we can test that any Boolean expression returns true. Using the `pytest.approx` method, we can also check that a floating-point value is close to an expected value. We can also use the `is` keyword in our assertions to check if two values are the same instance, or if the value is either `None` or `not None`.  

Let's look at two more advanced used of pytest. First, we can write a pytest test to check that a particular piece of code raises an exception. This is really useful, as many times we want to test our code in ways that should cause it to break, and we want to confirm that it raises the correct exceptions in those cases. For pytest, we use the `pytest.raises` assertion in a `with` statement. Then, inside of the `with` block, we can place the code that we want to execute that should result in an exception. So, when that code is executed, the assertion will confirm that it raises the correct exception.

The other useful thing we can do in pytest is check the output a program prints to the terminal. By default, that output would still be printed to the terminal even if we are running a unit test, so we need a way to capture it. We can do that by including the `capsys` capture fixture as a parameter in our test method. Then, we can execute our code in our test, and `capsys` will capture any output it produces. Below that, we can get the output using the `readouterr` method, and then finally we can examine the data we captured using an assertion. It looks a bit complex, but it is actually quite simple once we walk through it. 

That's a quick overview of some of the ways we can use pytest in our code. In the example project for this module, we'll write a few unit tests of our own to get some more experience with this topic. I also encourage you to check out the official pytest documentation, as well as any other tutorials and resources we've linked throughout the textbook. 

