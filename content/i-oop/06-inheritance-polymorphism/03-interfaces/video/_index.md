---
title: "Interfaces"
pre: "2. "
weight: 20
date: 2020-01-25T00:53:26-05:00
hidden: true
---

{{< youtube hpBFUcKaSh8 >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

Next, let's review the concept of interfaces and how they relate to inheritance in our object-oriented languages. This is actually an interesting approach for learning this material, since traditionally we'll introduce pure inheritance first, and then talk about interfaces as a particular type of inheritance. However, the concept of a common interface actually is much older than object-oriented programming, so it makes sense to talk about it first in this context. In programming, we use the term "interface" to describe the types of messages that can be received by an object.

Put another way, the interface of an object defines the behaviors that object can perform. If we think about it, we use the term graphical user interface to describe how we interact with a computer system graphically, so the interface in that sense is the list of things we can perform on the system.

Finally, to put it in technical terms, we could say that the interface for a class is simply the methods that it contains. By calling those methods, we are using the interface of the class.

So, with that definition, we can say that, if two objects accept the same set of messages, they have the same interface. Because of that, we can use them in the same way. A great example is a car - various types of cars may have many differences, but almost all of them have a steering wheel, gas pedal, and brake pedal. In that way, they share a common interface, and if we know how to use one car with that interface, we can use any other car that has the same interface. Likewise, if two classes define the same methods, they share a similar interface and we can use them in similar ways.

In Java, we use inheritance and classes created specifically as interfaces to accomplish this. We'll see some examples of how this works in a later part of this chapter.

Python, on the other hand, uses a unique method of typing known as duck typing to determine if two objects share the same interface. As the saying goes: "if it walks like a duck and quacks like a duck, it must be a duck!" So, in Python, if two unrelated classes include the same methods, we can treat them as having the same interface, even if those classes do not share any formal inheritance relationship. However, in this course we'll learn how to create formal interfaces in Python to build that relationship, and we'll see how to do that later in this chapter. 

So, let's look at an example. Let's say we wish to create an interface called `IDrivable`, which requires any class using that interface to implement a method called `drive` that will return a value that represents the magnitude of the drive. We won't define exactly what that means at this point, but we'll see shortly various ways we can use it.

So, we can then create several different classes that implement that interface. That means that these classes all define a method called `drive()`. So, we could possibly create a `Car` class that we can drive, a `Plane` class, maybe even a `GolfBall` or `Fundraiser` class. 

Each of those classes could possibly include method called `drive`, so we could say they all implement the `IDrivable` interface. Likewise, since they all have the same interface, we can treat them all as objects that are of the `IDrivable` data type. Yes, that's right, an interface can also be treated like a data type! Remember, data types simply tell us how to handle different values stored in our system, so it makes total sense to say an interface that defines a set of behaviors can be treated like a data type.

Finally, one quick note about interfaces and why they are useful. The Java programming language, along with many other object-oriented languages, use interfaces as the way to implement multiple inheritance. With interfaces, any class that implements multiple interfaces must simply provide implementations for each method defined in those interfaces. As we'll see later in this chapter, Python handles multiple inheritance things a bit differently. 

