---
title: "Associations"
pre: "3. "
weight: 30
date: 2020-01-15T00:53:26-05:00
hidden: true
---

{{< youtube gbD5VcZzCIM   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

Finally, let's look at one other important aspect of any UML class diagram - associations. Associations are arrows that we can add between two classes in a UML class diagram that show that those two classes are related in some way. While there is a generic association arrow that we can use, it is much more common for us to see one of four specialized association types in our diagrams. So, let's look at each of those and see what they do.

First, we have the realization relationship, which is sometimes known as the weak is-a relationship. We use this relationship to show that a class is implementing a particular interface class, which is a special type of abstract class that only includes methods. So, in this example, we are saying that the `CellPhone` class implements the `IBlendable` interface and includes an implementation of the `blend` method. Put another way, we could say a cell phone **is a** blend-able item. Notice how that feels like a pretty weak association - a cell phone is not really a subtype of all blend-able items, it just happens to have the ability to be a blend-able item. That's why we call this a weak is-a relationship.

The next one is the generalization relationship, also known as the strong is-a relationship. This association is made between a parent class and a direct subclass, showing that the subclass inherits from the parent class. In this case, we are saying that the `Banana` class is a child class of the parent `Fruit` abstract class. Notice that the elements in the `Fruit` class are italicized, meaning that they are abstract. So, another way we could say this is that a banana **is a** fruit, which feels like a much stronger relationship. Thus, we would call this a strong is-a relationship.

Another type of UML association is aggregation, or a weak has-a relationship. This is for when one class includes a an attribute that stores objects of another class type, but the enclosing class can still stand alone without the objects it would contain. In this diagram, we see an element for a `ShoppingCart` class, and an association that shows it could contain 0 or more `GroceryItem` objects. Put another way, we could say that the shopping cart **has a** list of grocery items, but the cart itself is independent of the grocery items, hence why we call this a weak has-a relationship.

The last type of UML association is the composition, or strong has-a relationship. In this association, one class consists of elements of many other classes, but those elements are required in order for the enclosing class to be functional. So, in this diagram, we see that the `Frog` class contains four legs (two rear and two front), as well as a tongue. In other words, a frog **has** a set of two front legs, two back legs, and a tongue, but without those things it wouldn't really be a frog. So, we'd say that this is a strong has-a relationship. 

So, let's take a look at an example. Consider this very simple class diagram - what does it tell us? Well, first we see that it consists of two classes, a `Professor` and a `Class`. We also see a relationship between the two. Can you tell what type it is? Since it has an open diamond on one end, we know that this is an aggregation, or a weak has-a relationship. Finally, we see some numbers above each end of the association. Those numbers give the multiplicity of the association - how many of each element are present in the association. Here, we can see that there is a 1 on the side of the association next to `Professor`, while there is a rang of 1 to infinity on the side of the `Class` element. So, if we read this association out loud, we could say something like "One professor has one or more classes," which accurately describes the relationship shown in this diagram.

UML Class Diagrams are a very useful way to reason about the design of our object-oriented programs, and allow us to share information with other developers quickly and easily. Learning to both read UML diagrams as well as create them yourself is a very important skill to practice for any developer, especially if you'll be working on a team with other developers. Hopefully this information has given you a good start, but you'll get plenty of chances to practice your skills throughout the rest of this course. Good luck!