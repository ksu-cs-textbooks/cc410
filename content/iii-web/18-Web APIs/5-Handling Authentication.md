---
title: "Handling Authentication"
weight: 25
pre: "5. "
---
Another important concept related to web APIs is handing authentication. First, let's review a bit about what authentication is and why it is important.

## Authentication vs. Authorization

In computer security, we commonly use two related terms to describe limits placed on access to a particular resource. 

* **Authentication** refers to providing information that confirms the user's identity. This could be through the use of a password or some other secure token that is only known to the user, or through some other means.
* **Authorization** refers to determining if the user has access to a particular resource. 

So, a user must first be **authenticated** to determine their identity. Then, the application must determine if that user is **authorized** to use the resource requested. 

In this discussion, we are only concerned with authentication. 

## HTTP Authentication

One simple form of authentication that can be used for a web API is already built in to HTTP itself. The HTTP standard allows the webserver to ask for authentication credentials when accessing a given URL. So, the client can provide those credentials within the HTTP headers of a request, and the server will confirm that they are correct before providing the response.

This method is simple and easy to use, and we saw it earlier in this chapter already. However, it does have one major caveat - these authentication schemes require placing the secure information directly in the HTTP headers of an HTTP request. Since HTTP is a text-based protocol, anyone who sees that request (such as an internet service provider or a malicious user performing a [man in the middle attack](https://en.wikipedia.org/wiki/Man-in-the-middle_attack)) can obtain the authentication information from it and then use it themselves. 

So, HTTP authentication should **only** be used when combined with another encryption method, such as the use of [HTTPS](https://en.wikipedia.org/wiki/HTTPS) to create a secure connection between the client and the server.

## API Keys

Due to the limitations of HTTP authentication, many web APIs, especially RESTful APIs, use an authentication method known as API keys. In this method, a user registers with the provider of the API, and along with their user account is given a special key, called an API key, to identify themselves. This key is usually a very long string of alphanumeric data, and should be protected just like any password. 

When making a request to the API, the user should include the API key along with the request. The server will then check that the API is key valid before returning the response. 

Unfortunately, as with HTTP authentication, API keys are also included directly in the HTTP request, so they should be combined with encryption such as HTTPS to prevent them from being compromised.

## Other Methods

Finally, many APIs today use a variety of other methods for authentication. One popular choice is the [OAuth](https://en.wikipedia.org/wiki/OAuth), which is a way for users of a web API to request authentication through a 3rd-party service, and then pass the results of that authentication request to the web API. 

Many users on the internet today are familiar with websites that present the option to log in using a different service, such as Facebook or Google, instead of registering an account directly with the site itself. This authentication method similar to OAuth, and sometimes is actually implemented using OAuth, such as [OpenID](https://en.wikipedia.org/wiki/OpenID).

Applications that use a web API can follow a similar process. The application first requests authentication via the 3rd-party service by submitting information such as a password or API key, and then it will receive a response. That response is their "ticket" to access other resources. So, when the application sends a request to the web API, it sends along the "ticket" to prove its identity.

