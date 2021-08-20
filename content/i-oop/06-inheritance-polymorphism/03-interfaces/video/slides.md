---
type: "reveal"
hidden: true
---
<section>
    <h2>Interface</h2>
    <ul>
        <li>Determines which messages can be received by an object.</li>
        <li class="fragment">Defines the behaviors that object can perform.</li>
        <li class="fragment">Lists the methods that object contains.</li>
    </ul>
</section>
<section>
    <h6>If two objects accept the same set of messages, they have the same <i>interface</i>.</h6>
    <br>
    <h6 class="fragment">In Java, this is done through inheritance and interfaces.</h6>
    <br>
    <h6 class="fragment">Python uses <i>duck typing</i>, but we'll create formal interfaces.</h6>
</section>
<section>
    <h3>IDrivable Interface</h3>
    <p>Classes must include a method called<br><code>drive</code><br>that returns the magnitude of the drive.</p>
</section>
<section>
    <h3>IDrivable Interface</h3>
    <ul>
        <li><code>Car.drive()</code></li>
        <li><code>Plane.drive()</code></li>
        <li><code>GolfBall.drive()</code></li>
        <li><code>Fundraiser.drive()</code></li>
    </ul>
    <p class="fragment">All implement the interface, so all can be treated like IDrivable objects!</p>
</section>
<section>
    <h3>Multiple Inheritance</h3>
    <pre class="java"><code>public class Car implements IDrivable, 
        IHeatable, IPlayable {
    // code here
}</code></pre>
    <p>Java uses interfaces for multiple inheritance</p>
</section>