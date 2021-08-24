---
title: "HTTP and Servers"
pre: "2. "
weight: 20
date: 2020-03-31T00:53:26-05:00
hidden: true
---

{{< youtube TjtLgwuzrDM >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

Next, let's talk a bit about how we can actually send and receive data across the internet to make our web pages accessible to our users. For that, we use HTTP, or the Hypertext Transfer Protocol. This is another of the key web technologies first developed by Tim Berners-Lee as part of the World Wide Web. In short, HTTP defines how web servers and web browsers can communicate with each other, and it follows a request and response model. Interestingly, HTTP is defined as a text-based protocol, meaning that it can easily be read and interpreted without any special tools. 

This diagram shows the request and response model used by HTTP. Typically, a web browser sends a request to a web server, which includes information about the data desired. To access a web page itself, it would use a GET request, along with the URL, or uniform resource locator, of the page that it wants to access. Then, the web server will send an associated response giving the status of that request and the appropriate data. The response includes a status code indicating if the request was successful or if an error occurred, and it may also include data such as HTML if the request was valid. 

We can actually see this ourselves by using a program such as NetCat, or `nc` on most Linux systems, to perform an HTTP request. An HTTP request can be as simple as the top line shown here. We first have our HTTP command, in this case GET, followed by the path of the page that is requested. We also include `HTTP/1.1`, which specifies the version of the HTTP protocol to be used. At the end of the request, we include a blank line to show that the request has ended. Then, the web server will respond with some HTTP headers about the request, including the status code on the first line. On this slide, we see an actual response from a Google web server!

In fact, we can try to replicate this real quick. Let's try an example. 

**EXAMPLE HERE**

We're already pretty familiar with using web browsers, but let's look at the other side of the connection. A web server is a special application that is designed to listen for and respond to HTTP requests. In the early days, web servers were simply responsible for converting the path in an HTTP request into a file path on the server, and then it would respond with that file containing HTML content. Some common web servers include Apache, Internet Information Services or IIS, and nginx.

Unfortunately, one major limitation of that approach is that the pages are static. As the World Wide Web became more commonplace, many people recognized a need to generate new pages on the fly. So, in the late 1990s, there was a rise in websites using dynamic web pages. In essence, the web server would examine the web request, and use that data to determine what content should be generated on the page. Then, it would generated that text on the fly and send it back in response to that request. Initially, this was a very manual process of constructing the HTML content by simply concatenating pages together, but as the technology matured, many web applications started using templates that simplified this process significantly. 

That covers the basic information behind web servers. In the next part of this chapter, we'll look at web frameworks and how we can use them in our applications.


