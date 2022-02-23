---
title: "Documentation Formats"
weight: 15
pre: "3. "
---

{{% youtube K3HY0snRb08 %}}

[Video Materials]({{<relref "./video">}})

Developer documentation often faces a challenge not present in other kinds of documents - the need to be able to display snippets of code.  Ideally, we want code to be formatted in a way that preserves indentation.  We also don't want code snippets to be subject to spelling and grammar checks, especially auto-correct versions of these algorithms, as they will alter the snippets.  Ideally, we might also apply syntax highlighting to these snippets. Accordingly, a number of textual formats have been developed to support writing text with embedded program code, and these are regularly used to present developer documentation.  Let's take a look at several of the most common.

## HTML

Since its inception, HTML has been uniquely suited for developer documentation.  It requires nothing more than a browser to view - a tool that nearly every computer is equipped with (in fact, most have two or three installed).  And the `<code>` element provides a way of styling code snippets to appear differently from the embedded text, and `<pre>` can be used to preserve the snippet's formatting.  Thus:

```html
<p>This algorithm reverses the contents of the array, <code>nums</code></p>
<pre><code>for(int i = 0; i < nums.length/2; i++) {
    int tmp = nums[i];
    nums[i] = nums[nums.length - 1 - i];
    nums[nums.length - 1 - i] = tmp;
}
</code></pre>
```

Will render in a browser as:

<div style="border: 1px solid gray; padding: 1rem">
<p>This algorithm reverses the contents of the array, <code>nums</code></p>
<pre><code>for(int i = 0; i < nums.length/2; i++) {
    int tmp = nums[i];
    nums[i] = nums[nums.length - 1 - i];
    nums[nums.length - 1 - i] = tmp;
}
</code></pre>
</div><br>

JavaScript and CSS libraries like [highlight.js](https://highlightjs.org/), [prism](https://prismjs.com/), and others can provide syntax highlighting functionality without much extra work. 

Of course, one of the strongest benefits of HTML is the ability to create _hyperlinks_ between pages.  This can be invaluable in documenting software, where the documentation about a particular method could include links to documentation about the classes being supplied as parameters, or being returned from the method.  This allows developers to quickly navigate and find the information they need as they work with your code.

## Markdown
    
However, there is a significant amount of [boilerplate](https://en.wikipedia.org/wiki/Boilerplate_code) involved in writing a webpage (i.e. each page needs a minimum of elements not specific to the documentation to set up the structure of the page).  The extensive use of HTML elements also makes it more time-consuming to write and harder for people to read in its raw form. [Markdown](https://www.markdownguide.org/) is a markup language developed to counter these issues.  Markdown is written as plain text, with a few special formatting annotations, which indicate how it should be transformed to HTML.  Some of the most common annotations are:

* Starting a line with hash (`#`) indicates it should be a `<h1>` element, two hashes (`##`) indicates a `<h2>`, and so on...
* Wrapping a statement with underscores (`_`) or asterisks (`*`) indicates it should be wrapped in a `<i>` element
* Wrapping a statement with double underscores (`__`) or double asterisks (`**`) indicates it should be wrapped in a `<b>` element 
* Links can be written as `[link text](url)`, which is transformed to `<a href="url">link text</a>`
* Images can be written as `![alt text](url)`, which is transformed to `<img alt="alt text" src="url"/>`

Code snippets are indicated with backtick marks (`` ` ``).  Inline code is written surrounded with single backtick marks, i.e. `` `int a = 1` `` and in the generated HTML is wrapped in a `<code>` element.  Code blocks are wrapped in _triple_ backtick marks, and in the generated HTML are enclosed in both `<pre>` and `<code>` elements.  Thus, to generate the above HTML example, we would use:

<pre><code class="language-md" data-lang="md">
This algorithm reverses the contents of the array, `nums`
```
for(int i = 0; i < nums.length/2; i++) {
    int tmp = nums[i];
    nums[i] = nums[nums.length - 1 - i];
    nums[nums.length - 1 - i] = tmp;
}
```
</code></pre>

Most markdown compilers also support specifying the language (for language-specific syntax highlighting) by following the first three backticks with the language name, i.e.:

<pre><code class="langauge-md" data-lang="md">
```java
String aString = "abc123";
```
</code></pre>

Nearly every programming language features at least one open-source library for converting Markdown to HTML. In addition to being faster to write than HTML, and avoiding the necessity to write boilerplate code, Markdown offers some security benefits.  Because it generates only a limited set of HTML elements, which specifically excludes some most commonly employed in web-based exploits (like using `<script>` elements for script injection attacks), it is often safer to allow users to contribute markdown-based content than HTML-based content. **Note: this protection is dependent on the settings provided to your HTML generator - most markdown converters can be configured to allow or escape HTML elements in the markdown text.**

In fact, both the Codio guides in this course, as well as the website used to store the project milestones, was written using Markdown. Codio includes its own Markdown converter, whereas the website was converted to HTML using the [Hugo framework](https://gohugo.io/), a static website generator built using the [Go programming language](https://golang.org/).  

Additionally, chat servers like RocketChat and Discord support using markdown in posts! Try it out sometime!

GitHub even incorporates a markdown compiler into its repository displays.  If your file ends in a `.md` extension, GitHub will evaluate it as Markdown and display it as HTML when you navigate your repository.  If your repository contains a README.md file at the top level of your project, it will also be displayed as the front page of your repository. GitHub uses an expanded list of annotations known as [GitHub-flavored markdown](https://github.github.com/gfm/) that adds support for tables, task item lists, strikethroughs, and others. You can also use Markdown in GitHub pull requests, comments, and more!

{{% notice info info-1 "README and LICENSE files" %}}

It is best practice to include a `README.md` file at the top level of a project stored as Git repository.  This document provides an overview of the project, as well as helpful instructions on how it is to be used and where to go for more information.  For open-source projects, you should also include a LICENSE file that contains the terms of the license the software is released under. For example, much of the content in this course is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/). 

{{% / notice %}}

## XML

Extensible Markup Language (XML) is a close relative of HTML - they share the same ancestor, Standard Generalized Markup Language (SGML).  It allows developers to develop their own custom markup languages based on the XML approach, i.e. the use of elements expressed via tags and attributes.  XML-based languages are usually used as a data serialization format.  For example, this snippet represents a serialized fictional student:

```xml
<student>
    <firstName>Willie</firstName>
    <lastName>Wildcat</lastName>
    <wid>8888888</wid>
    <degreeProgram>BCS</degreeProgram>
</student>
```

While XML is most known for representing data, it can also be used to create documentation, most notably in the Microsoft .NET ecosystem.
