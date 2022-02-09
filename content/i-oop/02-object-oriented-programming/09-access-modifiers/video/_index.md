---
title: "Access Modifiers"
pre: "4. "
weight: 40
date: 2020-12-31T00:53:26-05:00
hidden: true
---

{{< youtube a1oUEgvW09Y >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

Now that we've explored encapsulation, let's look at another related concept - **information hiding**. As we discussed earlier, we want to make sure that the behavior of one module cannot affect the state of other modules. To do this, we must restrict access to the state of each module. 

Let's look at a quick example first, where everything in the module is publicly accessible. On the surface, this seems like a great idea - if external code cannot read the state of our module or access its behaviors, then what good is it? So, by allowing open access, any other part of the program can make use of this module.

So, let's assume we have another module that governs the growth of crops in our ecosystem. Obviously, growing crops involves the soil, so we'd want to make sure that module can access our module. 

However, what if the `grow` method in the Crops module wants to take nutrients from the soil? Should we allow it to directly access that variable and change it's value? 

Unfortunately, if there is a bug in the Crops module, it could cause a major change to the state of the Soil module, such as setting the nutrients variable to an invalid value. In that case, this definitely violates the concept of encapsulation we just introduced - code from outside our module was able to modify our module's state, and it would be very difficult to track down such a bug. How would we even know that the culprit was the Crops module instead of our own module?

So, beyond just encapsulation, we want our modules to implement **information hiding**. Information hiding involves protecting the state of our module from unwanted changes by controlling access to the variables and methods stored inside of the module. So, if an external module wants to access or change our state, it must instead go through an accessor method, one that **we** control and can add our own error checking code to. In that way, any and all changes to the state of this module are directly controlled by code within the module itself!

So, what would this look like? Notice that now we have a solid box around our state, protecting it from external access. Instead, we have a set of **accessor methods**, sometimes known as **getters** and **setters** that other modules can use to access and update our state. Inside of those accessor methods, we can implement some error checking to make sure that any state updates are valid, and we can even execute some of our own behaviors based on changes to our state! This shows a properly encapsulated class, with information hiding to prevent unwanted state changes. As we'll see in this chapter, Java supports the use of the `private` keyword to clearly prevent access to variables and methods. Unfortunately, Python does not support direct information hiding, but developers can prepend variable and method names with underscores to show that those items should be treated as private. This is another weakness of Python as a true object-oriented language, as it's systems for information hiding can be easily circumvented by a programmer. 

In addition, let's look at another important related concept, the `static` keyword, and how this impacts the structure of our modules. When we define a module or class, we are building the blueprint of an object that gets stored in memory. Then, when we create an instance of our class, a location in memory is set aside to store that object's state, and it also has a unique set of behaviors attached to it. However, we can also mark both variables and methods with the `static` keyword in Java, or using the `@staticmethod` annotation and class variables in Python. 

In essence, this tells the computer that there should only be a single memory location for those static variables, one that is shared by all instances of the class. Likewise, any static methods are not associated with a particular instance of the object, but the class itself. So, if we create a couple of instances of our Soil module, we'll see that those instances include a copy of the `data` structure and the `update` behavior, but the static `rate` variable and `newRate` method are only attached to the class itself. We can still access those items through each of the instances of the Soil module, but any changes made to the `rate` variable will be reflected in all instances of the Soil module. So, in this example, we are showing that all the soil on earth uses the same rate value, and we can simply store that as a static variable attached to the Soil class itself. Likewise, if we want to update that rate, it makes sense to only have a static method for that. In fact, the Java compiler will tell us that only static methods can modify static variables, helping us enforce this in our code. Unfortunately, once again Python will allow us to modify class variables from any code in our program, so we'll have to be careful when doing this in our Python code. 

