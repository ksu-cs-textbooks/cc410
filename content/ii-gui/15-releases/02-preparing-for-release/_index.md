---
title: "Preparing for Release"
weight: 10
pre: "2. "
---

{{% youtube 6dsYPgyzxhk %}}

[Video Materials}({{<relref "./video">}})

Before we release our software, there are a few steps that we should perform to make sure it is ready for release. Most of these steps are things that we've already been doing as part of our development process, but it is always good to review them once again and make sure everything is ready for release.

1. **Unit Testing**: where possible, make sure your project includes adequate unit testing. You should aim to achieve a high level of code coverage, but also keep in mind that code coverage is not a substitute for actually making sure your tests properly test the code for errors. 
2. **Documentation**: add documentation comments to your code, and use them to generate useful documentation for your users. Ideally, the code comments should be detailed enough to allow any other developer to interface with your code if it is a library, or possibly add their own features. You may also need to write a short `README.md` file giving basic instructions for how to use your application.
3. **Code Style**: make sure your code does not contain any style errors. Tools such as `checkstyle` and `flake8` are powerful ways to make sure your code is complete, easy to read, and follows standard coding styles.
4. **Debugging & Logging**: review your code and make sure that any debugging statements are either disabled or configured properly. Likewise, you may wish to adjust the amount of logging performed, or disable logging entirely. 
5. **Review & Reduce Dependencies**: if your application relies on many external dependencies or libraries, you may want to review them and make sure they are strictly required. The fewer dependencies your application has, the easier it is for your users to manage those dependencies. If needed, provide an easy way to acquire dependencies using build tools such as `Gradle` or `pip3`, or consider packaging dependencies with your application if the license allows it.
6. **Test on Multiple Platforms**: where possible, try to use your application on as many different platforms and versions of the underlying programming language as possible. A common issue is that software works correctly on the developer's system, only to cause issues when executed on another version or operating system. 
7. **Make Hard Coded Variables Configurable**: if your application includes any hard-coded variables that would need to be changed by the user, consider making them configurable using a configuration file. A popular option is to use a clone of the `dotenv` project from the Ruby programming language. Popular options include [dotenv-java](https://github.com/cdimascio/dotenv-java) for Java and [python-dotenv](https://pypi.org/project/python-dotenv/) for Python.
8. **Remove any Sensitive Information**: make sure that your code or configuration files don't include any sensitive information, such as default passwords, API or SSH keys, or any other information that would not be good to release publicly. If this information has been committed to git, you will want to remove it from the repository's history as well. Refer to the [Removing sensitive data from a repository](https://docs.github.com/en/github/authenticating-to-github/removing-sensitive-data-from-a-repository) guide from GitHub for information on how to do this.
9. **Create a Name**: before releasing your software, it is very helpful to come up with a uniquely identifiable name, especially if you intend to publish it to a software repository such as [Maven Central](https://search.maven.org/) or [PyPi](https://pypi.org/). 

Of course, these are just a few of the things we may want to review before deciding our application is ready for publication. It's always worth taking the time to think about how useful our application will be to our users before taking the next step. 
 
