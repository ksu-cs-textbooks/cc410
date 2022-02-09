---
type: "reveal"
hidden: true
---

<section>
    <h3>Using a Web API</h3>
    <ul>
        <li>Endpoint?</li>
        <li>Parameters?</li>
        <li>Authentication?</li>
        <li>Responses?</li>
    </ul>
</section>
<section>
    <h3>NASA APOD</h3>
    <img class="plain stretch" src="/images/18/410_18_apod.png">
    <p class="imagecredit">Image Credit: <a href="https://api.nasa.gov/">NASA</a></p>
</section>
<section>
    <h3>Access via CURL</h3>
    <pre style="font-size: 36px"><code>curl -X GET https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY</code></pre>
</section>
<section>
    <h3>JSON Response</h3>
    <pre style="font-size: 25px" class=""><code>{
    "date":"2021-04-19",
    "explanation":"What does the center of our galaxy look like?  In visible light, the ...",
    "hdurl":"https://apod.nasa.gov/apod/image/2104/GalacticCore_SpitzerSchmidt_6143.jpg",
    "media_type":"image",
    "service_version":"v1",
    "title":"The Galactic Center in Infrared",
    "url":"https://apod.nasa.gov/apod/image/2104/GalacticCore_SpitzerSchmidt_960.jpg"
}</code></pre>
</section>
<section>
    <h5>The Galactic Center in Infrared</h5>
    <img class="plain stretch" src="/images/18/410_18_apod.jpg">
    <p class="imagecredit">Image Credit: <a href="https://apod.nasa.gov/apod/ap210419.html">NASA</a></p>
</section>