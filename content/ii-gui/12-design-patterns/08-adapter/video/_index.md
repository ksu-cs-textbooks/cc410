---
title: "Structural Patterns"
pre: "3. "
weight: 30
date: 2020-02-28T00:53:26-05:00
hidden: true
---

{{< youtube Ibxsanf8DFc >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

Next, let's review one of the structural design patterns. The adapter pattern is used when we'd like to adapt an existing interface to match a different, more desirable interface. This could include renaming methods, designing new methods that call multiple methods in the existing interface, or translating data types and values to fit a different use case. 

Let's look at a quick example - converting temperature from fahrenheit degrees to celsius degrees. So, let's assume we have a class that represents a temperature in fahrenheit, and we'd like to write an adapter that fits the `Celsius` interface shown below. There are a couple of different approaches we can use within the adapter pattern.

First, we could create an object adapter, which simply encapsulates an existing `Fahrenheit` object and implements the desired interface. So, when we call the `getTempCelsius()` method, it will call the `getTempFahrenheit()` method on the encapsulated object, then convert the result before returning it. This method works well if we want to completely hide the the interface that we are adapting and only make the new interface's methods available.

The other option would be to create a class adapter by inheriting the existing `Fahrenheit` class and then implementing the new `Celsius` interface as well. So, when we call the `getTempCelsius()` method, our code will call the `getTempFahrenheit()` method that is present in the parent class, then convert the result and return it. This approach works well when we want to keep the old interface's methods and just add our own. In that way, any code expecting the old interface will still work as we write new code that uses the adapter. 

However, in most cases we probably want to choose the object adapter route, so we can better control exactly what our code can access in the underlying object. In most cases, when we are writing an adapter we want to prevent anyone from bypassing it and accessing the old interface directly, as that could be very difficult to maintain or test if the old interface changes in ways we don't expect. Thankfully, the adapter pattern makes this very easy to do!