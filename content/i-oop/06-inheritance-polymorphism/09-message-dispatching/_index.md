---
title: "Message Dispatching"
weight: 45
pre: "9. "
---

{{% youtube NOAmwPixxuM %}}

[Video Materials}({{<relref "./video">}})

The term _dispatch_ refers to how a language decides which polymorphic operation (a method or function) a message should trigger.

Consider polymorphic functions in Java, also known as **method overloading**, where multiple methods use the same name but have different parameters. Here's an example for calculating the rounded sum of an array of numbers:

###### Java

```java
public int roundedSum(int[] a){
    int sum = 0;
    for (int i : a) {
        sum += i;
    }
    return sum
}

public int roundedSum(double[] a){
    double sum = 0;
    for (double i : a) {
        sum += i;
    }
    return Math.round(sum);
}
```

How does the computer know which version to invoke at runtime?  It should not be a surprise that it is determined by the arguments - if an integer array is passed, the first is invoked, if a float array is passed, the second.

Python works a bit differently. In Python, **method overloading** is not allowed, so there cannot be two methods with the same name within a class. To achieve the same effect, optional parameters are used. In addition, because Python is dynamically typed, we could instead write our function to accept values of multiple types:

###### Python

```python
def rounded_sum(a: List[Union[int, float]]) -> int:
    sum_value: float = 0.0
    for i in a:
        sum_value += i
    return round(sum_value)
```

As we can see, that function will accept a list of either integer values or floating-point values, and it can properly handle them in either case. In Python, the name of the method is the only thing that is used to determine which piece of code should be executed, not the arguments.

## Object-Oriented Polymorphism

However, inheritance can cause some challenges in selecting the appropriate polymorphic form.  Consider the following fruit implementations that feature a `blend()` method:

{{< tabs >}}

{{% tab name="Java" %}}

```java
public class Fruit {

    public String blend() {
        return "A pulpy mess, I guess";
    }
}

public class Banana extends Fruit {

    @Override
    public String blend() {
        return "Yellow mush";
    }
}

public class Strawberry extends Fruit {

    @Override
    public String blend() {
        return "Gooey red sweetness!";
    }
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
class Fruit:
    
    def blend(self) -> str:
        return "A pulpy mess, I guess"

    
class Banana(Fruit):
    
    def blend(self) -> str:
        return "Yellow mush"
    

class Strawberry(Fruit):
    
    def blend(self) -> str:
        return "Gooey red sweetness!"
```

{{% /tab %}}

{{< /tabs >}}

Let's add some fruit instances to a list, and invoke their `blend()` methods:

{{< tabs >}}

{{% tab name="Java" %}}

```java
LinkedList<Fruit> toBlend = new LinkedList<>();
toBlend.add(new Fruit());
toBlend.add(new Banana());
toBlend.add(new Strawberry());
for(Fruit f : toBlend){
    System.out.println(f.blend());
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
to_blend: List[Fruit] = list()
to_blend.append(Fruit())
to_blend.append(Banana())
to_blend.append(Strawberry())
for f in to_blend:
    print(f.blend())
```

{{% /tab %}}

{{< /tabs >}}

What will be printed? If we look at the declared types, we'd expect each of them to act like a `Fruit` instance, so in that case the output would be just three lines of `A pulpy mess, I guess?`

However, that is not correct! This is the powerful aspect of polymorphic method dispatch. In both Java and Python, we don't look at the declared type of the object, but the actual underlying type of the instance itself. So, if the object was created as a `Banana` or `Strawberry`, then it will use the overridden methods from those child classes instead of the parent `Fruit` class. So, the actual output we'll get is:

```
A pulpy mess, I guess
Yellow mush
Gooey red sweetness!
```

In both Java and Python, we see an example of **method overriding**. If we include a method of the same name in the child class (and the same set of parameters, in the case of Java), we can override the method that exists in the parent class. In Java, we must use the `@Override` decorator, but Python doesn't require anything special. 

## Abstract vs. Interface

Of course, we can also update this example to either use an **abstract** class or an **interface**. There are some pros and cons to either option, but here's a good rule of thumb to start with:

* Use **inheritance** without making the parent class abstract only if it makes sense for the parent class to be instantiated itself. So, it might make sense to have a parent `Car` class and a subclass `SportsCar` that are both able to be instantiated.
* Use **inheritance with abstract classes** if the parent class should not be instantiated. For example, when modeling the animal kingdom with a parent `Canine` class and subclasses `Dog` and `Wolf`, it might be best if the parent class cannot be instantiated directly.
* Use **interfaces** when you want to design a set of methods or behaviors that a class should implement, but which may not otherwise create strong a relationship between the classes. For example, we could create an `IUpdatable` interface to require several classes to implement a method called `update`, but the classes themselves might not be related otherwise. 

Finally, remember that there are not really any correct answers here - each option comes with trade-offs, and it is up to you as a developer to help determine which is best. Therefore, it is very helpful to have experience with all three approaches so you understand how each one can be used. 
