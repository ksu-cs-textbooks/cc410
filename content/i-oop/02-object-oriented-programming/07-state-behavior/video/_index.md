---
title: "State and Behavior"
pre: "3. "
weight: 30
date: 2020-12-31T00:53:26-05:00
hidden: true
---

{{< youtube 7UN8fXcpv7s >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

Next, let's review another key concept from object-oriented programming: **state and behavior**. The **state** of a computer program refers to the instantaneous values of all of the variables present in the program at any given time during the program's execution. So, in this simple diagram, we would say that the program's state is the current value of the three variables: temp = 30, moisture = 95, and nutrients = 75. If we change the value of any one of these variables, then our program's state will change. The **behavior** of a program, then, is the program's code that determines how the state changes as the program executes. 

So, there are a couple of unique ways that we can reason about this in our mind. First, remember that every computer program can be represented on a **Turing machine**, the simplest theoretical computer. All of the state is just single 1s and 0s on an infinitely long tape, and the behavior is just a list of rules that govern how the Turing machine manipulates the bits on the tape. However, that is a pretty abstract way to think about a computer program. 

Instead, we can also think of a computer program as a **state machine** - we could simply list each possible state of the program, and then the behavior defines the transitions between those states. Of course, even a simple program might have thousands of states, and the behavior may be so complex that there might be millions of possible state transitions, but the concept is still sound. In fact, this is the core idea behind some interesting research areas in computer science in the field of automata theory. One research area deals with using those states and transitions to prove that a program works correctly in all possible instances, which could be very important for software in implantable healthcare devices or airplane avionics systems. 

So, going back to our example, what does this look like? For example, we have a method called `update` that defines a behavior of our application - one that changes the program's state. 

The first instruction in the `update` method will reduce the value of the temp variable. So, when we execute that instruction, the _behavior_ it defines...

will change the value of the temp variable, thereby altering the program's state. 

The next two instructions in the `update` method will do the same thing, reducing the value of the moisture variable and increasing the nutrients variable. 

This is just a quick example of how the code in a module can define the **behavior** of that module, and that behavior can then change the overall **state** of the program itself. 

How does this relate to encapsulation? A properly encapsulated module will ensure that the module's behavior can only modify that module's state, without affecting any other part of the program.

This is the **scope** of the module. It can only modify data that is within its scope. As we'll learn later in this module, we can control access to data within a module using access modifiers, protecting that module's scope.

So, if we can guarantee that each module is properly encapsulated, we can reason about them **independently** without worrying about one module's behavior unintentionally (or intentionally) affecting the state of another module. This is a key concept in object-oriented programming - as long as we properly encapsulate our classes, the program's code becomes much easier to manage and debug. 