---
title: "Generated Documentation"
weight: 35
pre: "7. "
---
One of the biggest innovations in documenting software was the development of documentation generation tools. These were programs that would read source code files, and combine information parsed from the code itself and information contained in code comments to generate documentation in an easy-to-distribute form (often HTML).

This approach meant that the language of the documentation was embedded _within the source code itself_, making it far easier to update the documentation as the source code was refactored.  Then, every time a release of the software was built, the documentation could be regenerated from the updated comments and source code.  This made it far more likely developer documentation would be kept up-to-date.

So, once we have properly documented our code using documentation comments, we can then use tools such as Javadoc for Java or pdoc3 for Python to automatically generate documentation for developers. That documentation contains all of the contents of our documentation comments, and serves as a handy reference for any developers who wish to use our code.

In the Java ecosystem, this is best represented by the [Java API](https://docs.oracle.com/javase/8/docs/api/) itself, which is generated using Javadoc directly from the source code of the Java SDK itself.

For Python, there are many documentation generators available, but we've chosen to use pdoc3. An example of its output is the [pdoc3 Documentation](https://pdoc3.github.io/pdoc/doc/pdoc/).

In either case, the use of these tools, combined with up to date documentation comments in our code, means that we can easily generate documentation quickly and easily. 
