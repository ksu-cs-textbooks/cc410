---
type: "reveal"
hidden: true
---
<section>
    <h3>Adapter Pattern</h3>
    <ul>
        <li>Make a Class Fit an Interface</li>
        <li>Simplify Complex Interfaces</li>
        <li>Translate Data Types & Method Names</li>
    </ul>
</section>
<section>
    <h3>Classes<h3>
    <pre><code class="java">class Fahrenheit:<br>
    function getTempFahrenheit():
        return this.temp
    </code></pre>
    <pre><code class="java">interface Celsius:<br>
    function getTempCelsius()
    </code></pre>
</section>
<section>
    <h3>Object Adapter</h3>
    <pre><code class="java" style="font-size:35px">class FahrenheitToCelsius implements Celsius:<br>
    Fahrenheit fahrenheitTemp<br>
    function getTempCelsius():
        return (fahrenheitTemp.getTempFahrenheit() - 32) * (5 / 9)
    </code></pre>
</section>
<section>
    <h3>Class Adapter</h3>
    <pre><code class="java" style="font-size:34px">class FahrenheitToCelsius inherits Fahrenheit implements Celsius:<br>
    function getTempCelsius():
        return (parent.getTempFahrenheit() - 32) * (5 / 9)
    </code></pre>
</section>
<section>
    <h3>Best Practices</h3>
    <ul>
        <li>Typically Encapsulation Preferred</li>
        <li>Limit API to Desired Methods</li>
        <li>Hide Underlying Types</li>
    </ul>
</section>