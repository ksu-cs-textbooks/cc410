---
title: "Running Tests"
weight: 50
pre: "10. "
---
Once we've written our unit tests, we can execute them against our code to see how well it works. Tests are usually run with a _test runner_, a program that will execute the test code against the code to be tested.  The exact mechanism involved depends on the testing framework.  

As we discovered in the "Hello Real World" project, both JUnit and pytest have a way to automatically discover all of the tests we've created, provided we place them in the correct location and possibly give them the correct name. 

Outside of Codio, many integrated development environments, or IDEs, support running unit tests directly through their interface. We won't cover much of that in this class, but it is handy to know that it can be done graphically as well.

Once the test runner is done executing our tests, we'll be given information about the tests which failed. We've also learned how to create an HTML report that gives us helpful information about our tests and why they failed. So, we can look through that information to determine if our code needs to be updated, or if the test is not testing our code correctly. 

Occasionally, you may end up with problems executing your tests. So, as with any development process, it is helpful to work incrementally, and run your tests each time you add or change code. This allows you to catch errors as they happen when the code is fresh in your mind, and it will be that much easier to fix the problem. 

It's also a good idea to run all of your previously passed tests anytime you make a change to your code. This practice is known as _regression testing_, and can help you identify errors your changes introduce that break what had previously been working code.  This is also one of the strongest arguments for writing test code rather than performing ad-hoc testing; automated tests are easy to repeat. 

## Code Coverage

The term _test code coverage_ refers to how much of your program's code is executed as your tests run. It is a useful metric for evaluating the _depth_ of your test, if not necessarily the quality.  Basically, if your code is not executed in the test framework, it is not tested in any way. If it is executed, then at least _some_ tests are looking at it.  So aiming for a high code coverage is a good starting point for writing tests.

While test code coverage is a good starting point for evaluating your tests, it is simply a measure of quantity, not quality. It is easily possible for you to have all of your code covered by tests, but still miss errors.  You need to carefully consider the edge cases - those unexpected and unanticipated ways your code might end up being used.
