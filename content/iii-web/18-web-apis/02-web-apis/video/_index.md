---
title: "Introduction"
pre: "1. "
weight: 10
date: 2020-04-19T00:53:26-05:00
hidden: true
---

{{< youtube G3LqkMXfW6A >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

In this chapter, we're going to take a deeper look at web APIs and how they work. As you are probably already aware, a web API is an interface to a web application. It defines how we interact with the web server containing the resources of that application, and gives us the ability to access and even sometimes modify those resources. Typically the web API itself defines a set of endpoints, represented as URLs, that we can interact with. It is probably easiest to think of these endpoint URLs as individual functions that we can call on the server. In fact, if we recall that function calling is sometimes referred to as message passing, this analogy makes a lot of sense. In addition, the web API might define a set of parameters expected and the value to be returned, just like a function. Finally, most web APIs are built upon the HTTP protocol. In fact, if we think about it, HTTP itself could be thought of as a web API - it tells us how to interact with a server on the internet, and includes information about the types of requests we can send and the responses to expect.

A great example of a web API is provided by Twilio. Twilio is an online messaging platform used by many businesses to send messages to customers and clients. One of the big features of Twilio is the ability to send SMS, or text, messages. So, to send a text message using Twilio's web API, we could send it an HTTP POST request using this `curl` command. Even without really understanding what `curl` does and how it works, we can easily see what this is sending. It includes a few parameters in the data payload of the POST request that is sent to a particular URL endpoint, along with some authentication information to prove our identity.

When we send that request, we'll get a response that looks like this. This response contains all sorts of information about the message we just sent, helpfully formatted in JSON to make it easy to parse. We can then use this response information to tell our application what to do next. 

Most web APIs follow a RESTful architectural style today, but there is another standard we should quickly discuss. The Simple Object Access Protocol, or SOAP, was proposed in 1998 as a way to interact with web applications over the web. In fact, it is currently an accepted web standard through the World Wide Web Consortium, or W3C. So, unlike REST, which is just a style, SOAP actually has a defined protocol and standard message format. However, because it uses XML and doesn't define a standard model for interaction, many developers today have preferred the power and flexibility that comes from following the RESTful style instead of implementing the SOAP standard. 

Another major aspect of working with web APIs is documentation - if users cannot understand how to interface with the API, it isn't very useful. So, just like we have standards for documentation comments in our code that help us generate documentation for other developers, many description languages, or DLs, have arisen to document web APIs. Specifically, those DLs cover the endpoints, parameters, and expected responses of an API. In addition, they may include many helpful tools for not only generating user-readable documentation, but even generating code libraries that make it easy to interface with the API itself.

A great example of a web API description language is the OpenAPI Standard. This slide shows part of an OpenAPI Standard document for a web API for a Tic Tac Toe board game. At the top, we can see the endpoint `/board`, which will accept a GET request to get the state of the board and game's winner. If that request is valid and an HTTP 200 response is sent, we cn see that it sends a `status` schema back to the user. At the bottom of the file, we can see a list of the various schemas that could be used. We can think of these schemas just like the custom data types, or structs, that we learned about way back in the beginning of this course. It simply defines what attributes and data types we can expect to find in our JSON response.

Finally, let's also briefly talk about authentication. Many web APIs only allow registered users to access them, mostly to prevent abuse and to establish rate limits, requiring users who consume more resources to pay for additional access. In the past, this was mainly done by making use of the built-in HTTP authentication mechanism. However, that system sends the username and password in plain text, which can be intercepted by any malicious user. So, many APIs today instead rely on the concept of an API key - a long alphanumeric string of data that is given to a user to identify themselves. So, as long as the API key is properly included as part of the request, it will authenticate the user sending the request. Of course, just like HTTP authentication, these keys are sent along with the request in plain text, so it is highly recommended to use an encryption scheme such as the one used by HTTPS to access these web APIs. 

So, that's a quick overview of web APIs and some of the related concepts. The text in this chapter goes into a bit more detail on each aspect. In the next video, we'll perform a quick example, just to see what it takes to access a simple web API for testing. 

