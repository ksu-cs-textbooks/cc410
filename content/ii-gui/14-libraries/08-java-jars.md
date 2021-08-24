---
title: "Java JARs"
weight: 40
pre: "8. "
---

Java typically uses a special type of file called a [JAR](https://en.wikipedia.org/wiki/JAR_(file_format)) file, short for "Java Archive" file, to create a downloadable package that may contain Java source code, compiled class files, and additional data. We can even include compiled Javadoc documentation directly in a JAR file.

Most software libraries for Java are distributed as JAR files, including from the major repositories such as [Maven Central](https://search.maven.org/). In addition, most websites that offer direct downloading of Java libraries typically use the JAR file format. 

A JAR file itself is built using the same format as the [ZIP](https://en.wikipedia.org/wiki/ZIP_(file_format)) file format. The Java Runtime Environment includes a special command `jar` that can be used to create a JAR file or extract the contents from an existing JAR file.

Finally, a JAR file can include additional information in a manifest file, giving the details such as the version of the software and the developer. The manifest file can also specify the main class of the application included in the JAR file. If so, then the JAR file can effectively be executed as an application, and many operating systems support double-clicking on a JAR file to run it as a Java program. 

## Installing a JAR File

There are a couple of ways we can install a JAR file into our applications. In effect, we need to add them to our [classpath](https://en.wikipedia.org/wiki/Classpath), which is used by the Java compiler and Java runtime environment to locate the resources it needs to operate.

When using Gradle, this process can be greatly simplified. In the `build.gradle` file, there are two important sections. First, there is a section for `repositories` that lists the repositories we can use for downloading and installing packages:

```groovy
repositories {
    // Use Maven Central for resolving dependencies.
    mavenCentral()
}
```

As shown here, our project will use [Maven Central](https://search.maven.org/) to resolve and install any packages required.

Below that, there is a section for `dependencies` that lists the packages required by this project:

```groovy
dependencies {
    // Use JUnit Jupiter API for testing.
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.6.2', 'org.hamcrest:hamcrest:2.2', 'org.junit.jupiter:junit-jupiter-params', 'org.mockito:mockito-inline:3.8.0', 'org.mockito:mockito-junit-jupiter:3.8.0'

    // Use JUnit Jupiter Engine for testing.
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine'

    // This dependency is used by the application.
    implementation 'com.google.guava:guava:29.0-jre', files('lib/restaurantregister-v0.1.0.jar')
}
```

The dependencies section contains three lists of packages

* `testImplementation` - packages used for compiling unit tests
* `testRuntimeOnly` - packages used for running unit tests
* `implementation` - packages required to compile and run the main source of the application

Typically, we'll install most libraries by adding them to the `implementation` list. In this example, we can see that our application uses two libraries:

1. The [Google Guava](https://github.com/google/guava/wiki) library, which will be installed from the repository listed above.
2. A custom library called `restaurantregister`, which was manually downloaded as a JAR file that is now contained in the `lib` folder of our project's directory. In this way, we can add any manually downloaded JAR files to our application by simply listing them in the `build.gradle` file. 

### References

* [Using JAR Files: The Basics](https://docs.oracle.com/javase/tutorial/deployment/jar/basicsindex.html) from Oracle Java Tutorials
* [JAR File Overview](https://docs.oracle.com/javase/8/docs/technotes/guides/jar/jarGuide.html) from Oracle
* [JAR (file format)](https://en.wikipedia.org/wiki/JAR_(file_format)) on Wikipedia
