---
title: "Java Interfaces"
weight: 20
pre: "4. "
---
{{% youtube 0AmFNql48_Y %}}

The Java programming language includes direct support for the creation of interfaces via the `interface` keyword. We've already seen one example of an interface created in Java, but let's look at another example and dissect it a bit.

## Interface Example

Here is a simple interface for a set of classes that are based on the [Collection](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html) interface in Java 8:

```java
public interface IMyCollection {
    int size();
    boolean isEmpty();
    boolean add(Object o);
    boolean remove(int i);
    Object get(int i);
    boolean contains(Object o);
}
```

You may also review the full [Collection](http://hg.openjdk.java.net/jdk8/jdk8/jdk/file/tip/src/share/classes/java/util/Collection.java) interface source code from the OpenJDK library.

Here's another example interface in Java for a Stack:

```java
public interface IMyStack {
    void push(Object o);
    Object pop();
    Object peek();
}
```

When creating an interface in Java, there are a few things to keep in mind:

* Instead of the `class` keyword, we use the `interface` keyword in our declaration.
* Interfaces usually only contain methods, but may contain attributes.
* Any methods are automatically `public` and `abstract`. We do not have to include those keywords in the method declaration.
* Any attributes are automatically `public`, `static`, and `final`. They are generally used for constants. 
* Interfaces cannot contain a constructor, and are not able to be directly instantiated. They are a special case of an `abstract` class.
* Interface methods do not include any code. Instead of a set of curly braces `{}`, they end with a semicolon `;`.

## Implementing Interfaces

Once we've created an interface, we can then create a class that **implements** that interface. Any class that implements an interface must provide an implementation for all methods defined in the interface. 

For example, we can create a `MyList` class that implements the `IMyCollection` interface defined above, as shown in this example:

```java
public class MyList implements IMyCollection {
    
    private Object[] list;
    private int size;
    
    public List() {
        this.list = new Object[10];
        this.size = 0;
    }

    public int size() {
        return this.size;
    }
    
    public boolean isEmpty() {
        return this.size == 0;
    }
    
    public boolean add(Object o) {
        if (this.size < 10) {
            this.list[this.size++] = o;
            return true'
        }
        return false;
    }
    
    public boolean remove(int i) {
        if (i < 10) {
            this.list[i] = this.list[9];
            this.list[9] = null;
            size--;
            return true;
        }
        return false;
    }
    
    public Object get(int i) {
        return this.list[i];
    }
    
    public boolean contains(Object o) {
        for (Object obj : this.list) {
            if (obj.equals(o)) {
                return true;
            }
        }
        return false;
    }
}
```

Notice that we use the `implements` keyword as part of the class declaration to list the interface that we are implementing in this class. Then, in the class, we include implementations for each method defined in the `IMyCollection` interface. Those implementations are simple and full of bugs, but they give us a good idea of what an implementation of an interface could look like. We can also include attributes and a constructor, as well as additional methods as needed. 

## Multiple Inheritance

One of the biggest benefits of using interfaces in Java is the ability to create a class that implements multiple interfaces. This is a special case of inheritance called **multiple inheritance**. Any class that implements multiple interfaces must provide an implementation for every method defined in each of the interfaces it implements. 

For example, we can create a special `MyListStack` class that implements both the `IMyCollection` and `IMyStack` interfaces we defined above:

```java
public class MyListStack implements IMyCollection, IMyStack {

    // include all of the code from the MyList class
    
    public void push(Object o) {
        this.add(o);
    }
    
    public Object pop() {
        Object out = this.list[this.size - 1];
        this.remove(this.size - 1);
        return out;
    }
    
    public Object peek(){
        return this.list[this.size - 1];
    }
}
```

To implement multiple interfaces, we can simply list them following the `implements` keyword, separated by a comma. 

## Interfaces as Types

Finally, recall from the previous page that we can treat any interface as a data type, so we can store classes that implement the same interface together. Here's an example:

```java
IMyCollection[] collects = new IMyCollection[2];
collects[0] = new MyList();
collects[1] = new MyListStack();
collects[0].add("String");
collects[1].add("Hello");
```

However, it is important to remember that, even though the second element in the `collects` array is an instance of the `MyListStack` class, we cannot access the `push` and `pop` methods directly. This is because the `collects` array is using the `IMyCollection` data type. So, we only have access to methods that are defined in that interface. Put another way, we've told the Java compiler that those objects can only accept those messages. 

If we want to treat that item as an instance of the `MyListStack` class, we can **cast** it to the correct type.

```java
if (collects[1] instanceof MyListStack) {
    ((MyListStack) collects[1]).push("World");
}
```

In Java, we can use the `instanceof` operator to determine if a particular object is an instance of a particular class or data type. If so, we can then cast it by placing the desired data type in parentheses before the variable we'd like to cast. In this example, we see that we can then wrap that in another set of parentheses and then access the methods or attributes of the desired type.

### References

* [What is an Interface](https://docs.oracle.com/javase/tutorial/java/concepts/interface.html) from the Oracle Java Tutorials
