---
title: "Web APIs"
weight: 10
pre: "2. "
---
{{% youtube G3LqkMXfW6A %}}

As the name implies, a web API is simply an interface for accessing and modifying resources stored on a web server. So, from a certain point of view, we could think of the basic HTTP itself as a web API. However, traditionally web APIs are meant to be built on top of HTTP itself -- HTTP defines how web servers and web clients can communicate in general, but a web API uses additional information in the structure of the request, such parameters included as part of the URL or the body of the request, to specify exactly what resources should be affected and the action to be performed on those resources.

Web APIs are popular because they decouple the resources stored on the server from the client-side application that is designed to only interact with the web API. So, if an organization has some data or resources they'd like to make available, they can create a web API to make those resources available, and then other developers can build tools that interface with that web API to use those resources in some unique way.

![Web API Graphic](../../images/18/api.png)^[https://commons.wikimedia.org/w/index.php?title=File:Open-APIs-v5.png&oldid=492355805]

## Example - Communication Platforms

A great example of this can be found by looking at online tools such as [Twilio](https://www.twilio.com/) and [Discord](https://discord.com/). Both of these tools are communication platforms -- Twilio focuses on communication between a company and its customers and clients, while Discord is more focused on providing a chat and discussion platform for social groups. 

What makes these companies similar is that they both provide a very robust web API for interacting with their platforms. In the case of [Twilio](https://www.twilio.com/docs/api), the web API is the only way to really use their product, which is primarily targeted at developers themselves. For [Discord](https://discord.com/developers/docs/intro), they provide the core application for interacting with their platform that is used by most users, but their web API allows developers to make use of their platform in a variety of unique ways. Of course, these are just two examples from a very large number of web APIs available on the internet today, and that number continues to grow.

##### Twilio - Sending Text Messages

Let's look at a quick example from the [Twilio API Documentation](https://www.twilio.com/docs/sms/send-messages), sending an SMS, or [Short Message Service](https://en.wikipedia.org/wiki/SMS), message to a particular phone number. Many users would commonly refer to these as "text messages."

First, let's look at how to send this message using `curl` - a Linux terminal tool for making raw HTTP requests to web servers and web APIs:

```bash
EXCLAMATION_MARK='!'
curl -X POST https://api.twilio.com/2010-04-01/Accounts/$TWILIO_ACCOUNT_SID/Messages.json \
--data-urlencode "Body=Hi there$EXCLAMATION_MARK" \
--data-urlencode "From=+15017122661" \
--data-urlencode "To=+15558675310" \
-u $TWILIO_ACCOUNT_SID:$TWILIO_AUTH_TOKEN
```

Even without knowing exactly how `curl` works, we should be able to learn quite a bit about how this API works just by examining this command. First, we can guess that it is using an HTTP POST request, based on the `-X POST` portion of the command. Following that, we see the URL `https://api.twilio.com/2010-04-01/Accounts/$TWILIO_ACCOUNT_SID/Messages.json`, which gives us the **endpoint** for this command. Just like programming APIs include classes and functions that we can call and get return values from through message passing, web APIs have endpoints which we can send requests to and receive responses. In fact, web APIs really reinforce the concept that "message passing" and calling a function are similar. 

Below that, we see three lines of data prefixed by `--data-urlencode`. We can guess that these three lines construct the data that will be sent as the payload of the HTTP POST request. In fact, this data is structured nearly identically to the data that is generated when an HTML form is submitted using a POST request and the `application/x-www-form-urlencoded` encoding method.

Finally, the last portion `-u $TWILIO_ACCOUNT_SID:$TWILIO_AUTH_TOKEN` provides the user authentication information for this request. The first part before the colon `:` is the username, and the second part is the password. So, when this information is sent, it will also include a username and password to authenticate the request. That way, Twilio will know exactly which user is sending the request, and it prevents unauthorized users from sending spam text messages through their system.

Finally, notice that many parts of this command are prefixed by a dollar sign `$`. This simply means that those are meant to be variables, so it is up to the developer to replace those variables with the correct values, either by setting them as shown on the first line, or by some other means. 

So, it looks like this `curl` command is just sending an HTTP POST request to a specific endpoint in the Twilio API. It will include three data elements, as well as some authentication information.

##### Twilio - Response

When we send that request to Twilio, their documentations says we should expect a response that looks like the following:

```json
{
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
}
```

We won't dig too deeply into this response, but we can easily see that it includes lots of useful information about the request itself. We can see when it was sent, what it contained, any if it caused any errors, all directly from the response. The [Twilio API Documentation](https://www.twilio.com/docs/sms/send-messages) describes each of these in detail. 

{{% notice tip %}}

# Other Programming Languages

With this little bit of information, it is very simple to figure out how to send these requests from nearly any programming language. As long as it can construct a valid HTTP POST request and receive the response, it can be used. Thankfully, Twilio has also developed many helper libraries for different programming languages that greatly simplify this process. 

We'll mostly be looking at these web APIs without digging into how to use them from a specific programming language, but you should understand that it can be easily done in just about any language you choose. 

{{% / notice %}}
