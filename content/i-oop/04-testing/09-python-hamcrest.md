---
title: "Python Hamcrest"
weight: 45
pre: "9. "
---
We can also choose to use the [Hamcrest](https://pyhamcrest.readthedocs.io/en/v2.0.2/#) assertion library in our code, either instead of the pyunit assertions or in addition to them. Hamcrest includes some very helpful assertions that are not part of pyunit, and also includes version for many languages, including both Python and Java. Most of the autograders in previous Computational Core courses are written with the Hamcrest assertion library!

### Basic Assertions

Hamcrest uses a single basic assertion method called `assert_that()` to perform all assertions. It comes in two basic forms:

* `assert_that(actual, matcher)` - asserts that `actual` passes the `matcher`.
* `assert_that(actual, matcher, message)` - asserts that `actual` passes the `matcher`. If not, it will print `message` as part of the failure.

The real power of Hamcrest lies in the use of [Matchers](https://pyhamcrest.readthedocs.io/en/v2.0.2/library/), which are used to determine if the `actual` value passes a test. If not, then the `assert_that` method will fail, just like a pyunit assertion. 

For example, to test if an actual value returned by a fictional `calculator` object is equal to an expected value, we could use this statement:

```python
assert_that(calculator.add(1, 3), is_(4))
```

As we can see, reading this statement out loud tells us everything we need to know: "Assert that `calculator.add(1, 3)` is 4!"

Here are a few of the most commonly used Hamcrest matchers, as listed in the [Hamcrest Tutorial](https://pyhamcrest.readthedocs.io/en/v2.0.2/tutorial/). The full list of matchers can be found in the [Matcher Library](https://pyhamcrest.readthedocs.io/en/v2.0.2/library/) in the Hamcrest documentation:

* `is_(expected)` - a shortcut for equality - an example of [**syntactic sugar**](https://en.wikipedia.org/wiki/Syntactic_sugar) as discussed below. Notice the underscore to differentiate it from the Python keyword `is`
* `equal_to(expected)` - will call the `actual.equals(expected)` method to test equality
* `instance_of(type)` - can be used to check if an object is the correct type, helpful for testing inheritance
* `none()` - check if the value is `None`
* `not_none()` - check if the value is not `None`
* `same_instance(expected)` - checks if two objects are the same instance
* `has_entry(key, value)`, `has_key(key)`, `has_value(value)` - matchers for working with mapping types like [dictionaries](https://docs.python.org/3/library/stdtypes.html#typesmapping)
* `has_item(item)` - matcher for sequence types like [lists](https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range)
* `close_to(expected, delta)` - matcher for testing floating-point values within a range
* `greater_than(expected)`, `greater_than_or_equal_to(expected)`, `less_than(expected)`, `less_than_or_equal_to(expected)` - numerical matchers
* `equal_to_ignoring_case(expected)`, `equal_to_ignoring_whitespace(expected)`, `cotnains_string(string)`, `ends_with(string)`, `starts_with(string)` - string matchers
* `all_of(matcher1, matcher2, ...)`, `any_of(matcher1, matcher2, ...)`, `is_not(matcher)` - boolean logic operators used to combine multiple matchers

### Syntactic Sugar

Hamcrest includes a helpful matcher called `is_()` that makes some assertions more easily readable. For example, each of these assertion statements from the [Hamcrest Tutorial](https://pyhamcrest.readthedocs.io/en/v2.0.2/tutorial/) all test the same thing:

```python
assert_that(theBiscuit, equal_to(myBiscuit))
assert_that(theBiscuit, is_(equal_to(myBiscuit)))
assert_that(theBiscuit, is_(myBiscuit))
```

By including the `is_()` matcher, we can make our assertions more readable. We call this _syntactic sugar_ since it doesn't add anything new to our language structure, but it can help make it more readable.
