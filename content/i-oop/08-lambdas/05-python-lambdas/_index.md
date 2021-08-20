---
title: "Python Lambdas"
weight: 25
pre: "5. "
---

{{% youtube HlFoT0B0GPk %}}

[Video Materials](video)

Lambda expressions, typically called **lambda functions** in most Python documentation, are effectively a syntactic shortcut for defining a function within Python code. This is because normal Python functions are already first-class citizens in the language - we can already pass existing named functions as arguments to other functions! So, lambdas in Python are simply shortcuts we can use to create a new anonymous function where needed, but we can always use normal functions to perform the same task.

## Python Functions vs. Lambdas

Python lambda functions are effectively the same as Python functions. For example, we can write an addition function in Python in the following way:

```python
def addition(x, y):
    return x + y
```

The same concept can be expressed as a lambda function, and we can even store it in a variable:

```python
addition_lambda = lambda x, y: x + y
```

Those two functions are effectively identical - they produce the same result, and can be treated as variables as well as callable functions.

The basic syntax of a lambda function in Python includes the following:

1. The keyword `lambda`
2. A list of parameters separated by commas, which can be named, positional, keyword, or variable parameters. Basically, any way you can define the parameters for a normal Python function can also be used for a lambda function.
3. A colon after the parameters:
4. A **single expression** that creates the result of the lambda function. Lambdas may not include multiple expressions, or any statements such as `return` or `pass`. 

In addition, Python lambda functions are **not compatible** with type annotations. So, when working with object-oriented Python, we will almost always prefer to write our own functions using the normal syntax, which allows us to perform type checking using Mypy. 

## Python Lambda Example

Here's a quick example of using both lambda functions and normal class functions as first-class citizens in Python. This example is adapted from a similar example given in [Lambda Expressions](https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html#syntax) from the Oracle Java Tutorials:

```python
class Calculator:
    
    @staticmethod
    def addition(x, y):
        return x + y
    
    def operate_binary(self, a, b, operation):
        return operation(a, b)
    
    @staticmethod
    def main():
        calc = Calculator()
        subtraction = lambda x, y: x - y
        print("40 + 2 = {}".format(calc.operate_binary(40, 2, Calculator.addition)))
        print("20 - 10 = {}".format(calc.operate_binary(20, 10, subtraction)))
        print("7 * 6 = {}".format(calc.operate_binary(7, 6, lambda: x, y: x * y)))

if __name__ == "__main__":
    Calculator.main()
```

In this code, we are defining two different functions that we'll use later as arguments:

* `addition` is a static method within the `Calculator` class that adds two values together. 
* `subtraction` is a variable in the `main` function that is storing a **lambda function** that will subtract two values.

Then, we've created a higher-order function `operate_binary` in the `Calculator` class, which accepts two integers as parameters `a` and `b`, as well as a **callable** object in the `operation` parameter. In effect, the `operation` parameter is meant to be a function, either a traditional Python function or a lambda function.

In our `main` function, we call `calc.operate_binary` in two different ways. On the first line, we provide `Calculator.addition` as the third argument. Notice that we **are not** including the parentheses at the end of the function name. In that way, we aren't _calling_ the function `Calculator.addition`, but we are referencing it as an attribute within the `Calculator` class. We can do this because functions are first-class citizens in Python, so we can treat them just like any other variable. Inside the `calc.operate_binary` function, we see that it calls the function stored in the `operation` variable by putting parentheses after the name, pass in any arguments as needed.

In the second example, we are passing the `subtraction` variable, which is a lambda function we created earlier, to the `calc.operate_binary` higher order function. So, it will be stored in `operation` and executed there.

Finally, we can create an anonymous lambda function directly within the function call to `calc.operate_binary`. This is why, typically, most lambda functions in Python are thought of as **anonymous functions** - we don't give them a name or store them in a variable, we simply create them as needed when we pass them to higher-order functions. 

For more information on using lambda functions in Python, check out the references linked below.

### References

* [How to Use Python Lambda Functions](https://realpython.com/python-lambda/) from Real Python
* [Python Lambda Functions](https://www.geeksforgeeks.org/python-lambda-anonymous-functions-filter-map-reduce/) from GeeksforGeeks
* [Python Lambda](https://www.w3schools.com/python/python_lambda.asp) from w3schools
* [Functional Programming HOWTO](https://docs.python.org/3/howto/functional.html) from Python Documentation
