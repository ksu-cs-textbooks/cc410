---
title: "Java Hamcrest"
weight: 30
pre: "6. "
---
We can also choose to use the [Hamcrest](http://hamcrest.org/JavaHamcrest/) assertion library in our code, either instead of the JUnit assertions or in addition to them. Hamcrest includes some very helpful assertions that are not part of JUnit, and also includes version for many languages, including both Java and Python. Most of the autograders in previous Computational Core courses are written with the Hamcrest assertion library!

### Basic Assertions

Hamcrest uses a single basic assertion method called `assertThat()` to perform all assertions. It comes in two basic forms:

* `assertThat(actual, matcher)` - asserts that `actual` passes the `matcher`.
* `assertThat(message, actual, matcher)` - asserts that `actual` passes the `matcher`. If not, it will print `message` as part of the failure.

The real power of Hamcrest lies in the use of [Matchers](http://hamcrest.org/JavaHamcrest/javadoc/2.2/org/hamcrest/Matchers.html), which are used to determine if the `actual` value passes a test. If not, then the `assertThat` method will fail, just like a JUnit assertion. 

For example, to test if an actual value returned by a fictional `calculator` object is equal to an expected value, we could use this statement:

```java
assertThat(calculator.add(1, 3), is(4));
```

As we can see, reading this statement out loud tells us everything we need to know: "Assert that `calculator.add(1, 3)` is 4!"

Here are a few of the most commonly used Hamcrest matchers, as listed in the [Hamcrest Tutorial](http://hamcrest.org/JavaHamcrest/tutorial). The full list of matchers can be found in the [Matchers](http://hamcrest.org/JavaHamcrest/javadoc/2.2/org/hamcrest/Matchers.html) class in the Hamcrest documentation:

* `is(expected)` - a shortcut for equality - an example of [**syntactic sugar**](https://en.wikipedia.org/wiki/Syntactic_sugar) as discussed below. 
* `equalTo(expected)` - will call the `actual.equals(expected)` method to test equality
* `isCompatibleType(type)` - can be used to check if an object is the correct type, helpful for testing inheritance
* `nullValue()` - check if the value is `null`
* `notNullValue()` - check if the value is not `null`
* `sameInstance(expected)` - checks if two objects are the same instance
* `hasEntry(entry)`, `hasKey(key)`, `hasValue(value)` - matchers for working with [Maps](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) such as [HashMaps](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html)
* `hasItem(item)` - matcher for [Collections](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html) such as [LinkedList](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html)
* `hasItemInArray(item)` - matcher for arrays
* `closeTo(expected, delta)` - matcher for testing floating-point values within a range
* `greaterThan(expected)`, `greaterThanOrEqualTo(expected)`, `lessThan(expected)`, `lessThanOrEqualTo(expected)` - numerical matchers
* `equalToIgnoringCase(expected)`, `equalToIgnoringWhiteSpace(expected)`, `containsString(string)`, `endsWith(string)`, `startsWith(string)` - string matchers
* `allOf(matcher1, matcher2, ...)`, `anyOf(matcher1, matcher2, ...)`, `not(matcher)` - boolean logic operators used to combine multiple matchers

### Syntactic Sugar

Hamcrest includes a helpful matcher called `is` that makes some assertions more easily readable. For example, each of these assertion statements from the [Hamcrest Tutorial](http://hamcrest.org/JavaHamcrest/tutorial) all test the same thing:

```java
assertThat(theBiscuit, equalTo(myBiscuit)); 
assertThat(theBiscuit, is(equalTo(myBiscuit))); 
assertThat(theBiscuit, is(myBiscuit));
```

By including the `is` matcher, we can make our assertions more readable. We call this _syntactic sugar_ since it doesn't add anything new to our language structure, but it can help make it more readable.

## Examples

There are lots of great examples of how to use Hamcrest available on the web. Here are a couple that are worth checking out:

* [Using Hamcrest for Testing - Tutorial](https://www.vogella.com/tutorials/Hamcrest/article.html) from Vogella
* [Testing with Hamcrest](https://www.baeldung.com/java-junit-hamcrest-guide) from Baeldung
