---
title: "Introduction"
pre: "1. "
weight: 10
date: 2020-03-06T00:53:26-05:00
hidden: true
---

{{< youtube 9hdiuaZ2wRY >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

In this chapter, we're going to look at how we can use external libraries within our own applications. One of the major mantras of most programmers is "don't reinvent the wheel" and I feel that making ample use of good external libraries is the greatest example of that mantra put into practice. There are libraries out there for nearly any use, from parsing command-line arguments to interfacing with online APIs, that we can easily use. On this slide, we sees a quick diagram showing what it might look like for us to make use of a library for playing Ogg Vorbis files, an audio file format similar to an MP3. In our application, represented by the "program" box on the right, we include the library and then call its functions to use it. So, we can get the name of an Ogg file, and then send it to the library called "libvorbisfile" to help us read the file and turn it into an audio stream, which it will send back. So, the library is outside of our application's code, but we can interact with it by passing messages, or calling functions, as defined by the publicly available API of the library. 

Put another way, a software library is simply a collection of shared resources that can by used by a computer program. However, that library can actually come in many forms and be used in many ways.

There are three basic types of software libraries that we'll discuss here. The first is a static library. A static library is library code that is directly linked into our program's executable code. This means that the library is contained within our application itself. This makes more sense for programs written in languages like C or C++ that are actually compiled directly to an executable. However, since this course focuses on Java and Python, which each rely on a secondary application to run on our computer, we really don't deal with static libraries. Similarly, a dynamic library is one that our program can link to and access when it is executed. On Windows, these are typically called DLL files, short for "dynamic-link library." Finally, the third type of library is the class library, sometimes also referred to as an object library. A class library is a set of source code files, or compiled classes, that we can make use of in our own applications. The vast majority of libraries that we'll use in Java and Python take the form of a class library, though some of them may also make use of their own dynamic libraries to interface directly with the hardware on our computer. 

Let's also briefly discuss the difference between a library and a framework, as many developers tend to use the terms interchangeably, even though they have different meanings. In short, a library is code that we import and use in our application. So, our code is the one calling the library and telling it what to do. A framework, on the other hand, is a wrapper around the code that we write. So, the framework is responsible for calling the pieces of code that we are writing. Frameworks are most typically used for writing websites and scientific applications, so we haven't worked with them directly yet, but we may explore them a bit later in this course.

Finally, you might be wondering where to find libraries for your applications. For that, we can turn to repositories. In programming, we use the term repository not only to refer to things such as git, which is a code repository, but also to places where libraries are stored and can be found and downloaded. For Java, the most commonly used repository is Maven Central. Previously many developers used JCenter, but that service is actually being discontinued in 2021 and most developers are encouraged to move to Maven Central if they haven't already. Our `gradle` application in Java handles searching for packages and downloading them from Maven Central for us. For Python, the community hosts a service called PyPI, or the Python Package Index, which is where the `pip3` tool goes to download and install various libraries. In addition, it is worth noting that services such as GitHub are also great places to find libraries and download them, particularly for Java, since posting a library to Maven Central can be a bit difficult to do.