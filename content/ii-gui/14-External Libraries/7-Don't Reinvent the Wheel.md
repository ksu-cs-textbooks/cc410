---
title: "Don't Reinvent the Wheel"
weight: 35
pre: "7. "
---
The use of software libraries can be complex, as seen in the earlier discussions in this chapter. There are licensing issues to consider, security issues to worry about, and even then we might struggle to find the library that best fits our needs. However, let's take a step back and review why we should definitely still consider using these libraries wherever possible in our work.

## "Don't Reinvent the Wheel"

The saying "don't reinvent the wheel" is a good one to keep in mind when writing new software. In most cases, large parts of any software we wish to write have already been written many times before. So, instead of doing all of the work to recreate that software, we can instead try to find a library or framework that does what we need, and spend our time working on how to make that software fit our needs.

In the article [A Padawan Programmer's Guide to Developing Software Libraries](https://www.cell.com/cell-systems/pdf/S2405-4712(17)30336-8.pdf), the authors list a very important lesson as the first lesson any developer should learn when approaching a new project: "Identify a Need for a New Piece of Software." In essence, whenever we wish to develop something, we should first consider whether it has been done before. If so, it may be worth looking at how we can adapt an existing solution to fit our needs, rather than building a new one from scratch.

A great example of this is building a database-driven website. A naive approach (one taken by this textbook's author while in college) would be to write all of the code to generate each page by hand, without using any external frameworks or libraries besides the one required to interface with the database. The website would work, but it would be very complex and prone to errors. In addition, maintaining that code could be difficult due to its complexity.

A better solution would be to find a website framework that is able to handle interfacing with the database and generating pages for you, and then customizing those pages to fit our needs. 

Likewise, when writing a program to perform statistical analysis or machine learning on some data, we can usually rely on well written, well documented, and typically very efficient libraries to handle the work for us. By doing so, we reduce the risk of our code producing incorrect results due to the algorithm being incorrect (though we could just as easily use the algorithm incorrectly or provide it bad data). 

In short, it is always worth taking the time to review the libraries and frameworks available for our programming language. We may find that we can easily combine a few of them together to achieve our desired result.

{{% notice note %}}

# A Cautionary Tale

Of course, relying on a library developed by someone else does have its pitfalls. For example, what if the original developer suddenly decides to "unpublish" the library, making it unavailable for download in the future? That could cause issues for any developer or application that relies on that library, making them also stop working. As libraries are often built on other libraries, such a cascading effect could have dire consequences.

This very thing happened in 2016, when a developer chose to remove his libraries from npm, a large repository of packages for the JavaScript programming language, due to a dispute with another company. One of those libraries was [left-pad], a simple library to help align strings of text by adding spaces to the front of them. However, as it turns out, many larger libraries within the JavaScript ecosystem relied on that library as a dependency. Once of these tools was [Babel](https://babeljs.io/), a compiler for JavaScript that is commonly used by many developers in the field. 

In JavaScript, it is very common to constantly get updated versions of libraries from npm, sometimes daily or weekly, just to make sure the latest updates are applied when publishing a new version of a web application. When the [left-pad] library suddenly disappeared, many other libraries found themselves unable to update and publish new versions because of the missing dependency. It effectively disrupted the entire JavaScript ecosystem!

Thankfully, the left-pad library was restored soon after, and it has since been deprecated in favor of using a function built-in to JavaScript. 

For more information on this event, see [this article](https://arstechnica.com/information-technology/2016/03/rage-quit-coder-unpublished-17-lines-of-javascript-and-broke-the-internet/) from Ars Technica.

{{% / notice %}}

On the next pages, we'll briefly look at how to work with external libraries in both Java and Python. As always, feel free to review the content for your chosen language, but you are welcome to read both sections if desired.
