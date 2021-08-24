---
title: "Using Web APIs"
pre: "2. "
weight: 20
date: 2020-04-19T00:53:26-05:00
hidden: true
---

{{< youtube 38AtVRSdYYE >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

Let's take a quick look at an example of using a web API to access some data. When using a web API, there a few things we need to know. First and foremost, we need to know the URL of the API endpoint we are going to access. Next, we need to know if it requires any parameters, and what they are. In addition, if the web API requires authentication for us to access it, we'll need to set that up and get our API key. Finally, we should know what kind of a response to expect, just so we can tell if it worked or if it is sending us an error message.

For this example, let's use the NASA astronomy picture of the day API. NASA has lots of fun and interesting APIs available for developers to use, and they are all free for testing and generally well documented. Here's the documentation for the astronomy picture of the day API, sometimes referred to as APOD. It gives us the URL of the endpoint, as well as the HTTP method we should use. Below are a set of parameters we can include in our request. It also includes the API key, which is a demo key that we can use for testing. There is also some information about the response we can expect, but it isn't shown here.

So, to make this request, we can just use the `curl` command to send a request to that endpoint, along with the URL:

```bash
curl -X GET https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY
```

As we can see, when we send that request, we get the following JSON response. In the response, we can see lots of information about the daily image, including the data, title, explanation, and a URL we can use to access the image itself. So, if we are writing an application to actually display the image, we can send this web API request, get this response, parse it, find the URL, and then send another HTTP GET request to that URL to access the image itself.

If everything goes correctly, we'll get this image! It's that simple.

That's a quick overview of what it actually looks like to interface with a web API. As you can see, it is very simple, and it can be done easily from any programming language that is able to send and receive HTTP messages. Hopefully you'll try it out yourself!

