---
type: "reveal"
hidden: true
---
<section>
    <h3>Builder Pattern</h3>
    <ul>
        <li>Build Complex Objects</li>
        <li>Separate Object Creation from Other Code</li>
        <li>Reduce Complex Links Between Objects</li>
    </ul>
</section>
<section>
    <h3>Target Classes</h3>
    <pre><code class="java">class Crayon:<br>
    String color
    </code></pre>
    <pre><code class="java">class CrayonBox:<br>
    List[Crayon] contents<br>
    function addCrayon(Crayon c):
        contents.add(c)
    </code></pre>
</section>
<section>
    <h3>Builder Interface</h3>
    <pre><code class="java">interface CrayonBoxBuilder:<br>
    function buildBox()
    </code></pre>
</section>
<section>
    <h3>Builder Class</h3>
    <pre><code class="java stretch">class EightBoxBuilder implements CrayonBoxBuilder:<br>
    function buildBox():
        CrayonBox box = new CrayonBox()
        box.add(new Crayon("White"))
        box.add(new Crayon("Black"))
        box.add(new Crayon("Red"))
        box.add(new Crayon("Orange"))
        box.add(new Crayon("Yellow"))
        box.add(new Crayon("Green"))
        box.add(new Crayon("Blue"))
        box.add(new Crayon("Violet"))
    </code></pre>
</section>
<section>
    <h3>Builder Class</h3>
    <pre><code class="java stretch">class SixteenBoxBuilder implements CrayonBoxBuilder:<br>
    function buildBox():
        CrayonBox box = new CrayonBox()
        box.add(new Crayon("White"))
        box.add(new Crayon("Black"))
        box.add(new Crayon("Red"))
        box.add(new Crayon("Dark Red"))
        box.add(new Crayon("Blue Green"))
        box.add(new Crayon("Sunbeam"))
        box.add(new Crayon("Sky Blue"))
        box.add(new Crayon("Royal Purple"))
        box.add(new Crayon("Tan"))
        box.add(new Crayon("Brown"))
        box.add(new Crayon("Pink"))
        box.add(new Crayon("Eggshell"))
        ...
    </code></pre>
</section>
<section>
    <h3>Using the Builder</h3>
    <pre><code class="java" style="font-size:39px">class Main:<br>
    function main():
        CrayonBoxBuilder builder = new SixteenBoxBuilder()
        CrayonBox box = builder.buildBox()
    </code></pre>
</section>
<section>
    <h3>Factory Method Pattern</h3>
    <ul>
        <li>Get Objects By Name/Enum/ID</li>
        <li>Don't Need Underlying Type</li>
        <li>Easily Modify Factory Class</li>
        <li>Decoupled Architecture</li>
    </ul>
</section>
<section>
    <h3>Factory Method Class</h3>
    <pre><code class="java stretch" style="font-size:38px">class CrayonBoxFactory:<br>
    function getBox(int size):
        if size == 8:
            return new EightBoxBuilder().buildBox()
        else if size == 16:
            return new SixteenBoxBuilder().buildBox()
        else if size == 32:
            return new ThirtyTwoBoxBuilder().buildBox()
        else if size == 48:
            return new FortyEightBoxBuilder().buildBox()
        ...
    </code></pre>
</section>
<section>
    <h3>Using the Factory Method</h3>
    <pre><code class="java" style="font-size:39px">class Main:<br>
    function main():
        CrayonBoxFactory factory = new CrayonBoxFactory()
        CrayonBox box = factory.getBox(16)
    </code></pre>
</section>
<section>
    <h3>Singleton Pattern</h3>
    <ul>
        <li>Only One Instance</li>
        <li>Conserve Resources</li>
        <li>Globally Shared State</li>
        <li>Alternative to Static</li>
    </ul>
</section>
<section>
    <h3>Singleton Class</h3>
    <pre><code class="java stretch" style="font-size:38px">class CrayonBoxFactorySingleton:<br>
    static CrayonBoxFactorySingleton instance = null<br>
    static function getInstance():
        if instance is null:
            instance = new CrayonBoxFactorySingleton()
        return instance<br>
    function getBox(int size):
        if size == 8:
            return new EightBoxBuilder().buildBox()
        else if size == 16:
            return new SixteenBoxBuilder().buildBox() 
        ...
    </code></pre>
</section>
<section>
    <h3>Using the Factory Singleton</h3>
    <pre><code class="java" style="font-size:31px">class Main:<br>
    function main():
        CrayonBox box = CrayonBoxFactorySingleton.getInstance().getBox(16)
    </code></pre>
</section>
<section>
    <h3>Creational Patterns</h3>
    <ul>
        <li>Simplify Building Objects</li>
        <li>Reduce Links Between Classes</li>
        <li>Don't Repeat Yourself (DRY)</li>
        <li>Easily Add New Types of Items</li>
        <li><i>Think About Imports</i></li>
    </ul>
</section>