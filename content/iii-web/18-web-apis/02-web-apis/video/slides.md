---
type: "reveal"
hidden: true
---

<section>
    <h3>Web APIs</h3>
    <ul>
        <li>Interface to Web Application</li>
        <li>Access & Modify Server Resources</li>
        <li>Defines Endpoints, Parameters, Responses</li>
        <li>Built on HTTP</li>
    </ul>
</section>
<section>
    <h3>Example - Twilio</h3>
    <pre class=""><code class="sh">EXCLAMATION_MARK='!'
curl -X POST https://api.twilio.com/2010-04-01/Accounts/$TWILIO_ACCOUNT_SID/Messages.json \
--data-urlencode "Body=Hi there$EXCLAMATION_MARK" \
--data-urlencode "From=+15017122661" \
--data-urlencode "To=+15558675310" \
-u $TWILIO_ACCOUNT_SID:$TWILIO_AUTH_TOKEN</code></pre>
</section>
<section>
    <h3>Response</h3>
    <pre class="stretch" style="font-size: 29px"><code class="js">{
    "account_sid": "ACXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
    "api_version": "2010-04-01",
    "body": "Hi there!",
    "date_created": "Thu, 30 Jul 2015 20:12:31 +0000",
    "date_sent": "Thu, 30 Jul 2015 20:12:33 +0000",
    "date_updated": "Thu, 30 Jul 2015 20:12:33 +0000",
    "direction": "outbound-api",
    "error_code": null,
    "error_message": null,
    "from": "+14155552345",
    "messaging_service_sid": null,
    "num_media": "0",
    "num_segments": "1",
    "price": null,
    "price_unit": null,
    "sid": "SMXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
    "status": "sent",
    "subresource_uris": {
        "media": "/2010-04-01/Accounts/ACXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX/Messages/SMXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX/Media.json"
    },
    "to": "+14155552345",
    "uri": "/2010-04-01/Accounts/ACXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX/Messages/SMXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX.json"
}</code></pre>
</section>
<section>
    <div style="float: right; width: 50%">
        <h3>REST</h3>
        <ul>
            <li>Arch. Style</li>
            <li>JSON, HTML, etc.</li>
            <li>HTTP</li>
            <li>Suggested Interaction Model</li>
        </ul>
    </div>
    <div style="float: left; width: 50%">
        <h3>SOAP</h3>
        <ul>
            <li>Web Standard</li>
            <li>XML</li>
            <li>Structured</li>
            <li>No Interaction Model</li>
        </ul>
    </div>
</section>
<section>
    <h3>Documentation</h3>
    <ul>
        <li>RESTful API DLs</li>
        <li>Endpoints</li>
        <li>Parameters</li>
        <li>Responses</li>
    </ul>
</section>
<section>
    <h3>OpenAPI Example</h3>
    <pre class="stretch" style="font-size: 20px"><code class="yaml">
paths:
    # Whole board operations
    /board:
        get:
            summary: Get the whole board
            description: Retrieves the current state of the board and the winner.
            responses:
                "200":
                    description: "OK"
                    content:
                        $ref: "#/components/schemas/status"
schemas:
    status:
        type: object
        properties:
        winner:
            $ref: "#/components/schemas/winner"
        board:
            $ref: "#/components/schemas/board"
    board:
        type: array
        maxItems: 3
        minItems: 3
        items:
            type: array
            maxItems: 3
            minItems: 3
            items:
            $ref: "#/components/schemas/mark"
    winner:
        type: string
        enum: [".", "X", "O"]
        description: Winner of the game. `.` means nobody has won yet.
        example: "."
    </code></pre>
</section>
<section>
    <h3>Authentication</h3>
    <ul>
        <li>HTTP Authentication</li>
        <li>API Keys</li>
        <li>OAuth</li>
    </ul>
</section>