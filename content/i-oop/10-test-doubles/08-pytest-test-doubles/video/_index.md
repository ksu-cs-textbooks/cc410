---
title: "Python Test Doubles"
pre: "3.P. "
weight: 35
date: 2020-02-28T00:53:26-05:00
hidden: true
---

{{< youtube pNqcrx785Gs >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

To use test doubles in Python, we're going to rely on the built-in `unittest.mock` library. This is by far the easiest way to work with fake objects and method stubs in Python, and we don't have to install anything else to use it. So, all we have to do is import a few parts of that library into our code. In most cases, we're going to use the `patch` annotation, so that's what we'll import initially.

To create a fake object using patch, we'll add the `@patch` annotation above the unit test method that will use the fake object. In the `@patch` annotation, we include the full path of the object we are creating as a string, as well as a `spec` attribute that points to the name of the class we would like it to mimic. So, in this example, we are creating fake versions of the `people.Teacher` and `people.Person` classes, using those class names as the spec we'd like to follow. Then, inside of our method definition, we include those objects as parameters. Notice that the `@patch` annotations are applied inside out. So, the first one for `Teacher` is the last method parameter, and they work inward from there. This also means that any parameterized unit tests will have the `@pytest.mark` annotations above the `@patch` annotations. Finally, inside of our unit test method, we can use those objects just like we would real instances of that class. They'll satisfy any type checking we do, and will work just fine as lon as we don't call any methods on that object. 

However, if we want to call those methods, we'll have to include method stubs in our code. In Python, there are several ways to do this, but the easiest is to just replace the method's `return_value` attribute with our desired output. Any fake object in Python will already include default implementations of any method, but they will just return nothing. So, we can just update that value to return `"Teacher Person"`, and then in our unit test we can verify that we receive the correct output.

Creating a stub for a property is similar. Instead of changing a method's return value, we attach a `PropertyMock` to the type of the fake object. Each fake object created by Python will be given its own type, which we can modify to achieve certain outcomes. So, we simply update the `name` attribute of the type of our `fake_teacher` object to a `PropertyMock` that returns our desired value. Now, in our code, anything that accesses the `name` property will receive that value. Pretty handy!

Finally, what if we want to create a fake version of a static class? This is a bit more difficult, but thankfully it can be done. Here, we are using the `patch.object` method to create a method stub for a static method in the `TeacherRules` class. The only catch is that we must do this in a `with` statement, which makes sure that the fake static method doesn't stick around after the unit test. When those static methods are called anywhere within that `with` statement, it will use our stubbed versions, allowing us to control what the rest of the application sees.

As we can see, using `unittest.mock` to create fake objects and method stubs in Python is quite simple. However, this is just scratching the surface of what that library can really do. So, feel free to refer to the documentation for additional information and ideas of ways you can use `unittest.mock` in your unit tests. 
