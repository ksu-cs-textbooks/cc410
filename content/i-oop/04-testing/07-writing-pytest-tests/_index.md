---
title: "Writing pytest Tests"
weight: 35
pre: "7. "
---

{{% youtube _5txXZHtFkw %}}

[Video Materials]({{<relref "./video">}})

Writing tests is in many ways just as challenging and creative an endeavor as writing programs.  Tests usually consist of invoking some portion of program code, and then using _assertions_ to determine that the actual results match the expected results.  The result of these assertions are typically reported on a per-test basis, which makes it easy to see where your program is not behaving as expected.  

Consider a class that is a software control system for a kitchen stove. We won't write the code for the class itself, because it is important for us to be able to write tests that effectively test the code without even seeing it. It might have properties for four burners, which correspond to what heat output they are currently set to.  Let's assume this is as an integer between 0 (off) and 5 (high).  When we first construct this class, we'd probably expect them all to be off!  A test to verify that expectation would be:

```python
from src.hello.Stove import Stove

class TestStove:
    
    def test_burners_should_be_off_at_initialization(self):
        stove = Stove()
        assert stove.burner_one == 0, "Burner is not off after initialization"
        assert stove.burner_two == 0, "Burner is not off after initialization"
        assert stove.burner_three == 0, "Burner is not off after initialization"
        assert stove.burner_four == 0, "Burner is not off after initialization"
```

Here we've written the test using the [pytest](https://docs.pytest.org/en/stable/) test framework, which is one of the most commonly used Python unit testing frameworks today.

Notice that the test is simply a method, defined in a class.  This is very common for test frameworks, which tend to be written using the same programming language the programs they test are written in (which makes it easier for one programmer to write both the code unit and the code to test it).  The test method itself is prefixed with `test`, as well as the file where the test is stored. In addition, the class name also includes the word `Test`. These naming conventions help pytest find test methods in the code, as described in the [pytest Guide](https://docs.pytest.org/en/stable/goodpractices.html#conventions-for-python-test-discovery). Omitting the `test` prefix in the method name allows us to build other helper methods within our test classes as needed. 

Inside the method, we create an instance of stove, and then use the `assert` statement to determine that the actual and expected values match.  If they do, the assertion is marked as passing, and the test runner will display this pass.  If it fails, the test runner will report the failure, along with details to help find and fix the problem (what value was expected, what it actually was, and which test contained the assertion). 

The pytest framework provides for two kinds of tests, _standard tests_, which are written as functions that have no parameters, and _parameterized tests_, which do have parameters.  The values for these parameters are supplied with a special method annotation, typically `@pytest.mark.parametrize`.  For example, we might test that when we set a burner to a setting within the valid 0-5 range, it is set to that value:

```python
from src.hello.Stove import Stove
import pytest

class TestStove:
        
    @pytest.mark.parametrize("value", [0, 1, 2, 3, 4, 5])
    def test_should_be_able_to_set_burner_one_to_valid_range(self, value):
        stove = Stove()
        stove.burner_one = value
        assert stove.burner_one == value, "Burner does not have expected value"
```

{{% notice warning "Spelling" %}}

Note the creative spelling of the `@parametrize` annotation! Be careful to not misspell it (by spelling it correctly) in your code.

{{% / notice %}}

The values in the parentheses of the `@parametrize` annotation are the values supplied to the parameter list of the parameterized test method.  Thus, this test is actually _six_ tests; each test makes sure that one of the settings is working.  We could have done all six as separate assignments and assertions within a single test method, but using a parameterized test means that if only one of these settings doesn't work, we will see that one test fail while the others pass.  This level of specificity can be very helpful in finding errors.

So far our tests cover the expected behavior of our stove.  But where tests really prove their worth is with the _edge cases_ - those things we as programmers don't anticipate.  For example, what happens if we try setting our range to a setting above 5?  Should it simply clamp at 5?  Should it not change from its current setting?  Or should it shut itself off entirely because its user is clearly a pyromaniac bent on burning down their house? If the specification for our program doesn't say, it is up to us to decide.  Let's say we expect it to be clamped at 5:

```python
@pytest.mark.parametrize("value", [6, 18, 1000000])
def test_burner_one_should_not_exceed_five(self, value):
    stove = Stove()
    stove.burner_one = value
    assert stove.burner_one == 5, "Burner does not have expected value"
```

Note that we don't need to exhaustively test all numbers above 5 - it is sufficient to provide a representative sample, ideally the first value past 5 (6), and a few others.  Also, now that we have defined our expected behavior, we should make sure the documentation of our burner one property matches it:

```python
@property
def burner_one(self) -> int:
   """Sets the value of Burner One.
   
   Should be an integer between 0 (off) and 5 (high)
   If a value higher than 5 is provided, the burner will be 
   set to 5 instead. 
   
   Args:
       value: the value of the burner
   """
```

This way, other programmers (and ourselves, if we visit this code years later) will know what the expected behavior is.  We'd also want to test the other edge cases: i.e. when the burner is set to a negative number.

For a complete guide to parameterized tests in pyunit, refer to the [pyunit Guide](https://docs.pytest.org/en/stable/parametrize.html#parametrize-basics).

{{% notice tip "Edge Cases" %}}

Recognizing and testing for edge cases is a critical aspect of test writing. But it is also a difficult skill to develop, as we have a tendency to focus on expected values and expected use-cases for our software. But most serious errors occur when values outside these expectations are introduced.  Also, remember special values, like `float("inf"),`, `float("-inf")`, and `float("nan")`.

{{% / notice %}}
