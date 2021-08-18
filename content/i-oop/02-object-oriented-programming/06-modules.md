---
title: "Modules"
weight: 30
pre: "6. "
---
It might seem like the kind of modules that Parnas was describing don't exist in Java or Python, but they actually do - we just don't call them "modules".  Consider how you would compute the square root of a number:

{{< tabs >}}

{{% tab name="Java" %}}

```java
Math.sqrt(9.5);
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
math.sqrt(9.5)
```
{{% /tab %}}

{{< /tabs >}}

The `Math` or `math` class in this example is actually used _just like a module!_  We can't see the underlying implementation of the `sqrt()` method, it just provides to us a well-defined interface (i.e. you call it with the symbol `sqrt` and a value as a parameter). This method and other related math functions are encapsulated within the `Math` or `math` class.  

We can define our own module-like classes by making them `static`, i.e. we could group our vector math functions into a static `VectorMath` class.

{{< tabs >}}

{{% tab name="Java" %}}

```java
import java.lang.Math;

public static class VectorMath(){
    
    public static double dotProduct(Vector3 a, Vector3 b){
        return a.x * b.x + a.y * b.y + a.z * b.z;
    }
    
    public static double magnitude(Vector3 a){
        return Math.sqrt(Math.pow(a.x, 2) + Math.pow(a.y, 2) + Math.pow(a.z, 2));
    }
}
```
Usage:

```java
Vector3 vect1 = new Vector3(3.0, 4.0, 5.0);
Vector3 vect2 = new Vector3(6.0, 7.0, 8.0);
System.out.println(VectorMath.dotProduct(vect1, vect2));
System.out.println(VectorMath.magnitude(vect1));
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
import math

class VectorMath:
    
    @staticmethod
    def dot_product(a: Vector3, b: Vector3) -> float:
        return a.x * b.x + a.y * b.y + a.z * b.z
    
    @staticmethod
    def magnitude(a: Vector3) -> float:
        return math.sqrt(a.x ** 2 + a.y ** 2 + a.z ** 2)
```
Usage:

```python
vect1: Vector3 = Vector3(3.0, 4.0, 5.0)
vect2: Vector3 = Vector3(6.0, 7.0, 8.0)
print(VectorMath.dot_product(vect1, vect2))
print(VectorMath.magnitude(vect2))
```

{{% /tab %}}

{{< /tabs >}}