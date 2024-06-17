---
type: "reveal"
hidden: true
---
<section>
    <h3>Terminology Disclaimer</h3>
    <p>These terms are loosely defined and used interchangeably.</p>
    <p>Most of the time, <b>mock</b> is common for all types.</p>
</section>
<section>
    <img class="plain stretch" src="/cc410/images/13/410_13_stub.png">
    <p class="imagecredit">Image Credit: <a href="https://blog.pragmatists.com/test-doubles-fakes-mocks-and-stubs-1a7491dfa3da">Pragmatists Blog</a></p>
</section>
<section>
    <h3>Stub</h3>
    <ul>
        <li><i>method stub</i></li>
        <li>Shortcut implementation of a method</li>
        <li>Typically returns hard-coded data</li>
        <li>Mimic external function calls and possible results</li>
        <li>Test error states as well as expected states</li>
    </ul>
</section>
<section>
    <img class="plain stretch" src="/cc410/images/13/410_13_fake.png">
    <p class="imagecredit">Image Credit: <a href="https://blog.pragmatists.com/test-doubles-fakes-mocks-and-stubs-1a7491dfa3da">Pragmatists Blog</a></p>
</section>
<section>
    <h3>Fake</h3>
    <ul>
        <li><i>fake object</i></li>
        <li>Mimic a real object</li>
        <li>Satisfy type checker</li>
        <li>Contain/Return default data</li>
        <li>Simple implementations</li>
    </ul>
</section>
<section>
    <img class="plain stretch" src="/cc410/images/13/410_13_mock.png">
    <p class="imagecredit">Image Credit: <a href="https://blog.pragmatists.com/test-doubles-fakes-mocks-and-stubs-1a7491dfa3da">Pragmatists Blog</a></p>
</section>
<section>
    <h3>Mock</h3>
    <ul>
        <li><i>test spy</i></li>
        <li>Mimic a real object</li>
        <li>Track all operations</li>
        <li>Verify that our code calls other code</li>
        <li>See side effects of our code beyond return values</li>
    </ul>
</section>