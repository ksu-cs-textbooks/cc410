---
title: "Lambda Calculus"
pre: "1. "
weight: 10
date: 2020-01-25T00:53:26-05:00
hidden: true
---

{{< youtube ZsJT_pEJEAI >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

In this chapter, we're going to cover another interesting tidbit of programming that you may not have seen before - lambda expressions. Before that, however, we should quickly review where lambdas come from and why they are present in our object-oriented programming languages today. Alonzo Church, shown here, was a famous mathematician who introduced a new system of notation in mathematics, which we call lambda calculus.

Lambda calculus was first introduced in 1930, and is a mathematical notation used to describe computation. Recall that most traditional mathematical notations, such as the simple "3 + 5" all the way up to "x + y = z" are all meant to express value only - they don't say anything about the process needed to compute those values, only that those values can be represented by those expressions. In lambda calculus, each individual step represents a computation, which can then be performed on a Turing machine or any computer that is compatible with a Turing machine. In an earlier course, you probably learned that a Turing machine is the simplest theoretical computer, which can perform any computation that is done on a modern computer as long as it has infinite time and infinite memory. So, lambda calculus was an important development in mathematics that coincided with the development of modern computers. Lambda calculus is built around the concept of mathematical functions. I won't go too deep into mathematical functions here - its only important to know that a mathematical function converts input to outputs, and given the same input it will always produce the same output. 

In computer science, lambda calculus is the basis of a programming paradigm known as functional programming. This slide gives a couple of diagrams showing the relationship between various modern programming paradigms. Functional programming is a form of declarative programming, in which programs simply describe the output it should produce, without actually listing the individual steps required to create the output. We can contrast that with imperative programming, in which the individual steps to perform the calculation are listed and performed in sequence by the computer. Most programming languages you've learned up to this point are imperative languages. Within imperative languages, we see a smaller group under the structured programming paradigm. We covered structured programming earlier this semester - programs are constructed of simple structures like conditional statements and loops. Then, we have the procedural programming paradigm, which adds functions or subroutines to structured programming, allowing us to build more modular programs and reuse pieces of code multiple times. Then, finally object-oriented programming is a special form of procedural programming, where procedures are the behaviors that are combined with state to make up an object. So, in this class, we are treating both Java and Python as object-oriented languages, which fit within the procedural, structured, and imperative programming paradigms. However, both languages include a couple of features borrowed from the functional programming paradigm, which is the basis for lambda expressions. 

So, what are those features? First, both Java and Python support the idea of treating functions like first-class citizens in the language. That means that we can store a function itself as a variable, and pass that function as an argument to other functions. This may seem strange at first, but this is actually a core idea from Von Neumann architecture, which you should have learned about in an earlier course. In Von Neumann architecture, the computer treats program code just like any other data, and in effect functional programming allows us to do the same within our code!

The other concept taken from functional programming is the use of higher-order functions, which are simply functions in our program that can accept other functions as arguments and then make use of them. We'll see an example of this later in this chapter.

Before we move on, let's look at a quick example of both the imperative and functional programming paradigm to see how they work. Both of these examples are taken from Wikipedia, which is always a great resource for learning about computer science theory. In this example, we have an imperative program written in JavaScript that will find the even values in a list, multiply them by 10, and sum them up. In the imperative example, it does so using a for loop. So, we can step through this for loop and see what it does. 

If we keep track of the value stored in the `result` variable, we'll see it take on these values. First, the loop will examine the number 1, and find that it is not even, so it will be skipped. The next value, 2, is odd, so the value 20 will be added to `result`. Next, it will look at 3 and skip it, then it will reach 4 and add 40 to the `result`, which now stores 60. We can continue this process until we've examined all 10 values in the array, and the final result is 300. Since we've been working within the imperative programming paradigm throughout this program, this analysis should be pretty easy for us to do.

Let's compare that to this code, which is still written in JavaScript, but this time using the functional programming paradigm. It looks quite a bit different. In fact, it looks like one big chain of function calls, which is really what the functional programming paradigm is. It is just applying functions to data until the result we want is found.

So, in this case, let's look at the array of number as a whole, as see what each function does. We'll start with these 10 values. Then, we'll perform the `filter` function on them, and the `filter` function itself is a higher-order function that accepts a second function as input. In this case, that function is a lambda expression that returns true is the value is even, and false if it is odd. 

So, when we use the `filter` function to filter our array based on that lambda expression, we'll be left with only the even values. Those values are then given to the `map` function, which is used to perform an operation on each value. That operation is once again given to us by a lambda expression, which tells us to replace each number with that number multiplied by 10.

So, the `map` function will leave us with this array, which contains the values 20, 40, 60, 80, and 100. Finally, that array will be used as input to the `reduce` function, which once again accepts a lambda expression as input. That lambda expression tells us how to take two values from the input and "reduce" them to a single value. In this case, they are added together. 

So, the reduce function will add 20 and 40 to get 60, and it will also add 60 and 80 to get 140. Then, it will go back through the process and start again, repeating it until it is just left with a single value, 300. That value is then represented by the `result` variable in our program. 

Notice how, at no point, did the functional programming paradigm tell the computer what do to - it just told the computer what output it should produce! Behind the scenes, each of these functions may be represented by imperative code that actually gets executed, but at the high level we are just listing the functions we'd like to perform on the input itself. This makes functional programming very powerful, since it can be easily reasoned with and programs can be proven to work correctly since there aren't any side effects. 

Next up, we'll quickly look at how to use lambda expressions in both Java and Python. 