---
title: "Python Interfaces"
weight: 30
pre: "6. "
---

{{% youtube kTLQbt3hseI %}}

[Video Materials}({{<relref "./video">}})

The Python programming language doesn't include direct support for interfaces in the same way as other object-oriented programming languages. However, it is possible to construct the same functionality in Python with just a little bit of work. For the full context, check out [Implementing in Interface in Python](https://realpython.com/python-interface/#using-abstract-method-declaration) from Real Python. It includes a much deeper discussion of the different aspects of this code and why we use it.

## Formal Python Interface

To create an interface in Python, we will create a class that includes several different elements. Let's look at an example for a `MyCollection` interface that we could create, which can be used for a wide variety of collection classes like lists, stacks, and queues:

```python
import abc
from typing import List


class IMyCollection(metaclass=abc.ABCMeta):

    @classmethod
    def __subclasshook__(cls, subclass: type) -> bool:
        if cls is IMyCollection:
            attrs: List[str] = ['size', 'empty']
            callables: List[str] = ['add', 'remove', 'get', 'contains']
            ret: bool = True
            for attr in attrs:
                ret = ret and (hasattr(subclass, attr) 
                               and isinstance(getattr(subclass, attr), property))
            for call in callables:
                ret = ret and (hasattr(subclass, call) 
                               and callable(getattr(subclass, call)))
            return ret
        else:
            return NotImplemented
        
    @property
    @abc.abstractmethod
    def size(self) -> int:
        raise NotImplementedError
        
    @property
    @abc.abstractmethod
    def empty(self) -> bool:
        raise NotImplementedError
        
    @abc.abstractmethod
    def add(self, o: object) -> bool:
        raise NotImplementedError
        
    @abc.abstractmethod
    def remove(self, i: int) -> bool:
        raise NotImplementedError
        
    @abc.abstractmethod
    def get(self, i: int) -> object:
        raise NotImplementedError
        
    @abc.abstractmethod
    def contains(self, o: object) -> bool:
        raise NotImplementedError
```

This code includes quite a few interesting elements. Let's review each of them:

* First, we import the `abc` library, which as you may recall is the library for Abstract Base Classes. 
* We're also importing the `List` class from the `typing` library to assist with some type checking.
* In the class definition for our `IMyCollection` class, we are listing the `abc.ABCMeta` class as the **metaclass** for this class. This allows Python to perform some analysis on the code itself. You can read more about [Python Metaclasses](https://realpython.com/python-metaclasses/) from Real Python.
* Inside of the class, we are overriding one class method, `__subclasshook__`. This method is used to determine if a given class properly implements this interface. When we use the Python `issubclass` method, it will call this method behind the scenes. See below for a discussion of what that method does.
* Then, each property and method in the interface is implemented as an abstract method using the `@abc.abstractmethod` decorator. Those methods simply raise a `NotImplementedError`, which enforces any class implementing this interface to provide implementations for each of these methods. Otherwise, the Python interpreter will raise that error for us.

### Subclasshook Method

The `__subclasshook__` method in our interface class above performs a task that is normally handled automatically for us in many other programming languages. However, since Python is dynamically typed, we will want to override this method to help us determine if any given object is compatible with this interface. This method uses a couple of **metaprogramming** methods in Python. 

First, we must check and make sure the class that this method is being called on, `cls`, is our interface class. If not, we'll need to return `NotImplemented` so Python will continue to use the normal methods for checking type.^[See https://stackoverflow.com/questions/40764347/python-subclasscheck-subclasshook for details]

Then, we see two lists of strings named `attrs` and `callables`. The `attrs` list is a list of all of the Python properties that should be part of our interface - in this case it should have a `size` and `empty` property. The `callables` list is a list of all the callable methods other than properties. So, our `IMyCollection` class will include `add`, `remove`, `get`, and `contains` methods.

Below that, we find two `for` loops. The first loop will check that the given class, stored in the `subclass`, contains properties for each item listed in the `attrs` list. It first uses the `hasattr` metaprogramming method to determine that the class has an attribute with that name, and then uses the `isinstance` method along with the `getattr` method to make sure that attribute is an instance of a Python property. 

Similarly, the second `for` loop does the same process for the methods listed in the `callables` list. Instead of using `isinstance`, we use the `callable` method to make sure that the attribute is a callable method. 

This method is a little complex, but it is a good look into how the compiler or interpreter for other object-oriented languages performs the task of making sure a class properly implements an interface. For our use, we can just copy-paste this code into any interface we create, and then update the `attrs` and `callables` lists as needed. 

## A Second Interface

Let's look at one more formal Python interface, this time for a stack:

```python
import abc
from typing import List


class IMyStack(metaclass=abc.ABCMeta):

    @classmethod
    def __subclasshook__(cls, subclass: type) -> bool:
        if cls is IMyStack:
            attrs: List[str] = []
            callables: List[str] = ['push', 'pop', 'peek']
            ret: bool = True
            for attr in attrs:
                ret = ret and (hasattr(subclass, attr) 
                               and isinstance(getattr(subclass, attr), property))
            for call in callables:
                ret = ret and (hasattr(subclass, call) 
                               and callable(getattr(subclass, call)))
            return ret
        else:
            return NotImplemented
        
    @abc.abstractmethod
    def push(self, o: object) -> None:
        raise NotImplementedError
        
    @abc.abstractmethod
    def pop(self) -> object:
        raise NotImplementedError
        
    @abc.abstractmethod
    def peek(self) -> object:
        raise NotImplementedError
```

This is a simpler interface which simply defines methods for `push`, `pop`, and `peek`. 

## Implementing Interfaces

Once we've created an interface, we can then create a class that **implements** that interface. Any class that implements an interface must provide an implementation for all methods defined in the interface. 

For example, we can create a `MyList` class that implements the `IMyCollection` interface defined above, as shown in this example:

```python
from typing import List


class MyList(IMyCollection):

    def __init__(self) -> None:
        self.__list: List[object] = list()
        self.__size: int = 0
        
    @property
    def size(self) -> int:
        return self.__size
        
    @property
    def empty(self) -> bool:
        return self.__size == 0
        
    def add(self, o: object) -> bool:
        self.__list.append(o)
        self.__size += 1
        return True
        
    def remove(self, i: int) -> bool:
        del self.__list[i]
        return True
    
    def get(self, i: int) -> object:
        return self.__list[i]
    
    def contains(self, o: object) -> object:
        for obj in self.__list:
            if obj == o:
                return True
        return False
```
        
Notice that we include the interface class in parentheses as part of the class declaration, which will tell Python the interface that we are implementing in this class. Then, in the class, we include implementations for each method defined in the `IMyCollection` interface. Those implementations are simple and full of bugs, but they give us a good idea of what an implementation of an interface could look like. We can also include more attributes and a constructor, as well as additional methods as needed. 

## Multiple Inheritance

Python also allows a class to implement more than one interface. This is a special type of inheritance called **multiple inheritance**. Any class that implements multiple interfaces must provide an implementation for every method defined in each of the interfaces it implements. 

For example, we can create a special `MyListStack` class that implements both the `IMyCollection` and `IMyStack` interfaces we defined above:

```python
from typing import List


class MyListStack(IMyCollection, IMyStack):

    # include all of the code from the MyList class
    
    def push(self, o: object) -> None:
        self.add(o)
        
    def pop(self) -> object:
        out = self.__list[self.__size - 1]
        self.remove(self.__size - 1)
        return out
        
    def peek(self) -> object:
        return self.__list[self.__size - 1]
```

To implement multiple interfaces, we can simply list them inside of the parentheses as part of the class definition, separated by a comma. 

## Interfaces as Types

Finally, recall from the previous page that we can treat any interface as a data type, so we can treat classes that implement the same interface in the same way. Here's an example:

```python
collects: List[IMyCollection] = list()
collects.append(MyList())
collects.append(MyListStack())
collects[0].add("String")
collects[1].add("Hello")
```

However, it is important to remember that, because the second element in the `collects` array is an instance of the `MyListStack` class, we can also access the `push` and `pop` methods directly. This is because Python uses dynamic typing and duck typing, so as long as the object supports those methods, we can use them. Put another way, if the object is able to receive those messages, we can pass them to the object. 

There are two special methods we can use to determine the type of an object in Python.

```python
if isinstance(collects[1], MyListStack):
    # do something
```

The `isinstance` method in Python is used to determine if an object is an instance of a given class.

```python
if issubclass(collects[1], IMyStack):
    # do something
```

The `issubclass` method is used to determine if an object is a subclass of a given class. Since we are creating a formal interface in Python and overriding the `__subclasshook__` method, this will determine if the object properly includes all required properties and methods defined by the interface. 

### References

* [Implementing an Interface in Python](https://realpython.com/python-interface/#using-abstract-method-declaration) from Real Python
* [Python Metaclasses](https://realpython.com/python-metaclasses/) from Real Python
