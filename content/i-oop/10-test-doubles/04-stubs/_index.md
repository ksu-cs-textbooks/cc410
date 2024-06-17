---
title: "Stubs"
weight: 20
pre: "4. "
---
{{< youtube SQUTcxc3RYo  >}}

[Video Materials]({{% relref "./video" %}})

{{% notice note "Inconsistent Naming" %}}

Unfortunately, the naming of many of these test doubles, such as stubs, mocks, and fakes, are used either inconsistently or interchangeably within different systems, documentation, and other resources. I'm going to stick to one particular naming scheme, which is best described in the resources linked earlier in this chapter. However, in practice, these terms may be used differently in different areas. 

{{% / notice %}}

There are three major types of test doubles that we'll cover in this chapter. The first are **stubs**, sometimes referred to as **stub methods** or **method stubs**. A [stub](https://en.wikipedia.org/wiki/Method_stub) is simply an object that is used to return predefined data when its methods are called, without any internal logic.  

![Stub](/images/13/stub.png)[^1]

[^1]: https://blog.pragmatists.com/test-doubles-fakes-mocks-and-stubs-1a7491dfa3da

For example, if the methods we are testing should sum up the data that results from several calls to a method that is outside of our module, we could create a stub that simply returns the values 1 - 5, and then verify that our method calculates the sum of 15. In this way, we're verifying that our code works as intended (it sums the values), without really worrying whether the other module returns correct data or not. 

The only thing we must be careful with when creating these stubs is that the data they return is plausible for the test we are performing. If the data should be valid, then we should be careful to return values that are the correct type and within the correct range. Likewise, if we want to test any possible error conditions or invalid values, we'll have to make sure our stub returns the appropriate values as the real object would.
