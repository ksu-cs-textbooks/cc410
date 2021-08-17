---
title: "Binary Formats"
weight: 20
pre: "4. "
---
We already know that all the data stored by a computer is in a binary format. So, it of course makes sense to also look at ways we can store a program's state using a binary file format. 

## Binary Files

Many programming languages, including Java and Python, include libraries that can be used to generate binary files containing the state of an object in memory. Each language, and indeed each version of the language, may use a different format for storing the binary data in the file.

In this course, we won't dig into the actual format of the binary file itself, since that can quickly become very complex. However, we will discuss some of the pros and cons related to using a binary file format for serialization compared to a text format.

### Pros

One major advantage to the binary file format is that they are typically smaller in size than a comparable textual representation. This depends a bit on the language itself, but in general the binary structure doesn't need to store the name of each object and attribute in the file, just values they contain.

Likewise, reading and writing binary files is often very efficient, since the data doesn't have to be parsed to and from strings, which is an especially costly process for numeric data. 

Finally, since the binary files are generally not readable or editable by humans, they could prevent a user from intentionally or accidentally editing the data. Of course, this **should not** be thought of as any sort of a security mechanism, since any technically adept user could easily reverse-engineer the file format.

### Cons

A major downside of using binary files to store state is the fact that those files are only readable by the programming language they were created by, and in many cases they are locked to a particular version of the language. In some instances, even small changes to the source code of an object itself may invalidate any previously stored state when stored in a binary format.

Compare this to a textual format such as JSON, which can be easily read by any programming language. In fact, many times the JSON produced by a web server is created by a language other than JavaScript, and then the JavaScript running in the web application can easily parse and use it, no matter which language originally constructed it.

Another major downside is the fact that the files cannot be easily read or edited by a human. In some instances, the ability to manually edit a text file, such as a configuration file for a large application, is a very handy skill. We've already looked at several different configuration files for the applications we've built in this course, and the ability to edit them quickly helps us make major changes to the structure of our application. 

## Summary

The choice of textual or binary files for storing state is a tricky one. There are many reasons to choose either type, and it really comes down to how the data will be used. Many applications recently have moved from a proprietary, binary format to a more open format. For example, Microsoft Office documents are now stored in an XML format (`docx`, `xlsx`, `pptx`), making it easy for other tools to read and edit those documents. On the other hand, many computer games still prefer to store state and assets in binary, both to make them load quickly but also to prevent users from easily cheating by modifying the files. 

On the next few pages, we'll quickly look at how to generate and read some of these file formats in both Java and Python. As always, feel free to read the page for the language you are studying, but each page might contain useful information.
