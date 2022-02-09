---
type: "reveal"
hidden: true
---

<section>
    <h3>REST</h3>
    <ul>
        <li><i>Representational State Transfer</i></li>
        <li>Software Architectural Style</li>
        <li>Stateless!</li>
        <li>Standardized Operations</li>
        <li>Uniform Interface</li>
    </ul>
</section>
<section>
    <h3>Stateless</h3>
    <ul>
        <li>Application State Stored by each Client</li>
        <li>Resource State Stored by Server</li>
        <li>Server Does Not Track Application State</li>
        <li>Each Request is Independent!</li>
    </ul>
</section>
<section>
    <h3>Uniform Interface</h3>
    <ul>
        <li>Resource ID in Requests</li>
        <li>Easy Manipulation</li>
        <li>Self Descriptive Messages</li>
        <li>Hypermedia as the engine of application state (HATEOAS)<br>All Application Info from Server!</li>
    </ul>
</section>
<section>
    <h3>REST and CRUD</h3>
    <ul>
        <li>Read All - GET <code>/students</code></li>
        <li>Read One - GET <code>/students/{ID}</code></li>
        <li>Create - POST <code>/students</code></li>
        <li>Update - POST or PUT <code>/students/{ID}</code></li>
        <li>Destroy - DELETE <code>/students/[ID]</code></li>
    </ul>
</section>
<section>
    <h3>Example - Canvas!</h3>
    <img class="plain stretch" src="/images/17/410_17_canvas_1.png">
</section>
<section>
    <h3>Read All</h3>
    <img class="plain stretch" src="/images/17/410_17_canvas_2.png">
</section>
<section>
    <h3>Create</h3>
    <img class="plain" style="width: 100%" src="/images/17/410_17_canvas_3_1.png">
    <p>Payload</p>
    <img class="plain" style="width: 100%" src="/images/17/410_17_canvas_3_2.png">
</section>
<section>
    <h3>Read One</h3>
    <img class="plain stretch" src="/images/17/410_17_canvas_4.png">
</section>
<section>
    <h3>Edit</h3>
    <img class="plain stretch" src="/images/17/410_17_canvas_5.png">
</section>
<section>
    <h3>Update</h3>
    <img class="plain" style="width: 100%" src="/images/17/410_17_canvas_7_1.png">
    <p>Payload</p>
    <img class="plain" style="width: 100%" src="/images/17/410_17_canvas_7_2.png">
</section>
<section>
    <h3>Delete</h3>
    <img class="plain stretch" src="/images/17/410_17_canvas_6.png">
</section>