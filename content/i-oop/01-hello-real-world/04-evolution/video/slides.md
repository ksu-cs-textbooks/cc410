---
type: "reveal"
---
<section>
	<h2>Early Code (Fortran)</h2>
	<img class="plain stretch" src="/cc410/images/1/410fortran.png">
</section>
<section>
	<h2>Spaghetti Code</h2>
	<pre><code>1 i=0
2 i=i+1
3 PRINT i; "squared=";i*i
4 IF i>=100 THEN GOTO 6
5 GOTO 2
6 PRINT "Program Completed."
7 END</code></pre>
	<p class="imagecredit">Credit: <a href="https://en.wikipedia.org/wiki/Spaghetti_code">Wikipedia</a></p>
</section>
<section>
	<h4>GOTO Considered Harmful - Dijkstra</h4>
	<img class="plain stretch" src="/cc410/images/1/410goto.png">
	<p class="imagecredit">Image Credit: <a href="https://xkcd.com/292/">XKCD</a></p>
</section>
<section>
	<h4>Structured Programming Paradigm</h4>
	<p>Programs only consist of:</p>
	<ul>
		<li>Sequences (Blocks of Statements)</li>
		<li>Selection (Conditionals)</li>
		<li>Iteration (Loop & Recursion)</li>
		<li><i>Subroutines (Functions)</i></li>
	</ul>
</section>
<section>
	<h2>Sequences</h2>
	<img class="plain stretch" src="/cc410/images/1/410sequence.png">
</section>
<section>
	<h2>Selection</h2>
	<img class="plain stretch" src="/cc410/images/1/410select.png">
</section>
<section>
	<h2>Iteration</h2>
	<img class="plain stretch" src="/cc410/images/1/410loop.png">
</section>
<section>
	<h2>Subroutines</h2>
	<img class="plain stretch" src="/cc410/images/1/410function.png">
</section>
<section>
	<h2>Structured Code</h2>
	<pre><code>1 FOR i=1 TO 100
2     PRINT i;"squared=";i*i
3 NEXT i
4 PRINT "Program Completed."
5 END</code></pre>
	<p class="imagecredit">Credit: <a href="https://en.wikipedia.org/wiki/Spaghetti_code">Wikipedia</a></p>
</section>
<section>
	<h4>Object-Oriented Paradigm</h4>
	<p>Organize programs to represent real or theoretical "objects" that use:</p>
	<ul>
		<li>Encapsulation (Attributes)</li>
		<li>Message Passing (Calling Methods)</li>
		<li>Dynamic Dispatch (Object Chooses Code)</li>
	</ul>
</section>
<section>
	<h2>Object-Oriented Code</h2>
	<pre style="font-size:35px"><code>class Squares{
	public void printSquares(int limit){
		for(int i = 0; i < limit; i++){
			System.out.println("squared=" + (i*i));
		}
		System.out.println("Program Completed.");
	}
}</code></pre>
</section>
<section>
	<p>We will use only object-oriented, structured code in this class.<br><br>It will help us write programs that are easier for others to understand.</p>
</section>
