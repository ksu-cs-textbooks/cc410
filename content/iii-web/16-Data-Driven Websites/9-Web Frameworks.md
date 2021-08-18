---
title: "Web Frameworks"
weight: 45
pre: "9. "
---
{{% notice note %}}

# Content Note

Much of the content in this page was adapted from Nathan Bean's [CIS 400](https://textbooks.cs.ksu.edu/cis400/3-web-development/02-aspdotnet/05-web-frameworks/) course at K-State, with the author's permission. That content is licensed under a [Creative Commons BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.

{{% / notice %}}

{{% youtube 0EureiLnik0 %}}

As web _sites_ became web _applications_, developers began looking to use ideas and techniques drawn from traditional software development.  These included architectural patterns like [Model-View-Controller (MVC)](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) and [Pipeline](https://en.wikipedia.org/wiki/Pipeline_(software)) that simply were not possible with the server page model.  The result was the development of a host of web frameworks across multiple programming languages, including:

* [Ruby on Rails](https://rubyonrails.org/), which uses the [Ruby](https://www.ruby-lang.org/en/) programming language and adopts a MVC architecture
* [Laravel](https://laravel.com/), which uses the [PHP](https://www.php.net/) programming language and adopts a MVC architecture
* [Django](https://www.djangoproject.com/), which uses the [Python](https://www.python.org/) programming language and adopts a MVC architecture
* [Express](https://expressjs.com/), which uses the [Node implementation of the JavaScript](https://nodejs.org/en/) programming language and adopts the Pipeline architecture
* [Revel](https://revel.github.io/), which uses the [Go](https://golang.org/) programming language and adopts a Pipeline architecture
* [Cowboy](https://github.com/ninenines/cowboy), which uses the [erlang](https://www.erlang.org/) programming language and adopts a Pipeline architecture
* [Phoenix](https://www.phoenixframework.org/), which uses the [elixir](https://elixir-lang.org/) programming language, and adopts a Pipeline architecture

## Spring and Flask

In this course, we're going to explore a lightweight web framework that was built for our chosen language:

* Java: [Spring](https://spring.io/)
* Python: [Flask](https://palletsprojects.com/p/flask/)

Both of these frameworks are very powerful, but most importantly, they are extremely flexible and allow us to structure our web application in a way that makes sense for our needs.

On the next pages, we'll dive a bit deeper into how these web frameworks handle web _requests_ and generate appropriate _responses_ for them.
