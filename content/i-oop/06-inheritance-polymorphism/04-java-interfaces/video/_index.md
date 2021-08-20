---
title: "Java Inheritance"
pre: "3.J. "
weight: 30
date: 2020-01-25T00:53:26-05:00
hidden: true
---

{{< youtube 0AmFNql48_Y >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

Let's review inheritance in the Java programming language. First, we'll look at interfaces. In Java, an interface is as special type of class, so we'll use the `interface` keyword instead of the `class` keyword when declaring it. Inside of the interface, we typically only include methods that we want to be part of the interface. Any methods included in the interface are automatically `public` and `abstract` so we don't have to include those modifiers on your methods. Likewise, if we do include any attributes, they will automatically be treated as if the `public`, `static`, and `final` modifiers are attached. Finally, it is important to remember that Java interfaces cannot be instantiated, so we don't include an instructor. In addition, the methods themselves are abstract and don't contain any code.

Here's a quick example of a Java interface called `IMyQueue`, which defines the traditional operations that can be performed on a queue data structure. As we can see, it just lists the methods, along with the return type and parameters. We don't include the `public` or `abstract` keyword, but each of these methods are treated like `public` and `abstract` methods by Java.

Then, if we want to create a class that uses that interface, we list it in the class declaration after the `implements` keyword. Inside of that class, we have to include `public` methods that are implementations for each method defined in the interface. So, here we see the four methods defined by the interface!

Finally, we must remember that an interface in Java is a data type. So, even though we can't directly instantiate the interface itself, we can declare a variable using the interface's name as the data type, and then we'll have access to any methods defined by that interface through that variable. This is handy if we wish to store several different objects, each instantiated from different classes, in the same list. As long as they all implement the same interface, we can use that as our data type and treat them similarly. 

Now, let's look at the more traditional form of inheritance in Java. Recall that we can declare a class to be a subclass of another class, usually referred to as the superclass. When we do that, the subclass includes, or inherits, all state and behavior defined in the superclass. In Java, any methods or attributes marked with the `public` or `protected` modifier are accessible in the subclass. Likewise, the subclass can use the `super()` method to access elements from within the superclass. This is typically used within the constructor of the subclass to call the constructor of the superclass. Finally, the subclass can choose to override any methods defined in the superclass with new code. We'll see how that works later in this chapter.

So, here's a quick example of three classes in Java that demonstrate inheritance. We have a superclass name Canine that defines the protected attribute `name` as well as the public method `bark`. Then, we create a subclass called `Dog` that inherits from `Canine`. So, it will have a `name` attribute and a `bark` method, but it also adds its own `owner` attribute as well as a new method called `pet`. Finally, the `GuideDog` method inherits from `Dog`, so it will include the `name` attribute from `Canine` as well as the `owner` attribute from `Dog`, and it adds its own `trainer` attribute. 

Likewise, when we create an instance of a `GuideDog`, we can access all behaviors that are present in any of the superclasses as well as the class itself. So, an instance of `GuideDog` will have access to the `bark`, `pet` and `guide` methods. This is a great way to reduce the amount of repeated code between related classes. As we'll learn in the example project for this module, this can greatly simplify our programs if we are able to take proper advantage of inheritance.

Finally, let's discuss one other interesting topic - multiple inheritance. In Java a class can only be declared as a subclass of a single superclass, but it can implement multiple interfaces. So, when designing our programs, we'll have to keep that in mind. Generally there are very few instances where we'd want to directly inherit from multiple classes, but it could happen. For example, if we have a class `Teacher` and a class `Student`, we might want to create an object called `StudentTeacher` that represents a person with both roles. In Java, however, we cannot do this through direct inheritance. 

Instead, if we have a class called `Person` and interfaces for `Student` and `Teacher` that defines the behaviors of a teacher, we could create a subclass of `Person` that implements both the `Student` and `Teacher` behaviors. It is a subtle difference, but one we should be aware of.

