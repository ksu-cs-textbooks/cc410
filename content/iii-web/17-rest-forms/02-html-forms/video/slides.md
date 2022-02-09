---
type: "reveal"
hidden: true
---

<section>
    <h3>HTML Forms</h3>
    <ul>
        <li>Collect Information from User</li>
        <li>HTML <code>&lt;input&gt;</code> Elements</li>
        <li>Similar to GUI Elements</li>
        <li>Send Data to Web Server/Application</li>
    </ul>
</section>
<section>
    <h3>Simple Input Form</h3>
    <pre><code>&lt;form action="/search" method="POST">
    &lt;label for="keywords">Search Keywords&lt;/label>
    &lt;input type="text" id="keywords" name="keywords">
    &lt;button type="submit">Search&lt;/button>
&lt;/form></code></pre>
    <p>displays as</p>
    <img class="plain stretch" src="/images/17/410_17_form.png">
</section>
<section>
    <h3>Input Elements</h3>
    <ul>
        <li><code>text</code> - text input</li>
        <li><code>checkbox</code> - boolean checkbox</li>
        <li><code>date</code> - date picker</li>
        <li><code>file</code> - file chooser</li>
        <li><code>number</code> - numerical input</li>
        <li><code>password</code> - password field</li>
        <li><code>select</code> - drop-down box</li>
        <li><code>submit</code> - submit button</li>
    </ul>
</section>
<section>
    <h3>Related Elements</h3>
    <ul>
        <li><code>label</code> - caption for element</li>
        <li><code>fieldset</code> - group similar fields</li>
        <li><code>legend</code> - caption for fieldset</li>
    </ul>
</section>
<section>
    <h3>Form Submission</h3>
    <ol>
        <li>User Submits Form</li>
        <li>Data Encoded by Browser</li>
        <li>Data Sent to Server via HTTP</li>
        <li>Server Decodes Data</li>
        <li><i>Server Validates Data</i></li>
        <li>Response Returned via HTTP</li>
    </ol>
</section>
<section>
    <h3>HTML Form Example</h3>
    <pre><code class="stretch html" style="font-size: 20px; line-height: 27px">
    &lt;form action="/customitems" method="POST" >
        &lt;div class="form-row">
            &lt;div class="col form-group">
                &lt;label for="name">Name&lt;/label>
                &lt;input type="text" class="form-control" id="name" name="name" value="">
            &lt;/div>
        &lt;/div>
        &lt;div class="form-row">            
            &lt;div class="col form-group">
                &lt;label for="name">Price&lt;/label>
                &lt;input type="number" min="0" step="0.01" class="form-control" id="price" name="price" value="0.0">
            &lt;/div>
        &lt;/div>
        &lt;div class="form-row">
            &lt;div class="col form-group">
                &lt;label for="name">Calories&lt;/label>
                &lt;input type="number" min="0" step="1" class="form-control" id="calories" name="calories" value="0">
            &lt;/div>
        &lt;/div>
        &lt;button type="submit" class="btn btn-primary">Submit&lt;/button>
    &lt;/form>
    </code></pre>
</section>
<section>
    <h3>Rendered Form</h3>
    <img class="plain stretch" src="/images/17/410_17_customform.png">
</section>
<section>
    <h3>Developer Tools</h3>
    <img class="plain stretch" src="/images/17/410_17_devtools.png">
</section>
<section>  
    <h3>HTTP POST Request</h3>
    <img class="plain stretch" src="/images/17/410_17_devtools_1.png">
</section>
<section>
    <h3>HTTP Headers</h3>
    <img class="plain stretch" src="/images/17/410_17_devtools_2.png">
</section>
<section>
    <h5>Parsed Data</h5>
    <img class="plain" style="width: 60%" src="/images/17/410_17_devtools_3.png">
    <h5>Encoded Data</h5>
    <img class="plain" style="width: 60%" src="/images/17/410_17_devtools_4.png">
</section>