---
title: "Type Checking and Conversion"
weight: 40
pre: "8. "
---
You have probably used casting to convert numeric values from one type to another, i.e.:

###### Java

```java
double a = 5.5;
int b = (int) a;
```

###### Python

```
a: float = 5.5
b: int = int(a)
```

What you are actually doing when you cast is _transforming a value from one type to another_.  In the first case, you are taking the value of `a`, which is the floating-point value `5.5`, and converting it to the equivalent integer value `5`. 

Both of these are examples of an **explicit cast**, since we are explicitly stating the type that we'd like to convert our existing value to. 

In some languages, we can also perform an **implicit cast**. This is where the compiler or interpreter changes the type of our value behind the scenes for us. 

###### Java

```java
int a = 5;
double b = a + 2.5;
```

###### Python

```
a: int = 5
b: float = a + 2.5;
```

In these examples, the integer value stored in `a` is implicitly converted to the floating point value `5.0` before it is added to `2.5` to get the final result. This conversion is done automatically for us. 

However, as we've observed already, each language has some special cases where implicit casting is not allowed. In general, if the implicit cast will result in loss of data, such as when a floating-point value is converted to an integer, we must use an explicit cast instead. 

## Casting and Inheritance

Casting becomes a bit more involved when we consider inheritance.  As you saw in the previous discussion of inheritance, we can treat derived classes _as the base class_. For example, in Java, the code:

###### Java

```java
Student willie = new UndergraduateStudent("Willie", "Wildcat");
```

is actually _implicitly casting_ the `UndergraduateStudent` object "Willie Wildcat" into a `Student` class.  Because an `UndergraduateStudent` is a `Student`, this cast can be _implicit_. Going the other way requires an _explicit cast_ as there is a chance that the `Student` we are casting _isn't_ an `UndergraduateStudent`, i.e.:

###### Java

```java
UndergraduateStudent u = (UndergraduateStudent)willie;
```

If we tried to cast `willie` into a graduate student:

###### Java

```java
GraduateStudent g = (GraduateStudent)willie;
```

The program would throw a `ClassCastException` when run.

In Python, things are a bit differently. Recall that Python is a dynamically typed language. So, when we create an `UndergraduateStudent` object, the Python interpreter knows that that object has the type `UndergraduateStudent`. So, we can treat it as an instance of both the `Student` and `UndergraduateStudent` class. We don't have to perform any conversions to do so.

However, if we try to treat it like an instance of the `GraduateStudent` class, it would fail with an `AttributeError`. 

## Checking Types

Both Java and Python include special methods for determining if a particular object is compatible with a certain type. 

###### Java

```java
Student u = new UndergraduateStudent("Willie", "Wildcat");
if (u instanceof UndergraduateStudent) {
    UndergraduateStudent uGrad = (UndergraduateStudent) willie;
    // treat willie as an undergraduate student here
}
```

###### Python

```python
u: Student = UndergraduateStudent("Willie", "Wildcat")
if isinstance(u, UndergraduateStudent):
    # treat willie as an undergraduate student here
```

Java uses the `instanceof` operator to perform the check, while Python has a built-in `isinstance` method to perform the same task. Typically these statements are used as part of a conditional statement, allowing us to check if an object is compatible with a given type before we try to use that object in that way. 

So, if we have a list of `Student` objects, we can use this method to determine if those objects are instances of `UndergraduateStudent` or `GraduateStudent`. It's pretty handy!
