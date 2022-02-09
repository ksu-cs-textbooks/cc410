---
title: "Message Passing"
pre: "5. "
weight: 50
date: 2020-12-31T00:53:26-05:00
hidden: true
---

{{< youtube keEZ55ExLXY >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

Finally, let's take a look at message passing, another of the core concepts in object-oriented programming as proposed by Alan Kay. In effect, message passing simply means that modules should have a mechanism to send and receive "messages" between one another. In practice, this is implemented as method calls. 

So, let's go back to our example of an environment simulation, and look at the Soil module we've already defined and another module, the Weather module. As the simulation runs, the Weather module will simulate future weather conditions. As the soil dries after a rain, it will have to tell the Soil module to update its state.

So, the `simulate` behavior in the Weather module will **pass a message** to the Soil module, telling it to execute its `update` behavior. This is what a **method call** is at its core - by calling the `update` method in the `Soil` class, we're passing a message to that module and telling it something it needs to do. That message could include additional information, which are the **arguments** that the `update` method can store within its defined parameters. 

Then, once the `update` method has completed, it can send a response back to the Weather module as part of its **return value**. In effect, each message passed between modules can include both data sent to that module, as well as a response back to the source of the message. Or, using object-oriented programming terms, a method call can include arguments for the parameters of the method, and then the method can return a value which can be used by the module where the call originated from. 

There we go! We've covered two of the big concepts in object-oriented programming. When we design classes, they should be properly encapsulated, such that the state of the class can only be changed by the behaviors defined as methods within the class. As part of that, each class should implement information hiding to prevent unwanted access and modifications to the state, as well as protect access to internal behaviors or methods that other classes should not use. Finally, to allow objects to interact with one another, we can use message passing, or method calls, to trigger the behaviors of an object from within another object, sharing data back and forth through method arguments and return values. If we do this properly, this will make it much easier to reason about and test our code, since each class will be properly independent from all others. In a later module, we'll discuss the last of these concepts, dynamic dispatch, which has to do with how inheritance and polymorphism are implemented within an object-oriented programming language. For now, we'll just focus on creating classes that are properly encapsulated as part of this module's project milestone. Good luck!