---
title: "Types"
weight: 10
pre: "2. "
---

{{% youtube 6X3xXxPNguo %}}

[Video Materials](video)

Before we can discuss polymorphism in detail, we must first understand the concept of _types_.  In computer science, a _type_ is a way of categorizing a variable by its storage strategy, i.e., how it is represented in the computer's memory. It also defines how the value can be treated and what operations can be performed on it. 

You've already used types extensively in your programming up to this point.  Consider the declaration:

{{< tabs >}}

{{% tab name="Java" %}}

```java
int number = 5;
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
number: int = 5
```

{{% /tab %}}

{{< /tabs >}}

The variable **number** is declared to have the type **int**. In Java, the type included in the declaration tells the Java compiler that the value of the number will be stored using a specific scheme for integer values. For Python, the type is implied by the value itself - since 5 is a whole number, it is treated like an integer. The type annotation `int` is used by Mypy for type checking, but us ignored by the Python interpreter itself.

Each language stores these values in memory differently, and we won't worry about those technical differences in this course. What is important to remember is that the variable's data type tells the computer how to store that value, and also what operations can be performed on that value. 

For example, consider the following code:

{{< tabs >}}

{{% tab name="Java" %}}

```java
int x = 5;
int y = 7;
String string = " apples";
System.out.println(x + y); // 12
System.out.prinltn(x + string); // 5 apples
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
x: int = 5
y: int = 7
string: str = " apples"
print(x + y) # 12
print(x + string) # TypeError
```

{{% /tab %}}

{{< /tabs >}}

Consider the last two lines of each example - we are using the plus `+` operator between two different variables. In the first case, the two operands `x` and `y` are both integers. So, the computer will know that the plus operator should be treated like addition, and it will add those two integer values together. 

In the second case, one operand `x` is an integer, but the other operand `string` is a string value. What should happen in that case? As it turns out, each language does this a bit differently. In Java, the plus operator can also be used for concatenation, so the result will be `5 apples`. Python, however, will raise a `TypeError` since it doesn't know what the plus operator means when applied to a string and an integer. 

In either case, our computer is able to use the data type assigned to each variable to determine how it should be treated and what operations it can perform. 

## User-Defined Types
In addition to built-in types, most programming languages support _user-defined types_, that is, new types defined by the programmer.  For example, we could define an enumerator called `Grade`:

{{< tabs >}}

{{% tab name="Java" %}}

```java
public enum Grade {
  A,
  B,
  C,
  D,
  F;
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
from enum import Enum


class Grade(Enum):
  A = 1
  B = 2
  C = 3
  D = 4
  F = 5
```

{{% /tab %}}

{{< /tabs >}}

This defines a new data type `Grade`.  We can then create variables with that type:

{{< tabs >}}

{{% tab name="Java" %}}

```java
Grade courseGrade = Grade.A;
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
course_grade: Grade = Grade.A
```

{{% /tab %}}

{{< /tabs >}}

## Classes are Types

In an object-oriented programming language, a class also _defines a new type_!  As we discussed in an earlier chapter, a class defines the structure for the _state_ for objects implementing that type. Consider a class named `Student` as shown in this example:

{{< tabs >}}

{{% tab name="Java" %}}

```java
public class Student {
    
    private int creditPoints;
    private int creditHours;
    private String first;
    private String last;
    
    // accessor methods for first and last omitted

    public Student(String first, String last) {
        this.first = first;
        this.last = last;
    }
    
    /**
     * Gets the student's grade point average.
     */
    public double getGPA() {
        return ((double) creditPoints) / creditHours;
    }
    
    /**
     * Records a final grade for a course taken by this student.
     * 
     * @param grade       the grade earned by the student
     * @param hours       the number of credit hours in the course
     */
    public void addCourseGrade(Grade grade, int hours) {
        this.creditHours += hours;
        switch(grade) {
            case A:
                this.creditPoints += 4 * hours;
                break;
            case B:
                this.creditPoints += 3 * hours;
                break;
            case C:
                this.creditPoints += 2 * hours;
                break;
            case D:
                this.creditPoints += 1 * hours;
                break;
            case F:
                this.creditPoints += 0 * hours;
                break;
        }
    }
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
class Student:

    def __init__(self, first: str, last: str) -> None:
        self.__first: str = first
        self.__last: str = last
        self.__credit_points: int = 0
        self.__credit_hours: int = 0
        
    # properties for first and last omitted
    
    @property
    def gpa(self) -> float:
        """Gets the student's grade point average.
        """
        return self.__credit_points / self.__credit_hours
    
    def add_course_grade(self, grade: Grade, hours: int) -> None:
        """Records a final grade for a course taken by this student.
        
        Args
           grade: the grade earned by the student
           hours: the number of credit hours in the course
        """
        self.__credit_hours += hours
        if grade == Grade.A:
            self.__credit_points += 4 * hours
        elif grade == Grade.B:
            self.__credit_points += 3 * hours
        elif grade == Grade.C:
            self.__credit_points += 2 * hours
        elif grade == Grade.D:
            self.__credit_points += 1 * hours
        elif grade == Grade.F:
            self.__credit_points += 0 * hours
```

{{% /tab %}}

{{< /tabs >}}

If we want to create a new student, we would create an instance of the class `Student` which is an object of _type_ `Student`:

{{< tabs >}}

{{% tab name="Java" %}}

```java
Student willie = new Student("Willie", "Wildcat");
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
willie: Student = Student("Willie", "Wildcat")
```

{{% /tab %}}

{{< /tabs >}}

Hence, the _type_ of an object is _the class it is an instance of_.  This is a staple across all object-oriented languages.

## Static vs. Dynamic Typed Languages
A final note on types.  You may hear languages being referred to as _statically_ or _dynamically_ typed.  A _statically_ typed language is one where the type is set by the code itself, either _explicitly_ like Java:

```java
int foo = 5;
```

or _implicitly_, where the compiler or interpreter determines the type based on the value, as in this statement from C# using the special `var` type:

```csharp
var bar = 6;
```

In a statically typed language, a variable _cannot_ be assigned a value of a different type, i.e.:

```java
foo = 8.3;
```

Will fail with an error in Java, as a floating point value is a different type than an integer. However, we can _cast_ the value to a new type (changing how it is represented), i.e.:

{{< tabs >}}

{{% tab name="Java" %}}

```java
int x = (int)8.9;
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
x: int = int(8.9)
```

{{% /tab %}}

{{< /tabs >}}

For this to work, the language must know how to perform the cast. The cast may also lose some information - in the above example, the resulting value of `x` is *8* (the fractional part is discarded).

In contrast, in a _dynamically_ typed language the type of the variable changes when a value of a different type is assigned to it.  For example, in Python, this expression is legal:

###### Python

```python
a = 5
a = "foo"
```

and the type of **a** changes from an integer (at the first assignment) to string (at the second assignment).

C#, Java, C, C++, and Kotlin are all _statically typed languages_, while Python, JavaScript, and Ruby are _dynamically typed languages_. 
