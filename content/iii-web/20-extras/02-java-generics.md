---
title: "Generics in Java"
weight: 10
pre: "2. "
---

One major topic in the Java programming language that we've made use of but haven't really explained is the use of **generic types**. A generic type is a class or interface that can accept a parameter for the **type** of object that it stores. A great example is the [LinkedList](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html) class that we are very familiar with. When working with a class that supports generic types, we provide the type parameter in angle brackets `<>` as in this example:

```java
LinkedList<Person> personList = new LinkedList<>();
```

So, as we know, this `LinkedList` object will only allow us to store objects compatible with the `Person` type. If we try to add anything else to that list, the compiler will raise an error before we even can execute our code. Likewise, when we access an element in the list, it will automatically be given to us as a `Person` object, without any casting required.

```java
Person person = new Person("Willie", 42);
personList.add(person);

Person personOut = personList.get(0);  // no cast required!

Integer intObject = new Integer(5);
personList.add(intObject);             // COMPILER ERROR!
```

Compare that with a non-generic version of a List class, such as the one you probably created as part of a data structures course:

```java
public class MyArrayList {

    private Object[] array;
    private int size;
    
    public MyArrayList() {
        this.array = new Object[10];
        this.size = 0;
    }
    
    public Object get(int i) {
        return this.array[i];
    }
    
    public void add(Object obj) {
        this.array[size++] = obj;
    }

}
```

If we wish to use the simple class above, we can instantiate it using this code:

```java
MyArrayList myPersonList = new MyArrayList();
```

This class stores objects using the top-level `Object` class. So, it can store every possible type of object, but it doesn't have any way of enforcing types at all. Consider the same code example:

```java
Person person = new Person("Willie", 42);
myPersonList.add(person);           // Person is a subtype of Object

Person personOut = myPersonList.get(0);         // COMPILER ERROR!
Person personOut = (Person) personList.get(0);  // requires a cast

Integer intObject = new Integer(5);
myPersonList.add(intObject);        // Integer is a subtype of Object

Person secondOut = (Person) personList.get(1);  // EXCEPTION! 
                                    // Integer cannot be cast as a Person
```

Here, we see that we can add any object to the list, and the compiler will allow it. However, when we access those items, we'll have to cast them back to the type we need to use, and if we make a mistake, we'll encounter an exception. So, this is definitely not ideal.

## Solution 1 - Custom Classes

Of course, one easy solution would be to rewrite our `MyArrayList` class to accept only `Person` objects instead of the base `Object` type. This isn't that difficult to do. 

```java
public class MyPersonList {

    private Person[] array;
    private int size;
    
    public MyPersonList() {
        this.array = new Person[10];
        this.size = 0;
    }
    
    public Person get(int i) {
        return this.array[i];
    }
    
    public void add(Person obj) {
        this.array[size++] = obj;
    }
}
```

In effect, we can just replace the `Object` type in the code with the `Person` type, and it works just fine. If we want to create a list to store a different type, we can just duplicate this class, update a few types, and we are good to go, right? 

Hopefully by now we are well trained enough in object-oriented programming that our intuition is telling us that there must be a simpler way to do this. This seems to violate the [Don't Repeat Yourself (DRY)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) principle, since we are creating a bunch of classes that do the same thing with slightly different types. Thankfully, there is a great solution for this in Java.

## Solution 2 - Generic Types

To create a class that uses a generic type, we simply can replace each instance of the type with a variable. So, in our class itself, we can update it to handle generic types as shown in this example:

```java
public class MyGenericList<T> {

    private T[] array;
    private int size;
    
        public MyGenericList() {
        this.array = new T[10];
        this.size = 0;
    }
    
    public T get(int i) {
        return this.array[i];
    }
    
    public void add(T obj) {
        this.array[size++] = obj;
    }
}
```

It's really that simple. We add a generic parameter list to our class declaration, `<T>` in this example, and then replace all instances of the type with that parameter. Traditionally, we use `T` for the generic type variable, and most generic classes use single uppercase letters to represent type variables, making it clear which variables are types and which ones are other variables. 

Then, when we wish to use this class, we can treat it just like any other generic class:

```java
MyGenericList<Person> genericList = new MyGenericList<>();

Person person = new Person("Willie", 42);
genericList.add(person);

Person personOut = genericList.get(0);  // no cast required!

Integer intObject = new Integer(5);
genericList.add(intObject);             // COMPILER ERROR!
```

With that code, we've definitely followed the [Don't Repeat Yourself (DRY)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) principle, since there will only be one instance of the class in our code, and it can now support any generic type we choose.

#### Resources

* [Lesson: Generics](https://docs.oracle.com/javase/tutorial/java/generics/index.html) from the Oracle Java Tutorials
* [Basics of Java Generics](https://www.baeldung.com/java-generics) from Baeldung
* [Generics in Java](https://www.geeksforgeeks.org/generics-in-java/) from GeeksforGeeks
