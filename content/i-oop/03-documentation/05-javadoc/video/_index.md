---
title: "Javadoc"
pre: "2.J. "
weight: 20
date: 2020-01-14T00:53:26-05:00
hidden: true
---

{{< youtube QYAda6-2rVw   >}}

#### Resources

* <a href="{{% relref "./slides" %}}" target="_blank">Slides</a>

#### Video Script

Let's look at what it takes to create a Javadoc comment for our classes and methods. Each Javadoc comment can be broken into three basic parts. First is the summary fragment, which is the first whole sentence in the comment, usually ending with a period. This line gives a short overview of what the class, method, or attribute represents or is used for. Then, after that, we can optionally add additional paragraphs that further explain the element. Each of those paragraphs starts with an opening `p` tag, but unlike HTML there will be no closing `p` tag at the end. Instead, a blank line is used to show the end of a paragraph. Finally, both class and method comments may also include one of several tags available as part of the Javadoc standard. These tags are used to add additional information to the comment, such as the author and version of the class, or the method parameters and return value on a method.

In fact, here is a quick list of the tags that may be used for the class and method comments in Javadoc. This is not a complete list, but lists the tags that are by far the most common ones. For classes, the Javadoc comment should at a minimum include the @author and @version tags, denoting the person who wrote the code as well as the version of the code. For methods, if the method includes a parameter or return value, those should be included using the @param and @return tags. In addition, if the method might throw an exception, that should be denoted using the @throws tag. 

So, let's look at a couple of examples. This is a class comment for a fictional class used to represent a square. At the top, we see the summary fragment giving the big picture overview of what the class is used for. Below that, we have a paragraph starting with a `p` tag that provides some more information. Finally, at the bottom, we see both the @author and @version tags. It really is a pretty simple format.

Here's a sample method comment. We can see that the structure is very similar - it starts with a summary fragment, then has a paragraph of additional information. Since this method includes a parameter, we use the @param tag to describe the parameter that is expected. We also use an @return tag to describe the value that the method will return - in this case, the difference in area between the square and the circle. Finally, since this method could also throw an exception, we use the @throws tag to list the exception it could throw and the reason it would do so. 

Finally, we can also use Javadoc comments elsewhere in our code. Typically this would be used to denote the use of an attribute, such as the `length` attribute as seen in this example. Of course, if our code includes proper accessor methods, then much of that information may be included in the Javadoc comment for the accessor method instead of the attribute itself. So, as we can see, Javadoc is a very easy to use and flexible way to provide documentation directly within our code. 