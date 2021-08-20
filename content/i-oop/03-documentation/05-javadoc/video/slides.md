---
type: "reveal"
hidden: true
---
<section>
	<h3>Javadoc</h3>
    <ol>
        <li>Summary Fragment</li>
        <li>Additional Paragraphs</li>
        <li>Tags</li>
    </ol>
</section>
<section>
    <h3>Tags</h3>
    <p>Class:</p>
    <ul>
        <li>@author</li>
        <li>@version</li>
    </ul>
    <p>Method:</p>
    <ul>
        <li>@param</li>
        <li>@return</li>
        <li>@throws</li>
    </ul>
</section>
<section>
    <h3>Class Comment</h3>
    <pre class="stretch" style="font-size:40px"><code>/**
 * Represents a square shape.
 *
 * &lt;p>This class represents a square, 
 * storing the side length only.
 *
 * @author Russell Feldhausen russfeld@ksu.edu
 * @version 0.1
 */
public class Square {</code></pre>
</section>
<section>
    <h3>Method Comment</h3>
    <pre class="stretch" style="font-size:35px"><code>/**
 * Calculates and returns the area of the square not in the circle.
 *
 * &lt;p>This method will place the center of the circle at the center of
 * the square and compute the difference in area. 
 *
 * @param circle     a circle shape
 * @return           the difference in area
 * @throws IllegalArgumentException    if the circle is 
 *                                     larger than the square
 */
public double areaDifference(Circle circle){</code></pre>
</section>
<section>
    <h3>Attribute Comment</h3>
    <pre style="font-size:40px"><code>/** The side length of the square. */
private int length;</code></pre>
</section>