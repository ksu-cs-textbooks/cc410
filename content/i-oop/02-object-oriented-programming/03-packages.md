---
title: "Packages"
weight: 15
pre: "3. "
---

Let's start by focusing on encapsulation's benefits to organizing our code by exploring some examples of encapsulation you may already be familiar with.

## Packages

The Java and Python libraries are organized into discrete units called **_packages_**.  The primary purpose of this is to separate code units that potentially use the same name, which causes *name collisions* where the compiler or interpreter isn't sure which of the possibilities you mean in your program.  This means you can use the same name to refer to two different things in your program, provided they are in different packages. Many other languages refer to these as **_namespaces_**.

For example, there are two definitions for a `Date` class in Java: [java.util.Date](https://docs.oracle.com/javase/8/docs/api/java/util/Date.html) and [java.sql.Date](https://docs.oracle.com/javase/8/docs/api/java/sql/Date.html). While they are related, they serve different purposes, and we wouldn't want to get them confused. If we needed to create an instance of both in our program, we would use their fully-quantified name to help the compiler know which we mean:

###### Java

```java
java.sql.Date sqlDate = new java.sql.Date(System.currentTimeMillis());
java.util.Date utilDate = new java.util.Date(System.currentTimeMillis());
System.out.println(sqlDate.toString());
System.out.println(utilDate.toString());
```

Running that code gives this output:

```tex
2020-12-30
Wed Dec 30 17:23:50 GMT 2020
```

So, as we can see, these two classes are functionally different in some important ways. 

While Java does not support aliases in imports, we can use an alias in Python to import two classes with the same name using different identifiers. For example, if there are two `User` classes in different packages, we could import them like this:

###### Python

```python
from package_one import User as PackageOneUser
from package_two import User as PackageTwoUser

user_1 = PackageOneUser.User()
user_2 = PackageTwoUser.User()
```

Encapsulating code within a package helps ensure that the types defined within are only accessible with a fully qualified name, or when the using directive is employed.  In either case, the intended type is clear, and knowing the package can help other programmers find the type's definition.

## Creating Packages

We can also declare our own packages, allowing us to use packages to organize our own code just as Java and Python have done with their standard libraries. Below are quick examples for how to do this in Java and Python.

### Java

To create a class `ClassName` in a package `cc410.package_name`, we would include a `package` line at the top of the file:

```java
package cc410.package_name;

public class ClassName{
    //code here
}
```

The `ClassName.java` file would be stored in `app/src/main/java/cc410/package_name/`. Basically, the package name corresponds to the folders where the source code is stored. 

### Python

To create a class `ClassName` in a package `cc410.package_name`, we would simply place `ClassName.py` in the `src/cc410/package_name` directory. We'd also need to include an `__init__.py` file in that directory to make it a package. 

Finally, if we want the `cc410` package to act as a meta-package and be executable we would also include an `__init__.py` and a `__main__.py` file in the `src/cc410` directory as well.

{{% notice note "Seeing Double?" %}}

In previous textbooks, we created different sections for both Java and Python code, so generally students would only see one or the other.

In this class, we feel that it is important for developers to become familiar with more than one language, as it may help increase understanding. So, nearly all examples in this book will be presented using both Java and Python. We will clearly label each language where needed, but hopefully at this point you are comfortable enough with your chosen language to recognize it clearly. 

{{% / notice %}}
