---
title: "Test Doubles in JUnit"
weight: 35
pre: "7. "
---

{{% youtube sSokD2zkA8A %}}

[Video Materials]({{<relref "./video">}})

To create test doubles in JUnit, we'll rely on a separate library called Mockito. [Mockito](https://site.mockito.org/) is a framework for creating mock objects in Java that works well with JUnit, and has become one of the most commonly used tools for this task.

## Installing Mockito in Gradle

To install Mockito, we just update the `testImplementation` line in our `build.gradle` file to include both the `mockito-inline` library, as well as the `mockito-junit-jupiter` library that allows Mockito and JUnit to work together seamlessly.

```groovy {hl_lines=[3]}
dependencies {
    // Use JUnit Jupiter API for testing.
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.6.2', 'org.hamcrest:hamcrest:2.2', 'org.junit.jupiter:junit-jupiter-params', 'org.mockito:mockito-inline:3.8.0', 'org.mockito:mockito-junit-jupiter:3.8.0'

    // Use JUnit Jupiter Engine for testing.
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine'

    // This dependency is used by the application.
    implementation 'com.google.guava:guava:29.0-jre'
}
```

## Adding Mockito to a Test Class

There are many different ways to use Mockito with JUnit. One of the easiest ways that works in the latest versions of Mockito and JUnit is to use the `@ExtendWith` annotation above our test class:

```java
import static org.junit.jupiter.api.Assertions.assertTrue;
import static org.mockito.Mockito.when;

import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.extension.ExtendWith;
import org.mockito.Mock;
import org.mockito.junit.jupiter.MockitoExtension;

@ExtendWith(MockitoExtension.class)
public class UnitTestClass {
    // tests here
}
```

By including that annotation above our test class declaration, Mockito will automatically perform any setup steps required. In earlier versions of JUnit and Mockito, we would have to do these steps manually, but this process has been greatly simplified recently.

One thing we can do is modify this a bit to set Mockito to use [STRICT_STUBS](https://javadoc.io/static/org.mockito/mockito-core/3.8.0/org/mockito/quality/Strictness.html#STRICT_STUBS). This tells Mockito to print errors when we create any test doubles that aren't used, and the ones that are used are created properly. So, instead of using `@ExtendWith`, we can instead use `@MockitoSettings`:

```java
import static org.junit.jupiter.api.Assertions.assertTrue;
import static org.mockito.Mockito.when;

import org.junit.jupiter.api.Test;
import org.mockito.Mock;
import org.mockito.junit.jupiter.MockitoSettings;
import org.mockito.quality.Strictness;

@MockitoSettings(strictness = Strictness.STRICT_STUBS)
public class UnitTestClass {
    // tests here
}
```

Since this is recommended by the Mockito documentation, we'll go ahead and use it in our code. 

## Creating Fake Objects

Once we've added Mockito to our test class, we can create fake objects using the `@Mock` annotation above object declarations. This is commonly done on global objects in our test class:

```java
import static org.junit.jupiter.api.Assertions.assertTrue;
import static org.mockito.Mockito.when;

import org.junit.jupiter.api.Test;
import org.mockito.Mock;
import org.mockito.junit.jupiter.MockitoSettings;
import org.mockito.quality.Strictness;

@MockitoSettings(strictness = Strictness.STRICT_STUBS)
public class UnitTestClass {
    
    @Mock
    Person mockPerson;
    @Mock
    Teacher mockTeacher;
    
    // tests here
}
```

This will create fake objects that mimic the attributes and methods contained in the `Person` and `Teacher` class. However, by default, those objects won't do anything, and most methods will just return the default value for the return type of the method. 

Without doing anything else, we can use these fake objects in place of the real ones, as in this test:

```java
import static org.junit.jupiter.api.Assertions.assertTrue;
import static org.mockito.Mockito.when;

import org.junit.jupiter.api.Test;
import org.mockito.Mock;
import org.mockito.junit.jupiter.MockitoSettings;
import org.mockito.quality.Strictness;

@MockitoSettings(strictness = Strictness.STRICT_STUBS)
public class ClassroomTest {
    
    @Mock
    Person mockPerson;
    @Mock
    Teacher mockTeacher;
    
    public void testClassroomHasTeacher() {
        Classroom classroom = new Classroom()
        assertTrue(classroom.hasTeacher() == false);
        
        classroom.addTeacher(mockTeacher);
        assertTrue(classroom.hasTeacher() == true);
    }
}
```

As we can see, we are able to add the `mockTeacher` object to our classroom, and it is treated just like any other `Teacher` object, at least as far as the system is concerned thus far. 

However, if we want those fake objects to do something, we have to include method stubs as well.

## Adding Stubs

To add a method stub to a fake object, we can use the `when` method in Mockito. Here's an example:

```java
import static org.junit.jupiter.api.Assertions.assertTrue;
import static org.mockito.Mockito.when;

import org.junit.jupiter.api.Test;
import org.mockito.Mock;
import org.mockito.junit.jupiter.MockitoSettings;
import org.mockito.quality.Strictness;

@MockitoSettings(strictness = Strictness.STRICT_STUBS)
public class ClassroomTest {
    
    @Mock
    Person mockPerson;
    @Mock
    Teacher mockTeacher;
    
    @Test
    public void testClassroomGetTeacherName() {
        // create a method stub for `getName`
        when(mockTeacher.getName()).thenReturn("Teacher Person");
        
        Classroom classroom = new Classroom();
        classroom.addTeacher(mockTeacher);
        
        // assert that the classroom returns the teacher's name
        assertTrue(classroom.getTeacherName().equals("Teacher Person"));
    }
}
```

In this example, we are adding a method stub to our `mockTeacher` object that will return `"Teacher Person"` whenever the `getName()` method is called. Then, we are adding that fake `Teacher` object to the `Classroom` class that we are testing, and calling the `getTeacherName()` method. We're assuming that the `getTeacherName()` method in the `Classroom` class calls the `getName()` method of the `Teacher` object contained in the class. However, instead of using a real `Teacher` instance, we've provided a fake object that only knows what to do when that one method is called. So, it returns the value we expect, which passes our test!

## Faking Static Classes

There is one more complex use case we may run into in our testing - creating a fake version of a class with static methods. This is a relatively new feature in Mockito, but it allows us to test some functionality that is otherwise very difficult to mimic.

```java
import static org.junit.jupiter.api.Assertions.assertThrows;
import static org.junit.jupiter.api.Assertions.assertTrue;
import static org.mockito.Mockito.when;

import java.lang.IllegalArgumentException;
import org.junit.jupiter.api.Test;
import org.mockito.Mock;
import org.mockito.MockedStatic;
import org.mockito.Mockito;
import org.mockito.junit.jupiter.MockitoSettings;
import org.mockito.quality.Strictness;

@MockitoSettings(strictness = Strictness.STRICT_STUBS)
public class ClassroomTest {
    
    @Mock
    Person mockPerson;
    @Mock
    Teacher mockTeacher;
    
    @Test
    public void testTeacherFailsMinimumAgeRequirement() {
        // Create mock static class
        try (MockedStatic<TeacherRules> mockTeacherRules = Mockito.mockStatic(TeacherRules.class)) {
            
            // Create method stub for static class
            mockTeacherRules.when(() -> TeacherRules.getMinAge()).thenReturn(16);
            
            // Create method stub for fake Teacher
            when(mockTeacher.getAge()).thenReturn(15);
            
            // Test functionality
            Classroom classroom = new Classroom();
            assertThrows(IllegalArgumentException.class, () -> classroom.addTeacher(mockTeacher));
        }
    }
}
```

In this example, we have a `TeacherRules` class that includes a static method `getMinAge()` that returns the minimum age allowed for a teacher. To test this, we are creating a fake version of that class using the `Mockito.mockStatic()` method. We have to do this in a try with resources statement, which makes sure that the fake class does not persist outside of this test. 

Once we've created the fake class `mockTeacherRules`, we can add a method stub for the static method. We'll also add a method stub to return an invalid age on our fake `Teacher` object. Finally, when we try to add that teacher to a classroom, it should throw an exception since the teacher is not old enough.

This is a very brief introduction to using test doubles made with Mockito, but it should be enough for our use in this class. Feel free to refer to some of the documentation linked below for more examples and information.

### References

* [Mockito Official Site](https://site.mockito.org/)
* [Mockito Javadoc](https://javadoc.io/doc/org.mockito/mockito-core/latest/index.html)
* [Mockito JUnit Javadoc](https://javadoc.io/doc/org.mockito/mockito-junit-jupiter/latest/index.html)
* [Mockito Class Documentation](https://javadoc.io/doc/org.mockito/mockito-core/latest/org/mockito/Mockito.html)
* [Mockito Series](https://www.baeldung.com/mockito-series) from Baeldung
* [Unit Tests with Mockit](https://www.vogella.com/tutorials/Mockito/article.html) from Vogella
