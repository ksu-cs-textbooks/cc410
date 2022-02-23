---
title: "Java Lambdas"
weight: 20
pre: "4. "
---

{{% youtube AC9siHj92ms %}}

[Video Materials]({{<relref "./video">}})

Java introduced lambda expressions in Java version 8. As we would expect based on the previous pages, it allows us to create anonymous functions that can then be passed as arguments to other functions. Java includes several new types, such as [Predicate](https://docs.oracle.com/javase/8/docs/api/java/util/function/Predicate.html) and [Consumer](https://docs.oracle.com/javase/8/docs/api/java/util/function/Consumer.html), all contained in the [java.util.function](https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html) package. 

## Lambda Expression Syntax

In general, a lambda expression in Java consists of the following syntax:

1. A list of formal parameters in parentheses, separated by commas. You do not have to specify the data type of the parameters. Likewise, if there is a single parameter, the parentheses may also be omitted. 
2. An arrow `->`
3. A body, which may be either a single expression or a block of statements surrounded by curly braces `{}`

## Lambda Expression Example

Let's look at an example of creating and using a lambda expression in our code. This example comes from [Lambda Expressions](https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html#syntax) from the Oracle Java Tutorials:

```java
public class Calculator {
  
    interface IntegerMath {
        int operation(int a, int b);   
    }
  
    public int operateBinary(int a, int b, IntegerMath op) {
        return op.operation(a, b);
    }
 
    public static void main(String... args) {
    
        Calculator myApp = new Calculator();
        IntegerMath addition = (a, b) -> a + b;
        IntegerMath subtraction = (a, b) -> a - b;
        System.out.println("40 + 2 = " +
            myApp.operateBinary(40, 2, addition));
        System.out.println("20 - 10 = " +
            myApp.operateBinary(20, 10, subtraction));    
    }
}
```

In this simple calculator class, we are defining an internal `interface` called `IntegerMath`, which defines one `operation` between two integers, which also returns an integer. Then, in our `Calculator` class, we have a function `operateBinary` that accepts an argument of type `IntegerMath`. 

So, in our `main` method, we are creating two lambda expressions that use the type `IntegerMath`. One is a lambda that accepts two values and returns the sum, and the other accepts two values and returns the difference. Java will automatically recognize that those lambda expressions match the `operation` method defined in the `IntegerMath` interface. So, when we call the `operateBinary` method and provide either `addition` or `subtraction` as arguments, it will use those lambda expressions to compute the result. 

As we can see, we were able to create two functions, via lambda expressions, as first-class citizens in our language by storing them in variables, and then passing those functions as arguments to another method, which can then call the function itself. 

## Lambda Expressions In Practice

In practice, Java tends to use lambda expressions for tasks such as sorting, filtering, or mapping data in a collection. [Lambda Expressions](https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html#syntax) from the Oracle Java Tutorials gives another example that can be used to quickly generate a filter that will print a list of email addresses for people in list who are males between the ages of 18 and 25:

The function that accomplishes this work is shown below:

```java
public static void processPersonsWithFunction(
    List<Person> roster,
    Predicate<Person> tester,
    Function<Person, String> mapper,
    Consumer<String> block) {
    for (Person p : roster) {
        if (tester.test(p)) {
            String data = mapper.apply(p);
            block.accept(data);
        }
    }
}
```

We can use that function by passing three lambdas, as shown here:

```java
processPersonsWithFunction(
    roster,
    p -> p.getGender() == Person.Sex.MALE
        && p.getAge() >= 18
        && p.getAge() <= 25,
    p -> p.getEmailAddress(),
    email -> System.out.println(email)
);
```

In this case, `roster` is a list of `Person` objects, and we have created three lambda expressions to filter the list to include only the people we want, them map those people to an email address, and finally print those emails to the terminal. 

## Referencing Java Methods

Finally, while methods in Java aren't exactly first-class citizens, there is a shorthand that we can use to create lambda expressions that simply call a given method. 

For example, the lambda expression:

```java
a -> a.toLowerCase()
```

simply calls the `toLowerCase()` method of the String class. So, we could replace that with this [method reference](https://docs.oracle.com/javase/tutorial/java/javaOO/methodreferences.html):

```java
String::toLowerCase()
```

In effect, this allows us to reference a function as if it were a first-class citizen, even if we can't truly store it in a variable like other objects in Java.

There are four different types of [method references](https://docs.oracle.com/javase/tutorial/java/javaOO/methodreferences.html):

* **Static Method in a Class** : `ClassName::staticMethodName`
* **Instance Method of Particular Object**: `objectInstance::instanceMethodName`
* **Instance Method of Arbitrary Object of Given Type**: `ClassName::methodName`
* **Constructor**: `ClassName::new`

Many parts of the Java API accept method references along with lambda expressions, so this is yet another way we can make use of existing or anonymous functions in our code. 

For more information on using lambda expressions and method references in Java, check out the references linked below.

### References

* [Lambda Expressions](https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html#syntax) from the Oracle Java Tutorials
* [Method References](https://docs.oracle.com/javase/tutorial/java/javaOO/methodreferences.html) from the Oracle Java Tutorials
* [Java 8 - Lambda Expressions](https://www.tutorialspoint.com/java8/java8_lambda_expressions.htm) from Tutorials Point
* [Lambda Expressions in Java 8](https://www.geeksforgeeks.org/lambda-expressions-java-8/) from GeeksforGeeks
* [Java Lambda Expressions](https://www.w3schools.com/java/java_lambda.asp) from W3Schools
* [Best practices when you use Lambda expressions in Java](https://gelopfalcon.medium.com/best-practices-when-you-use-lambda-expressions-in-java-f51e96d44b25) by Gerardo Lopez Falcón on Medium
