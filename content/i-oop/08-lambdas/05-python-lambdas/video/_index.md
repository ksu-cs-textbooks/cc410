---
title: "Python Lambdas"
pre: "2.P. "
weight: 21
date: 2020-01-25T00:53:26-05:00
hidden: true
---

{{< youtube HlFoT0B0GPk >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>
#### Video Script

Lambda expressions in Python are quite simple. We start with the lambda keyword, followed by a list of parameters. These parameters can be any valid form of Python parameters, including named parameters, variable length parameters, and more. Following that, we have a colon, and then a single expression that represents the value to be returned by the lambda expression. In this case, the lambda will return the sum of the parameters `x` and `y`.

So, how can we use lambdas in practice? This is a simple `Calculator` class, which includes a static method called `addition`. It also includes a higher-order function called `operate_binary` that can accept another function as input, and then call the function it is given when it is executed. So, in our main method, we see a lambda expression subtraction. Then, we see that our program can call the `operate_binary` method in multiple ways, providing a function reference, a named lambda expression, or an inline lambda expression as input. In each instance, that lambda or function will be executed by the `operate_binary` method, and the result will be returned. 

Here's an even better example. Let's say we want to write a program that can go through a list of people and print the email addresses of all males that are between the ages of 18 and 25. While we can easily do that with imperative code, we can also do that with lambda expressions. So, at the top, we see a higher-order function called `process_persons` that accepts several lambda expressions, and then uses them to filter, map, and then consume the data. When we call that function, we can provide a list of people, as well as the three lambda expressions we need to get the data we want. 

Now, what if we want to change the search to only find females over 65, and print their phone number? We can simply change the lambda expressions when we call the function! No need to change the rest of the code, just the little bits that we are using. 

Lambda expressions are pretty powerful features, but they can be a bit complex. In general, I don't use them too much in Java or Python, but it is helpful to know about them in case you ever come across them in practice. 