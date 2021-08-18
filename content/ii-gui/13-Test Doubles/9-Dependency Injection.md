---
title: "Dependency Injection"
weight: 45
pre: "9. "
---
One other important topic to cover in unit tests is **dependency injection**. In short, [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection) is a way that we can build our classes so that the objects they depend on can be added to the class from outside. In that way, we can change them as needed in our unit tests as a way to test functionality using test doubles.

Consider the following example:

###### Java

```java
public class Teacher {

    private Gradebook gradebook;
    private List<Student> studentList;
    
    public Teacher() {
        this.gradebook = new Gradebook("Course Name");
        this.studentList = new List<>();
    }
    
    public void addStudent(Student s) {
        this.studentList.add(s);
    }
    
    public void submitGrades() {
        for (Student s : this.studentList) {
            this.gradebook.gradeStudent(s);
        }
    }
}
```

###### Python

```python
class Teacher:

    def __init__(self) -> None:
        self.__gradebook: Gradebook = Gradebook()
        self.__student_list: List[Student] = list()
        
    def add_student(self, s: Student) -> None:
        self.__student_list.append(s)
        
    def submit_grades(self) -> None:
        for s in self.__student_list:
            self.__gradebook.grade_student(s)
```

In this `Teacher` class, we see a private `Gradebook` instance. That instance is not accessible outside the class, so we cannot directly interact with it in our unit tests, at least without violating the security principles of the class it is in. So, if we want to test that the `submitGrades()` method properly grades every student in the `studentList`, we would need some way to replace the `gradebook` attribute with a test double.

This is where **dependency injection** comes in. Instead of allowing this class to instantiate its own gradebook, we can restructure the code to inject our own gradebook instance. There are several ways we can do this.

### Reduce Security of Attributes

Of course, one way we could accomplish this, even without dependency injection, would be to simply reduce the security of these objects. In Java, we could make them either `public`, which is generally a bad idea for something so secure as a gradebook, or package-private, with no modifier. We've used the package-private trick in one of the earlier example videos to access some GUI elements, but in this case we probably want something better.

In Python, we know that any attribute can be accessed externally, so this isn't as big of a concern. However, since we are using a double-underscore in the name, we'd have to get around the name mangling. We could switch it to a single underscore, which is still marked as internal to the class but would at least be more easily accessible to our tests. However, as with the Java example, there are other ways we could accomplish this.

### Constructor Injection

The first method of dependency injection is via the constructor. We could simply pass in a reference to a `Gradebook` object in the constructor, as in this example:

###### Java

```java
public Teacher(Gradebook grade) {
    if (grade == null) {
        throw new IllegalArgumentException("Gradebook cannot be null")
    }
    this.gradebook = grade
    this.studentList = new List<>();
}
```

###### Python

```python
def __init__(self, grade: Gradebook) -> None:
    if grade is None:
        raise ValueError("Gradebook cannot be None")
    self.__gradebook: Gradebook = grade
    self.__student_list: List[Student] = list()
```

The benefit of this approach is that we can easily replace an actual `Gradebook` instance in our unit tests with any test double we'd like, making it every easy to test the `submitGrades()` method.

Unfortunately, this does require any class that instantiates a `Teacher` object to also instantiate a `Gradebook` along with it, making that process more complex. This complexity can be reduced using some design patterns such as the builder pattern or factory method pattern. 

Finally, the class that instantiates the `Teacher` object would also have a reference to the `Gradebook` that teacher is using, so it could allow a malicious coder to have access to data that should be kept private. However, typically this isn't a major concern we worry about, since we must always assume that any programmer on this project could access any data stored in a class, as nothing is _truly_ private as we've already discussed. 

### Setter Injection

Alternatively, we can provide a setter method and allow injection via the setter. This could be done either in lieu of building a `Gradebook` object in the constructor, or in addition to it. 

###### Java

```java
public void setGradebook (Gradebook grade) {
    if (grade == null) {
        throw new IllegalArgumentException("Gradebook cannot be null")
    }
    this.gradebook = grade;
}
```

###### Python

```python
def set_gradebook(grade: Gradebook) -> None:
    if grade is None:
        raise ValueError("Gradebook cannot be None")
    self.__gradebook: Gradebook = grade`
```

You may recognize this approach from several earlier courses in this program - we use this technique for grading some of the data structures and programs by injecting our own data and seeing how your code interacts with it. We typically include `debug` in the name of these methods, to make it clear that they are only for debugging and should be removed from the final code. 

### Other Methods

In addition to the three methods listed above, there are some other ways we can accomplish this:

* Using Inheritance or Interfaces - we can declare methods to inject objects as part of a parent class or an interface. 
* Using the Factory Method pattern - we can replace the static methods in the factory class to return a test double instead of the real object. 
* Several frameworks exist to automate this process in various languages.

Many of these are discussed in greater detail in the [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection) article on Wikipedia.

## Best Practices

In general, we want to build our code in a way that it can easily be tested, and that means providing some way to perform dependency injection that doesn't interfere with the normal operation of our program.

Here are some quick tips that you may be able to use when you need to implement dependency injection:

1. Write your class in such a way that it can either function without the dependency being provided (i.e. it instantiates its own by default, and replaces it with the injected one as needed).
2. Verify that dependencies are properly instantiated when they are injected.
3. Make the methods that inject dependencies not public, so it is clear that they should only be used internally in testing and within the class or package they are present in.
4. Use design patterns such as the builder pattern or factory method pattern to simplify creation of these objects, automatically handling injection as needed.

Dependency injection is a very powerful testing technique, but one that must be used carefully to prevent introducing additional bugs and complexity to your application.
