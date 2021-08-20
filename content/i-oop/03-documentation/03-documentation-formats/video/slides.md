---
type: "reveal"
hidden: true
---
<section>
	<h3>Documentation Formats</h3>
    <ul>
        <li>HTML</li>
        <li>Markdown</li>
        <li>XML</li>
    </ul>
</section>
<section>
    <h3>HTML</h3>
    <pre><code class="html">&lt;p>This code finds the minimum value in an array&lt;/p>
&lt;pre>&lt;code>int min = nums[0];
for(int i = 0; i < nums.length; i++){
  if(nums[i] < min){
    min = nums[i];
  }
}&lt;/code>&lt;/pre></code></pre>
</section>
<section>
    <h3>HTML</h3>
    <p>Pros:</p>
    <ul>
        <li>Flexible & Style-able</li>
        <li>Read Directly in Browser</li>
    </ul>
    <p>Cons:</p>
    <ul>
        <li>Lots of Boilerplate</li>
        <li>Difficult to Maintain</li>
    </ul>
</section>
<section>
    <h3>Markdown</h3>
    <pre><code class="markdown">This code finds the minimum value in `array`
```java
for(int i = 0; i < nums.length; i++){
  if(nums[i] < min){
    min = nums[i];
  }
}
```</code></pre>
</section>
<section>
    <h3>Markdown</h3>
    <p>Pros:</p>
    <ul>
        <li>Easy to Read & Write</li>
        <li>Supported in GitHub</li>
    </ul>
    <p>Cons:</p>
    <ul>
        <li>Requires Rendering</li>
        <li>Less Flexible</li>
    </ul>
</section>
<section>
    <h3>XML</h3>
    <pre><code class="xml">&lt;student>
    &lt;firstName>Willie&lt;/firstName>
    &lt;lastName>Wildcat&lt;/lastName>
    &lt;wid>8888888&lt;/wid>
    &lt;degreeProgram>BCS&lt;/degreeProgram>
&lt;/student></code></pre>
</section>
<section>
    <h3>XML</h3>
    <p>Pros:</p>
    <ul>
        <li>Easy to Parse</li>
        <li>Nearly Universal</li>
    </ul>
    <p>Cons:</p>
    <ul>
        <li>Verbose</li>
        <li>Better for Data</li>
    </ul>
</section>