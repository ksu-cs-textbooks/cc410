---
title: "HTML Forms"
pre: "1. "
weight: 10
date: 2020-04-09T00:53:26-05:00
hidden: true
---

{{< youtube b0SPMKu5o0A >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

In this chapter, we're going to take a closer look at one part of HTML - building interactive forms that the user can use to send information to our web applications. Do this, we'll use the HTML `form` element, along with several `input` elements to collect the data. These HTML form elements are very similar to the GUI elements we've already worked with in this class, so hopefully many of the concepts feel familiar to you.

Here's a simple example of a form in HTML. We start with the `form` tag, which wraps around the entire form. Typically, we'll include two attributes in the start `form` tag - the `action`, which is the URL that the form should submit the data to, and the HTTP `method` that it should use to send the data. Inside of the form, we will usually have at least one `input` element, such as the `text` element we see in this example. The `input` elements are the ones that the user actually interacts with to input data or choose various options. In this case, the `input` element has the attribute `type` set to `"text"`, which tells us it is a text input. In addition, the `input` element should have a `name` attribute, which is the name used to identify the element when the form is submitted. Many forms also use that as the `id` attribute as well, but it is not required to be the same. Many times, we'll also include a `label` element for each `input` element, which acts as a caption to describe the input element itself. Finally, each form should have at least one `button` with the type `submit`, which is used to submit the form back to the server. So, when we put this HTML into a webpage, we'll see a form similar to the image on this slide. It's hopefully very straightforward!

There are a variety of types of input elements. Each one uses the `input` HTML tag, with a different `type` attribute. This list shows some common ones. We have the text input, which is a simple one-line text box. We can also have a checkbox, which is handy for selecting boolean options. There are special types for inputting dates, choosing files to upload, dealing with numerical data, and even a special input type just for handling passwords. We can also create drop-down boxes using the special `select` tag, which is very similar to the combobox element we used in our GUIs. Finally, the special `submit` type is used to submit the form itself. The textbook has a great table showing examples of each of these elements and how they work.

There are also a few related elements that we might want to use on our forms. As we saw earlier, the `label` element is used to add a caption or describe the `input` elements on the form. Additionally, we can use a `fieldset` element to group similar `input` elements together, and each `fieldset` can have a `legend` element that describes the set of fields. 

So, when a user submits a form using a standard web browser, there are a few things that happen. First, once the user clicks the submit button, the browser collects the data in the form and encodes it using the encoding standard that is specified for the form. By default, it will use a "URL encoding" scheme, but many forms may use a "multipart" scheme instead. Once the data is encoded, the data is sent to the server using an HTTP request. If the HTTP method on the form is "GET", then the data is included as the URL of the request. Otherwise, for a "POST" request, the data is sent in the body of the request instead. Once the server receives the HTTP request, it will then decode the data, and many times it will validate the data to make sure it is a valid submission. We'll look more closely at validation in a later exercise. Once the server has done its work, it prepares and sends a response back to the client. That response could be a simple acknowledgement, a redirect, or a note that the submission was invalid with a list of errors to be displayed to the user. It is really up to the application to determine how to handle this.

Let's look at a larger example. This is a simple HTML form that could be used to submit a new menu item for a restaurant. It includes some extra CSS classes from Bootstrap, as well as additional HTML attributes on some of the `input` elements. For example, the `number` fields in the form have a minimum value specified, as well as a step value. This allows the browser to perform some additional checking for us, and it may even display the field as a spinner to make it easy for the user to select a value. 

When that form is displayed on the page, it would look like this. I've already filled out the form with some sample data, so let's submit it and see what it does.

To examine the HTTP connection itself, I'm going to use the Developer Tools feature that is built in to Google Chrome. It is a great way to explore how a website interacts with a web server, and is an invaluable tool for a web developer when building a new application. 

First, when the form is submitted, you'll see that it is using the `POST` HTTP method, and sending the information to the URL ending in `"customitems"`. This matches the `method` and `action` attributes of the `form` tag we saw earlier. The server sent a 302 response code, which is the `FOUND` response. It is typically used to redirect the browser to another page - in this case, it will redirect the browser back to the index page of the application.

A little bit further down, we can see the HTTP request headers that our browser sent to the server. In that list, one of the options is the `Content-Type`, which gives information about how the form was encoded. Since we didn't specify an encoding standard in our `form` tag, it will use the default "URL Encoding" scheme. 

Finally, at the bottom, we can see the payload of our request. Chrome will helpfully show it in a parsed format, but we can click the "view soure" link to view the "URL Encoded" version of the data as well. So, that's the data that is actually sent to the server when we clicked the submit button. Pretty nifty!

That's a quick overview of HTML forms and the process they use to submit data back to a web server. The text in this chapter gives a bit more detail about some of the specifics, but hopefully this explainer helps you visualize the entire process. 
