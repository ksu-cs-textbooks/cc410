---
title: "Summary"
weight: 60
pre: "12. "
---

In this chapter, we learned about **software libraries** and how we can use them in our applications. We explored the different types of libraries, including **static libraries**, **shared libraries**, and **class libraries**. We discussed the differences between libraries and **frameworks** and how to tell the difference. We also covered **repositories** and how to search for and download helpful software packages we can use. 

In addition, we discussed the various **licenses** that may be attached to software libraries we use in our code, and how that may impact our ability to license and distribute our software in the future. We also looked at why it is worth the hassle of finding and downloading these libraries instead of writing the code ourselves.

Finally, we looked at the Java JAR and Python wheel file formats, and how to install those packages into our applications. We also listed some common software packages for both Java and Python that we may want to use ourselves. 

In the example project for this chapter, we'll look at how to download and install a custom package for our class project and how to integrate it into our code.

{{< quizdown >}}

---
primaryColor: '#512888'
secondaryColor: '#cccccc'
textColor: black
shuffleQuestions: true
shuffleAnswers: true
locale: en
---

# Software Library

A **software library** is best described by which statement?

1. [X] A package or module developed outside our application
1. [ ] A list of applications we can use on our computer
1. [ ] A common structure in code to solve a particular problem
1. [ ] A set of variables used to access the memory on a system

# Modular Code

What is one major benefit of writing code in a modular format that is discussed in this chapter? 

1. [X] Code can be reused between many applications
1. [ ] Programs are smaller and easier to understand
1. [ ] UML diagrams of the system are less complex
1. [ ] Short methods are more efficient

# Static Library

A **static library** is best described by which statement?

1. [X] Library code that is included in our application's executable file
1. [ ] Library code that is accessed dynamically at runtime
1. [ ] Library code that contains classes we can use in our code
1. [ ] Library code that is only used once by the application

# Shared Library

A **shared library** is best described by which statement?

1. [ ] Library code that is included in our application's executable file
1. [X] Library code that is accessed dynamically at runtime
1. [ ] Library code that contains classes we can use in our code
1. [ ] Library code that is only used once by the application

# Class Library

A **class library** is best described by which statement?

1. [ ] Library code that is included in our application's executable file
1. [ ] Library code that is accessed dynamically at runtime
1. [X] Library code that contains classes we can use in our code
1. [ ] Library code that is only used once by the application

# Framework

Which of the following statements accurately differentiates between a **software library** and a **software framework**?

1. [X] A framework calls our code, and our code calls a library's code
1. [ ] A library calls our code, and our code calls a framework's code
1. [ ] Our code calls a framework's code, and a framework calls a library's code
1. [ ] Our code calls a library's code, and a library calls a framework's code

# Framework Patterns

A software framework commonly uses what software design pattern, allowing us to override and implement parts of a method while it controls the overall structure of the method?

1. [X] Template method pattern
1. [ ] Factory method pattern
1. [ ] Adapter pattern
1. [ ] Iterator pattern

# Repository

When discussing software libraries, a **repository** is best described by which statement?

1. [X] A database of libraries that can be downloaded and used
1. [ ] An online storage device for user data
1. [ ] An encrypted store for usernames and passwords
1. [ ] A container for installing software libraries in an application

# Package

Many software libraries are distributed using **packages**, which are best described by which statement?

1. [X] The library and all supporting files bundled together
1. [ ] A file that only contains a single class
1. [ ] A tool for downloading and installing libraries
1. [ ] A container for installing software libraries in an application

# Security

Which of the following items are listed as a security concern to keep in mind when reviewing a software library (choose all that are correct)?

- [X] The purpose of the library 
- [X] How popular the library is
- [X] Whether the code is open source or not
- [X] The license applied to the software
- [X] The developer of the software

# Free Software

According to the Free Software Foundation, which of the following is **not** one of the four freedoms used to determine if software is truly free?

1. [X] Resell
1. [ ] Use
1. [ ] Study
1. [ ] Share
1. [ ] Improve

# Public Domain

A **public domain** software license is best described by which statement?

1. [X] Software can be used by anyone for any purpose without restriction
1. [ ] Few restrictions, typically protecting the author from liability
1. [ ] Derivative works must be released under the same license
1. [ ] Software is not open source or free and restrictions vary widely

# Permissive License

A **permissive** software license is best described by which statement?

1. [ ] Software can be used by anyone for any purpose without restriction
1. [X] Few restrictions, typically protecting the author from liability
1. [ ] Derivative works must be released under the same license
1. [ ] Software is not open source or free and restrictions vary widely

# Copyleft License

A **copyleft** software license is best described by which statement?

1. [ ] Software can be used by anyone for any purpose without restriction
1. [ ] Few restrictions, typically protecting the author from liability
1. [X] Derivative works must be released under the same license
1. [ ] Software is not open source or free and restrictions vary widely

# Proprietary License

A **proprietary** software license is best described by which statement?

1. [ ] Software can be used by anyone for any purpose without restriction
1. [ ] Few restrictions, typically protecting the author from liability
1. [ ] Derivative works must be released under the same license
1. [X] Software is not open source or free and restrictions vary widely

# Creative Commons CC0

The **Creative Commons CC0** license is an example of which type of software license?

1. [X] Public Domain License
1. [ ] Permissive License
1. [ ] Copyleft License
1. [ ] Proprietary License

# BSD and Apache

The **BSD** and **Apache** licenses are examples of which type of software license?

1. [ ] Public Domain License
1. [X] Permissive License
1. [ ] Copyleft License
1. [ ] Proprietary License

# GNU General Public License

The **GNU General Public License (GPL)** is an example of which type of software license?

1. [ ] Public Domain License
1. [ ] Permissive License
1. [X] Copyleft License
1. [ ] Proprietary License

# Apple

The **Apple Licensed Application End User License Agreement** is an example of which type of software license?

1. [ ] Public Domain License
1. [ ] Permissive License
1. [ ] Copyleft License
1. [X] Proprietary License

# Don't Reinvent the Wheel

True or false: when developing a new software application from scratch, it is not worth looking to see if a software library would meet that need since it is unlikely to exist? 

1. [ ] True
1. [X] False

{{< /quizdown >}}