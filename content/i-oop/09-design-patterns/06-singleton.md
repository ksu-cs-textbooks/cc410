---
title: "Singleton Pattern"
weight: 30
pre: "6. "
---

Finally, let's look at one other common creational pattern: the **singleton pattern**. The [singleton pattern](https://en.wikipedia.org/wiki/Singleton_pattern) is a simple pattern that allows a program to enforce the limitation that there is only a single instance of a class in use within the entire program. So, when another class needs an instance of this class, instead of instantiating a new one, it will simply get a **reference** to the single existing object. This allows the entire program to share a single instance of an object, and that instance can be used to coordinate actions across the entire system.

![Singleton UML](/images/12/singleton.png)[^1]

[^1]: https://commons.wikimedia.org/w/index.php?title=File:Singleton_UML_class_diagram.svg&oldid=488033377

The UML diagram for the singleton pattern is super simple. The class implementing the singleton pattern simply defines a private constructor, making sure that no other class can construct it. Instead, it stores a static reference to a single instance of itself, and includes a `get` method to access that single instance.

Let's look at how this could work in our ongoing example.

### Singleton Factory

Let's update our `DeckFactory` class to use the singleton pattern. 

{{< tabs >}}

{{% tab name="Java" %}}

```java
public class DeckFactory{
    // private static single reference
    private static DeckFactory instance = null;
    
    // private constructor
    private DeckFactory(){
        // do nothing
    }
    
    public static DeckFactory getInstance() {
        // only instantiate if it is called at least once
        if DeckFactory.instance == null{
            DeckFactory.instance = new DeckFactory();
        }
        return DeckFactory.instance;
    }

    public Deck getDeck(DeckType deck) {
        // existing code omitted
    }
}
```

{{% /tab %}}

{{% tab name="Python" %}}

There are actually two different ways to implement this in Python. The first is closer to the implementation seen in Java above and in C++ in the original book. 

```python
class DeckFactory:

    # private static single reference
    _instance: DeckFactory = None
    
    # constructor that cannot be called
    def __init__(self) -> None:
        raise RuntimeError("Cannot Construct New Object!")
        
    @classmethod
    def get_instance(cls) -> DeckFactory:
        # only instantiate if it is called at least once
        if cls._instance is None:
            # call `__new__()` directly to bypass __init__
            cls._instance = cls.__new__(cls)
        return cls._instance

    def get_deck(self, deck: DeckType) -> Deck:
        # existing code omitted
```

A more Pythonic way would be to simply make use of the `__new__()` method itself to create the singleton and return it anytime the `__init__()` method is called. In Python, when any class is constructed normally, as in `DeckFactory()`, the `__new__()` method is called on the class first to create the instance, and then the `__init__()` method is called to set the instance's attributes and perform any other initialization. So, by ensuring that the `__new__()` method consistently returns the same instance, we can guarantee that only a single instance exists.

```python
class DeckFactory:

    # private static single reference
    _instance: DeckFactory = None

    # new method to construct the instance
    def __new__(cls) -> DeckFactory:
        if cls._instance is None:
            # call `__new__()` on the parent `Object` class
            cls._instance = super().__new__(cls)
        return cls._instance

    def get_deck(self, deck: DeckType) -> Deck:
        # existing code omitted
```

In this way, any calls to construct a `DeckInstance()` in the traditional way would just return the same object. Very Pythonic!

See [Singleton](https://python-patterns.guide/gang-of-four/singleton/) on the excellent Python Design Patterns website for a discussion of these two implementations.

{{% /tab %}}

{{< /tabs >}}

### Using a Singleton

Now we can update our main method code to use our singleton `DeckFactory` instance instead of creating one when it is needed:

{{< tabs >}}

{{% tab name="Java" %}}

```java
public class CardGame{

    public static void main(String[] args) {
        // ask user for input and store in `deckType`
        String deckType = "Standard 52";
        Deck cards = DeckFactory.getInstance().getDeck((DeckType.valueOf(deckType)));
        // game code goes here
    }
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
from typing import List


class CardGame:

    @staticmethod
    def main(args: List[str]) -> None:
        # ask user for input and store in `deck_type`
        deck_type: str = "Standard 52"
        cards: Deck = DeckFactory.get_instance().get_deck(DeckType(deck_type))
        # Python method described above means the code doesn't change!
        # cards: Deck = DeckFactory().get_deck(DeckType(deck_type))
        # game code goes here
```

{{% /tab %}}

{{< /tabs >}}

Why would we want to do this? Let's assume we're writing software for a multiplayer game server. In that case, we may not want to instantiate a new copy of the `DeckFactory` class for each player. Instead, using the singleton pattern, we can guarantee that only one instance of the class exists in the entire system.

Likewise, if we need a system to assign unique numbers to objects, such as orders in a restaurant, we can create a singleton class that assigns those numbers across all of the point of sale systems in the entire store. This might be useful in your ongoing class project.
