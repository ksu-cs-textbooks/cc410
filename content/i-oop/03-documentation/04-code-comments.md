---
title: "Code Comments"
weight: 20
pre: "4. "
---

Of course, one of the most important ways that developers can add documentation to their software is through the use of [code comments](https://en.wikipedia.org/wiki/Comment_(computer_programming)). A code comment is simply extra text added to the source code of a program which is ignored by the compiler or interpreter - it is only visible within the source code itself. Nearly every programming language supports the inclusion of code comments to help describe or explain how the code works, and it is a vital way for developers to make notes, share information, and make sure anyone else reading the code can truly understand what it does.

## Writing Useful Comments

Unfortunately, there is not a well established rule for what constitutes a useful code comment, or even how many comments should be included in code. Various developers have proposed ideas such as [Literate Programming](https://en.wikipedia.org/wiki/Literate_programming), which involves writing complete explanations of the program's logic, all the way down to [Self-Documenting Code](https://en.wikipedia.org/wiki/Self-documenting_code), which proposes the idea that using properly named variables and well structured code will eliminate the need for any documentation at all, and everything in between. There are numerous articles and books written about how to document code properly that can be found through a simple online search.

For the purposes of this course, we recommend writing useful code comments anytime the code contains something interesting or unique, or something that required a bit of thinking and effort to create or understand. In that way, the next time a developer looks at the code, we can reduce the amount of time that developer spends trying to understand what the code is doing. 

In short, we should write comments that help us understand our code better, but we shouldn't focus on commenting every single line or expression, especially when it is pretty obvious what it does. To help with that, we can use properly named variables that accurately describe the data being manipulated, and use simple expressions that are easy to follow instead of complex ones. 

## Comment Formats

Each programming language defines its own specification for comments. Here is the basic information for both Java and Python.

{{< tabs >}}

{{% tab name="Java" %}}

```java
// Single line Java comments are prefixed by two slashes.

int x = 5; // Comments can be placed at the end of a line.

/*
 * This is an example of a block comment.
 *
 * It begins with a slash and an asterisk, and ends
 * with an asterisk and a slash.
 *
 * By convention, each line is prefixed with an asterisk
 * that is aligned with the starting asterisk, but this is not
 * strictly required.
 */
 
/**
 * This is an example of a documentation comment.
 *
 * It begins with a slash and a two asterisks, and ends
 * with an asterisk and a slash.
 *
 * By convention, each line is prefixed with an asterisk
 * that is aligned with the starting asterisk, but this is not
 * strictly required.
 *
 * These blocks are processed by Javadoc to create documentation.
 */
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
# Single line Python comments are prefixed by a hash symbol

x = 5 # comments can be placed at the end of a line

""" Python does not directly support block comments.

However, a bare string literal, surrounded by three double-quotes
can be used to create a longer comment. 

Python refers to these comments as docstrings when used
to document elements such as functions or classes
"""
```

{{% /tab %}}

{{< /tabs >}}

## Formal Code Documentation

In addition to comments within the source code, we can also include formal documentation comments about classes and methods in our code. These comments help describe the functionality of parts of our code, and can be parsed to create generated documentation. On the next two pages, we'll introduce the documentation standard for both Java and Python. Feel free to only read about the language you are learning, but it might be interesting to see how other languages handle the same idea in different ways.
