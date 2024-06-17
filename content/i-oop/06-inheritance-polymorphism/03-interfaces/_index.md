---
title: "Interfaces"
weight: 15
pre: "3. "
---

{{< youtube hpBFUcKaSh8  >}}

[Video Materials]({{% relref "./video" %}})

If we think back to the concept of _message passing_ in object-oriented languages, it can be useful to think of the collection of public methods available in a class as an _interface_, i.e., a list of messages you can dispatch to an object created from that class.  When you were first learning a language (and probably even now), you find yourself referring to these kinds of lists, usually in the language's documentation: 

{{< tabs >}}

{{% tab title="Java" %}}

###### Java API

![Java API](/images/6/java_api.png)

{{% /tab %}}

{{% tab title="Python" %}}

###### Python API

![Python API](/images/6/python_api.png)

{{% /tab %}}

{{< /tabs >}}

Essentially, programmers use these **interfaces** to determine what methods can be invoked on an object.  In other words, which _messages_ can be _passed_ to the object.  This interface is determined by the class definition, specifically what methods it contains.

In dynamically typed programming languages, like Python, JavaScript, and Ruby, if two classes accept the same message, you can treat them interchangeably, i.e. if the `Kangaroo` class and `Car` class both define a `jump()` method, you could populate a list with both, and call the `jump()` method on each:

```python
jumpables = [new Kangaroo(), new Car(), new Kangaroo()]
for jumper in jumpables:
    jumper.jump()
```

This is sometimes called [duck typing](https://en.wikipedia.org/wiki/Duck_typing), from the sense that "if it walks like a duck, and quacks like a duck, it might as well be a duck."

However, for statically typed languages we must explicitly indicate that two types both possess the same message definition, by making the interface _explicit_.  We do this by declaring an `interface` class, which is a special type of class.  For example, an interface for classes that possess a parameter-less jump method might look like this in Java:

```java
interface IJumpable {
    void jump();
}
```

In some languages, it is common practice to preface Interface names with the character `I`. The `interface` declaration defines an **interface** - the shape of the messages that can be passed to an object implementing the interface - in the form of a method signature.  Note that this signature _does not include a body_, but instead ends in a semicolon (`;`).  An interface simply indicates the message to be sent, _not the behavior it will cause!_  We can specify as many methods in an `interface` declaration as we want.

{{% notice note "Python Interfaces" %}}

On a later page, we'll discuss how to create a similar structure in Python, which defines the methods that must be implemented by any class that inherits from our interface class. For now, we'll discuss how interfaces are traditionally implemented in most other object-oriented languages such as Java.

{{% / notice %}}

Also note that the method signatures in an `interface` declaration _do not have access modifiers_.  This is because the whole purpose of defining an interface is to signify methods _that can be used by other code_.  In other words, `public` access is implied by including the method signature in the `interface` declaration. In addition, because the methods do not have implementations, they are also **abstract** as well. 

This `interface` can then be implemented by other classes, usually by listing the interfaces as part of the class declaration. In most languages, a class may implement multiple interfaces. When a class implements an interface, it _must define public methods with signatures that match those that were specified by the interface(s) it implements_. Here's an example of a couple of classes implementing the `IJumpable` interface in Java:

```java
public class Kangaroo implements IJumpable {
    public void jump() {
        // implement method to jump over a fence here 
    }
}
```

```java
public class Car implements IJumpable {
    public void jump() {
        // implement method to jumpstart a car here
    }
    
    public void start() {
        // implement method to normally start a car here
    }
}
```

We can then treat these two disparate classes as though they shared the same type, defined by the `IJumpable` interface:

```java
List<IJumpable> jumpables = new LinkedList<>();
jumpables.add(new Kangaroo());
jumpables.add(new Car());
jumpables.add(new Kangaroo());
for(IJumpable jumper : jumpables) {
    jumper.jump();
}
```

Note that while we are treating the Kangaroo and Car instances _as_ `IJumpable` instances, we can _only_ invoke the methods defined in the `IJumpable` interface, even if these objects have other methods. Essentially, the interface represents a new _type_ that can be shared amongst disparate objects in a statically-typed language. The interface definition serves to assure the static type checker that the objects implementing it can be treated as this new type - i.e. the `interface` provides a mechanism for implementing polymorphism. 

We often describe the relationship between the interface and the class that implements it as a *is-a* relationship, i.e. a `Kangaroo` _is a_ `IJumpable` (i.e. a Kangaroo is a thing that can jump).  We further distinguish this from a related polymorphic mechanism, inheritance, by the strength of the relationship.  We consider interfaces **weak is-a** connections, as other than the shared interface, a Kangaroo and a Car don't have much to do with one another.

In Java, like most other object-oriented languages, a class can implement as many interfaces as we want, they just need to be separated by commas, i.e.:

```java
public class Frog implements IJumpable, ICroakable, ICatchFlies {
    // method here
}
```

On the next few pages, we'll look at how to implement interfaces more explicitly in both Java and Python. As always, feel free to read the page for the language you are studying, but it might be useful to review the other page as well. Then, we'll look at inheritance, which represents a **strong is-a** relationship.
