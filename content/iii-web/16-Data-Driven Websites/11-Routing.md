---
title: "Routing"
weight: 55
pre: "11. "
---
Of course, one major question that we still need to resolve is "how does the web framework look at a web request and determine what code to execute?" To do that, most web frameworks introduce the concept of **routing**.

In a web framework, a **route** is usually a mapping from a path to a particular function in a controller. 

For example, a simple web framework might match the path `/`, representing the top level page on the server, to a function called `getIndex()` in one of the controllers in the web application itself. 

So, when an incoming HTTP GET request asks for the page at path `/`, the web framework will call the code in our `getIndex()` function, which will usually return a model and a template to render. Then, the framework will render that template using the data in the model, and send that as a response back to the user's client web browser. 

## Complex Routes

Routes in our web application can be much more complex than mapping simple paths to functions. For example, the route could specify one function when the path is requested using an HTTP GET request, and an entirely different function when the path is requested using an HTTP POST request, which includes some additional data.

A great example is logging in to a website. If the user sends an HTTP GET request to the `/login` path, it could call a function named `getLoginPage()` to render a login page that asks the user for a username and password.

When the user enters that information on the page and clicks the "submit" button, it will send an HTTP POST request to the same `/login` path, along with the username and password that the user entered. In that case, the web framework can be configured to send that request to a different function, `postLogin()` that will determine if the username and password match an existing user account. If so, the user will be logged in and the website will send an appropriate response. If not, it can even direct the web framework to render the same login template as before, including an extra message to let the user know that the information submitted was invalid.

## Data in Routes

Finally, routes can also include placeholders for data, similar to wildcards. This is most commonly used in [RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer) routing, short for "Representation State Transfer," which we'll cover in a later chapter.

For example, a web application might be configured with a route that matches the path `/title/<id>`, where `<id>` is a placeholder for some data that is provided as part of the path. So, if the user requests the item at path `/title/123`, the web framework will know that the user is requesting information about the title with the ID of `123`. 

In fact, if you look closely at many websites today, you'll see this pattern all over! A great example is IMDb (the "Internet Movie Database"), where the url `https://www.imdb.com/title/tt0076759/` takes you to [this page](https://www.imdb.com/title/tt0076759/) about the original _Star Wars_ movie. In that URL, we see the RESTful route `/title/tt0076759`, where `tt0076759` is the identifier for _Star Wars_.

We can even explore this by changing the identifier a bit and seeing where that takes us. If we increment the identifier by 1, we get `https://www.imdb.com/title/tt0076760/`, which takes us to the page about the movie _[Starship Invasions](https://www.imdb.com/title/tt0076760/)_, released in the same year as _Star Wars_. In fact, by trying several similar identifiers, we can quickly guess that some of the data on IMDb from movies was loaded alphabetically by year of release!

{{% notice tip %}}

# Leaking Data via Routes

While RESTful routes using sequential identifiers such as this one are really useful, they can also cause issues. One common cause of this is attaching sequential identifiers to user uploaded data. In this way, any user who uses the platform can upload a piece of data, and then use the identifier attached to that piece of data to guess the identifier of data from other users. This is referred to as an [Insecure Direct Object Reference](https://cheatsheetseries.owasp.org/cheatsheets/Insecure_Direct_Object_Reference_Prevention_Cheat_Sheet.html) or IDOR. If the website doesn't properly limit access to this data, it could result in private data being publicly available. 

This was most recently in the news when it was revealed that the data from the Parler social network was downloaded by exploiting this bug, among others. [Wired](https://www.wired.com/story/parler-hack-data-public-posts-images-video/) does a good job describing how it happened.

{{% / notice %}}

