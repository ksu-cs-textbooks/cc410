---
title: "Builder Pattern"
weight: 20
pre: "4. "
---

{{% youtube P-aAi5-wcZw %}}

[Video Materials}({{<relref "./video">}})

The first pattern we'll look at is the **builder pattern.** The [builder pattern](https://en.wikipedia.org/wiki/Builder_pattern) is used to simplify building complex objects,  where the class that needs the object shouldn't have to include all of the code and details for how to construct that object. By decoupling the code for constructing the complex object from the classes that use it, it becomes much simpler to change the representations or usages of the complex object without changing the classes that use it, provided they all adhere to the same general API.

![Builder Pattern UML](/images/12/builder.jpg)[^1]

[^1]: https://commons.wikimedia.org/w/index.php?title=File:W3sDesign_Builder_Design_Pattern_UML.jpg&oldid=488851706

The UML diagram above gives one possible structure for the builder pattern. It includes a `Builder` interface that other objects can reference, and `Builder1` is a class that implements that interface. There could be multiple builders, one for each type of object. The `Builder1` class contains all of the code needed to properly construct the `ComplexObject` class, consisting of `ProductA1` and `ProductB1`. If a different `ComplexObject` must be created, we can create another class `Builder2` that also implements the `Builder` interface. To the `Director` class, both `Builder1` and `Builder2` implement the same interface, so they can be treated as the same type of object.

## Example: Deck of Cards

A great example of this would be creating a deck of cards for various card games. There are actually many different types of card decks, depending on the game that is being played:

* Standard 52 Cards:  2-10, J, Q, K, A in four Suits
* Standard 52 Cards with Jokers: add one or two Jokers to a Standard 52 Card Deck
* [Pinochle Deck](https://en.wikipedia.org/wiki/Pinochle): 9, J, Q, K, 10, A in four suits, two of each; 48 cards total
* [Old Maid](https://en.wikipedia.org/wiki/Old_maid_(card_game)): Remove any 1 card from a Standard 52 Card Deck
* [Uno](https://en.wikipedia.org/wiki/Uno_(card_game)): One 0 and Two each of 1-9, Skip, Draw Two and Reverse in four colors, plus four Wild and four Wild Draw Four; 108 cards total
* [Rook](https://en.wikipedia.org/wiki/Rook_(card_game)): 1-14 in four colors, plus a Rook (Joker); 57 cards total

As we can see, even though each individual card is similar, constructing a deck for each of these games might be quite the complex process. 

Instead, we can use the builder pattern. Let's look a how this could work.

### The Card Class

First, we'll assume that we have a very simple `Card` class, consisting of three attributes:

* `SuitOrColor` - the suit or color of the card. We'll use a special color for cards that aren't associate with a group of other carsd
* `NumberOrName` - the number or name of the card
* `Rank` - the sorting rank of the card (lowest = 1). 

{{< tabs >}}

{{% tab name="Java" %}}

```java
public class Card{
    String suitOrColor;
    String numberOrName;
    int rank;
    
    public Card(String suit, String number, int rank) {
        this.suitOrColor = suit;
        this.numberOrName = number;
        this.rank = rank;
    }
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
class Card:
    def __init__(self, suit: str, number: str, rank: int) -> None:
        self._suit_or_color: str = suit
        self._number_or_name: str = number
        self._rank: int = rank
```

{{% /tab %}}

{{< /tabs >}}

### The Deck Class

The `Deck` class will only consist of an aggregation, or list, of the cards contained in the deck. So, our builder class will return an instance of the `Deck` object, which contains all of the cards in the deck. 

The `Deck` class could also include generic methods to shuffle, draw, discard, and deal cards. These would work with just about any of the games listed above, regardless of the details of the deck itself. 

{{< tabs >}}

{{% tab name="Java" %}}

```java
import java.util.LinkedList;
import java.util.List;

public class Deck{
    List<Card> deck;
    
    public Deck() {
        deck = new LinkedList<>();
    }
    
    void shuffle();
    Card draw();
    void discard(Card card);
    List<List<Card>> deal(int hands, int size);
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
from typing import List


class Deck:
    def __init__(self) -> None:
        self._deck: List[Card] = list()
    
    def shuffle(self) -> None:
    def draw(self) -> Card:
    def discard(self, card: Card) -> None:
    def deal(self, hands: int, size: int) -> List[List[Card]]:
```

{{% /tab %}}

{{< /tabs >}}

### The Builder Interface

Our `DeckBuilder` interface will be very simple, consisting of a single method: `buildDeck()`. The type of the class that implements the `DeckBuilder` interface will determine which type of deck is created. If the decks created by the builder have additional options, we can add additional methods to our `DeckBuilder` interface to handle those situations.

### The Builder Classes

Finally, we can create our builder classes themselves. These classes will handle actually building the different decks required for each game. First, let's build a standard 52 card deck.

{{< tabs >}}

{{% tab name="Java" %}}

```java
public class Standard52Builder implements DeckBuilder {
    String[] suits = {"Spades", "Hearts", "Diamonds", "Clubs"};

    public Deck buildDeck() {
        Deck deck = new Deck();
        for (String suit : suits) {
            for (int i = 2; i <= 14; i++) {
                if (i == 11) {
                    deck.add(new Card(suit, "Jack", i));
                } else if (i == 12) {
                    deck.add(new Card(suit, "Queen", i));
                } else if (i == 13) {
                    deck.add(new Card(suit, "King", i));
                }else if (i == 14) {
                    deck.add(new Card(suit, "Ace", i));
                } else {
                    deck.add(new Card(suit, "" + i, i));
                }
            }
        }
        return deck;
    }
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
from typing import List


class Standard52Builder(DeckBuilder):
    suits: List[str] = ["Spades", "Hearts", "Diamonds", "Clubs"]
    
    def build_deck(self):
        deck: Deck = Deck()
        for suit in suits:
            for i in range(2, 15):
                if i == 11:
                    deck.append(Card(suit, "Jack", i))
                elif i == 12:
                    deck.append(Card(suit, "Queen", i))
                elif i == 13:
                    deck.append(Card(suit, "King", i))
                elif i == 14:
                    deck.append(Card(suit, "Ace", i))
                else:
                    deck.append(Card(suit, str(i), i))
        return deck
```

{{% /tab %}}

{{< /tabs >}}

As we can see, the heavy lifting of actually building the deck is offloaded to the builder class. We can easily use this same framework to create additional `Builder` classes for the other types of decks listed above.

### Using the Builder

Finally, once we've created all of the builders that we'll need, we can use them directly in our code anywhere we need them:

{{< tabs >}}

{{% tab name="Java" %}}

```java
public class CardGame{

    public static void main(String[] args) {
        DeckBuilder builder = new Standard52Builder();
        Deck cards = builder.buildDeck();
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
        builder: DeckBuilder = Standard52Builder()
        cards: Deck = builder.build_deck()
        # game code goes here
```

{{% /tab %}}

{{< /tabs >}}
    
From here, if we want to use any other decks of cards, all we have to do is switch out the single line for the type of builder we instantiate, and we'll be good to go! This is the powerful aspect of the builder pattern - we can move all of the complex code for creating objects to a builder class, and then any class that uses it can quickly and easily construct the objects it needs in order to function.

On the next page, we'll see how we can expand this pattern by including the factory pattern to help simplify things even further.
