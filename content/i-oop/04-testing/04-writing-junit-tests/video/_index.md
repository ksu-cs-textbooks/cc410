---
title: "JUnit"
pre: "2.J. "
weight: 20
date: 2020-01-15T00:53:26-05:00
hidden: true
---

{{< youtube w6rtzfr1jQ4   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

For the Java programming language, we're going to use the JUnit test framework to develop our unit tests. JUnit is one of the most popular unit test frameworks for Java today, and it is very easy to use. On this slide, we have a simple JUnit test that could be used to test the `Square` class we introduced in an earlier chapter. First, we have to import a few items from the JUnit library. While we normally could do this with a wildcard import that contains an asterisk, the Google Style guide requires us to import each class explicitly, so that's what we'll do here. Test methods are annotated using the `@Test` method decorator. This works very similar to the `@Override` decorator we're already familiar with - it just tells JUnit that this method should be treated like a unit test. Typically, we name our test methods with very descriptive names, as that method name is the first thing we'll see when a test fails. If the method name is descriptive enough, we'll know exactly what test failed. Then, inside the test, we execute our code, and use one or more assertion statements to verify that the output produced is correct. In this case, we are using the constructor to instantiate a new Square object, and then checking to make sure it sets the `length` attribute properly. While this may seem obvious, tests like this one are very important - if we aren't sure that the class sets its attributes correctly, then many of our later tests will also fail. 

Of course, at some point we may want to write a test that runs the same code with multiple inputs. For that, we'll want to use a Parameterized Test. To use parameterized tests in JUnit, we'll need to add that library to our `build.gradle` file. Don't worry, this is included in the Example project as well, so you'll be able to find it there when you need it.

Once we've installed that library, we can write a parameterized unit test as shown in this example. Instead of the `@Test` decorator, we use the `@ParameterizedTest` decorator, and we add a second decorator called `@ValueSource` that lists the values we'd like to use. By default, JUnit allows us to use any primitive data type here, as well as strings. For more complex types, the textbook also describes the `@CsvSource` decorator that can be used instead. When our test is executed, this test method will be called multiple times, once for each entry in the `@ValueSource` list. That entry will be provided to the method as a parameter, and then we can use that parameter in our code. In this case, the code will construct multiple different `Square` objects and make sure that they all are constructed correctly.

JUnit includes many different assertions that we can use, some of which are listed here on this slide. We can quickly assert that a particular value is true or false, or that two values are equal or not equal. There are special assertions for dealing with arrays and lines of output, and we can also use assertions to make sure that values are either `null` or `not null`, as well as confirming that two objects are actually the same instance or not. This is useful when we want to make sure our code is returning the exact object we want, and not a copy. 

Let's look at two more advanced used of JUnit. First, we can write a JUnit test to check that a particular piece of code throws an exception. This is really useful, as many times we want to test our code in ways that should cause it to break, and we want to confirm that it throws the correct exceptions in those cases. For JUnit, we use the `assertThrows` assertion. However, it is made more complex because the second argument to that assertion has to be an `Executable` item. We've not covered this yet in this course, but we can easily create an `Executable` using a lambda expression as seen here. We include a set of parentheses, followed by an arrow and the function call we'd like to check. This is, in effect, creating an anonymous function that can be passed as an argument to another function. So, when that code is executed, the assertion will confirm that it throws the correct exception.

The other useful thing we can do in JUnit is check the output a program prints to the terminal. By default, that output would still be printed to the terminal even if we are running a unit test, so we need a way to capture it. We do that by creating a different output stream that can be used to replace the default `System.out` stream that we normally use. Lines 2-4 of this function perform that operation. Then, we can execute our code, which will capture any output it produces in our output stream. Below that, we reset the `System.out` output stream back to what it was, and then finally we can examine the data we captured using an assertion. It looks a bit complex, but it is actually quite simple once we walk through it. 

That's a quick overview of some of the ways we can use JUnit in our code. In the example project for this module, we'll write a few unit tests of our own to get some more experience with this topic. I also encourage you to check out the official JUnit documentation, as well as any other tutorials and resources we've linked throughout the textbook. 

