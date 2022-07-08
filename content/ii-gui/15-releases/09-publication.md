---
title: "Publication"
weight: 45
pre: "9. "
---

At long last, we have a package ready to go! The last optional step would be to publish our package to a package repository so others can easily download and use it through their development tools. We won't directly do that as part of this course, but below are some quick links and basic instructions to follow if you'd like to publish a package to a repository for your language.

## Java - Maven Central

Unfortunately, the process of getting a package posted on Maven Central is quite complex. It requires creating the packages as described in this chapter, as well as signing them with a PGP encryption key. Then, we'll need to create a Project Object Model, or `pom` file that describes the project and includes some additional metadata. Finally, we'll need to provide hosting for the actual packages themselves, though much of that can be handled through an open source repository hosted by Sonatype.

While this will make your package easier for other Java developers to discover and use, many smaller developers find this to be overly cumbersome if the project can be easily downloaded as a JAR file.

If you do choose to publish your package to Maven Central, here are some resources to help you get started:

* [Guide to uploading artifacts to the Central Repository](https://maven.apache.org/repository/guide-central-repository-upload.html) from the Apache Maven Project
* [Requirements](https://central.sonatype.org/pages/requirements.html) from Sonatype
* [Open Source Software Repository Hosting (OSSRH)](https://central.sonatype.org/pages/ossrh-guide.html) from Sonatype
* [Working with PGP Signatures](https://central.sonatype.org/pages/working-with-pgp-signatures.html) from Sonatype

{{% notice note "Java Package Naming" %}}

Java packages that are published to a central repository such as Maven Central must use a group ID based on a DNS domain name that you own or have control over. If the project is hosted on GitHub, you can use `io.github.<username>` as your group ID, since GitHub provides you the website `<username>.github.io` as part of GitHub pages. Otherwise, you may have to perform additional steps to reserve your group ID.

In addition, typically you will then place your code in a Java package that matches your group ID, which is your DNS domain name in reverse order. For example, the library code for this class uses the domain name `cc410.cs.ksu.edu`, which is a domain that we host at K-State. In the [source code](https://github.com/K-State-Computational-Core/restaurantregister-java) for this project, we place all of our code in the Java package `edu.ksu.cs.cc410`. In that way, we can guarantee that our package name is unique and no one else can use it.

{{% / notice %}}

## Python - PyPi

Thankfully, for Python this process is very simple. The [Packaging Projects](https://packaging.python.org/tutorials/packaging-projects/) tutorial from Python includes the steps to publish a package directly to PyPi:

1. Register an account at [test.pypi.org](https://test.pypi.org/account/register/) to test your package.
2. Create an [API Token](https://test.pypi.org/help/#apitoken) on [test.pypi.org](https://test.pypi.org/)
3. Install the `twine` package: `pip3 install --upgrade twine`
4. Upload the package to [test.pypi.org](https://test.pypi.org/) using `twine`:

```bash
python3 -m twine upload --repository testpypy dist/*
```

When you run that command, you'll be prompted for a username and password. If you created an [API Token](https://test.pypi.org/help/#apitoken), use `__token__` as the username and then enter your token as the password, including the `pypi-` prefix.

If everything goes correctly, you should now be able to see your package on [test.pypi.org](https://test.pypi.org/). The tutorial linked above includes instructions on how to test it by installing your package from the test PyPi repository.

Once you are satisfied, you can basically perform the same steps on the real [PyPi](https://pypi.org/) repository. You may need to update your package name in the `setup.cfg` file to make sure it is unique. 
