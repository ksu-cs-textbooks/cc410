---
title: "Python Inheritance"
weight: 35
pre: "7. "
---

In an object-oriented language, inheritance is a mechanism for deriving part of a class definition from another existing class definition.  This allows the programmer to "share" code between classes, reducing the amount of code that must be written.

Consider the Student class we created earlier:

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

This would work well for representing a student.  But what if we are representing multiple _kinds_ of students, like undergraduate and graduate students?  We'd need separate classes for each, but both would still have names and calculate their GPA the same way.  So, it would be handy if we could say "an undergraduate is a student, and has all the properties and methods a student has" and "a graduate student is a student, and has all the properties and methods a student has."  This is exactly what inheritance does for us, and we often describe it as an *is-a* relationship.  We distinguish this from the interface mechanism we looked at earlier by saying it is a **strong is-a** relationship, as an `Undergraduate` student is, for all purposes, _also_ a `Student`.

Let's define an undergraduate student class:

```python
class UndergraduateStudent(Student):

    def __init__(self, first: str, last: str) -> None:
        super().__init__(first, last)
```

In Python, we list the classes that a new class is inheriting from in parentheses at the end of the class definition. So, `class UndergraduateStudent(Student):` indicates that `UndergraduateStudent` inherits from (is a) `Student`.  Thus, it has the attributes `first` and `last` that are inherited from `Student`, as well as the `gpa` property.  Similarly, it inherits the `add_course_grade()` method.

In fact, the only method we need to define in our `UndergraduateStudent` class is the constructor - and we only need to define this because the base class has a defined constructor taking two parameters, `first` and `last` names.  This `Student` constructor must be invoked by the `UndergraduateStudent` constructor - that's what the `super().__init__(first, last)` line does - it invokes the `Student` constructor with the `first` and `last` parameters passed into the `UndergraduateStudent` constructor. In Python, the `super()` method call is usually the first line in the child class's constructor, but it doesn't have to be. It can be omitted if the parent class includes a default (parameter-less) constructor.

## Inheritance, State, and Behavior

Let's define a `GraduateStudent` class as well.  This will look much like an `UndergraduateStudent`, but all graduates have a bachelor's degree:

```python
class GraduateStudent(Student):
    
    def __init__(self, first: str, last: str, degree: str) -> None:
        super().__init__(first, last)
        self.__bachelor_degree = degree
        
    @property
    def bachelor_degree(self) -> str:
        return self.__bachelor_degree
```

Here we added a property for `bachelor_degree`.  Since the attribute itself is meant to be a private attribute (the name begins with two underscores `__`), it should only be written to by the class, as is done in the constructor.  To the outside world, it is treated as read-only through the getter method. Of course, in Python, nothing is truly private, so a determined developer can always access these attributes if desired. 

Thus, the `GraduateStudent` has all the state and behavior encapsulated in `Student`, _plus_ the additional state of the bachelor's degree title.

## Protected Attributes

What you might not expect is that any fields that are `private` in the base class are inaccessible in the derived class. This is due to the way that Python performs [name mangling](https://www.geeksforgeeks.org/name-mangling-in-python/) of names that begin with two underscores `__`. Thus, the private fields `credit_points` and `credit_hours` cannot be used in a method defined in `GraduateStudent`.  This is again part of the _encapsulation_ and _data hiding_ ideals - we've encapsulated and hid those variables within the base class, and any code outside that assembly, even in a derived class, is not allowed to mess with it.

However, we often will want to allow access to such variables in a derived class. In Python, we can use a single underscore `_` in front of a variable or method name to indicate that it should be treated like a **protected** attribute, which is only accessed by the class that defines it and any classes that inherit from that class. However, as with anything else in Python, this attribute will still be accessible to any code within our program, so it is up to developers to respect the naming scheme and not try to access those directly.

In UML, protected attributes are denoted by a hash symbol `#` as the visibility of the attribute. 

## Inheritance and Memory

What happens when we construct an instance of `GraduateStudent`?  First, we invoke the constructor of the `GraduateStudent` class:

```python
grad_student: GraduateStudent = GraduateStudent("Willie", "Wildcat", "Computer Science")
```

This constructor then invokes the constructor of the base class, `Student`, with the arguments `"Willie"` and `"Wildcat"`.  Thus, we allocate space to hold the state of a student, and populate it with the values set by the constructor.  Finally, execution returns to the super class of `GraduateStudent`, which allocates the additional memory for the reference to the `bachelor_degree` property.  Thus, the memory space of the `GraduateStudent` _contains_ an instance of the `Student`, somewhat like nesting dolls.

Because of this, we can treat a `GraduateStudent` object as a `Student` object.  For example, we can store it in a list that contains `Student` instances, along with `UndergraduateStudent` objects:

```python
students: List[Student] = list()
students.append(grad_student)
students.append(UndergraduateStudent("Dorothy", "Gale"))
```

Because of their relationship through inheritance, both `GraduateStudent` class instances and `UndergraduateStudent` class instances are considered to be of type `Student`, as well as their supertypes.

## Nested Inheritance

We can go as deep as we like with inheritance - each base type can be a superclass of another base type, and has all the state and behavior of all the inherited base classes.

This said, having too many levels of inheritance can make it difficult to reason about an object.  In practice, a good guideline is to limit nested inheritance to two or three levels of depth.

## Abstract Classes

If we have a base class that only exists to be inherited from (like our `Student` class in the example), we can mark it as _abstract_ by inheriting from the `ABC` class. `ABC` is short for **abstract base class**.  An abstract class _cannot be instantiated_ (that is, we cannot create an instance of it by calling its constructor) unless all of its abstract methods have been overridden.  It can still define fields and methods, but you can't construct it.  If we were to re-write our `Student` class as an abstract class:

```python
from abc import ABC


class Student(ABC):
    
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

Now with `Student` as an abstract class, attempting to create a `Student` instance:

```python
the_wiz: Student = Student("Wizard", "Oz")
```

would still be allowed since our `Student` class does not define any abstract methods. However, we can add an abstract method, such as the `student_type` method shown below.

```python
    @abstractmethod
    def student_type(self) -> str:
        raise NotImplementedError
```

If that method is placed within our `Student` class, we could no longer directly instantiate the class since it contains an abstract method. However, we can still create instances of the derived classes `GraduateStudent` and `UndergraduateStudent`, and treat them as `Student` instances, provided that they override the abstract method `student_type` in their code. It is best practice to make any class that serves only as a base class for derived classes and will never be created directly an abstract class.

{{% notice info info-i "Sealed Classes" %}}

Some programming languages, such as C#, include a special keyword `sealed` that can be added to a class declaration. A **sealed** class is not inheritable, so no other classes can extend it. This further adds security to the programming model by preventing developers from even creating their own version of that class that would be compatible with the original version.

This could theoretically be done in Python through the use of metaprogramming. However, due to the fact that no attributes or methods are truly private in Python, it wouldn't have the desired effect of preventing other classes from gaining access to protected attributes and methods. So, we won't cover how to do this here. 

{{% / notice %}}

## Interfaces and Inheritance 

A class can use both inheritance and interfaces.  In Python, a class can inherit multiple base classes, either as interfaces or as true parent classes. They work the same way - how the class is handled really depends on the code in the class that is being inherited. 

```python
class UndergraduateStudent(Student, ITeachable, IEmailable):
```

For more on multiple inheritance in Python, check out the [Multiple Inheritance in Python](https://realpython.com/lessons/multiple-inheritance-python/) article from Real Python.
