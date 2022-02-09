---
type: "reveal"
hidden: true
---

<section>
    <h3>HTTP</h3>
    <ul>
        <li>Hypertext Transfer Protocol</li>
        <li>How Web Servers & Web Browsers Interact</li>
        <li>Follows a Request-Response Model</li>
        <li>Text-Based Protocol</li>
    </ul>
</section>
<section>
    <img class="plain stretch" src="/images/16/410_16_http.png">
</section>
<section>
    <h3>HTTP Request</h3>
    <pre><code class="plaintext">GET / HTTP/1.1</code></pre>
    <h3>HTTP Response</h3>
    <pre class="stretch" style="font-size: 35px"><code class="nohighlight">HTTP/1.1 200 OK
Date: Wed, 16 Jan 2019 15:39:33 GMT
Expires: -1
Cache-Control: private, max-age=0
Content-Type: text/html; charset=ISO-8859-1
P3P: CP="This is not a P3P policy! See g.co/p3phelp for more info."
Server: gws
X-XSS-Protection: 1; mode=block
X-Frame-Options: SAMEORIGIN
Set-Cookie: 1P_JAR=2019-01-16-15; expires=Fri, 15-Feb-2019 15:39:33 GMT; path=/; domain=.google.com
Set-Cookie: NID=154=XyALfeRzT9rj_55NNa006-Mmszh7T4rIp9Pgr4AVk4zZuQMZIDAj2hWYoYkKU6Etbmjkft5YPW8Fens07MvfxRSw1D9mKZckUiQ--RZJWZyurfJUyRtoJyTfSOMSaniZTtffEBNK7hY2M23GAMyFIRpyQYQtMpCv2D6xHqpKjb4; expires=Thu, 18-Jul-2019 15:39:33 GMT; path=/; domain=.google.com; HttpOnly
Accept-Ranges: none
Vary: Accept-Encoding<br>
&lt;!doctype html&gt;...</code></pre>
</section>
<section>
    <h3>Demo</h3>
</section>
<section>
    <h3>Web Servers</h3>
    <ul>
        <li>Convert Request Path to File Path</li>
        <li>Load and Respond with File Contents</li>
        <li>Apache, IIS, nginx</li>
    </ul>
</section>
<section>
    <h3>Dynamic Web Pages</h3>
    <ul>
        <li>Examine Request Path</li>
        <li>Generate Text on the Fly</li>
        <li>Respond with Generated Text</li>
        <li>Improved with Templates</li>
    </ul>
</section>