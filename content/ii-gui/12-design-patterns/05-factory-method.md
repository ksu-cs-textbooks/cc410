---
title: "Factory Method Pattern"
weight: 25
pre: "5. "
---

The next pattern we'll explore is the **factory method pattern**. The [factory method pattern](https://en.wikipedia.org/wiki/Factory_method_pattern) is used to allow us to construct an object of a desired type without actually having to specify that type explicitly in our code. Instead, we just provide the factory with an input specifying the type of object we need, and it will return an instance of that type. By making use of the factory method pattern, classes that require access to these object don't need to be updated any time an underlying object type is modified. Instead, they can simply reference the parent or interface data types, and the factory handles creating and returning objects of the correct type whenever needed.

![factory method pattern UML](/images/12/factory.jpg)[^1]

[^1]: https://commons.wikimedia.org/w/index.php?title=File:W3sDesign_Factory_Method_Design_Pattern_UML.jpg&oldid=488851997

As we can see in the UML diagram for this pattern, it looks very similar to the builder pattern we saw previously. There is a `Creator` interface, which defines the interface that each factory uses. Then, the concrete `Creator1` class is actually used to create the class required. 

Let's continue our deck of cards example from the previous page to include the factory method pattern.

### Decks Enum

To simplify this process, we'll create a quick enumeration of the possible decks available in our system. This makes it easy to expand later and include more decks of cards.

{{< tabs >}}

{{% tab name="Java" %}}

```java
public enum DeckType {
    STANDARD52("Standard 52"),
    STANDARD52ONEJOKER("Standard 52 with One Joker"),
    STANDARD52TWOJOKER("Standard 52 with Two Jokers"),
    PINOCHLE("Pinochle"),
    OLDMAID("Old Maid"),
    UNO("Uno"),
    ROOK("Rook");
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
from enum import Enum


class DeckType(str, Enum):
    STANDARD52 == "Standard 52"
    STANDARD52ONEJOKER == "Standard 52 with One Joker"
    STANDARD52TWOJOKER == "Standard 52 with Two Jokers"
    PINOCHLE == "Pinochle"
    OLDMAID == "Old Maid"
    UNO == "Uno"
    ROOK == "Rook"
```

{{% /tab %}}

{{< /tabs >}}

### Factory Class

Next, we'll define a simple factory class, which is able to build each type of card deck. We'll leave out the parent interface for now, since this project will only ever have a single factory object available. 

{{< tabs >}}

{{% tab name="Java" %}}

```java
import java.lang.IllegalArgumentException;

public class DeckFactory{

    public Deck getDeck(DeckType deck) {
        if(deck == DeckType.STANDARD52){
            return new Standard52Builder().buildDeck();
        }else if(deck == DeckType.STANDARD52ONEJOKER){
            return new Standard52OneJokerBuilder().buildDeck();
        }else if(deck == DeckType.STANDARD52TWOJOKER){
            return new Standard52TwoJokerBuilder().buildDeck();
        }else if(deck == DeckType.PINOCHLE){
            return new PinochleBuilder().buildDeck();
        }else if(deck == DeckType.OLDMAID){
            return new OldMaidBuilder().buildDeck();
        }else if(deck == DeckType.UNO){
            return new UnoBuilder().buildDeck();
        }else if(deck == DeckType.ROOK){
            return new RookBuilder().buildDeck();
        }else {
            throw new IllegalArgumentException("Unsupported DeckType");
        }
    }
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
class DeckFactory:

    def get_deck(self, deck: DeckType) -> Deck:
        if deck == DeckType.STANDARD52:
            return Standard52Builder().buildDeck()
        elif deck == DeckType.STANDARD52ONEJOKER:
            return Standard52OneJokerBuilder().buildDeck()
        elif deck == DeckType.STANDARD52TWOJOKER:
            return Standard52TwoJokerBuilder().buildDeck()
        elif deck == DeckType.PINOCHLE:
            return Standard52Builder().buildDeck()
        elif deck == DeckType.OLDMAID:
            return OldMaidBuilder().buildDeck()
        elif deck == DeckType.UNO:
            return UnoBuilder().buildDeck()
        elif deck == DeckType.ROOK:
            return RookBuilder().buildDeck()
        else:
            raise ValueError("Unsupported DeckType");
```

{{% /tab %}}

{{< /tabs >}}

### Using the Factory

Now that we've created our factory class, we can update our main method to use it instead. In this case, we'll get the type of deck to be used directly from the user as input:

{{< tabs >}}

{{% tab name="Java" %}}

```java
public class CardGame{

    public static void main(String[] args) {
        // ask user for input and store in `deckType`
        String deckType = "Standard 52";
        Deck cards = DeckFactory().getDeck((DeckType.valueOf(deckType)));
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
        cards: Deck = DeckFactory().get_deck(DeckType(deck_type))
        # game code goes here
```

{{% /tab %}}

{{< /tabs >}}

This code is actually doing quite a bit in only two lines, so let's go through it step by step. First, we're assuming that we are getting user input to determine which deck should be used. This could be done via a GUI, the terminal, or some other means. We're storing that input in a string, just to demonstrate the power of the factory method pattern. As long as the string matches one of the available deck types in the `DeckType` enum, it will work. Of course, this may be difficult to do, so our input code might need to verify that the user inputs a valid option. 

However, if we have a valid option, we can convert it to the correct enum value, and then pass that as an argument to the `getDeck()` method of our `DeckFactory` class. The factory will look at the parameter, construct the correct deck using the appropriate builder class, and then return it back to our application. Pretty handy!

## Practical Example: Database Connections

One of the most common places the factory method pattern appears is in the construction of database connections. In theory, we'd like any of our applications to be able to use different types of databases, so many database connection libraries use the factory method pattern to create a database connection. Here's what that might look like - this code will not actually work, but is representative of what it looks like in practice:

{{< tabs >}}

{{% tab name="Java" %}}

```java
public class DbTest{

    public static void main(String[] args) {
        // connect to Postgres
        DbConnection conn = DbFactory.get("postgres");
        conn.connect("username", "password", "database");
        
        // connect to MySql
        DbConnection conn2 = DbFactory.get("mysql");
        conn2.connect("username", "password", "database");
        
        // connect to Microsoft SQL Server
        DbConnection conn3 = DbFactory.get("mssql");
        conn3.connect("username", "password", "database");
    }
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
class DbTest:

    @staticmethod
    def main(args: List[str]) -> None:
        # connect to Postgres
        conn: DbConnection = DbFactory.get("postgres")
        conn.connect("username", "password", "database")
        
        # connect to MySql
        conn2: DbConnection = DbFactory.get("mysql")
        conn2.connect("username", "password", "database")
        
        # connect to Microsoft SQL Server
        conn3: DbConnection = DbFactory.get("mssql")
        conn3.connect("username", "password", "database")
```

{{% /tab %}}

{{< /tabs >}}

In each of these examples, we can get the database connection object we need to interface with each type of database by simply providing a string that specifies which type of database we plan to connect to. This makes it quick and easy to switch database types on the fly, and as a developer we don't have to know any of the underlying details for actually connecting to and interfacing with the database. Overall, this is a great use of the factory method pattern in practice today.
