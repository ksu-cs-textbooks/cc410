---
title: "Classes"
weight: 25
pre: "5. "
---

{{% youtube fKuJNhMIQUE %}}

[Video Materials](video)

In a UML class diagram, individual classes are represented with a box divided into three compartments, each of which is for displaying specific information:

![Class Diagram example](/cc410/images/5/410_5_classbox.svg)

The first compartment identifies the class - it contains the name of the class. The second compartment holds the _attributes_ of the class (the _fields_ and _properties_).  And the third compartment holds the _operations_ of the class (the _methods_) of the class.

In the diagram above, we can see the `Fruit` class modeled on the left side. 

{{% notice info info-1 "Java vs. Python in UML" %}}

UML is a very flexible tool, but it can become difficult to create UML diagrams that accurately reflect the differences between programming languages. So, different developers might implement the same UML class diagram in slightly different ways. 

For example, in Java we would use a `boolean` data type to represent a Boolean value, whereas Python uses the `bool` type. Likewise, Java also includes a class called `Boolean` that is an object wrapper around a primitive `boolean` variable, allowing it to be used in various Java collections. Additionally, some other languages do not include a Boolean data type at all, and instead use a small integer with 0 representing true and other values representing false. 

In prior CC courses, it was important for the software to exactly match the specification so that our autograders would work. In that case, we provided UML diagrams that were somewhat unique to each programming language. For this course, we will create UML diagrams that are a bit more generalized. 

In the descriptions below, we'll include discussions of ways to properly represent each UML element for each language, but it may allow for some flexibility. In general, as long a similarly experienced developer can follow the UML diagram and/or the source code and correlate the two, we will consider that good enough.

{{% / notice %}}

### Attributes

The _attributes_ in UML represent the _state_ of an object.  For most object-oriented languages, this would correspond to the _fields_ and _properties_ of the class.

We indicate fields in our UML diagram with a typed element. So, to create a private Boolean variable named `blended`, we would include the following:

{{< tabs >}}

{{% tab name="Java" %}}

```
- blended: boolean
```

{{% /tab %}}

{{% tab name="Python" %}}

```
- blended: bool
```

For Python, we may also choose to include the underscores in front of the name to show that it should be treated as a private attribute, as implied by the `-` at the start of the element:

```
- __blended: bool
```

However, this can make the UML a bit more difficult to read, so we generally won't do this in the UML diagrams in this course.

{{% /tab %}}

{{< /tabs >}}

### Accessor Methods

Java and Python handle accessor methods differently, and they can be denoted in UML in many different ways. 

A general solution would be to include a _stereotype_ after the element, indicating if a public getter or setter should be created for that element. So, to create a getter and a setter for our `blended` attribute, we could do the following:

{{< tabs >}}

{{% tab name="Java" %}}

```
- blended: boolean <<get,set>>
```

{{% /tab %}}

{{% tab name="Python" %}}

```
- blended: bool <<get,set>>
```

{{% /tab %}}

{{< /tabs >}}

Of course, each language would handle this a bit differently. In Java, we would create public `getBlended()` and `setBlended(boolean)` methods in our class. In Python, we would use the `@property` and `@blended.setter` decorators to create a Python property. While all of those are technically methods, they are really meant to implement the functionality of an attribute, so we'll treat them as part of the attribute in UML.

What if our accessors implement unique functionality, or we want one of them to be protected instead of public? In those cases, we may want to include the explicit accessor methods as operations as described below. However, in general, it is best practice to make our UML as concise as possible, so we generally don't list accessor methods directly unless there is a good reason to do so. 

### Operations

The _operations_ in UML represent the _behavior_ of the object, i.e. the _methods_ we can invoke upon it.  These are declared using the pattern:

```
visibility name([parameter list])[:return type]
```

The  `[visibility]` portion uses the same symbols as typed elements, with the same correspondences. The `name` is the name of the method, and the `[parameter list]` is a comma-separated list of typed elements, corresponding to the parameters of the method. The `[:return type]` indicates the return type for the method. That portion can be omitted if the method doesn't explicitly return a value (`void` in Java or `None` in Python).  

Thus, in the example above, the protected method `Blend` has no parameters and returns a string.  

Consider a method that adds together two integers and returns the result. The examples below show how the method's _signature_ corresponds to its UML element.

{{< tabs >}}

{{% tab name="Java" %}}

```java
public int add(int a, int b){
    return a + b;
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
def add(a: int, b: int) -> int:
    return a + b
```

{{% /tab %}}

{{< /tabs >}}

###### UML

```
+ add(a: int, b: int): int
```

## Static and Abstract

In UML, we indicate a class is static by _underlining_ its name in the first compartment of the class diagram.  We can similarly indicate operations and methods are static by underlining the entire line referring to them.

To indicate a class is abstract, we _italicize_ its name.  Abstract methods are also indicated by italicizing the entire line referring to them.

We'll talk more about some of these concepts in a later chapter. 
