---
title: "Java Lambdas"
pre: "2.J. "
weight: 20
date: 2020-01-25T00:53:26-05:00
hidden: true
---

{{< youtube AC9siHj92ms   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>
#### Video Script

Lambda expressions in Java are quite simple. We start with a list of parameters in parentheses. These parameters only include a name, but don't have any types associated with them. Following that, we have an arrow symbol, and then a statement or block of statements in curly braces that explain the value to be returned by the lambda expression. In this case, the lambda will return the sum of the parameters `x` and `y`.

So, how can we use lambdas in practice? This is a simple `Calculator` class, which defines an internal interface called `IntegerMath` that includes a single operation performed on two variables. Then, we can use that interface within the `operateBinary` method to represent a function we'd like to accept as input, and within the `operateBinary` function we can call the function we are given. So, in our main method, we see two different lambda expressions for addition and subtraction, which are then used as an argument to the `operateBinary` method. In this way, we can write methods that perform part of a task, and give the rest of the code as a lambda expression when we call it.

Here's an even better example. Let's say we want to write a program that can go through a list of people and print the email addresses of all males that are between the ages of 18 and 25. While we can easily do that with imperative code, we can also do that with lambda expressions. So, at the top, we see a higher-order function called `processPersonsWithFunction` that accepts several lambda expressions, and then uses them to filter, map, and then consume the data. When we call that function, we can provide a list of people, as well as the three lambda expressions we need to get the data we want. 

Now, what if we want to change the search to only find females over 65, and print their phone number? We can simply change the lambda expressions when we call the function! No need to change the rest of the code, just the little bits that we are using. 

Lambda expressions are pretty powerful features, but they can be a bit complex. In general, I don't use them too much in Java or Python, but it is helpful to know about them in case you ever come across them in practice. 