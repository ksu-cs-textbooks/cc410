---
title: "Formats"
pre: "1. "
weight: 10
date: 2020-01-15T00:53:26-05:00
hidden: true
---

{{< youtube K3HY0snRb08   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

In this chapter, we're going to discuss how to create useful documentation for the programs we're developing. We've already talked a bit about the different types of documentation we could provide, targeted at both the end users of the software as well as other developers. In this video, we'll briefly discuss some of the different formats we could use to create that documentation. 

The first format we'll discuss is the hypertext markup language, or HTML. As you are probably aware, HTML is the language used for web pages on the World Wide Web, so it is very ubiquitous. If you've ever written raw HTML code by hand, you'll know that HTML consists of a set of tags that are used to enclose various pieces of the page. In this example, we see the `p` tag, which represents a paragraph. We have an opening `p` tag, and then a matched closing tag with a slash in the name. Below that, we see the `pre` and `code` tags, which are used to represent computer code in a webpage. The `pre` tag is short for "preformatted text", which tells the browser not to adjust the formatting at all. Otherwise, our spacing and tabs may be lost when this text is rendered in a web browser. HTML can be further extended using CSS and JavaScript to style the pages and make them more interactive. In fact, the slides I'm using right now are created using HTML, so we can see an example of the syntax highlighting that is possible. 

HTML has a few pros and cons. As discussed, HTML is a very flexible format, capable of just about anything we can think of. It is also easily style-able using CSS, so we can make our documentation look exactly like we want it to. Also, because HTML is such a universal format, it can be read directly by any web browser without any additional work. Unfortunately, creating HTML documentation requires lots of boilerplate code, and it can be very difficult to maintain as the document gets larger. So, while most documentation is presented in an HTML format, it is not commonly written directly in HTML. Instead, we typically use other languages that can be converted to HTML.

One of those languages is Markdown. Markdown was developed to be a much simpler way to express the formatting available in HTML, focusing on making it simple to read and write. There are many special formatting characters used in Markdown, such as hash symbols to create header elements, and the use of asterisks or underscores for bold and italics. As seen in this example, we can also use backticks to enclose pieces of code. Single backticks are used for inline code, such as a variable name as part of a paragraph, whereas code enclosed by triple backticks will create a code block, equivalent to what we saw earlier in HTML. We can even specify then language of the code, and the resulting documentation will include code syntax highlighting if it is supported by the renderer.

The two biggest benefits from using Markdown is the fact that it is very easy to read and write raw Markdown code. In addition, Markdown itself is widely supported across many developer tools such as GitHub. GitHub uses a special version of Markdown called "GitHub-Flavored Markdown" for its readme files, merge requests, and more. In fact, we use Markdown to develop the Codio guide page you are probably reading right now, as well as the various open textbooks used by K-State Computer Science students. It is a very easy to use format! Unfortunately, for Markdown to be displayed with proper formatting, it must be rendered. Some tools, such as GitHub and Codio, handle that behind the scenes. However, for other uses, we may need to use a Markdown renderer to create the HTML version of our documentation that can be easily read by others. Finally, because Markdown has limited formatting options, it can seem like it is a bit less flexible than writing raw HTML. However, most Markdown renderers support the inclusion of raw HTML code directly in Markdown, so that shouldn't be a major problem.

The other format we'll briefly discuss here is the extensible markup language, or XML. XML is actually a parent language to HTML, and it is commonly used to store and represent data in a way that can be parsed and read by any computer program. It can also be used for documentation, primarily by the Microsoft .NET family of programming languages. In this example, we're using XML to represent the data for a fictional student at K-State. We can easily see how it is very similar to HTML, with a set of opening and closing tags that define each element.

As we can see, XML is a very easy to parse language, and because of that it is nearly universal. If two different computer systems need to share data back and forth, one of the common ways to do this is using XML. In that way, the XML code itself stores all the information another program would need in order to load the data and process it. Unfortunately, just like HTML, XML can be a very verbose language, and it is typically better suited for storing data rather than documentation in many cases. However, it is something we may see from time to time, so it is worth being aware of. 