---
title: "Template Inheritance"
weight: 60
pre: "12. "
---

One thing you may have also noticed is that many web applications use the same layout across many different pages. Since each page in a web framework requires a different template, it could be very difficult to make sure that each of those pages includes the same information, and updating them would be a major hassle if there were several hundred or thousands of pages in the application.

Thankfully, most web frameworks also include the ability for templates to be composed of other templates. In that way, we can create a hierarchical structure of templates, and even create smaller templates that we can reuse over and over again in our code.

## Layout Template

One of the most common ways to accomplish this is through the use of a top-level **layout template**, which defines the overall layout of the pages used by the web application. This could include specific CSS and JavaScript files, metadata, and even a common header, navigation bar, and footer for each page.

For example, here is a short layout template for the [Jinja2](https://palletsprojects.com/p/jinja/) template engine used with Flask in Python, which would be stored in the file `layout.html`:

```django
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>{% block title %}{% endblock %} - Web Application</title>
  </head>
    
  <body>
      
    <header>
      <nav>
        <a href="/">Homepage</a>
      </nav>
    </header>

    <main>
        {% block content %}{% endblock %}
    </main>

    <footer>
      <div>
        <span>&copy; 2021 Web Application</span>
      </div>
    </footer>

  </body>
</html>
```

This layout includes a header with a title and some metadata. In addition, the body includes both a header and a footer with some information that should be included on every page in the application. Between those, we see a main section.

In Jinja2, the sections surrounded by curly braces and percent signs `{%  %}` define **blocks** that can be replaced by other content. So, when we use this layout template, we can replace the `title` and `content` block with information specific to that page. 

## Using a Template

To use this layout template, we can just specify it as part of another template. For example, here is a template for a home page, titled `index.html`:

```django
{% extends "layout.html" %}

{% block title %}Home Page{% endblock %}

{% block content %}

<p>Hello World!</p>

{% endblock %}
```

Pretty simple, isn't it? This template basically defines the content to be placed in the `title` and `content` blocks, and at the top it specifies that it will use the template in `layout.html` as it's layout template. So, when the template is rendered, we receive the following HTML:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Home Page - Web Application</title>
  </head>
    
  <body>
      
    <header>
      <nav>
        <a href="/">Homepage</a>
      </nav>
    </header>

    <main>
        <p>Hello World!</p>
    </main>

    <footer>
      <div>
        <span>&copy; 2021 Web Application</span>
      </div>
    </footer>

  </body>
</html>
```

This use of template inheritance can be done in most template engines used in web frameworks.

In addition, we can place other templates inside of our page template. We'll see how to do that in the example project for this chapter.
