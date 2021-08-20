---
title: "Message Dispatching"
pre: "4. "
weight: 40
date: 2020-01-25T00:53:26-05:00
hidden: true
---

{{< youtube NOAmwPixxuM >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

Here's one other important topic to cover when learning about inheritance - message dispatching. As we've already learned, message passing is just another way to think about method calls. One class can call a method in another class by passing it a message. However, when we throw inheritance in the mix, it is more difficult to determine where to send that message. There might be multiple different methods that look the same in the superclass as well as the subclass. So, how can we figure out which method to use? Both programming languages handle this situation a bit differently. In Java, it will look at the name of the method as well as the data types of the arguments provided and try to find a compatible match. In this way, Java also allows _method overloading_, where two methods can share the same name but have different sets of parameters. Python, on the other hand, only looks at the name of the method when determining which method to call. If the parameters are compatible it will work, but if not it will just raise an error when we try to call the method. However, the real interesting thing happens in the case of method overriding. Remember that a method in a superclass can be overridden by the subclass. When that happens, the method call will execute code based on the original object that was instantiated, regardless of the data type it is currently stored in.

This is best understood by observing an example. Here, I've adapted the previous example so that our `Canine`, `Dog`, and `GuideDog` classes all include a method called `bark`. That method is overridden in both subclasses with different code. The general `Canine` class will print "I'm scary", while the `Dog` class will print "I'm friendly". Finally, the `GuideDog` class will print "I'm helpful" when the `bark` method is called. 

So, let's create a list that stores three elements that are compatible with the `Canine` data type. The first item will be an object instantiated from the `Canine` class, while the second is a `Dog` object and the third is a `GuideDog` object. Then, we'll use a simple `for` loop to iterate through the list and call the `bark` method. In all honesty, the output we get makes total sense in Python. Since Python uses dynamic typing, we'd expect each object to be treated like the object we created, regardless of what data type we say it is. However, in Java, we are using an array that should only store `Canine` objects. So, we'd expect them to act line canines and say "I'm scary", right? Instead, we'll get the same output, where each object will print the output based on the original source of the object, not it's current data type. This is one of the most powerful features of inheritance, which we know as **polymorphism**. Polymorphism basically says that we can treat an object like several different data types, each one representing a superclass of that object. However, dynamic dispatch says that we'll use the version of the code in the class closest to the actual object itself, not the type. Pretty nifty!

Finally, remember that we can always check the type of an object in both Java and Python. In the case of inheritance, this will tell us if the object is compatible with that type, not necessarily that it is actually that type and not a subclass. But, it is a good tool to have at our disposal as we deal with more complex objects and inheritance in our code.

So, now that we've learned all about inheritance and interfaces, how do we know which one to use in our code? To be honest, that question can be a bit subjective, and everyone does it a bit different. However, here are some quick best practices that I recommend you keep in mind as you work on your final project. If you have two classes that are closely related to each other, and it is logical that they would share both state and behaviors in common, you'll want to use traditional inheritance. If it makes sense for the superclass to be instantiated, then you can leave it at that. However, if the superclass really shouldn't be an object by itself, you may wish to make that class abstract instead. Finally, if two classes should share some similar behaviors but are otherwise not closely related, it would be best to define those shared behaviors as an interface instead. That will give you the most flexibility, and make it clear that these two classes can perform similar functions even if they aren't closely related. 

There we go! We've covered lots of new information about inheritance, interfaces, and polymorphism. In the example project for this chapter, we'll explore how to use this in our code, and then you'll get to use this knowledge to update our ongoing project with some better structure. Good luck!

