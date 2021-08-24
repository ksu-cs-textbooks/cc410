---
title: "Generics in Python"
weight: 15
pre: "3. "
---

One major topic in the Python programming language that we've made use of but haven't really explained is the use of **generic types**. A generic type is a class or interface that can accept a parameter for the **type** of object that it stores. A great example is the [List](https://docs.python.org/3/tutorial/datastructures.html) class that we are very familiar with. When providing type hints for a list class, we can provide the type that should be stored in the class in square brackets `[]`:

```python
person_list: List[Person] = list()
```

So, as we know, this `List` object will only allow us to store objects compatible with the `Person` type. If we try to add anything else to that list, the type checker will raise an error. Of course, since we are working in a dynamically-typed language, there is nothing that will prevent us from doing so in practice, but using a type checker such as Mypy will help us find these errors in our code. Likewise, when we access an element in the list, it will automatically be given to us as a `Person` object, without any casting or type inference required.

```python
person: Person = Person("Willie", 42)
person_list.append(person)

person_out: Person = person_list[0]  # no cast or type check required

person_list.append("Test")                # TYPE CHECK ERROR!
```

Compare that with a non-generic version of a List class, such as the one you probably created as part of a data structures course:

```python
from typing import List


class MyArrayList:

    def __init__(self) -> None:
        self.__array: List[Object] = list()
        
    def append(self, obj: Object) -> None:
        self.__array.append(obj)
        
    def get(self, i: int) -> Object:
        self.__array[i]
```

If we wish to use the simple class above, we can instantiate it using this code:

```python
my_person_list: MyArrayList = MyArrayList()
```

This class stores objects using the top-level `Object` class. So, it can store every possible type of object, but it doesn't have any way of enforcing types at all. Consider the same code example:

```
person: Person = Person("Willie", 42)
my_person_list.append(person)  # Person is a subtype of Object

person_out: Person = my_person_list[0]       # TYPE CHECK ERROR
if isinstance(my_person_list[0], Person):    # requires a type cast
    person_out: Person = my_person_list[0]

my_person_list.append("Test")       # str is a subtype of Object

second_out: Person = my_person_list[1]       # TYPE CHECK ERROR
                                    # It will be a string, but type checker
                                    # can't tell what type it should be
```

Here, we see that we can add any object to the list, and the type checker will allow it. However, when we access those items, we'll have to cast them back to the type we need to use, and if we make a mistake, we might run into issues. So, this is definitely not ideal.

## Solution 1 - Custom Classes

Of course, one easy solution would be to rewrite our `MyArrayList` class to accept only `Person` objects instead of the base `Object` type. This isn't that difficult to do. 

```python
from typing import List


class MyPersonList:

    def __init__(self) -> None:
        self.__array: List[Person] = list()
        
    def append(self, obj: Person) -> None:
        self.__array.append(obj)
        
    def get(self, i: int) -> Person:
        self.__array[i]
```

In effect, we can just replace the `Object` type in the code with the `Person` type, and it works just fine. If we want to create a list to store a different type, we can just duplicate this class, update a few types, and we are good to go, right? 

Hopefully by now we are well trained enough in object-oriented programming that our intuition is telling us that there must be a simpler way to do this. This seems to violate the [Don't Repeat Yourself (DRY)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) principle, since we are creating a bunch of classes that do the same thing with slightly different types. Thankfully, there is a great solution for this in Python.

## Solution 2 - Generic Types

To create a class that uses a generic type, we simply can replace each instance of the type with a variable. So, in our class itself, we can update it to handle generic types as shown in this example:

```python
from typing import List, TypeVar, Generic


T = TypeVar('T')

class MyGenericList(Generic[T]):

    def __init__(self) -> None:
        self.__array: List[T] = list()
        
    def append(self, obj: T) -> None:
        self.__array.append(obj)
        
    def get(self, i: int) -> T:
        self.__array[i]
```

It's really that simple. We first create a `TypeVar` to represent our generic type. Traditionally, we use `T` for the generic type variable, and most generic classes use single uppercase letters to represent type variables, making it clear which variables are types and which ones are other variables. Then, we subclass the `Generic[T]` base class to show that this is a generic class, and then replace all instances of the type with that parameter. 

Then, when we wish to use this class, we can treat it just like any other generic class:

```python
generic_list: MyGenericList[Person] =  MyGenericList()

person: Person = Person("Willie", 42)
generic_list.append(person) 

person_out: Person = generic_list[0]         # Properly Type Checked

my_person_list.append("Test")                # TYPE CHECK ERROR
```

With that code, we've definitely followed the [Don't Repeat Yourself (DRY)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) principle, since there will only be one instance of the class in our code, and it can now support any generic type we choose.

#### References

* [Generics](https://docs.python.org/3/library/typing.html#generics) from Python Documentation
* [Generics](https://mypy.readthedocs.io/en/stable/generics.html) from Mypy Documentation
