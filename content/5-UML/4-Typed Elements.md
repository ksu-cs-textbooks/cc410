---
title: "Typed Elements"
weight: 20
pre: "4. "
---
A second basic building block for UML diagrams is a _typed element_.  Typed elements (as you might expect from the name) have a _type_.  Fields and parameters are typed elements, as are method parameters and return values.

The pattern for defining a typed element is:

```
[visibility] element: type [constraint]} 
```

The optional $[visibility]$ indicates the visibility of the element, the $element$ is the name of the typed element, and the $type$ is its type, and the $[constraint]$ is an optional constraint.  

### Visibility

In UML _visibility_ (based on access modifiers in Java, or the use of underscores in Python) is indicated with symbols, i.e.:

* `+` indicates public access.
* `-` indicates private access.
* `#` indicates protected access, which we will discuss in a later chapter.

Consider, for example, a private `size` field. In a Java class, we would do the following:

###### Java

```java
private int size;
```

In Python, we might have the following assignment in our constructor:

###### Python

```python
self.__size: int = 0;
```

In a UML diagram, that field would be expressed as:

```
- size: int
```

### Constraints

A typed element can include a _constraint_ indicating some restriction for the element.  The constraints are contained in a pair of curly braces after the typed element, and follow the pattern:

```
{element: boolean expression}
```

For example:

```
- age: int {age: >= 0}
```

indicates the private variable `age` must be greater than or equal to 0.
