---
type: "reveal"
hidden: true
---
<section>
    <h2>Primitive Data Types</h2>
    <ul>
        <li>Integer: <code>int</code></li>
        <li>Floating Point: <code>double</code> or <code>float</code></li>
        <li>Boolean: <code>boolean</code> or <code>bool</code></li>
        <li>String: <code>char/String</code> or <code>str</code></li>
    </ul>
</section>
<section>
    <h4>Java</h4>
    <pre class="java"><code>int x = 5;
double y = 5.5;
boolean z = true;
String word = "Hello";
System.out.println(x + word) // what does this output?</code></pre>
    <h4>Python</h4>
    <pre class="python"><code>x: int = 5
y: float = 5.5
z: bool = True
word: str = "Hello"
print(x + word) # what does this output?</code></pre>
</section>
<section>
    <h4>Java</h4>
    <pre class="java"><code>int x = 5;
double y = 5.5;
boolean z = true;
String word = "Hello";
System.out.println(x + word) // "5Hello"</code></pre>
    <h4>Python</h4>
    <pre class="python"><code>x: int = 5
y: float = 5.5
z: bool = True
word: str = "Hello"
print(x + word) # what does this output?</code></pre>
</section>
<section>
    <h4>Java</h4>
    <pre class="java"><code>int x = 5;
double y = 5.5;
boolean z = true;
String word = "Hello";
System.out.println(x + word) // "5Hello"</code></pre>
    <h4>Python</h4>
    <pre class="python"><code>x: int = 5
y: float = 5.5
z: bool = True
word: str = "Hello"
print(x + word) # TypeError!</code></pre>
</section>
<section>
    <h6>The data type determines how variables are treated.</h6>
    <br>
    <h6 class="fragment">Different data types<br>support different operations.</h6>
</section>
<section>
    <h3>Custom Data Type - Enum</h3>
    <p>An enum is a list of named values.</p>
    <div style="float: right; width: 50%">
        <h6>Python</h6>
        <pre class="python stretch"><code>from enum import Enum<br><br>
class Grade(Enum):
    A = 1
    B = 2
    C = 3
    D = 4
    F = 5</code></pre>
    </div>
    <div style="float: left; width: 50%">
        <h6>Java</h6>
        <pre class="java"><code>public enum Grade {
    A,
    B,
    C,
    D,
    F;
}</code></pre>
    </div>
</section>
<section>
    <h3>Custom Data Type - Enum</h3>
    <p>An enum defines a <b>new data type.</b></p>
    <h4>Java</h4>
    <pre class="java"><code>Grade gradeA = Grade.A;
Grade gradeB = Grade.B;
student.setGrade(Grade.C);</code></pre>
    <h4>Python</h4>
    <pre class="python"><code>grade_a: Grade = Grade.A
grade_b: Grade = Grade.B
student.set_grade(Grade.C)</code></pre>
</section>
<section>
    <h6>Classes define new data types composed of one or more other types.</h6>
    <br>
    <h6 class="fragment">This new data type is the <b><i>state</i></b> of the object built from the class.</h6>
</section>
<section>
    <h3>Type Systems</h3>
    <ul>
        <li>Java - Strong, Static Typing</li>
        <li>Python - Strong, Dynamic Typing</li>
    </ul>
    <p class="fragment">We are using Mypy to make Python act like a statically typed language.</p>
</section>
