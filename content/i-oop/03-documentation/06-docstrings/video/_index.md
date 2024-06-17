---
title: "Docstrings"
pre: "2.P. "
weight: 21
date: 2020-01-14T00:53:26-05:00
hidden: true
---

{{< youtube -aX1FAMnlgw   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

Let's look at what it takes to create a Python docstring comment for our classes and methods. Each docstring comment can be broken into three basic parts. First is the summary line, which is the first whole sentence in the comment, usually ending with a period. This line gives a short overview of what the class, method, or file represents or is used for. Then, after that, we can optionally add additional paragraphs that further explain the element. Each of those paragraphs starts indented at the same level as the opening quotes. A blank line is used to show the end of a paragraph. Finally, many docstrings may also include one of several sections that are part of the Google style guide. These sections are used to add additional information to the comment, such as the author and version of the class, or the method parameters and return value on a method.

In fact, here is a quick list of the sections that may be used for the file, class and method comments in Python. This is not a complete list, but lists the sections that are by far the most common ones. For files, the docstring comment should at a minimum include the author and version sections, denoting the person who wrote the code as well as the version of the code. For methods, if the method includes a parameter or return value, those should be included using the Args and Returns sections. In addition, if the method might raise an exception, that should be denoted using the Raises section. 

So, let's look at a couple of examples. First, we have a sample file comment, which should be placed at the top of any Python file. Since we are writing object-oriented Python, most files will contain a single class, so the file comment may be quite short. However, it should include the author and version sections, which are both helpful items for us to include in our comments.

This is a class comment for a fictional class used to represent a square. At the top, we see the summary line giving the big picture overview of what the class is used for. Below that, we have a paragraph that provides some more information. Finally, at the bottom, we see an Attributes section that lists the attribute available in the class. However, we could also choose to document that attribute as part of the Python property that actually implement it - either way is valid. It really is a pretty simple format.

Here's a sample method comment. We can see that the structure is very similar - it starts with a summary line, then has a paragraph of additional information. Since this method includes a parameter, we use the Args section to describe the parameter that is expected. We also use a Return section to describe the value that the method will return - in this case, the difference in area between the square and the circle. Finally, since this method could also raise an exception, we use the Raises section to list the exception it could throw and the reason it would do so. So, as we can see, Python docstrings are a very easy to use and flexible way to provide documentation directly within our code. 