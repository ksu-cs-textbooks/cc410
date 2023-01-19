---
type: "reveal"
hidden: true
---
<section>
    <h3>Iterator Pattern</h3>
    <ul>
        <li>Make a Class Iterable</li>
        <li>Use with For Each Loops</li>
        <li>Act Like a Collection</li>
    </ul>
</section>
<section>
    <h3>Iterator</h3>
    <ul>
        <li>Class to Keep Track of Location</li>
        <li>Typically Includes <code>next</code> Method</li>
        <li>Defined Way To Find End</li>
        <li>Other Methods May Be Included</li>
    </ul>
</section>
<section>
    <h3>Iterable Interface</h3>
    <pre><code class="java stretch">class CrayonBox implements Iterable[Crayon]:<br>
    List[Crayon] contents<br>
    function addCrayon(Crayon c):
        contents.add(c)<br>
    function getIterator():
        return contents.getIterator()<br>
    function get(int i):
        return contents[i]<br>
    function contains(Crayon c):
        return contents.contains(c)<br>
    function size():
        return contents.size()
    </code></pre>
</section>
<section>
    <h3>Using an Iterable</h3>
    <pre><code class="java" style="font-size:31px">class Main:<br>
    function main():
        CrayonBox box = CrayonBoxFactorySingleton.getInstance().getBox(16)
        //get iterator and print
        for Crayon c in box:
            print(c.color)
    </code></pre>
</section>
<section>
    <h3>Iterator Pattern</h3>
    <ul>
        <li>Offload Most of Work to Underlying Collection</li>
        <li>Implement Helpful Collection Methods</li>
        <li><i>Don't Reinvent the Wheel</i></li>
    </ul>
</section>
<section>
    <h3>Template Method Pattern</h3>
    <ul>
        <li>Define Method Structure in Parent</li>
        <li>Override Portions in Child</li>
        <li>Same Basic Steps, Different Details</li>
    </ul>
</section>
<section>
    <h3>Parent Class</h3>
    <pre><code class="java stretch">abstract class Recipe:<br>
    function bakeSomething():
        gatherIngredients()
        combineIngredients()
        putInOven()<br>
    abstract function gatherIngredients()
    abstract function combineIngredients()
    abstract function putInOven()
    </code></pre>
</section>
<section>
    <h3>Child Class</h3>
    <pre><code class="java stretch">class Cake inherits Recipe:<br>
    function gatherIngredients():
        getFlour()
        getSugar()
        getEggs()
        getButter()<br>
    function combineIngredients()
        creamEggsAndButter()
        addSugar()
        addFlour()<br>
    function putInOven()
        setOven(350)
        setTimer(30)
    </code></pre>
</section>