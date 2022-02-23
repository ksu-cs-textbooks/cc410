---
title: "Associations"
weight: 30
pre: "6. "
---

{{% youtube gbD5VcZzCIM %}}

[Video Materials]({{<relref "./video">}})

Class diagrams also express the associations _between_ classes by drawing lines between the boxes representing them. 

 ![UML Association](/images/5/association.png) 

<!--
{{< mermaid >}}
classDiagram
  direction RL
  ClassA -- ClassB

{{< /mermaid >}}
-->


There are two basic types of associations we model with UML: **has-a** and **is-a** associations.  We break these into two further categories, based on the strength of the association, which is either **strong** or **weak**.  These associations are:

<table>
  <tr>
    <th>Association Name</th>
    <th>Association Type</th>
    <th>Typical Usage</th>
  </tr>
  <tr>
    <td>Realization</td>
    <td>weak is-a</td>
    <td>Interfaces</td>
  </tr>
  <tr>
    <td>Generalization</td>
    <td>strong is-a</td>
    <td>Inheritance</td>
  </tr>
  <tr>
    <td>Aggregation</td>
    <td>weak has-a</td>
    <td>Collections</td>
  </tr>
  <tr>
    <td>Composition</td>
    <td>strong has-a</td>
    <td>Encapsulation</td>
  </tr>
</table>

## Is-A Associations

Is-a associations indicate a relationship where one class __is a__ instance of another class.  Thus, these associations represent _polymorphism_, where a class can be treated as another class, i.e. it has both its own, and the associated classes' _types_.

### Realization (Weak is-a)

Realization refers to making an interface "real" by implementing the methods it defines. An **interface** is a special type of abstract class that only includes abstract methods. In effect, it is creating an defined list of operations, or an _interface_ (or API), that subclasses must include so that they can all be used in the same way. For Java, this corresponds to a class that implements an `interface`. The Python language doesn't have interfaces, but we'll learn how to create something similar using abstract classes. We call this a **is-a** relationship, because the class can be treated as being the same data type of the interface class.  It is also a **weak** relationship as the same interface can be implemented by otherwise unrelated classes.  In UML, realization is indicated by a dashed arrow in the direction of implementation:

![Realization in UML](/images/5/410_5_realization.svg) 

<!--
{{< mermaid >}}
classDiagram
  direction RL
  class CellPhone{
    +model : String
    +blend() String
  }
  class Blendable{
    &lt;&lt;interface>>
    +blend() String
  }
  CellPhone ..|> Blendable

{{< /mermaid >}}
-->

### Generalization

Generalization refers to extracting the shared parts from different classes to make a *general* base class of what they have in common.  For Java and Python, this corresponds to _inheritance_.  We call this a **strong is-a** relationship, because the class has all the same state and behavior as the base class.  In UML, realization is indicated by a solid arrow in the direction of inheritance:

![Generalization in UML](/images/5/410_5_generalization.svg) 

<!-- 
{{< mermaid >}}
classDiagram
  direction RL
  class Banana{
    +blend() String
  }
  class Fruit:::abstract {
    &lt;&lt;abstract>>
    +blend()* String
  }
  Banana --|> Fruit

{{< /mermaid >}}
-->

Also notice that we show that `Fruit` and its `blend()` method are abstract by italicizing them. The association tells us that the `Banana` class **is a** `Fruit`. 

## Has-A Associations

Has-a associations indicates that a class holds one or more references to instances of another class.   In Java or Python, this corresponds to having a variable or collection with the type of the associated class. This is true for both kinds of has-a associations.  The difference between the two is how strong the association is.

### Aggregation 

Aggregation refers to collecting references to other classes.   As the aggregating class has references to the other classes, we call this a **has-a** relationship.  It is considered **weak** because the aggregated classes are only collected by the aggregating class, and can exist on their own.  It is indicated in UML by a solid line from the aggregating class to the one it aggregates, with an open diamond "fletching" on the opposite site of the arrow (the arrowhead is optional). 

![Aggregation in UML](/images/5/410_5_aggregation.svg)

<!--
{{< mermaid >}}
classDiagram
  direction RL
  class ShoppingCart{
    +items : List~GroceryItem~ 
    +totalPrice : double &lt;~get,set~&gt;
  }
  class GroceryItem {
    +price : double &lt;~get~&gt; 
    +weight : int &lt;~get~&gt; 
  }
  GroceryItem "0..*" --o "1" ShoppingCart

{{< /mermaid >}}
-->

### Composition

Composition refers to assembling a class from other classes, "composing" it.  As the composed class has references to the other classes, we call this a **has-a** relationship.  However, the composing class typically _creates_ the instances of the classes composing it, and they are likewise destroyed when the composing class is destroyed.  For this reason, we call it a **strong** relationship.  It is indicated in UML by a solid line from the composing class to those it is composed of, with a solid diamond "fletching" on the opposite side of the arrow (the arrowhead is optional).

![Composition in UML](/images/5/410_5_composition.svg)

{{% notice tip tip-1 "Aggregation vs. Composition" %}}

Aggregation and composition are commonly confused, especially given they both are defined by holding a variable or collection of another class type. Here's a helpful analogy to explain the difference, based on the diagrams listed above:

Aggregation is like a shopping cart.  When you go shopping, you place groceries into the shopping cart, and it holds them as you push it around the store.  Thus, a `ShoppingCart` class might have a `List<Grocery>` named `items`, and you would add the items to it.  When you reach the checkout, you would then take the items back out.  The individual `Grocery` objects existed _before_ they were aggregated by the `ShoppingCart`, and also _after_ they were removed from it. The `ShoppingCart` class just keeps track of them. 

In contract, composition is like an organism.  Say we create a class representing a `Dog`.  It might be composed of classes like `Tongue`, `Ear`, `Leg`, and `Tail`.  We would probably construct these parts in the `Dog` class's constructor, and when we dispose of the `Dog` object, we wouldn't expect these component classes to stick around. So, they are inherently a part of the encapsulating class.

Additionally, sometimes the attributes containing these external items may be omitted from the UML diagram of the composing or aggregating class. This is mainly because the existence of those attributes can be inferred by the relationships themselves. However, in this course, we will include the relevant attributes in the encapsulating class, as well as the association arrows, in our UML diagrams

{{% / notice %}}

## Multiplicity

With aggregation and composition, we may also place numbers on either end of the association, indicating the number of objects involved.  We call these numbers the _multiplicity_ of the association.

![Composition in UML](/images/5/410_5_composition.svg)

For example, the `Frog` class in the composition example has two instances of front and rear legs, so we indicate that each `Frog` instance (by a `1` on the Frog side of the association) has exactly two (by the `2` on the leg side of the association) legs.  The tongue has a `1` to `1` multiplicity as each frog has one tongue.

![Aggregation in UML](/images/5/410_5_aggregation.svg)

Multiplicities can also be represented as a range (indicated by the start and end of the range separated by `..`).  We see this in the `ShoppingCart` example above, where the count of `GroceryItems` in the cart ranges from 0 to infinity (infinity is indicated by an asterisk `*`).

Generalization and realization are always one-to-one multiplicities, so multiplicities are typically omitted for these associations.
