---
title: "UML Example"
weight: 40
pre: "8. "
---

Let's work through an example of creating a UML class diagram based on existing code. This is loosely based off a project from an earlier course, so some of the structure may be familiar. 

## The Project

This project is a number calculator that makes use of object-oriented concepts such as inheritance, interfaces, and polymorphism to represent different types of numbers using different classes. We'll also follow the [Model-View-Controller (MVC)](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) architectural pattern.  

### Number Interface

We'll start by looking at the `Number` interface, which is the basis of all of the number classes. We're omitting the method code in these examples, since we are only concerned with the overall structure of the classes themselves.

{{< tabs >}}

{{% tab name="Java" %}}

```java
public interface Number {
    Number add(Number n);
    Number subtract(Number n);
    Number multiply(Number n);
    Number divide(Number n);
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
class Number(metaclass=abc.ABCMeta):

    @classmethod
    def __subclasshook__(cls, subclass: type) -> bool:
        
    @abc.abstractmethod
    def add(self, n: Number) -> Number:

    @abc.abstractmethod
    def subtract(self, n: Number) -> Number:

    @abc.abstractmethod
    def multiply(self, n: Number) -> Number:

    @abc.abstractmethod
    def divide(self, n: Number) -> Number:
```

{{% /tab %}}

{{< /tabs >}}

In UML, we'd represent this interface using the following box. It includes the `<<interface>>` stereotype, as well as the listed methods shown in _italics_ since they are all abstract. Finally, each method in an interface is assumed to be `public`, so we'll include a plus symbol `+` in front of each method.

![Number Interface](/images/5/410_5_ex_number.svg)

### Real Number Class

Next is the class for representing real numbers. This class will be a **realization** of the `Number` interface, as we can see in the code:

{{< tabs >}}

{{% tab name="Java" %}}

```java
public class RealNumber implements Number {

    private double value;

    public RealNumber(double value){ }

    public Number add(Number n){ }

    public Number subtract(Number n){ }

    public Number multiply(Number n){ }

    public Number divide(Number n){ }

    @Override
    public String toString(){ }

    @Override
    public boolean equals(Object o){ }
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
class RealNumber(Number):

    def __init__(self, value: float) -> None:
        self.__value = value
        
    def add(self, n: Number) -> Number:

    def subtract(self, n: Number) -> Number:

    def multiply(self, n: Number) -> Number:

    def divide(self, n: Number) -> Number:

    def __str__(self) -> str:

    def __eq__(self, o: object) -> bool:
```

{{% /tab %}}

{{< /tabs >}}

it also includes implementations for a couple of other methods beyond the interface, including a constructor. So, in our UML diagram, we'll add another box to represent that class, and use the realization association arrow to show the connection between the classes. Remember that the arrow itself points toward the interface or parent class. 

![RealNumber Class](/images/5/410_5_ex_realnumber.svg)

### Other Number Classes

From here, it's pretty easy to see how we can use inheritance to create a `RationalNumber` class and an `IntegerNumber` class. The only way that they differ from the `RealNumber` class are the attributes. So, we'll quickly add those to our UML diagram as well. 

![All Number Classes](/images/5/410_5_ex_allnumber.svg)

### Complex Numbers

At this point, we can add a new class to represent [complex numbers](https://en.wikipedia.org/wiki/Complex_number). A complex number consists of two parts - a real part and an imaginary part. So, it will both implement the `Number` interface, but it will also be composed of two `RealNumber` attributes. Notice that we're using `RealNumber` as the attribute instead of the `Number` interface. This is because we don't want a complex number to contain a complex number, so we're being careful about our inheritance. In code, this class would look like this:

{{< tabs >}}

{{% tab name="Java" %}}

```java
public class ComplexNumber implements Number {

    private RealNumber real;
    private RealNumber imaginary;

    public ComplexNumber(RealNumber real, RealNumber imaginary){ }

    public Number add(Number n){ }

    public Number subtract(Number n){ }

    public Number multiply(Number n){ }

    public Number divide(Number n){ }

    @Override
    public String toString(){ }

    @Override
    public boolean equals(Object o){ }
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
class ComplexNumber(Number):

    def __init__(self, real: RealNumber, imaginary: RealNumber) -> None:
        self.__real = real
        self.__imaginary = imaginary
        
    def add(self, n: Number) -> Number:

    def subtract(self, n: Number) -> Number:

    def multiply(self, n: Number) -> Number:

    def divide(self, n: Number) -> Number:

    def __str__(self) -> str:

    def __eq__(self, o: object) -> bool:
```

{{% /tab %}}

{{< /tabs >}}

In our UML diagram, we'll add a box for this class. We'll also add both a realization association to the `Number` interface, but also a composition association to the `RealNumber` class, complete with the cardinality of the relationship.

![Imaginary Numbers](/images/5/410_5_ex_imaginary.svg)

### MVC Components

Once we've created all of our number classes, we can quickly create our `View` and `Controller` classes as well. They will handle getting input from the user, performing operations, and displaying the results.

{{< tabs >}}

{{% tab name="Java" %}}

```java
public class View {

    public View(){ }

    public void show(Number n){ }

    public String input(){ }

}

public class Controller {

    private List<Number> numbers;
    private View view;

    public Controller(){ }

    public void build(){ }
    
    public void sum(){ }

    public static void main(String[] args){ }
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
class View:

    def __init__(self) -> None:

    def show(self, n: Number) -> None:

    def input(self) -> str:


class Controller:

    def __init__(self) -> None:
        self.__numbers: List[Number] = list()
        self.__view: View = View()
    
    def build(self) -> None:

    def sum(self) -> None:

    @classmethod
    def main(self, args: List[str]) -> None:

```

{{% /tab %}}

{{< /tabs >}}

In the code, we see that the `Controller` class contains an attribute for a single `View()` instance, and also a list of `Number` instances. So, we'll end up using a composition association between `Controller` and `View`, and an aggregation association between `Controller` and the `Number` interface.

![Full UML](/images/5/410_5_ex_all.svg)

This is a small example, but it demonstrates many of the important object-oriented concepts in a single UML diagram:

* The `Number` class is an interface and abstract class
* `RealNumber` implements the `Number` class through a **realization** association
* `RationalNumber` and `IntegerNumber` show direct inheritance through a **generalization** association
* `ImaginaryNumber` contains two `RealNumber` instances, showing the **composition** association and a multiplicity of 2.
* The `Controller`, `View` and `Number` classes make up the various parts of an MVC architecture.
* The `Controller` stores a list of `Number` instances, demonstrating the **aggregation** association.
* The `Controller` also contains a single `View` instance, which is another **composittion** association with multiplicity of 1.

## Further Reading

UML is a very broad topic to cover in a single module, let alone a single class. For more information on building and reading UML diagrams, refer to these sources:

* [UML Class Diagram Tutorial](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-class-diagram-tutorial/) from Visual Paradigm
* [UML Class Diagram Tutorial (Video)](https://www.youtube.com/watch?v=UI6lqHOVHic) from Lucidchart

There are also many textbooks devoted to teaching UML concepts, as well as lots of examples online to learn from. The O'Reilly subscription through the K-State Libraries offers several books to choose from that can be accessed for free through [this link](https://go.oreilly.com/kansas-state-university):

* [Unified Modeling Language User Guide](https://learning.oreilly.com/library/view/unified-modeling-language/0321267974/)
* [Learning UML 2.0](https://learning.oreilly.com/library/view/learning-uml-2-0/0596009828/)

