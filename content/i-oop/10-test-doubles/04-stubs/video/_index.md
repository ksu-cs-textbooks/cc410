---
title: "Stubs, Fakes, & Mocks"
pre: "2. "
weight: 20
date: 2020-02-28T00:53:26-05:00
hidden: true
---

{{< youtube SQUTcxc3RYo >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

Next, let's review the three basic types of test doubles that we'll work with in this chapter. However, before we do that, a quick note on terminology. In this chapter, and throughout this course, I'll try to do my best to use consistent terms for these three items, However, in practice and in industry, these terms are used very loosely and interchangeably. In fact, it seems like there are just as many discussions online pertaining to the use and definition of these terms as there are discussion of how to actually use them properly. So, I'm presenting one set of terms here, which is a set that I find to be useful. However, in practice, most places will simply use the term "mock" to refer to all three of these in various ways including both of the frameworks we'll explore in Java and Python. So, with that said, here they are.

The first one we'll look at is a stub, sometimes referred to as a method stub. A stub is simply a fake implementation of a method that returns some value, typically one that is hard coded in to the stub. It is most typically used to mimic accessing a data structure or performing a long and complex calculation. 

The biggest reason to use a stub is to avoid making function calls to external classes or packages, and instead replacing those function calls with stubs that mimic the same API and possible return values. In addition, we can write our tests to not only test for expected return values, but we can also easily test what our code will do if the external class returns an error value for some reason, making sure our class can handle anything that it receives.

The next one is the fake object, sometimes referred to as a mock object, though we will use the term differently. As shown here, a fake object is used as a substitute for a real object in our code. In this case, we could create a fake version of the class that handles user accounts, allowing us to use some default accounts for testing instead of accessing the real system where they are stored.

One major use of a fake object is to satisfy the type checker in our program. A fake object implements the same interface as the real one, though those implementations may simply contain or return some default data. However, we can improve our fake objects by adding some method stubs to them, allowing it to perform a few operations just like the real object would. Finally, many fake objects include some simplified implementation of the data stored in the class. A classic example is creating a fake class to represent a database, using a small hash table to store a few elements instead of accessing the entire database of real data when running unit tests. 

Finally, we have the mock object, sometimes referred to as a test spy. A mock object is similar to fake, but with one major change. We can use a mock object to keep track of the methods called and operations performed on it, and then review those results to make sure our code is functioning properly. 

Consider the example where our code must call a specific method in an external class and provide it some data. Instead of calling that external class, we can replace it with a mock object and then examine the method that was called and the arguments that were provided. In this way, we can examine not only the returned values of our code, but also the side effects that come from it interacting with other parts of the system. So, using mocks in a strategic way allows us to examine how well our code interfaces with the rest of the application.

So, in total, we have lots of different ways we can use test doubles in our unit tests. It all comes down to simplifying our code and making sure we are only testing the class or method we are concerned about. By replacing any external classes or methods with fakes and stubs, we can carefully control what our test does and what our code sees, making sure that it works exactly as intended. 