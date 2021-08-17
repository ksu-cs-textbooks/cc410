---
title: "Items to Exclude"
weight: 35
pre: "7. "
---
Another important concept to keep in mind when serializing data is that there are some items that _don't_ serialize very well, and others that can be omitted. Let's review a few of those now.

## Operating System Objects

One example of things that don't serialize well are objects provided by the operating system itself. This includes things such as open files, input and output streams, and threads. In each case, these objects rely on data provided by the operating system, making it difficult to serialize the object directly.

Instead, we can externally save the state, such as the current position we are reading from in the file, or the current object the thread is manipulating, and then use that to recreate the object later on. 

## Dependent Data

The other type of data that you may not wish to serialize is data that is dependent on other data. For example, a program might contain multiple copies of the same class, or have a class where one attribute is computed from other attributes. In order to save space, you may choose to only serialize the data that is required to reconstruct the rest, and perform the reconstruction when loading the data from the file. This will save storage space, but may cost additional computation time. So, we must evaluate the tradeoff and determine which option fits our use case the best.
