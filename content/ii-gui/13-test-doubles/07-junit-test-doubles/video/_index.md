---
title: "Java Test Doubles"
pre: "3.J. "
weight: 30
date: 2020-02-28T00:53:26-05:00
hidden: true
---

{{< youtube sSokD2zkA8A >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

To use test doubles in Java, we're going to rely on the Mockito library. Mockito is one of the most popular libraries for this task in Java, and it easily integrates with the JUnit 5 framework we're already using.

To install Mockito, we just have to add a couple of entries to our `build.gradle` file, as shown here. The `mockito-inline` library contains the core Mockito classes, and the `mockito-junit-jupiter` library includes additional functionality that allows Mockito to interface directly with JUnit 5. 

Once we've installed those two libraries, we can use Mockito in our unit tests. This example shows the initial set of classes that need to be imported into our code in order to perform the basic work of creating fake objects and method stubs. At the bottom, we use the special `@ExtendWith` annotation above our test class to show that JUnit should use Mockito with this unit test. However, by default, this allows us to create fake objects and stubs that are unused without Mockito complaining.

So, instead, we can use the `@MockitoSettings` annotation and set the strictness to `STRICT_STUBS` as shown here. In this way, if we write a unit test that includes a fake object or stub that is unused, or if we try to call a method in a fake object that does not include a stub, Mockito will warn us so we can correct the error. This setting will most likely be enabled by default in future versions of Mockito, but for now we'll include it ourselves.

To create a fake object using Mockito, we can just declare an object with the `@Mock` annotation above it. That tells Mockito to create a fake version of the object instead of the real implementation. Then, we can use those objects in our code just like any other object. For example, we can add our fake `Teacher` object to our `Classroom` object, and it will see that it received an object of the expected type. As long as we don't call any methods in the `Teacher` class, we'll be fine.

However, if we want to call those methods, we'll have to include method stubs in our code. In Mockito, there are several ways to do this, but the easiest is to use the `when()` method as shown here. In this method, we are showing that when the `getName()` method is called on our fake teacher object, it should just return the string `"Teacher Person"`. So, in our unit test below, whenever that method is called in the `Classroom` class, it will get that result, and we can use it to verify the expected output.

Finally, what if we want to create a fake version of a static class? This is a bit more difficult, but thankfully it was added to a recent version of Mockito. We can use the `mockStatic()` method as shown here to create a fake version of a static class. The only catch is that we must do this in a try with resources statement, which makes sure that the fake static class doesn't stick around after the unit test. Just like any other class, we can add method stubs to static methods in our fake static class, and then when those static methods are called anywhere within our test it will use our stubbed versions, allowing us to control what the rest of the application sees.

As we can see, using Mockito to create fake objects and method stubs in Java is quite simple. However, this is just scratching the surface of what Mockito can really do. So, feel free to refer to the documentation for additional information and ideas of ways you can use Mockito in your unit tests. 