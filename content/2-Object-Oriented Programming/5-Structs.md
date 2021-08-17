---
title: "Structs"
weight: 25
pre: "5. "
---
Many object-oriented languages, such as C++ and C#, include the concept of a **struct** that form the basis of objects. A struct is an example of a [compound data type](https://en.wikipedia.org/wiki/Composite_data_type), a data type *composed* from other types.  This allows us to represent data in more complex ways by combining multiple primitive data types into a new type. This too, is a form of encapsulation, as it allows us to collect several values into a single data structure.  Consider the concept of a vector from mathematics - if we wanted to store three-dimensional vectors in a program, we could do so in several ways.  Perhaps the easiest would be as an array or list:

###### Java

```java
double[] vector = {3.0, 4.0, 5.0};
```

###### Python

```python
vector: List[float] = [3.0, 4.0, 5.0]
```

However, other than the variable name, there is no indication to other programmers that this is intended to be a three-element vector.  And, if we were to accept it in a function, say a dot product, we'd need to check that the length of both arrays or lists was exactly 3:

###### Java

```java
public double dotProduct(double[] a, double[] b){
    if(a.length != 3 || b.length != 3){
        throw new IllegalArgumentException();
    }
    return a[0] * b[0] + a[1] * b[1] + a[2] * b[2];
}
```


###### Python

```python
def dot_product(a: List[float], b: List[float]) -> float:
    if len(a) != 3 or len(b) != 3:
        raise ValueError()
    return a[0] * b[0] + a[1] * b[1] + a[2] * b[2]
```

A struct provides a much cleaner option, by allowing us to define a type that is composed of exactly three integers. Java and Python don't directly support structs, but we can use classes with just variables and a constructor to mimic a struct in those languages:

###### Java

```java
public class Vector3{
    public double x;
    public double y;
    public double z;
    
    public Vector3(double x, double y, double z){
        this.x = x;
        this.y = y;
        this.z = z;
    }
}
```

###### Python

```python
class Vector3:
    
    def __init__(self, x: float, y: float, z: float) -> None:
        self.x = x
        self.y = y
        self.z = z
```


Then, our dot product method can take two arguments of the `Vector3` type:


###### Java

```java
public double dotProduct(Vector3 a, Vector3 b){
    return a.x * b.x + a.y * b.y + a.z * b.z;
}
```


###### Python

```python
def dot_product(a: Vector3, b: Vector3) -> float:
    return a.x * b.x + a.y * b.y + a.z * b.z
```

There is no longer any concern about having the wrong number of elements in our vectors - it will always be three.  We also get the benefit of having unique names for these *fields* (in this case, `x`, `y`, and `z`).

Thus, a struct allows us to create *structure* to represent multiple values in one variable, encapsulating the related values into a single data structure. We can then use those data structures as new data types in our program. Variables, and compound data types, together represent the *state* of a program.  We'll examine this concept in detail next.
