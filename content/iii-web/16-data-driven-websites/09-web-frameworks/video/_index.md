---
title: "Web Frameworks"
pre: "3. "
weight: 30
date: 2020-03-31T00:53:26-05:00
hidden: true
---

{{< youtube 0EureiLnik0   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

Over time, websites became more and more interactive, and developers started to build web sites as web applications, following the same techniques they used for other applications. Over time, these techniques gave rise to web frameworks. A web framework is a piece of software that simplifies the process of building web applications by providing most of the code needed to read web requests and make responses. Recall that frameworks are like external libraries, but they wrap around our code and call our methods as needed. Many web frameworks follow the Model-View-Controller architecture, to typically all we need to do is define the models, the controllers, and the templates, as well as some way to map incoming requests through a process called routing.

In this course, we'll learn about either the Spring framework for Java, or the Flask framework for Python. Both are commonly used web frameworks in their respective language, and are powerful yet easy to use. In the example project for this chapter, we'll go over how to install and use one of these frameworks in an existing application.

This diagram shows the process that a web framework follows to process an incoming web request. First, that request goes to the front controller of the application. In most cases, this is part of the framework itself, so we don't have to handle this part. However, the front controller is responsible for processing that request and delegating it to one of our own controllers. Typically, we do this by including information about routes, which we'll talk about in the next slide. Our controller then receives the request and collects any data required to respond to it. This might include reading data from a database or accessing an external API. Once it has collected the data, it builds a model that contains the data and returns it, along with a template that should be rendered with that data. Next, the front controller accesses that template, and uses the model to populate the template with the data. Again, we don't write this process directly, but we are typically responsible for writing the template itself and defining where the model's data goes in the page. Finally, the rendered HTML content from the template is packaged into an HTTP response, and sent back to the web browser that made the request.

A major part of this process is routing, which is how we define which requests go to which controller methods. Typically a route is simply a mapping between a request path and a function in a controller, but our routes can also include placeholders for data to be taken directly from the path in the request. In a later chapter, we'll explore RESTful routing, which uses data in the routes to build a web application with a very easy to follow structure.

Finally, many web frameworks support template inheritance. Much like we can use the same CSS file across our entire application, we can also create base templates that are used to build each page of our web application. By using a base template, we can follow the "don't repeat yourself" rule by minimizing the amount of duplicated code in our application. Then, if we want to change the design of our pages later on, we only have to change the base template. In addition, we can even reuse parts of other templates across many pages, allowing us to build our web pages in a modular way. 

That's a quick overview of web frameworks. To be honest, the best way to learn how to use them is simply by doing so, so don't worry if it doesn't quite make sense at this point. The example project for this chapter will go through all the steps of installing a web framework and building your first routes, controller, and templates. Hopefully by getting some hands-on experience with web frameworks, you'll start to see the numerous ways they can be used to build interactive applications on the web. 