---
title: "Metadata"
weight: 20
pre: "4. "
---
Another major step in creating a software release is to add some **metadata** to your project. The [metadata](https://en.wikipedia.org/wiki/Metadata) attached to an application typically includes items such as the version, author, and title. Depending on the format, it may also include additional items such as the main website for the application, and a place where bugs or issues may be reported.

The Java JAR file format includes a file named `Manifest.txt` that can include this information. The Oracle Java Tutorials website includes a page for [Setting Package Version Information](https://docs.oracle.com/javase/tutorial/deployment/jar/packageman.html) that describes the various entries that can be added to that file. In addition, some of this metadata may be added to your project when it is published on one of the repositories available for Java, such as [Maven Central](https://search.maven.org/).

The Python wheel file format uses a special file called `setup.cfg` that lists all of the [metadata](https://packaging.python.org/tutorials/packaging-projects/#configuring-metadata) that can be included in the project. There are many different items that can be specified in that file, which are all covered in the [Core metadata specifications](https://packaging.python.org/specifications/core-metadata/) file in the Python documentation. 

In either case, before publishing a release of our application, we should take a minute or two and add any required metadata to our project. This will make it easier for other users to find our application, and it helps us clearly specify items such as the version of our application and any dependency requirements.
