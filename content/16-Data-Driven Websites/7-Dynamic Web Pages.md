---
title: "Dynamic Web Pages"
weight: 35
pre: "7. "
---
{{% notice note %}}

# Content Note

Much of the content in this page was adapted from Nathan Bean's [CIS 400](https://textbooks.cs.ksu.edu/cis400/3-web-development/02-aspdotnet/03-dynamic-pages/) course at K-State, with the author's permission. That content is licensed under a [Creative Commons BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.

{{% / notice %}}

Modern websites are more often full-fledged applications than collections of static files. These applications remain built upon the foundations of the core web technologies of HTML, CSS, and JavaScript.  In fact, the client-side application is typically built of _exactly_ these three kinds of files!  So how can we create a dynamic web application?

One of the earliest approaches was to write a program to _dynamically create_ the HTML file that was being served.  Consider this method:

###### Java

```java
public String GeneratePage() {
    StringBuilder sb = new StringBuilder();
    sb.append("<!DOCTYPE html>\n");
    sb.append("<html>\n");
    sb.append("<head>\n");
    sb.append("<title>My Dynamic Page</title>\n");
    sb.append("</head>\n");
    sb.append("<body>\n");
    sb.append("<h1>Hello, world!</h1>\n");
    sb.append("<p>Time on the server is ");
    SimpleDateFormat formatter= new SimpleDateFormat("yyyy-MM-dd 'at' HH:mm:ss z");
    Date date = new Date(System.currentTimeMillis());
    sb.append(formatter.format(date) + "\n");
    sb.append("</p>\n");
    sb.append("</body>\n");
    sb.append("</html>\n");
    return sb.toString();
}
```

###### Python

```python
def generate_page(self) -> str:
    sb: List[str] = list()
    sb.append("<!DOCTYPE html>")
    sb.append("<html>")
    sb.append("<head>")
    sb.append("<title>My Dynamic Page</title>")
    sb.append("</head>")
    sb.append("<body>")
    sb.append("<h1>Hello, world!</h1>")
    sb.append("<p>Time on the server is ")
    now = datetime.now()
    sb.append(now.strftime("%d/%m/%Y %H:%M:%S"))
    sb.append("</p>")
    sb.append("</body>")
    sb.append("</html>")
    return "\n".join(sb)
```

It generates the HTML of a page showing the current date and time.  Remember too that HTTP responses are simply text, so we can generate a response as a string as well:

###### Java

```java
public String generateResponse() {
    String page = generatePage();
    StringBuilder sb = new StringBuilder();
    sb.append("HTTP/1.1 200\n");
    sb.append("Content-Type: text/html; charset=utf-8\n");
    sb.append("ContentLength:" + page.length() + "\n");
    sb.append("\n");
    sb.append(page);
    return sb.toString();
}
```

###### Python

```python
def generate_response(self) -> str:
    page: str = generate_page()
    sb: List[str] = list()
    sb.append("HTTP/1.1 200");
    sb.append("Content-Type: text/html; charset=utf-8");
    sb.append("ContentLength:" + page.length());
    sb.append("");
    sb.append(page);
    return "\n".join(sb)
```

The resulting string could then be streamed back to the requesting web browser.  This is the basic technique used in all server-side web frameworks: they dynamically assemble the response to a request by assembling strings into an HTML page.  Where they differ is what language they use to do so, and how much of the process they've abstracted.

For example, this approach was adopted by Microsoft and implemented as _Active Server Pages (ASP)_.  By placing files with the _.asp_ extension among those served by an IIS server, C# or Visual Basic code written on that page would be executed, and the resulting string would be served as a file.  This would happen on each request - so a request for `http://somesite.com/somepage.asp` would execute the code in the `somepage.asp` file, and the resulting text would be served.

You might have looked at the above examples and shuddered.  After all, who wants to assemble text like that?  And when you assemble HTML using raw string concatenation, you don't have the benefit of syntax highlighting, code completion, or any of the other modern development tools we've grown to rely on.  Thankfully, most web development frameworks provide some abstraction around this process, and by and large have adopted some form of _template syntax_ to make the process of writing a page easier.
