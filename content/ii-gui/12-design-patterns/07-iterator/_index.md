---
title: "Iterator Pattern"
weight: 35
pre: "7. "
---

{{% youtube FWR6C6LS-Y8 %}}

[Video Materials]({{<relref "./video">}})

Let's review three other commonly used software design patterns. These are either patterns that we've seen before, or ones that we might end up using soon in our code.

## Iterator Pattern

The first pattern is the **iterator pattern**. The [iterator pattern](https://en.wikipedia.org/wiki/Iterator_pattern) is a behavioral pattern that is used to traverse through a collection of objects stored in a container. We explored this pattern in several of the data structures introduced in earlier data structures courses such as CC 310 and CC 315, as well as CIS 300. 

![Iterator Pattern Diagram](/images/12/iterator.jpg)[^1]

[^1]: https://commons.wikimedia.org/w/index.php?title=File:W3sDesign_Iterator_Design_Pattern_UML.jpg&oldid=488852077

In it's simplest form, the iterator pattern simply includes a `hasNext()` and `next()` method, though many implementations may also include a way to reset the iterator back to the beginning of the collection.

Classes that use the iterator can use the `hasNext()` method to determine if there are additional elements in the collection, and then the `next()` method is used to actually access that element.

In the examples below, we'll rely on the built-in collection classes in Java and Python to provide their own iterators, but if we must write our own collection class that doesn't use the built-in ones, we can easily develop our own iterators using documentation found online.

{{< tabs >}}

{{% tab name="Java" %}}

In Java, classes can implement the [Iterable](https://docs.oracle.com/javase/8/docs/api/java/lang/Iterable.html) interface, which requires them to return an [Iterator](https://docs.oracle.com/javase/8/docs/api/java/util/Iterator.html) object. In doing so, these objects can then be used in the Java **enhanced for** or **for each** loop.

```java
import java.lang.Iterable;
import java.util.Iterator;
import java.util.List;
import java.util.LinkedList;

public class Deck implements Iterable<Card> {

    List<Card> deck;
    
    public Deck() {
        deck = new LinkedList<>();
    }
    
    @Override
    public Iterator<Card> iterator() {
        return deck.iterator();
    }
    
    public int size() {
        return this.deck.size();
    }
}
```

Here, we are making use of the fact that the Java collections classes, such as `LinkedList`, already implement the `Iterable` interface, so we can just return the iterator from the collection contained in our object. Even though it is not explicitly required by the `Iterable` interface, it is also a good idea to implement a `size()` method to return the size of our collection.

With this code in place, we can iterate through the deck just like any other collection:

```java
public class CardGame{

    public static void main(String[] args) {
        String deckType = "Standard 52";
        Deck cards = DeckFactory.getInstance().getDeck((DeckType.valueOf(deckType)));
        
        for(Card card : cards) {
            // do something with each card
        }
    }
}
```

{{% /tab %}}

{{% tab name="Python" %}}

In Python, we can simply provide implementation for the `__iter__()` method in a class to return an iterator object, and that iterator object should implement the `__next__()` method to get the next item, as well as the `__iter__()` method, which just returns the iterator itself. Python does not define an equivalent to the `has_next()` method; instead, the `__next__()` method should raise a `StopIteration` exception when the end of the collection is reached.

For the purposes of type checking, we can use the `Iterator` type and the `Iterable` parent class (which works similar to an interface).

```python
from typing import Iterable, Iterator


class Deck(Iterable[Card]):

    def __init__(self) -> None:
        self._deck: List[Card] = list()
    
    def __iter__(self) -> Iterator[Card]:
        return iter(self._deck)
        
    def __len__(self) -> int:
        return len(self._deck)
        
    def __getitem__(self, position: int) -> Card:
        return self._deck[position]
```

Here, we are making use of the fact that the built-in Python data types, such as list and dictionary, already implement the `__iter__()` method, so we can just return the iterator obtained by calling `iter()` on the collection.

In addition, we've also implemented the `__len__()` and `__getitem__()` [magic methods](https://docs.python.org/3/reference/datamodel.html#emulating-container-types), or "dunder methods", that help our class act more like a container. With these, we can use `len(cards)` to get the number of cards in a `Deck` instance, and likewise we can access each individual card using array notation, as in `cards[0]`. There are several other magic methods we may wish to implement,  which are described in the link above.

With this code in place, we can iterate through the deck just like any other collection:

```python
from typing import List


class CardGame:

    @staticmethod
    def main(args: List[str]) -> None:
        deck_type: str = "Standard 52"
        cards: Deck = DeckFactory.get_instance().get_deck(DeckType(deck_type))
            
        for card in cards:
            # do something with each card
```

###### Reference

See [Iterator](https://python-patterns.guide/gang-of-four/iterator/) on Python Design Patterns for more details.

{{% /tab %}}

{{< /tabs >}}