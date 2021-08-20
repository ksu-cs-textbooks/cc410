---
title: "Lambda Calculus"
weight: 10
pre: "2. "
---

{{% youtube ZsJT_pEJEAI %}}

[Video Materials](video)

The basis of lambda expressions comes from a special branch of mathematics known as [Lambda Calculus](https://en.wikipedia.org/wiki/Lambda_calculus). It was first introduced by Alonzo Church, who is often connected with Alan Turing in the early days of theoretical computer science. (You may have heard of the [Church-Turing thesis](https://en.wikipedia.org/wiki/Church%E2%80%93Turing_thesis) that relates to the computability of functions on a Turing machine.)

## Lambda Calculus

Lambda calculus is a formal notation used to describe computation. Recall that most mathematics uses expressions or equations, which express values, but don't necessarily include the information needed to express the process of computation itself. By having a formal notation for computation, we can study the fundamental aspects of computer science and mathematics in a more rigorous way.

In programming, lambda calculus leads to a particular programming paradigm known as [Functional Programming](https://en.wikipedia.org/wiki/Functional_programming). The programming paradigm we've been studying, [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming) is usually combined with the [procedural programming](https://en.wikipedia.org/wiki/Procedural_programming) paradigm, itself a subset of [imperative programming](https://en.wikipedia.org/wiki/Imperative_programming). In imperative programming, we write code that consists of commands that modify the programs _state_. So, to compute the square of a number, we would create a variable in our _state_ to store the result, and then modify that state by computing the correct value and storing it in that variable. The commands to do this are typically written as procedures (or _functions_) in procedural programming, so we can reuse those pieces of code throughout our program. Procedural programming typically follows the [structured programming](https://en.wikipedia.org/wiki/Structured_programming) paradigm as well, where programs are constructed of smaller structures such as sequences, conditional statements, and iterative statements. Object-oriented programming, as we've learned, further refines this process by grouping related _state_ and _behaviors_ (_methods_ which represent functions or procedures in other paradigms) into _objects_ that can be seen as independent pieces of a larger program.

Functional programming is quite different. Instead of creating an imperative list of steps to be taken to modify the state of the program and achieve a result, functional programming involves constructing and applying mathematical functions, which simply translate values from inputs to outputs. Functional programming is a form of [declarative programming](https://en.wikipedia.org/wiki/Declarative_programming), where computer programs are built simply by expressing the logic of the computation but not the individual steps or control flow necessary to achieve the desired result. In effect, a declarative programming language is used to state _what_ a program does, but not necessarily _how_ to do it.

## Functional Programming Example

Here is an example of the imperative and functional programming paradigms being used to compute the same value. In this case, the program will multiply all even numbers in an array by 10, and then add them up and store the final result in a variable called `result`. These examples use the [JavaScript](https://en.wikipedia.org/wiki/JavaScript) programming language, which should be somewhat readable to us even though we've only studied Java or Python. This example is taken directly from the [functional programming](https://en.wikipedia.org/wiki/Functional_programming) article on Wikipedia:

###### Imperative

```js
const numList = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
let result = 0;
for (let i = 0; i < numList.length; i++) {
  if (numList[i] % 2 === 0) {
    result += numList[i] * 10;
  }
}
```

###### Functional

```js
const result = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
               .filter(n => n % 2 === 0)
               .map(a => a * 10)
               .reduce((a, b) => a + b);
```

The imperative programming code is very similar to what we would write in Java or Python. We start with our array of numbers, then use a for loop to iterate through the entire array. Inside of the for loop, we determine if the individual number is an even number using the modulo operator. If so, we multiply that number by 10 and add that value to the `result` variable.

The functional programming code achieves the same result through the use of three [higher-order functions](https://en.wikipedia.org/wiki/Higher-order_function). A higher-order function is a function that can accept a function as input - in this case a **lambda expression** in the form of an anonymous function that converts one or more input parameters into an output value. We'll dig deeper into lambda expressions later in this chapter, but for now we'll just observe what they do.

So, our functional program can be broken down into four parts:

1. We start with our array of numbers from 1 through 10. That is the input we provide to the first function. 
2. On that array, we apply the `filter` function. This function accepts a lambda expression as an argument. That lambda should take a value from the array, and convert it to a boolean value, which is used to **filter** the values in the array. In this case, that boolean value will be `true` if the value `n` from the array is an even number. The `filter` function then uses that lambda to return a new array that just contains those values in the original array that return `true` in the lambda function provided to `filter`. So, our new array will contain `[2, 4, 6, 8, 10]`.
3. Then, we apply the `map` function to that new array returned from `filter`. The `map` function also takes a lambda as an argument, and that lambda is used to transform, or **map**, the values from the array to new values. In this case, it will convert the existing value `a` to the value `a * 10`. So, once the `map` function is complete, the array would contain `[20, 40, 60, 80, 100]`. Remember that this value isn't stored as _state_ in the program, per se, but is representing the values that would result from applying these functions to the input array itself. 
4. Finally, we use the `reduce` function to reduce all of the values in the array to a single resulting value. The `result` function uses a lambda expression as an argument. That lambda is used to describe how to combine two values from the array, `a` and `b`, to a single resulting value. In this case, we want to sum the values in the array, so the lambda will return in `a + b` as the result. The `reduce` function will repeatedly use that lambda to **reduce** two values in the array to a single value until only one value remains. That value will be the result of that function, which will be then represented by the `result` variable. Notice that it isn't _stored_ in that variable, since again we don't have the concept of _state_. Instead, we are just stating that the variable `result` now **represents** the value that is the result of applying these functions to the given input value.

Functional programming can be challenging to understand at first, especially for programmers that come from an imperative programming paradigm. However, it is very powerful, and has some interesting uses. Once of the more common uses of functional programming is the creation of programs that can be proven to work correctly. This is because there is no actual computation performed, so there can be no side effects from those computations. Therefore, as long as the functional statements yield the correct results via a mathematical proof, we know that the program works correctly. 

## Functional Programming Today

Many programming languages today either support some form of functional programming, or at least support the use of **lambda expressions** within their code. Some languages, such as Python, JavaScript and Go, support the functional programming paradigm directly. Other languages, such as Java and C#, have introduced the ability to do some functional programming over time. 

Other languages, such as Haskell, F#, Erlang, and Lisp are built almost exclusively for functional programming. While they are most used in academia, functional programming is also very commonly used in web back-end development, statistics, data science, and more. 
