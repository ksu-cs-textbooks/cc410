---
title: "REST"
pre: "2. "
weight: 20
date: 2020-04-09T00:53:26-05:00
hidden: true
---

{{< youtube VyEBbwUi6Co >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

Another important concept in the design of web applications is REST. REST is short for "Representational State Transfer" and is a software architectural style that is used in many web applications. REST can be a bit difficult to understand at first, since there are many different moving parts to put together, but hopefully at the end of this video it makes a bit more sense. The important things to remember about REST is that it creates entirely stateless applications. We'll discuss that a bit more on the next slide. In addition, REST specifies some standardized operations on the data, and is basically used to create a uniform interface for the web application that is easy to understand and work with.

First, let's talk about what it means to be stateless. In a web application, there are actually two different types of state. One is the state of the application itself, which includes the current web page or resource that the client is viewing. Typically, we could think of that as the last page the client requested, but on the web it isn't nearly that simple. For example, we are probably used to opening many tabs in our web browser, so we may actually have several different pages open at any given time, all from the same web application. So, instead of storing any application state on the web server itself, that state is all stored on the client, and usually it is done so in a way that there really isn't any state at all, as we'll see shortly. The other type of state is the resource state, which is stored on the server itself. This is typically stored in a database, but there are other methods available. The resources are the data stored on the web application, such as the pages on a blog or the grades in a learning management system like Canvas. So, a stateless protocol simply means that the server is responsible for tracking the state of the resources, but not the application itself. By doing so, the server can treat each request as an independent action, and act upon it without worrying about any previous state. It's a very nice system.

How does it do this? Typically it does so by embedding the application state in the URLs themselves. We already saw an example of this earlier, where IMDB includes information in the URL that is used to get information about a particular movie. This allows for easy manipulation of the data - if we know the system, we can manually enter the URL of the resource we want, without even going through the rest of the application. Likewise, we can bookmark those URLs and they should work directly - no application state is stored on the server, so that request will be treated the same as if we clicked on that link on another page in the application. In addition, the server typically includes several self-descriptive messages if something goes wrong or if an action is needed. All of this is an example of a concept known as "HATEOAS", which is short for "Hypermedia as the engine of the application state". In my opinion, probably one of the most difficult to remember initialisms out there, but it basically means that we get all of the application info from the server itself. If we load a resource, and we might want to edit or delete that resource, the information for how to do that is included in the response itself. In most cases, that means that there are links or buttons on the web page that we can use to perform those actions. We, as the clients, don't need to have any prior knowledge about the application or how it works - it gives us all the information we need. That's what HATEOAS means.

Typically, we can think or a RESTful architecture as a mapping to the basic create, read, update, and destroy operations from a database. We refer to those operations as "CRUD" operations in short. So, in most cases, a "RESTful" application will follow a particular URL pattern for performing these CRUD operations on a resource. This table shows one possible way to do it, but each application may use a different format. This is because REST is an architectural style, and not a standard itself. For example, if we want to get a list of all the students in our application, we might send an HTTP `GET` request to the URL path `students`. On that page, each student might include a link for more details, which will redirect us to the URL `students` followed by the ID of that student. So, we can send an HTTP `GET` request to that URL to get information about a single student, all based on the ID. That ID is the "application state" that we've been talking about - it is all stored on the client-side in those links. If we want to create a new student, we can send a `POST` request with the information about the student to the `students` URL. Finally, we can use other methods to edit and even delete individual students. 

To really understand a RESTful architecture, it helps to look at an example. Thankfully, the Canvas Learning Management System that you might be familiar with is a great example of a RESTful application. So, let's look at a quick example of working with Canvas to explore a RESTful application. Here, I've loaded up a Canvas course, and chosen to go to the "Pages" section of the course. So, in the URL at the top of the screen, we see a very RESTful URL structure. The first part, `/courses/108108` tells us that we are loading information about the course with the ID of `108108`. Then, after that, we see the next part `pages/0-home`, which tells us that we are accessing the page with the ID `0-home` within that course. So, just within that URL, we have all of the application state we really need to find the resource we want. 

In Chrome's developer tools, we can see that request as an HTTP GET request as well. So, this is the application state that we are requesting from the web server, and it is able to use the information in the URL to find the exact resource we are requesting.

If we want to create a new page, there is a form that we can use on that same page - it is loaded using some JavaScript, so it doesn't generate a new request to the server. However, when we save the form, the website will send an HTTP POST request to the URL shown here. In this case, we can see that they are using a separate API for accessing certain actions, but the path is still familiar. Here, we are sending our POST request to the `pages` portion of the course with ID `108108`, so the web application will know exactly where to store the new page. In the body of the request, we can see a JSON block containing all of the information on the page itself. 

Once that page is created, we can then access that page by sending an HTTP GET request to the page's URL. As you might have guessed, it is the URL `courses/108108/pages/test`. Just by knowing the name of the page and the ID of the course, we can access that page! In fact, after submitting the page, the website automatically redirects us to this page using some JavaScript!

To edit the page, we have to send a different request to get an editable version of the page. In this case, the Canvas application appends `edit` to the end of the URL. This is very common in REST applications to represent pages for interacting with a particular resource. 

When I save that edited page, it will send an HTTP PUT request to the server, using the URL of the page. Once again, we can see in the request body that the payload contains the information stored on the page itself. 

Finally, if I click the button on the page to delete it, the web browser will send an HTTP DELETE request to the server, using the URL of the page. 

So, by using different HTTP methods and the same URL, we can access, update, or delete the resource from the web application. All the client needs to keep track of is the URLs for these actions, which represent the application's state. Meanwhile, the server keeps track of the resource, in this case the page, and will allow us to access or update it as needed. This is the core concept behind RESTful applications and their architecture. 
