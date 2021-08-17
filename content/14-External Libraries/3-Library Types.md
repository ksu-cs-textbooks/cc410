---
title: "Library Types"
weight: 15
pre: "3. "
---
There are many different types of software libraries available. However, many modern languages such as Java and Python have greatly simplified the task of using these libraries. This is because both Java and Python rely on an underlying program to execute our code (either the Java Runtime Environment, or JRE for Java, or the Python Interpreter for Python), which handles connecting our code to the various libraries available on our system. So as developers we rarely need to worry about the differences in our code. 

However, if we develop programs using languages like C or C++ that are designed to be compiled directly to executables that run on the system, these different library types become much more important.

## Static Library

A [**static library**](https://en.wikipedia.org/wiki/Static_library) is a software library that is _statically linked_ to our executable file when it is compiled. [Linking](https://en.wikipedia.org/wiki/Linker_(computing)) a library involves combining our application's code with the libraries it uses into a single executable. So, that library's code is included directly in our application, and we don't have to include any additional files in order for our application to function. However, that means that we'll have to recompile our application completely each time we want to update any of the libraries that it uses. In addition, if many applications on a system all use the same library, they'll all have to include a copy of that library in their executable, sometimes eating up valuable storage space in the process. Originally, all libraries were static libraries, but eventually developers came up with a new, more flexible system. 

## Shared Library

A **shared library** is a software library that can be shared among multiple executable files. Instead of being included in the application when it is compiled, the library code can be _dynamically linked_ when the application is executed. So, when we load our program, the operating system can search for any required shared libraries on the system, load them into memory, and link them to our application so we can use them. Users of the Microsoft Windows operating system may be familiar with the DLL file type, which is the "dynamic-link library" format used by that operating system. So, a DLL file is simply a software library that is meant to be dynamically linked to an application when it executes.

The major benefit of this approach is that the library can be installed on a system just once, and then many different applications can make use of it without including that library's code in their individual executables. In addition, the library can be updated once on a system and the new version will be available for any application that uses it.

Unfortunately, there are several downsides to this approach as well. One major issue is when applications require different versions of the same library in order to function. In that case, the operating system must maintain several versions of the same library, and if done incorrectly this could lead to one application overwriting the library required by another. In addition, this means that the space savings by sharing libraries among applications can be greatly diminished if applications are not able to share the same version of the library. In fact, there are entire articles on Wikipedia dedicated to the issues with dynamically linked libraries, a problem collectively known as [Dependency Hell](https://en.wikipedia.org/wiki/Dependency_hell)

## Class Library

As object-oriented programming became more common, many programming languages started to support **class libraries** as a way to share code between applications. In this case, a **class library** is simply a set of classes, usually either provided as source code or a compiled version of the code, which can then be integrated into another application. In this way, the library looks just like any other portion of the software, and can easily be used by developers in their applications.

A great example of a class library are the [standard libraries](https://en.wikipedia.org/wiki/Standard_library) included with many programming languages, including Java and Python. We've used these libraries extensively in our code, mainly to support reading to and writing from files, storing data in data structures, and even creating GUIs for our applications. Anytime we import something into our code that we didn't write ourselves, we're taking advantage of a class library that was written by another developer. 

Going forward, when we refer to a software library in this course, we will usually be referring to a class library as described above. 

### References

* [Static Library](https://en.wikipedia.org/wiki/Static_library) on Wikipedia
* [Linker (computing)](https://en.wikipedia.org/wiki/Linker_(computing)) on Wikipedia
* [Dependency Hell](https://en.wikipedia.org/wiki/Dependency_hell) on Wikipedia
* [Standard Library](https://en.wikipedia.org/wiki/Standard_library) 
