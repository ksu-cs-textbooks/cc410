---
type: "reveal"
hidden: true
---
<section>
	<h3>Python Docstrings</h3>
    <ol>
        <li>Summary Line</li>
        <li>Additional Paragraphs</li>
        <li>Optional Sections</li>
    </ol>
</section>
<section>
    <h3>Sections</h3>
    <p>File:</p>
    <ul>
        <li style="font-size:65px; line-height:70px">Author</li>
        <li style="font-size:65px; line-height:70px">Version</li>
    </ul>
    <p>Class:</p>
    <ul>
        <li style="font-size:65px; line-height:70px">Attributes</li>
    </ul>
    <p>Method:</p>
    <ul>
        <li style="font-size:65px; line-height:70px">Args</li>
        <li style="font-size:65px; line-height:70px">Returns</li>
        <li style="font-size:65px; line-height:70px">Raises
    </ul>
</section>
<section>
    <h3>File Comment</h3>
    <pre class="python"><code>"""Implements a Square shape.<br>
This file contains code for the Square shape class.<br>
Author: Russell Feldhausen russfeld@ksu.edu
Version: 0.1
"""</code></pre>
</section>
<section>
    <h3>Class Comment</h3>
    <pre class="python stretch"><code>class Square:
    """Represents a Square shape.<br>
    This class represents a square,
    storing the side length only.<br>
    Attributes:
        length: the side length of the square
    """</code></pre>
</section>
<section>
    <h3>Method Comment</h3>
    <pre class="python stretch"><code>def area_difference(circle: Circle) -> float:
    """Calculates the area of the square not in the circle.<br>
    This method will place the center of the circle at the 
    center of the square and compute the difference in area.<br>
    Args:
        circle: a circle shape<br>
    Returns:
        the difference in area as a float<br>
    Raises:
        ValueError: if the circle is larger than the square
    """</code></pre>
</section>