---
title: "Message Passing"
weight: 55
pre: "11. "
---
{{< youtube keEZ55ExLXY  >}}

[Video Materials]({{% relref "./video" %}})

The second criteria Alan Kay set for object-oriented languages was [message passing](https://en.wikipedia.org/wiki/Message_passing).  Message passing is a way to request a unit of code engage in a behavior, i.e. changing its state, or sharing some aspect of its state.  

Consider the real-world analogue of a letter sent via the postal service.  Such a message consists of: an address the message needs to be sent to, a return address, the message itself (the letter), and any data that needs to accompany the letter (the enclosures).  A specific letter might be a wedding invitation.  The message includes the details of the wedding (the host, the location, the time), an enclosure might be a refrigerator magnet with these details duplicated.  The recipient should (per custom) send a response to the host addressed to the return address letting them know if they will be attending.

In an object-oriented language, message passing primarily take the form of methods. Let's revisit our example `Vector3` class from earlier:

{{< tabs >}}

{{% tab title="Java" %}}

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
    
    public double dotProduct(Vector3 other){
        return this.x * other.x + this.y * other.y + this.z * other.z;
    }
    
    public void scale(double scalar){
        this.x *= scalar;
        this.y *= scalar;
        this.z *= scalar;
    }
}
```

{{% /tab %}}

{{% tab title="Python" %}}

```python
class Vector3:
    
    def __init__(self, x: float, y: float, z: float) -> None:
        self.x = x
        self.y = y
        self.z = z
        
    def dot_product(self, other: Vector3) -> float:
        return self.x * other.x + self.y * other.y + self.z * other.z
    
    def scale(self, scalar: float) -> None:
        self.x *= scalar
        self.y *= scalar
        self.z *= scalar
```

{{% /tab %}}

{{< /tabs >}}

We can also create a couple of instances of the class, and use its dot product method:

{{< tabs >}}

{{% tab title="Java" %}}


```java
Vector3 a = new Vector3(1.0, 1.0, 2.0);
Vector3 b = new Vector3(4.0, 2.0, 1.0);
double c = a.dotProduct(b);
```

{{% /tab %}}

{{% tab title="Python" %}}

```python
a: Vector3 = Vector3(1.0, 1.0, 2.0)
b: Vector3 = Vector3(4.0, 2.0, 1.0)
c: float = a.dot_product(b)
```

{{% /tab %}}

{{< /tabs >}}

Consider the invocation of `a.dotProduct(b)` (Java) or `a.dot_product(b)` (Python) above.  The method name, `dotProduct` or `dot_product` provides the details of what the message is intended to accomplish (the letter).  Invoking it on a specific variable, i.e. `a`, tells us who the message is being sent to (the recipient address).  The return type indicates what we need to send back to the recipient (the invoking code), and the parameters provide any data needed by the class to address the task (the enclosures).

Let's define a new method for our Vector3 class that emphasizes the role message passing plays in mutating object state:

{{< tabs >}}

{{% tab title="Java" %}}

```java
public void normalize(){
    double magnitude = Math.sqrt(Math.pow(this.x, 2) + Math.pow(this.y, 2) + Math.pow(this.z, 2));
    this.x /= magnitude;
    this.y /= magnitude;
    this.z /= magnitude;
}
```

{{% /tab %}}

{{% tab title="Python" %}}

```python
def normalize(self) -> None:
    magnitude: float = math.sqrt(self.x ** 2 + self.y ** 2 + self.z ** 2)
    self.x /= magnitude
    self.y /= magnitude
    self.z /= magnitude
```

{{% /tab %}}

{{< /tabs >}}

We can now invoke the `normalize()` method on a `Vector3` object to mutate its state, shortening the magnitude of the vector to length 1.

{{< tabs >}}

{{% tab title="Java" %}}

```java
Vector3 f = new Vector3(9.0, 3.0, 2.0);
f.normalize();
```

{{% /tab %}}

{{% tab title="Python" %}}

```python
f: Vector3 = Vector3(9.0, 3.0, 2.0)
f.normalize()
```

{{% /tab %}}

{{< /tabs >}}

Note how here, `f` is the object receiving the message `normalize`.  There is no additional data needed, so there are no parameters being passed in.  Our earlier dot product method took a second vector as its argument, and used that vector's values to mutate its state.  

Message passing therefore acts like those special molecular pumps and other gate mechanisms of a cell that control what crosses the cell wall.  The methods defined on a class determine how outside code can interact with the object. An extra benefit of this approach is that a method becomes an _abstraction_ for the behavior of the code, and the associated state changes it embodies.  As a programmer using the method, we don't need to know the exact implementation of that behavior - just what data we need to provide, and what it should return or how it will alter the program state.  This makes it far easier to reason about our program, and also means we can change the internal details of a class (perhaps to make it run faster) without impacting the other aspects of the program.

{{% notice info "Function vs. Method" %}}

You probably have noticed that in many programming languages we speak of _functions_, but in Java and other object-oriented languages, we'll often speak of _methods_.  You might be wondering just what is the difference?

Both are forms of message passing, and share many of the same characteristics.  Broadly speaking though, _methods_ are _functions_ defined as part of an object.  Therefore, their bodies can access the state of the object.  In fact, that's what the `this` keyword in Java means - it refers to _this object_, i.e. the instance of the class that the method is currently executing for. In Python, any class methods include a parameter typically named `self` that represents the same concept - the instance of the class that the method was called on. For non-object-oriented languages, there is no concept of `this` (or `self` as it appears in other languages).

However, many times developers will use the terms **function** and **method** interchangeably. Likewise, variables stored in a class may be referred to as both **attributes** and **fields**. Sadly, we are not very exacting about how we use our own terms, even though our field requires us to be exacting in other ways. So, we'll just have to do our best to read the context clues and interpret what is meant. In this book, we'll try to use these terms as clearly as we can.

{{% / notice %}}
