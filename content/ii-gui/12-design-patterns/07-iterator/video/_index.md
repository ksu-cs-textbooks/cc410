---
title: "Behavioral Patterns"
pre: "4. "
weight: 40
date: 2020-02-28T00:53:26-05:00
hidden: true
---

{{< youtube FWR6C6LS-Y8 >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

Finally, let's review two of the behavioral patterns introduced by the "Gang of Four" in their _Design Patterns_ book. First, we have the iterator pattern, which allows us to make a class iterable like a list or other collection that is built-in to our language. By doing so, we can use our class in special ways, such as within a for each or enhanced for loop, and we can even treat it just like any other collection data type. Thankfully, both Java and Python have some great built-in support for the iterator pattern.

At its core, the iterator pattern relies on a special type of object, called an iterator, to keep track of the current position in the data structure. The iterator itself usually includes a method called `next` that will return the next item in the data structure. In addition, most iterators include some way to determine when you've reached the end of the structure, and other methods may be included depending on the language. One question you might be asking - why do we return an iterator instead of just adding the `next` method to our class containing the data? In a nutshell, using a separate iterator allows us to use this class in multiple loops at the same time, since each one will use its own iterator. For example, we could write two nested for-each loops that allow us to compare all possible pairs of objects in our data structure. Without a separate iterator class, this would not be possible since those two loops would be using the same location. 

Let's see what this looks like in pseudocode. Here, we'd update the `CrayonBox` class from a prior video to use the iterator pattern. In both Java and Python, we can implement a specific interface or use a given type to tell the language that this object is using the iterator pattern. Inside of the class, we've included a method to get an iterator, as well as some other collection methods that allow us to access a single item, check if a given item is contained in the collection, and get the size of the collection. In each case, since we are using the `List` class that is built-in to our language, we can rely on that underlying data structure to do most of this work for us. In fact, many times implementing the iterator pattern is as simple as using an existing collection class as our underlying data structure, and then providing a few methods that will call the associated methods in our underlying collection. As with the adapter pattern, we typically want to do this instead of just inheriting from the collection itself so we can control what methods are available and what they do. 

Once we've properly built our class to follow the iterator pattern, we can use it in a for each loop directly in our application. This is much simpler and easier to read than using a standard for loop to loop through the collection, and it avoids the risk of introducing an off-by-one error if we aren't careful. 

In summary, we can quickly implement the iterator pattern in our code by just offloading most of the work to the underlying data structure we are using. Both Java and Python include many basic data structures that will do this, including lists, sets, and hash maps or dictionaries. Basically, we don't want to reinvent the wheel if there's already a perfectly good wheel available for us to use. 

The last pattern we'll look at is the template method patten. This pattern allows us to build the overall structure of a method in a parent class, but we can break the individual steps into additional methods that can be overridden by any child classes. This allows us to create many different versions of the class that perform different operations, but they all follow the same basic structure or pattern.

Here's a quick example from baking. No matter what we are baking, we'll probably follow these three basic steps - gathering the ingredients, combining them in some way, and then putting them in the oven. So, we can build a template method that consists of those three methods in that order, and then define those actual methods as abstract methods that must be overridden in any child class. 

In our child class for baking a cake, we can then provide implementations for each method, providing the details for what it takes to bake a cake. In this example, I'm just calling additional methods, but this could really be any appropriate code to perform the desired action. Then, in our main class, we can call the template method `bakeSomething()`, which will call these methods in the correct order to actually bake a cake.

In this chapter, we reviewed several design patterns that we can use in our applications. In the example project, we'll do another example so you can walk through the process of building these patterns yourself, and then you'll be able to apply what you've learned by using these patterns in your ongoing projects. Good luck!

