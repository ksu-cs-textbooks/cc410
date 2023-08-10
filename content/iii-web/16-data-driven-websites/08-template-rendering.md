---
title: "Template Rendering"
weight: 40
pre: "8. "
---

{{% notice info "Content Note" %}}

Much of the content in this page was adapted from Nathan Bean's [CIS 400](https://textbooks.cs.ksu.edu/cis400/3-web-development/02-aspdotnet/04-template-rendering/) course at K-State, with the author's permission. That content is licensed under a [Creative Commons BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.

{{% / notice %}}

It was not long before new technologies sprang up to replace the ad-hoc string concatenation approach to creating dynamic pages.  These template approaches allow you to write a page using primarily HTML, but embed snippets of another language to execute and concatenate into the final page.  This is very similar to the formatted strings we've used in Java and Python, i.e.:

{{< tabs >}}

{{% tab title="Java" %}}


```java
String output = String.format("%s, %d", "Computer", 410)
```

{{% /tab %}}

{{% tab title="Python" %}}

```python
output: str = "{}, {}".format("Computer, 410)
```

{{% /tab %}}

{{< /tabs >}}

The example above concatenates the string `"Computer"` and the number `410` with a comma between them. While the template strings above use either format specifiers like `%s` or curly braces `{}` to call out the script snippets, most HTML template libraries initially used some variation of angle brackets + additional characters.  As browsers interpret anything within angle brackets (`<>`) as HTML tags, these would not be rendered if the template was accidentally served as HTML without executing and concatenating scripts.  Two early examples are:

* `<?php echo "This is a PHP example" ?>`
* `<% Response.Write("This is a classic ASP example) %>`

And abbreviated versions:

* `<?= "This is the short form for PHP" ?>`
* `<%= "This is the short form for classic ASP" %>`

Template rendering proved such a popular and powerful tool that rendering libraries were written for most programming languages, and could be used for more than just HTML files - really _any_ kind of text file can be rendered with a template.  Thus, you can find template rendering libraries for JavaScript, Python, Ruby, and pretty much any language you care to (and they aren't that hard to write either).

Classic PHP, Classic ASP, and ASP.NET web pages all use a single-page model, where the client (the browser) requests a specific file, and as that file is interpreted, the dynamic page is generated.  This approach worked well in the early days of the world-wide-web, where web sites were essentially a collection of pages.  However, as the web grew increasingly interactive, many web sites grew into full-fledged **web applications**, or full-blown programs that didn't lend themselves to a page-based structure.  This new need resulted in new technologies to fill the void - web frameworks.  We'll talk about these next.
