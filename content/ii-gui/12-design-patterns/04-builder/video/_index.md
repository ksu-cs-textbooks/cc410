---
title: "Creational Patterns"
pre: "2. "
weight: 20
date: 2020-02-28T00:53:26-05:00
hidden: true
---

{{< youtube P-aAi5-wcZw >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

First, let's review three of the creational patterns introduced in the original _Design Patterns_ book. These are the builder pattern, factory method pattern, and the singleton pattern. Of the three, it makes the most sense to start with the builder pattern. The builder pattern is used when we need to create and instantiate complex objects, which are sometimes made up several independent parts that must all be fit together correctly. Instead of doing this in our application code wherever this object is used, we can abstract this work to a special class called a "builder" which handles the heavy lifting of creating the objects themselves. By doing this, we can reduce the links between pieces of our application - the builder is linked to all of the parts it builds, but the application itself is just linked to the builder and the final result it produces. 

Let's look at what this might look like in code. For these examples, we're going to use some pseudocode to represent the classes, but this code should be easily readable to developers who work in either Java or Python. So, let's assume we'd like to create a program that represents various boxes of crayons. We can have the simple box with just eight colors, all the way up to the jumbo boxes with 48 or even more colors. So, we'll need a simple Crayon class that represents each individual crayon, storing the color associated with that crayon. Then, we'll need a class to represent a box of crayons, which is simply a list of crayon objects as well as some method to manipulate the list. For now, we'll just include one method to add a crayon to the box. With this code, we can easily see what it would take to build a box of crayons. We start by instantiating each crayon for a given color, and then we add them to the crayon box object.

If we want to follow the builder pattern, we would first create an interface for all of the builders. This interface simply defines one method, the `buildBox()` method. That method will return the final crayon box object once it has been fully constructed.

The actual builder classes will implement that interface. For example, here is a class that will construct a box of eight crayons, consisting of most of the standard colors you might see. It instantiates the box, as well as all of the crayons it contains, and finally returns the completed box, all within the `buildBox()` method.

If we want to be able to create larger boxes, we can just create additional builder classes that implement the same interface. Here's a class for building a crayon box with 16 colors. As we can see, this box contains many unique colors that weren't included in the smaller box. The biggest benefit here is that we only need to maintain this one builder class for this box, and then we can instantiate it anywhere else in our code. Without this, we'd have to modify each of those locations any time we decided to change the colors present in a particular box, instead of just updating the single builder class. It's a very handy way to prevent repetition in our code. As always, we try to follow the principle of "don't repeat yourself" or "DRY" when we are writing our code.

So, with these builder classes in place, we can simply instantiate the builder we need, then call the `buildBox()` method that is defined in the `CrayonBoxBuilder` interface to actually create the box of crayons. This greatly simplifies our code anywhere we need to create a new box of crayons.

Next, let's look at the factory method pattern and how we can use it to even further enhance this example. The factory method pattern allows us to get an instance of an object by providing some information about the object we need, such as it's name, a value from an enumeration, or any other identification. We don't need to know the actual underlying type of the object, just the base type that it could be stored in. By doing so, we can further decouple our architecture so that each class using this type of object only needs to know about the base type and the class containing the factory method. All of the other details are contained within the factory itself. 

A factory class may look something like this. Here, we have a `getBox()` method that accepts a number of crayons as a parameter, and then uses that number of find the appropriate builder class to create that box of crayons. The factory method pattern, when used in this way, is a great extension to the builder pattern.

So, when we want to use it in our code, we just create an instance of the factory class, then use the `getBox` method to get a box of crayons of the desired size. We don't even need to know that the application is using the builder pattern behind the scenes, or the names of the various builder classes. All we know is that we have a factory that will create the desired crayon box wherever we need it.

Finally, let's review the singleton pattern. In short, the singleton pattern is used to ensure that there is only one instance of a class available on a system at any time, greatly reducing the amount of resources that could be consumed by a large application with multiple copies of the same class stored in memory. This is similar to static methods and attributes, but instead of them being statically defined as part of the class, we can use normal methods and attributes and make sure that there is only one instance of the class, achieving the same result. 

A great way to explore the singleton pattern is to combine it with our existing factory method pattern. We really don't need more than one copy of the factory class on the system, so instead of instantiating a new one each time we need it, we can use the singleton pattern to just share a single instance. So, we create a static variable in our class to store the instance, and provide a static `getInstance()` method that will create that instance if needed, and then return it. 

When we use that code in our class, instead of creating a factory instance, we just call the `getInstance` method on the class that is following the singleton pattern, and then we can call the `getBox` method on the singleton instance that is returned. At this point, the code to actually create a box of crayons where we need one is a single line, and all we really need to know is the size of the box we want. 

As we've seen, these creational patterns can greatly simplify the process of instantiating and building complex objects in our programs. By doing so, we can build our applications in a way that the architecture is more decoupled and less code is repeated, making it easy to make larger structural changes without having to modify the rest of the application. It also makes it easy to add new items or types on the fly - if we want to offer a box of crayons that contains 7 colors instead of eight, we can easily adapt the existing builder and factory to accomplish that without modifying any other code. 

In fact, one great way to think about how this can simplify the structure of our programs is to think about the number of external classes we must import in our class. Instead of importing everything, we can just import the factory class and the resulting data structure it returns. If done correctly, these creational patterns will greatly improve the structure of our applications.