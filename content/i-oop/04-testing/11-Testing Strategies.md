---
title: "Testing Strategies"
weight: 55
pre: "11. "
---
Unit testing is a small part of a much larger world of software testing strategies that we can employ in our workflow. On this page, we'll review some of the more common testing strategies that we may come across.

## White Box vs. Black Box Testing

First, it is important to differentiate between two different approaches to testing. The **white-box** testing approach means that the developer writing the test has full access to the source code, and it is used to verify not just the functionality of a program as it might appear externally, but also that the internal workings of the program are correct. 

By having access to the source code, you can take advantage of tools that determine code coverage, and develop tests that are specifically designed to test edge cases or paths found in the code itself. 

On the other hand, **black-box** testing means that the tester cannot see the source code of the application itself, and can only test it by calling the publicly available methods, sometimes referred to as the **application programming interface** or **API** of the software. 

For example, consider testing the code in a library that we didn't develop. We can access the documentation to see what functions it provides and how they should operate, and we can then write tests that verify those functions. This can be helpful to avoid some of the biases that may be introduced by reading the code itself. We could easily look at a line of code and convince ourselves that it is correct, such that we may not adequately test it's functionality. 

However, because we won't be able to see the code itself, it can be much harder to test edge cases or unique functionality in the code since we cannot inspect it ourselves. So, we'll have to be a bit more creative and deliberate in developing our test cases. 

## Integration Testing

Beyond unit testing, many software programs also undergo **integration testing**, where each individual software component is tested to make sure its interface matches the design specifications, and also that multiple parts of the system work together properly. As programs become larger and larger, it is important to not only test the individual units but the links between those units as well. By creating a well defined interface and performing integration testing, we can ensure that all parts of our program work well together. 

## Regression Testing

We've already discussed this a bit. **Regression testing** involves running our set of tests after a major change in the software, trying to ensure that we didn't introduce any new bugs or break any working features, causing the software to _regress_ in quality. 

This can be really important if we plan on developing a new version of our program that remains compatible with previous versions. In that case, we may end up developing an entirely new suite of tests for our new version, while still using the previous version's tests as a form of regression testing to ensure compatibility. As the software matures and new versions are released, maintaining backwards compatibility can be a major challenge.

## Acceptance Testing

Once the software is complete, a final phase of testing is the **acceptance testing**, where the software is tested by the eventual end user to confirm that it meets their needs. Acceptance testing could include phases such as **alpha testing** and **beta testing**, where incomplete versions of the software are tested by potential users to identify bugs. This is very common today in video game development.

## Test-Driven Development

Finally, one important concept in the world of software development is the **test-driven development** methodology. In contrast to more traditional software development methodologies where the software is developed and then tested, test-driven development requires that software tests be written first, and then the software itself is written to pass the tests. Through this method, if we adequately write our tests to match the requirements of the software, we can be sure that our software actually does what it should if it passes the tests.

This can be quite tricky, since writing tests can be much more complex than writing the actual software, and in some cases it is important to understand how the software itself will be structured before the tests can be effectively written.

### Further Reading

For more information about the world of software testing, check out the [Software Testing](https://en.wikipedia.org/wiki/Software_testing) article on Wikipedia, as well as the many articles linked from that page. 
