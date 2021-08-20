---
type: "reveal"
hidden: true
---
<section>
    <h3>Java Interfaces</h3>
    <ul>
        <li>Use the <code>interface</code> keyword</li>
        <li>Usually only methods</li>
        <li>All methods <code>public abstract</code></li>
        <li>All attributes <code>public static final</code></li>
        <li>No constructor, no code</li>
    </ul>
</section>
<section>
    <h3>Java Interface Example</h3>
    <pre class="java"><code>public interface IMyQueue {
    void enqueue(Object o);
    Object dequeue();
    Object peek();
    int size();
}</code></pre>
</section>
<section>
    <h3>Using a Java Interface</h3>
    <pre class="java stretch"><code>public class WaitingList implements IMyQueue {
    public void enqueue(Object o) {
        //code here
    }<br>
    public Object dequeue() {
        //code here
    }<br>
    public Object peek() {
        //code here
    }<br>
    public int size() {
        //code here
    }
}</code></pre>
</section>
<section>
    <h3>Interfaces are Types</h3>
    <pre class="java"><code>IMyQueue wait = new WaitingList();
wait.enqueue(new Person());
wait.dequeue();</pre></code>
    <p>We can call any methods<br>defined by the interface</p>
</section>
<section>
    <h3>Java Inheritance</h3>
    <ul style="font-size: 70px;">
        <li>Subclass inherits all <b>state</b> and <b>behavior</b></li>
        <li>Subclass has all <code>public</code> and <code>protected</code> attributes and methods of superclass</li>
        <li>Subclass constructor can call <code>super()</code> constructor</li>
        <li>Subclass can <b>override</b> superclass methods with new code</li>
    </ul>
</section>
<section>
    <pre class="java stretch"><code>public class Canine {
    protected name;
    public void bark() {
        //code here
    }
}<br>
public class Dog extends Canine {
    protected owner;
    public void pet() {
        //code here
    }
}<br>
public class GuideDog extends Dog {
    protected trainer;
    public void guide() {
        //code here
    }
}</code></pre>
</section>
<section>
    <h6>Subclass has all Superclass behaviors</h6>
    <pre class="java"><code>GuideDog lassie = new GuideDog();
lassie.bark();
lassie.pet();
lassie.guide();</code></pre>
</section>
<section>
    <h3>Multiple Inheritance</h3>
    <p>Classes in Java can only<br>directly inherit from one superclass</p>
    <p>Classes may implement<br>any number of interfaces</p>
</section>