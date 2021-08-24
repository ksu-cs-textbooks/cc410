---
title: "Repositories"
weight: 25
pre: "5. "
---

So far, we've learned about what software libraries are, and how they differ from other, similar tools such as software frameworks. However, you are probably wondering: "how do I find these libraries and add them to my application?" Let's discuss the various places you can learn about software libraries and how to use them in your applications.

## Repositories

One of the most common ways to find software libraries to include in your application is to review the libraries available in a **repository** of libraries for your language. A [repository](https://en.wikipedia.org/wiki/Content_repository) is simply a database of content that you can use, and most languages include a way to automatically find and install libraries that are available in a standard repository. Most of those libraries are provided as **packages**, which is simply a name for the library and any supporting files or resources all bundled together in a single downloadable file.

For example, in Python we've used the `pip3` tool to download and install many different tools for Python, such as `flake8` and `mypy`. The `pip3` tool downloads packages from a central repository called [PyPi](https://pypi.org/) (Python Package Index). The PyPi website includes a very robust search tool for finding and learning about the various packages available for Python. In the next chapter, we'll see how we can package our own applications up and make them ready for submission to PyPi.

In Java, we are using Gradle as our build tool, and it is able to download packages from many different repositories. In most cases, we will be using the [Maven Central](https://search.maven.org/) repository. 

## Direct Download

In addition to the repositories listed above, many software libraries and packages are available for download directly from the internet, usually from the library developer's website. For example, many of the Java libraries developed by the [Apache Software Foundation](http://apache.org/) can also be downloaded directly from their [Distribution Directory](https://downloads.apache.org/). Many Java packages are commonly offered via direct download as well as through repositories, mainly because the popularity of distributing software via a repository is more recent than the development of Java.

For Python, on the other hand, by far the most common method of installing packages is simply via the `pip3` command that downloads them directly from PyPi. However, it is possible to download these packages directly from PyPi as a **Python Wheel**, which we'll learn about in the next chapter.

In both languages, the ability to download and install these packages directly is important for many reasons. There may be instances where the developer may not have direct access to the Internet, such as in a highly secure computing environment. So, tools such as `pip3` and Gradle cannot be used to download the packages.

In fact, many developers working in a secure environment can choose to host their own internal repositories for software packages, making sure that they have access to the packages they need while still being able to control the exact version and contents of those packages. 

## Build from Source

Finally, many open-source software libraries can be directly built from the source code. The vast majority of open source software today stores their source code in publicly available code repositories such as [GitHub](https://github.com/), [GitLab](https://about.gitlab.com/), or [SourceForge](https://sourceforge.net/). So, a developer can choose to download the source code directly and build the library themselves, or possibly even edit the source code as needed to match a particular use case. In most open-source community, this kind of experimentation and reuse is highly encouraged.

Of course, this can present many hassles as well. Many more advanced software libraries contain thousands of lines of code, and they can be very complex to modify, build, and distribute. Most large scale open-source project has large amounts of automation that handles this process, so doing it ourselves as a single developer can be very daunting. In addition, any time the library is updated we'll need to manually update our version as well, or else we risk out software becoming obsolete and possibly vulnerable to security issues.

## Security

When downloading or installing software libraries, one aspect that should always be considered is the security of your application. There are many instances of open source software libraries containing either security flaws or malicious code, many of which are only discovered months or years after appearing in the application. So, we must always be aware of these risks and how they can impact the overall security of the application we are building.

While there is no way to avoid all security issues, here are some quick things we should keep in mind when reviewing which software libraries to include in our code:

1. **The developer**: Is this library developed and maintained by a company, a large group of people, or a single developer? Do I know who develops and maintains this software?
2. **The popularity**: Is this package commonly used by other developers? Are there other, more popular libraries that perform a similar function?
3. **The community**: Is there a place where known bugs and issues with this software are posted? Is there a place where I can go and ask questions if I need help?
4. **The code**: Is the code open source? Can I download and review the code if needed?
5. **The purpose**: Is this library going to be used for an important purpose, such as encrypting communications or securing files? If so, it may need more scrutiny than a library used to generate a simple image file. 
6. **The license**: What **license** does this software have? Can I legally use the software in my application?

On the next page, we'll dive a bit deeper into software licenses and the impact that may have on the libraries we can use in our application.
