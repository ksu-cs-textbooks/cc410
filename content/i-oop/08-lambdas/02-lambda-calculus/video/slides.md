---
type: "reveal"
hidden: true
---
<section>
    <h3>Alonzo Church</h3>
    <img class="plain stretch" src="/cc410/images/8/410_8_church_wiki.jpg">
    <p class="imagecredit">Image Credit: <a href="https://en.wikipedia.org/wiki/File:Alonzo_Church.jpg">Wikipedia</a></p>
</section>
<section>
    <h3>Lambda Calculus</h3>
    <ul>
        <li>Introduced in 1930</li>
        <li>Used to describe computation</li>
        <li>Can be executed by any Turing machine</li>
        <li>Built around mathematical functions</li>
    </ul>
</section>
<section>
    <h3>Programming Paradigms</h3>
    <img class="plain stretch" src="/cc410/images/8/410_8_paradigms.svg">
</section>
<section>
    <h6>Functions as First-Class Citizens</h6>
    <p>can store in variables<br>and use as arguments</p>
    <h6 class="fragment" data-fragment-index="1">Higher Order Functions</h6>
    <p class="fragment" data-fragment-index="1">accept other functions as input</p>
</section>
<section>
    <h3>Imperative</h3>
    <pre class="js"><code>const numList = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
let result = 0;
for (let i = 0; i < numList.length; i++) {
    if (numList[i] % 2 === 0) {
        result += numList[i] * 10;
    }
}</code></pre>
<p class="fragment" style="font-size: 70px">result = 20 -> 60 -> 120 -> 200 -> 300</p>
</section>
<section>
    <h3>Functional</h3>
    <pre class="js"><code>const result = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        .filter(n => n % 2 === 0)
        .map(a => a * 10)
        .reduce((a, b) => a + b);</code></pre>
<p class="fragment">[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]</p>
</section>
<section>
    <h3>Functional</h3>
    <pre class="js"><code>const result = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        .filter(n => n % 2 === 0)
        .map(a => a * 10)
        .reduce((a, b) => a + b);</code></pre>
<p>[2, 4, 6, 8, 10]</p>
</section>
<section>
    <h3>Functional</h3>
    <pre class="js"><code>const result = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        .filter(n => n % 2 === 0)
        .map(a => a * 10)
        .reduce((a, b) => a + b);</code></pre>
<p>[20, 40, 60, 80, 100]</p>
</section>
<section>
    <h3>Functional</h3>
    <pre class="js"><code>const result = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        .filter(n => n % 2 === 0)
        .map(a => a * 10)
        .reduce((a, b) => a + b);</code></pre>
<p>[60, 140, 100]</p>
</section>
<section>
    <h3>Functional</h3>
    <pre class="js"><code>const result = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        .filter(n => n % 2 === 0)
        .map(a => a * 10)
        .reduce((a, b) => a + b);</code></pre>
<p>[200, 100]</p>
</section>
<section>
    <h3>Functional</h3>
    <pre class="js"><code>const result = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        .filter(n => n % 2 === 0)
        .map(a => a * 10)
        .reduce((a, b) => a + b);</code></pre>
<p>300</p>
</section>