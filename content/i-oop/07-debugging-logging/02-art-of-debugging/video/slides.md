---
type: "reveal"
hidden: true
---
<section>
    <h3>The Art of Debugging</h3>
    <p>Credit to <a href="https://remysharp.com/2015/10/14/the-art-of-debugging">Remy Sharp</a></p>
</section>
<section>
    <h3>1 - Reproduce the Bug</h3>
    <ul>
        <li>When does it happen?</li>
        <li>What actions does the user take?</li>
        <li>How is the system configured?</li>
        <li>What is the minimum set of steps?</li>
        <li><b>Can we make it happen consistently?</b></li>
    </ul>
</section>
<section>
    <h3>2 - Find the Bug</h3>
    <ul>
        <li>Observe <i>state</i> and <b>behavior</b></li>
        <li>Use print statements, logger, or debugger</li>
        <li>Narrow down scope</li>
        <li>Identify specific methods and arguments/data</li>
        <li>Verify via unit tests</li>
    </ul>
</section>
<section>
    <h3>3- Fix the Bug</h3>
    <ul>
        <li>Use unit tests to trigger problem</li>
        <li>Carefully edit code to fix bug</li>
        <li>Test fix</li>
        <li>Perform regression tests</li>
        <li>Look for any related issues</li>
        <li>Commit and deploy fixed code</li>
    </ul>
</section>
