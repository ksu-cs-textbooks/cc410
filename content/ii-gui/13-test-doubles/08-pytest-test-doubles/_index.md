---
title: "Test Doubles in pytest"
weight: 40
pre: "8. "
---

{{% youtube pNqcrx785Gs %}}

[Video Materials}({{<relref "./video">}})

To create test doubles in Python, we'll rely on the built-in [unittest.mock](https://docs.python.org/3/library/unittest.mock.html) library. It includes lots of quick and easy methods for creating fake objects in Python, and it is compatible with the pytest testing framework that we're already using.

## Adding Mocks to a Test Class

There are many different ways to use the `unittest.mock` library. One of the easiest ways is to import the `patch` annotation

```python
from unittest.mock import patch


class TestClassroom:

    # tests here
    
```

## Creating Fake Objects

Once we've imported the `patch` annotation, we can use it to create fake objects for our test methods. 

```python
from unittest.mock import patch
from people.Person import Person
from people.Teacher import Teacher
from places.Classroom import Classroom


class TestClassroom:

    @patch('people.Teacher', spec=Teacher)
    @patch('people.Person', spec=Person)
    def test_classroom_has_teacher(self, fake_person, fake_teacher) -> None:
        # test code
    
```

This will create fake objects `fake_person` and `fake_teacher` that mimic the attributes and methods contained in the `Person` and `Teacher` classes, respectively. However, by default, those objects won't do anything, and most methods will not actually work by default.

Notice that the fake objects are added as parameters to our test method, but they are added in reverse order. This is because method annotations are interpreted "inside-out", so the one at the bottom, closest to the method, is interpreted first. So, in this example, our `fake_person` will be created first, followed by our `fake_teacher`. 

Without doing anything else, we can use these fake objects in place of the real ones, as in this test:

```python
from unittest.mock import patch
from people.Person import Person
from people.Teacher import Teacher
from places.Classroom import Classroom


class TestClassroom:

    @patch('people.Teacher', spec=Teacher)
    @patch('people.Person', spec=Person)
    def test_classroom_has_teacher(self, fake_person, fake_teacher) -> None:
        classroom: Classroom = Classroom()
        assert classroom.has_teacher == False
        
        classroom.add_teacher(fake_teacher)
        assert classroom.has_teacher == True 
```

As we can see, we are able to add the `fake_teacher` object to our classroom, and it is treated just like any other `Teacher` object, at least as far as the system is concerned thus far. 

However, if we want those fake objects to do something, we have to include method stubs as well.

## Adding Stubs

To add a method stub to a fake object, we can set the `return_value` of the method:

```python
from unittest.mock import patch
from people.Person import Person
from people.Teacher import Teacher
from places.Classroom import Classroom


class TestClassroom:

    @patch('people.Teacher', spec=Teacher)
    @patch('people.Person', spec=Person)
    def test_classroom_get_teacher_name(self, fake_person, fake_teacher) -> None:
        # create a method stub for `get_name` method
        fake_teacher.get_name.return_value = "Teacher Person"
        
        classroom: Classroom = Classroom()
        classroom.add_teacher(fake_teacher)
        
        # assert that the classroom returns the teacher's name
        assert classroom.get_teacher_name() == "Teacher Person"
```

In this example, we are adding a method stub to our `fake_teacher` object that will return `"Teacher Person"` whenever the `get_name()` method is called. Then, we are adding that fake `Teacher` object to the `Classroom` class that we are testing, and calling the `get_teacher_name()` method. We're assuming that the `get_teacher_name()` method in the `Classroom` class calls the `get_name()` method of the `Teacher` object contained in the class. However, instead of using a real `Teacher` instance, we've provided a fake object that only knows what to do when that one method is called. So, it returns the value we expect, which passes our test!

## Stubbing Properties

If our classes use properties instead of traditional getter and setter methods, we have to create our property stubs in a slightly different way:

```python
from unittest.mock import patch, PropertyMock
from people.Person import Person
from people.Teacher import Teacher
from places.Classroom import Classroom


class TestClassroom:

    @patch('people.Teacher', spec=Teacher)
    @patch('people.Person', spec=Person)
    def test_classroom_get_teacher_name(self, fake_person, fake_teacher) -> None:
        # create a property stub for `get_name` property
        type(fake_teacher).name = PropertyMock(return_value="Teacher Person")
        
        classroom: Classroom = Classroom()
        classroom.add_teacher(fake_teacher)
        
        # assert that the classroom returns the teacher's name
        assert classroom.get_teacher_name() == "Teacher Person"
```

In this case, we are creating an instance of the [PropertyMock](https://docs.python.org/3/library/unittest.mock.html#unittest.mock.PropertyMock) class that acts as a fake property for an object. However, because of how fake objects work, we cannot directly attach the `PropertyMock` instance directly to the `fake_teacher` object. Instead, we must attach it to the mock type object, which we can access by using the `type` method. Thankfully, even if we have several fake instances of the same class, these properties will be unique to the fake instance, not to the class they are faking. 

## Faking Static Classes

There is one more complex use case we may run into in our testing - creating a fake version of a class with static methods. 

```python
from unittest.mock import patch, PropertyMock
from people.Person import Person
from people.Teacher import Teacher
from places.Classroom import Classroom
from rules.TeacherRules import TeacherRules
import pytest


class TestClassroom:

    @patch('people.Teacher', spec=Teacher)
    @patch('people.Person', spec=Person)
    def test_teacher_fails_minimum_age_requirement(self, fake_person, fake_teacher) -> None:
        # create a fake version of the static method
        with patch.object(TeacherRules, 'get_minimum_age', return_value=16):
        
            # Add a fake property to the teacher
            type(fake_teacher).age = PropertyMock(return_value=15)
            classroom: Classroom = Classroom()
            
            with pytest.raises(ValueError):
                classroom.add_teacher(fake_teacher)

```

In this example, we have a `TeacherRules` class that includes a static method `get_minimum_age()` that returns the minimum age allowed for a teacher. To test this, we are creating a fake version of that static method using the `patch.object` method. We have to do this in a with statement, which makes sure that the fake method does not persist outside of this test. In this case, we'll set that method to return a value of `16`.

We'll also add a method stub to return an invalid age on our fake `Teacher` object. Finally, when we try to add that teacher to a classroom, it should raise an exception since the teacher is not old enough.

This is a very brief introduction to using test doubles made with the unittest.mock library, but it should be enough for our use in this class. Feel free to refer to some of the documentation linked below for more examples and information.

### References

* [unittest.mock](https://docs.python.org/3/library/unittest.mock.html) Documentatio
* [Understanding the Python Mock Object Library](https://realpython.com/python-mock-library/) from Real Python
