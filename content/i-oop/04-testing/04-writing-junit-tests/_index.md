---
title: "Writing JUnit Tests"
weight: 20
pre: "4. "
---

{{% youtube w6rtzfr1jQ4 %}}

[Video Materials]({{<relref "./video">}})

Writing tests is in many ways just as challenging and creative an endeavor as writing programs.  Tests usually consist of invoking some portion of program code, and then using _assertions_ to determine that the actual results match the expected results.  The result of these assertions are typically reported on a per-test basis, which makes it easy to see where your program is not behaving as expected.  

Consider a class that is a software control system for a kitchen stove. We won't write the code for the class itself, because it is important for us to be able to write tests that effectively test the code without even seeing it. It might have properties for four burners, which correspond to what heat output they are currently set to.  Let's assume this is as an integer between 0 (off) and 5 (high).  When we first construct this class, we'd probably expect them all to be off!  A test to verify that expectation would be:

```java
import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.jupiter.api.Test;

public class StoveTest{
    
    @Test
    public void testBurnersShouldBeOffAtInitialization(){
        Stove stove = new Stove();
        assertEquals(0, stove.getBurnerOne(), "Burner is not off after initialization");
        assertEquals(0, stove.getBurnerTwo(), "Burner is not off after initialization");
        assertEquals(0, stove.getBurnerThree(), "Burner is not off after initialization");
        assertEquals(0, stove.getBurnerFour(), "Burner is not off after initialization");
    }
}
```

Here we've written the test using the [JUnit 5](https://junit.org/junit5/docs/current/user-guide/) test framework, which is one of the most commonly used Java unit testing frameworks today.

Notice that the test is simply a method, defined in a class.  This is very common for test frameworks, which tend to be written using the same programming language the programs they test are written in (which makes it easier for one programmer to write both the code unit and the code to test it).  Above the test method is a method annotation `@Test` that tells JUnit to use this method as a unit test. Omitting the `@Test` annotation allows us to build other helper methods within our test classes as needed.  Annotations are a way of supplying metadata within Java code.  This metadata can be used by the compiler and other programs to determine how it works with your code.  In this case, it indicates to the JUnit test runner that this method is a test.

Inside the method, we create an instance of stove, and then use the `assertEquals(actual, expected, message)` method to determine that the actual and expected values match.  If they do, the assertion is marked as passing, and the test runner will display this pass.  If it fails, the test runner will report the failure, along with details to help find and fix the problem (what value was expected, what it actually was, and which test contained the assertion).

{{% notice tip "Install JUnit 5 Parameters Library" %}}

To use the portions listed below, we'll need to modify our `build.gradle` file to include the following dependencies:

```gradle
dependencies {
    // Use JUnit Jupiter API for testing.
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.6.2', 'org.hamcrest:hamcrest:2.2', 'org.junit.jupiter:junit-jupiter-params'

    // Use JUnit Jupiter Engine for testing.
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine'
    
    // This dependency is used by the application.
    implementation 'com.google.guava:guava:29.0-jre'
}
```

Notice that we added a `junit-jupiter-params` library.

{{% / notice %}}

The JUnit framework provides for two kinds of tests, _Test_, which are written as functions that have no parameters, and _ParameterizedTest_, which do have parameters.  The values for these parameters are supplied with another annotation, typically `@ValueSource`.  For example, we might test that when we set a burner to a setting within the valid 0-5 range, it is set to that value:

```java
import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.jupiter.api.Test;
import org.junit.jupiter.params.ParameterizedTest;
import org.junit.jupiter.params.provider.ValueSource;

public class StoveTest{
    
    @ParameterizedTest
    @ValueSource(ints = {0, 1, 2, 3, 4, 5})
    public void ShouldBeAbleToSetBurnerOneToValidRange(int setting){
        Stove stove = new Stove();
        stove.setBurnerOne(setting);
        assertEquals(setting, stove.getBurnerOne(), "Burner does not have expected value");
    }
}
```

The values in the parentheses of the `@ValueSource` annotation are the values supplied to the parameter list of the parameterized test method.  Thus, this test is actually _six_ tests; each test makes sure that one of the settings is working.  We could have done all six as separate assignments and assertions within a single test method, but using a parameterized test means that if only one of these settings doesn't work, we will see that one test fail while the others pass.  This level of specificity can be very helpful in finding errors.

So far our tests cover the expected behavior of our stove.  But where tests really prove their worth is with the _edge cases_ - those things we as programmers don't anticipate.  For example, what happens if we try setting our range to a setting above 5?  Should it simply clamp at 5?  Should it not change from its current setting?  Or should it shut itself off entirely because its user is clearly a pyromaniac bent on burning down their house? If the specification for our program doesn't say, it is up to us to decide.  Let's say we expect it to be clamped at 5:

```java 
@ParameterizedTest
@ValueSource(ints = {6, 18, 1000000})
public void BurnerOneShouldNotExceedFive(int setting){
    Stove stove = new Stove();
    stove.setBurnerOne(setting);
    assertEquals(5, stove.getBurnerOne(), "Burner does not have expected value");
}
```

Note that we don't need to exhaustively test all numbers above 5 - it is sufficient to provide a representative sample, ideally the first value past 5 (6), and a few others.  Also, now that we have defined our expected behavior, we should make sure the documentation of our BurnerOne property matches it:

```java
/**
 * Sets the value of Burner One.
 *
 * Should be an integer between 0 (off) and 5 (high)
 * If a value higher than 5 is provided, the burner will be 
 * set to 5 instead.
 *
 * @param value        the value of the burner
 */
public void setBurnerOne(int value){
```

This way, other programmers (and ourselves, if we visit this code years later) will know what the expected behavior is.  We'd also want to test the other edge cases: i.e. when the burner is set to a negative number.

For a complete guide to parameterized tests in JUnit, including how to use enumerations as a value source, refer to the [Guide to JUnit 5 Parameterized Tests](https://www.baeldung.com/parameterized-tests-junit-5) from Baeldung.

{{% notice tip "Edge Cases" %}}

Recognizing and testing for edge cases is a critical aspect of test writing. But it is also a difficult skill to develop, as we have a tendency to focus on expected values and expected use-cases for our software. But most serious errors occur when values outside these expectations are introduced.  Also, remember special values, like `Double.POSITIVE_INFINITY`, `Double.NEGATIVE_INFINITY`, and `Double.NaN`.

{{% / notice %}}
