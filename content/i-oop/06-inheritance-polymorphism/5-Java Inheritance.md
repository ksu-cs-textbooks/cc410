---
title: "Java Inheritance"
weight: 25
pre: "5. "
---
In an object-oriented language, inheritance is a mechanism for deriving part of a class definition from another existing class definition.  This allows the programmer to "share" code between classes, reducing the amount of code that must be written.

Consider the Student class we created earlier:

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

This would work well for representing a student.  But what if we are representing multiple _kinds_ of students, like undergraduate and graduate students?  We'd need separate classes for each, but both would still have names and calculate their GPA the same way.  So, it would be handy if we could say "an undergraduate is a student, and has all the properties and methods a student has" and "a graduate student is a student, and has all the properties and methods a student has."  This is exactly what inheritance does for us, and we often describe it as an *is a* relationship.  We distinguish this from the interface mechanism we looked at earlier by saying it is a **strong is a** relationship, as an `Undergraduate` student is, for all purposes, _also_ a `Student`.

Let's define an undergraduate student class:

```java
public class UndergraduateStudent extends Student {
    
    public UndergraduateStudent(String first, String last) {
        super(first, last);
    }

}
```

In Java, we use the `extends` keyword to declare that a class is inheriting from another class. So, `public class UndergraduateStudent extends Student` indicates that `UndergraduateStudent` inherits from (is a) `Student`.  Thus, it has the attributes `first` and `last` that are inherited from `Student`.  Similarly, it inherits the `getGPA()` and `addCourseGrade()` methods.

In fact, the only method we need to define in our `UndergraduateStudent` class is the constructor - and we only need to define this because the base class has a defined constructor taking two parameters, `first` and `last` names.  This `Student` constructor must be invoked by the `UndergraduateStudent` constructor - that's what the `super(first, last)` line does - it invokes the `Student` constructor with the `first` and `last` parameters passed into the `UndergraduateStudent` constructor. In Java, the `super()` method call **must** be the first line in the child class's constructor. It can be omitted if the parent class includes a default (parameter-less) constructor. 

## Inheritance, State, and Behavior

Let's define a `GraduateStudent` class as well.  This will look much like an `UndergraduateStudent`, but all graduates have a bachelor's degree:

```java
public class GraduateStudent extends Student {

    private String bachelorDegree;
    
    public GraduateStudent(String first, String last, String degree) {
        super(first, last);
        this.bachelorDegree = degree;
    }
    
    public String getBachelorDegree() {
        return this.bachelorDegree;
    }

}
```

Here we added a property for `bachelorDegree`.  Since the attribute itself is marked as `private`, it can only be written to by the class, as is done in the constructor.  To the outside world, it is treated as read-only through the getter method.  

Thus, the `GraduateStudent` has all the state and behavior encapsulated in `Student`, _plus_ the additional state of the bachelor's degree title.

## The `protected` Keyword

What you might not expect is that any fields declared `private` in the base class are inaccessible in the derived class.  Thus, the private fields `creditPoints` and `creditHours` cannot be used in a method defined in `GraduateStudent`.  This is again part of the _encapsulation_ and _data hiding_ ideals - we've encapsulated and hid those variables within the base class, and any code outside that assembly, even in a derived class, is not allowed to mess with it.

However, we often will want to allow access to such variables in a derived class.  Java uses the access modifier `protected` to allow for this access in derived classes, but not the wider world.

## Inheritance and Memory

What happens when we construct an instance of `GraduateStudent`?  First, we invoke the constructor of the `GraduateStudent` class:

```java
GraduateStudent gradStudent = new GraduateStudent("Willie", "Wildcat", "Computer Science");
```

This constructor then invokes the constructor of the base class, `Student`, with the arguments `"Willie"` and `"Wildcat"`.  Thus, we allocate space to hold the state of a student, and populate it with the values set by the constructor.  Finally, execution returns to the super class of `GraduateStudent`, which allocates the additional memory for the reference to the `BachelorDegree` property.  Thus, the memory space of the `GraduateStudent` _contains_ an instance of the `Student`, somewhat like nesting dolls.

Because of this, we can treat a `GraduateStudent` object as a `Student` object.  For example, we can store it in a list of type `Student`, along with `UndergraduateStudent` objects:

```java
List<Student> students = new LinkedList<>();
students.Add(gradStudent);
students.Add(new UndergraduateStudent("Dorothy", "Gale"));
```

Because of their relationship through inheritance, both `GraduateStudent` class instances and `UndergraduateStudent` class instances are considered to be of type `Student`, as well as their supertypes.

## Nested Inheritance

We can go as deep as we like with inheritance - each base type can be a superclass of another base type, and has all the state and behavior of all the inherited base classes.

This said, having too many levels of inheritance can make it difficult to reason about an object.  In practice, a good guideline is to limit nested inheritance to two or three levels of depth.

## Abstract Classes

If we have a base class that only exists to be inherited from (like our `Student` class in the example), we can mark it as _abstract_ with the `abstract` keyword.  An abstract class _cannot be instantiated_ (that is, we cannot create an instance of it using the `new` keyword).  It can still define fields and methods, but you can't construct it.  If we were to re-write our `Student` class as an abstract class:

```java
public abstract class Student {
    
    private int creditPoints;
    private int creditHours;
    protected String first;
    protected String last;
    
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

Now with `Student` as an abstract class, attempting to create a `Student` instance:

```java
Student theWiz = new Student("Wizard", "Oz");
```

would fail with an exception.  However, we can still create instances of the derived classes `GraduateStudent` and `UndergraduateStudent`, and treat them as `Student` instances.  It is best practice to make any class that serves only as a base class for derived classes and will never be created directly an abstract class.

{{% notice tip %}}

# Sealed Classes

Some programming languages, such as C#, include a special keyword `sealed` that can be added to a class declaration. A **sealed** class is not inheritable, so no other classes can extend it. This further adds security to the programming model by preventing developers from even creating their own version of that class that would be compatible with the original version.

This is currently a proposed feature for Java version 15. The full details of that proposed feature are described in the [Java Language Updates](https://docs.oracle.com/en/java/javase/15/language/sealed-classes-and-interfaces.html) from Oracle.

Since we are focusing on learning Java that is compatible with Java 8, we won't have access to that feature.

{{% / notice %}}

## Interfaces and Inheritance 

A class can use both inheritance and interfaces.  In Java, a class can only inherit _one_ base class, and it should always be listed first after the `extends` keyword.  Following that, we can have as many interfaces as we want listed after the `implements` keyword, all separated from each other and the base class by commas (`,`):

```java
public class UndergraduateStudent extends Student implements ITeachable, IEmailable {
  // TODO: Implement student class 
}
```
