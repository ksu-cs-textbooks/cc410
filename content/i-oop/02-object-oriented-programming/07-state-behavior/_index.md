---
title: "State and Behavior"
weight: 35
pre: "7. "
---

{{% youtube 7UN8fXcpv7s %}}

[Video Materials}({{<relref "./video">}})

The data stored in a program at any given moment (in the form of variables, objects, etc.) is the *state* of the program.  Consider a variable:

```java
int a = 5;
```

The state of the variable **a** after this line is **5**.  If we then run:

```java
a = a * 3;
```

The state is now **15**. Consider the `Vector3` struct we defined earlier. If we create an instance of that struct in the variable `b`:

```java
Vector3 b = new Vector3(1.2, 3.7, 5.6);
```

The state of our variable `b` is {$1.2, 3.7, 5.6$}.  If we change one of `b`'s fields:

```java
b.x = 6.0;
```

The state of our variable `b` is {$6.0, 3.7, 5.6$}.

We can also think about the state of the *program*, which would be something like:

{$a: 5, b:${$x: 6.0, y: 3.7, z: 5.6$}}

We can therefore think of a program as a *state machine*. We can in fact, draw our entire program as a state table listing all possible legal states (combinations of variable values) and the transitions between those states. Techniques like this can be used to reason about our programs and even prove them correct!

This way of reasoning about programs is the heart of [Automata Theory](https://en.wikipedia.org/wiki/Automata_theory), a subject you may choose to learn more about if you pursue graduate studies in computer science.

What causes our program to transition between states?  If we look at our earlier examples, it is clear that the *assignment* statement is a strong culprit.  Expressions clearly have a role to play, as do control-flow structures, which decide which transformations take place.  In fact, we can say that our program code is what drives state changes - the *behavior* of the program.

Thus, programs are composed of both _state_ (the values stored in memory at a particular moment in time) and _behavior_ (the instructions to change that state).  

Now, can you imagine trying to draw the state table for a large program?  Something on the order of EPIC?  

On the other hand, with encapsulation we can reason about state and behavior on a much smaller scale.  Consider this function working with our `Vector3` struct:

{{< tabs >}}

{{% tab name="Java" %}}

```java
public static Vector3 scale(Vector3 vec, double scale){
    double x = vec.x * scale;
    double y = vec.y * scale;
    double z = vec.z * scale;
    return new Vector3(x, y, z);
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
@staticmethod
def scale(vec: Vector3, scale: float) -> Vector3:
    x: float = vec.x * scale
    y: float = vec.y * scale
    z: float = vec.z * scale
    return Vector3(x, y, z)
```

{{% /tab %}}

{{< /tabs >}}

If this method was invoked with a vector {$4.0, 1.0, 3.4$} and a scale $2.0$, our state table would look something like:

<table>
  <tr>
    <th>step</th>
    <th>vec.x</th>
    <th>vec.y</th>
    <th>vec.z</th>
    <th>scale</th>
    <th>x</th>
    <th>y</th>
    <th>z</th>
    <th>return.x</th>
    <th>return.y</th>
    <th>return.z</th>
  <tr>
  <tr>
    <td>0</td>
    <td>4.0</td>
    <td>1.0</td>
    <td>3.4</td>
    <td>2.0</td>
    <td>0.0</td>
    <td>0.0</td>
    <td>0.0</td>
    <td>0.0</td>
    <td>0.0</td>
    <td>0.0</td>
  </tr>
  <tr>
    <td>1</td>
    <td>4.0</td>
    <td>1.0</td>
    <td>3.4</td>
    <td>2.0</td>
    <td>8.0</td>
    <td>0.0</td>
    <td>0.0</td>
    <td>0.0</td>
    <td>0.0</td>
    <td>0.0</td>
  </tr>
  <tr>
    <td>2</td>
    <td>4.0</td>
    <td>1.0</td>
    <td>3.4</td>
    <td>2.0</td>
    <td>8.0</td>
    <td>2.0</td>
    <td>0.0</td>
    <td>0.0</td>
    <td>0.0</td>
    <td>0.0</td>
  </tr>
  <tr>
    <td>3</td>
    <td>4.0</td>
    <td>1.0</td>
    <td>3.4</td>
    <td>2.0</td>
    <td>8.0</td>
    <td>2.0</td>
    <td>6.8</td>
    <td>0.0</td>
    <td>0.0</td>
    <td>0.0</td>
  </tr>
  <tr>
    <td>4</td>
    <td>4.0</td>
    <td>1.0</td>
    <td>3.4</td>
    <td>2.0</td>
    <td>8.0</td>
    <td>2.0</td>
    <td>6.8</td>
    <td>8.0</td>
    <td>2.0</td>
    <td>6.8</td>
  </tr>
</table>

Because the parameters `vec` and `scale`, as well as the variables `x`, `y`, `z`, and the unnamed `Vector3` we return are all defined only within the scope of the method, we can reason about them and the associated state changes _independently_ of the rest of the program.  This greatly simplifies both writing and debugging programs.
