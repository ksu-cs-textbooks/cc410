---
title: "JavaScript"
weight: 20
pre: "4. "
---

{{% notice info "Content Note" %}}

Much of the content in this page was adapted from Nathan Bean's [CIS 400](https://textbooks.cs.ksu.edu/cis400/3-web-development/01-core-web-technologies/05-js/) course at K-State, with the author's permission. That content is licensed under a [Creative Commons BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.

{{% / notice %}}

JavaScript (or ECMAScript, which is the standard JavaScript is derived from), was originally developed for Netscape Navigator by [Brendan Eich](https://en.wikipedia.org/wiki/Brendan_Eich).  The original version was completed in just 10 days.  The name "JavaScript" was a marketing move by Netscape as they had just secured the rights to use Java Applets in their browser, and wanted to tie the two languages together.  Similarly, they pushed for a Java-like syntax, which Brendan accommodated.  However, he also incorporated functional behaviors based on the [Scheme](https://en.wikipedia.org/wiki/Scheme_(programming_language)) language, and drew upon [Self](https://en.wikipedia.org/wiki/Self_(programming_language))'s implementation of object-orientation.  The result is a language that may look familiar to you, but often works in unexpected ways.

## JavaScript is a Dynamically Typed Language

Unlike the statically-typed Java language, JavaScript has _dynamic_ types like Python.  This means that we always declare variables using the `var` keyword, i.e.:

```js
var i = 0;
var story = "Jack and Jill went up a hill...";
var pi = 3.14;
```

The type of the variable is _inferred_ when it is set, and the type can change with a new assignment, i.e.:

```js
var i = 0; // i is an integer
i = "The sky is blue"; // now i is a string
i = true; // now i is a boolean
```

This would cause an error in C#, but is perfectly legal in JavaScript.  Because JavaScript is dynamically typed, it is impossible to determine type errors until the program is run.  

In addition to `var`, variables can be declared with the `const` keyword (for constants that cannot be re-assigned), or the `let` keyword (discussed below).

## JavaScript Types

While the type of a variable is inferred, JavaScript still supports types.  You can determine the type of a variable with the `typeof()` function.  The available types in JavaScript are:

* integers (declared as numbers without a decimal point)
* floats (declared as numbers with a decimal point)
* booleans (the constants `true` or `false`)
* strings (declared using double quotes (`"I'm a string"`), single quotes `'Me too!'`, or backticks `` `I'm a template string ${2 + 3}` ``) which indicate a template string and can execute and concatenate embedded JavaScript expressions.
* lists (declared using square brackets, i.e. `["I am", 2, "listy", 4, "u"]`), which are a generic catch-all data structure, which can be treated as an array, list, queue, or stack.
* objects (declared using curly braces or constructed with the `new` keyword, discussed later)

In JavaScript, there are two keywords that represent a null value, `undefined` and `null`.  These have a different meaning: `undefined` refers to values that have not yet been initialized, while `null` must be explicitly set by the programmer (and thus intentionally meaning nothing).

## JavaScript is a Functional Language

As suggested in the description, JavaScript is a functional language incorporating many ideas from Scheme. In JavaScript we declare functions using the `function` keyword, i.e.:

```js
function add(a, b) {
  return a + b;
}
```

We can also declare an anonymous function (one without a name):

```js
function (a, b) {
  return a + b;
}
```

or with the lambda syntax:

```js
(a,b) => {
  return a + b;
}
```

In JavaScript, functions are first-class objects, which means they can be stored as variables, i.e.:

```js
var add = function(a,b) {
  return a + b;
}
```

Added to arrays:

```js
var math = [
  add,
  (a,b) => {return a - b;},
  function(a,b) { a * b; },
]
```

Or passed as function arguments.

## JavaScript has Function Scope

Variable scope in JavaScript is bound to functions.  Blocks like the body of an `if` or `for` loop do not declare a new scope.  Thus, this code:

```js
for(var i = 0; i < 3; i++;)
{
  console.log("Counting i=" + i);
}
console.log("Final value of i is: " + i);
```

Will print:

```
Counting i=0
Counting i=1
Counting i=2
Final value of i is: 3
```

Because the `i` variable is not scoped to the block of the `for` loop, but rather, the function that contains it.

The keyword `let` was introduced in ECMAScript version 6 as an alternative for `var` that enforces block scope.  Using `let` in the example above would result in a reference error being thrown, as `i` is not defined outside of the `for loop` block.

## JavaScript is Event-Driven

JavaScript was written to run within the browser, and was therefore event-driven from the start.  It uses the event loop and queue pattern we saw in C#.  For example, we can set an event to occur in the future with `setTimeout()`:

```js
setTimeout(function(){console.log("Hello, future!")}, 2000);
```

This will cause "Hello, Future!" to be printed 2 seconds (2000 milliseconds) in the future (notice too that we can pass a function to a function).

## JavaScript is Object-Oriented

As suggested above, JavaScript is object-oriented, but in a manner more similar to Self than to C#.  For example, we can declare objects literally:

```js
var student = {
  first: "Mark",
  last: "Delaney"
}
```

Or we can write a constructor, which in JavaScript is simply a function we capitalize by convention:

```js
function Student(first, last){
  this.first = first;
  this.last = last;
}
```

And invoke with the `new` keyword:

```js
var js = new Student("Jack", "Sprat");
```

Objects constructed from classes have a _prototype_, which can be used to attach methods:

```
Student.prototype.greet = function(){
  console.log(`Hello, my name is ${this.first} ${this.last}`);
}
```

Thus, `js.greet()` would print `Hello, my name is Jack Sprat`;

ECMAScript 6 introduced a more familiar form of class definition:

```js
class Student{
  constructor(first, last) {
    this.first = first;
    this.last = last;
    this.greet = this.greet.bind(this);
  }
  greet(){
    console.log(`Hello, my name is ${this.first} ${this.last}`);
  }
}
```

However, because JavaScript uses function scope, the `this` in the method `greet` would not refer to the student constructed in the constructor, but the `greet()` method itself.  The constructor line `this.greet = this.greet.bind(this);` fixes that issue by binding the `greet()` method to the `this` of the constructor.

## The Document Object Model

The Document Object Model (DOM) is a tree-like structure that the browser constructs from parsed HTML to determine size, placement, and appearance of the elements on-screen.  In this, it is much like the elements tree we used with Windows Presentation Foundation (which was most likely inspired by the DOM).  The DOM is also accessible to JavaScript - in fact, one of the most important uses of JavaScript is to manipulate the DOM.

You can learn more about the DOM from [MDN's Document Object Model](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model) documentation entry.
