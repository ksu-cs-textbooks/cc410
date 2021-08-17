---
title: "Objects in Memory"
weight: 50
pre: "10. "
---
We often talk about the **_class_** as a *blueprint* for an **_object_**.  This is because classes define what properties and methods an object should have, in the form of a **_constructor_**.  Consider this class representing a planet:

###### Java

```java
public class Planet{
    
    private double mass;
    public double getMass(){
        return this.mass;
    }
    
    private double radius;
    public double getRadius(){
        return this.radius;
    }
    
    public Planet(double mass, double radius){
        this.mass = mass;
        this.radius = radius;
    }
}
```

###### Python

```python
class Planet

    @property
    def mass(self) -> float:
        return self.__mass
    
    @property
    def radius(self) -> float:
        return self.__radius
    
    def __init__(self, mass: float, radius: float) -> None:
        self.__mass = mass
        self.__radius = radius
```

It describes a planet as having a mass and a radius, which will be stored as the ratio of this planet's attribute compared to Earth. We can create a specific planet by invoking its constructor, i.e.:

###### Java

```java
Planet earth = new Planet(1.0, 1.0);
```

###### Python

```python
earth: Planet = Planet(1.0, 1.0)
```
   
In this example, `earth` is an *instance* of the class `Planet`.  We can create other instances, i.e.

###### Java

```java
Planet mars = new Planet(0.107, 0.53);
```

###### Python

```python
mars: Planet = Planet(0.107, 0.53)
```

We can even create a `Planet` instance to represent one of the exoplanets discovered by [NASA’s TESS](https://www.nasa.gov/tess-transiting-exoplanet-survey-satellite "Testing Extoplanet Survey Satelite"):

###### Java

```java
Planet hd21749b = new Planet(23.20, 2.836);
```

###### Python

```python
hd21749b: Planet = Planet(23.20, 2.836)
```

Let's think more deeply about the idea of a class as a blueprint.  A blueprint for what, exactly?  For one thing, it serves to describe the *state* of the object, and helps us label that state.  If we were to check the radius of our variable `mars`, we would access the getter for the `radius` field:

###### Java

```java
mars.getRadius()
```

###### Python

```python
mars.radius
```

But a class does more than just labeling the properties and fields and providing methods to mutate the state they contain.  It also specifies how *memory needs to be allocated* to hold those values as the program runs.

Looking at our `Planet` class again, we can see it contains two floating point values. So, when we run the constructor for that class, our computer will know that it needs to allocate enough space in memory for those two values (8 bytes each in Java, and 24 bytes each in Python).

State and memory are clearly related - the current state is what data is stored in memory.  It is possible to take that memory's current state, write it to persistent storage (like the hard drive), and then read it back out at a later point in time and restore the program to exactly the state we left it with.  This is actually what your operating system does when you put it into hibernation mode.

The process of writing out the state is known as *serialization*, and it's a topic we'll revisit later.

# Static Modifier

You might have wondered how the `static` modifier plays into objects.  Essentially, the `static` keyword indicates the field or method it modifies _exists in only one memory location_.  I.e. a static field references the _same_ memory location for all objects that possess it.  

Consider this simple example class:

###### Java

```java
public class Simple:
    public static int x;
    public int y;
    
    public Simple(int x, int y){
        this.x = x;
        this.y = y;
    }
}
```

###### Python

```python
class Simple:
    
    x: int = 0
        
    def __init__(self, x: int, y: int) -> None:
        Simple.x = x
        self.y = y
```

Notice that the Java language uses the `static` keyword for fields, whereas in Python the field is simply defined outside of the constructor, and only attached to the class name and not `self`.

We can also create a couple of instances:

###### Java

```java
Simple first = new Simple(10, 12);
Simple second = new Simple(8, 5);
```

###### Python

```python
first: Simple = Simple(10, 12)
second: Simple = Simple(8, 5)
```

Once we've created both instances, the value of `first.x` would be 8 - because `first.x` and `second.x` reference the _same_ memory location (a _static_ unchanging location), and `second.x` was set _after_ `first.x`.  If we changed it again:

```java
first.x = 3
```

Then both `first.x` and `second.x` would have the value 3, as they share the same memory location. `first.y` would still be 12, and `second.y` would still be 5.

Another way to think about `static` is that it means the field or method we are modifying belongs to the _class_ and not the individual _object_.  Hence, each object _shares_ a `static` variable, because it belongs to their class. 

Used on a method, the `static` keyword in Java or the `@staticmethod` decorator in Python indicates that the method belongs to the class definition, not the object instance.  Hence, we must invoke it _from the class_, not an object instance: i.e. `Math.pow()`.  

Finally, when used with a class in Java, `static` indicates we can't create objects from the class - the class definition exists on its own.  Hence, the `Math m = new Math();`  is actually an error, as the `Math` class is declared static. Python does not directly support the `static` keyword for classes themselves, but classes which only contain static attributes and methods could be considered static classes. 
