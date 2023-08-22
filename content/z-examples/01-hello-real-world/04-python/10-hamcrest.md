---
title: "Hamcrest"
weight: 100
pre: "4.P.10. "
---

{{% youtube C5HJWKFLm0Q %}}

Let's introduce one more useful tool as part of this example, the Hamcrest assertion library. [Hamcrest](https://github.com/hamcrest/PyHamcrest) is a library of unit test assertions that is available for multiple programming languages, including both Java and Python. Hamcrest makes it easy to write very advanced assertions in a way that is both readable and flexible. In fact, most of the autograders in prior CC courses use Hamcrest as the primary assertion library to make them easy to develop. Let's explore what it takes to add Hamcrest to our project.

## Installing Hamcrest

To make Hamcrest available, we simply have to add an entry for `pyhamcrest` to our `requirements.txt` file. Once we update that file, it will look like this:

```tex
coverage
flake8
flake8-docstrings
flake8-html
lxml
mypy
pdoc3
pep8-naming
pyhamcrest
pytest
pytest-html
tox
```

Then we can install it using this command from within the `python` folder:

```bash
pip3 install -r requirements.txt
```

That's all there is to it! We now can use Hamcrest in our unit tests

## Unit Test with Hamcrest

Now, let's build a unit test that uses Hamcrest. So, in the `test/hello` directory, create a new file called `test_HelloWorldHamcrest.py` and paste the following code in that file:

```python
"""Test Class for HelloWorld using Hamcrest.

Author: Russell Feldhausen russfeld@ksu.edu
Version: 0.1
"""

from hamcrest.core.assert_that import assert_that
from hamcrest.core.core.is_ import is_
from pytest import CaptureFixture
from _pytest.capture import CaptureResult
from typing import Any
from src.hello.HelloWorld import HelloWorld


class TestHelloWorldHamcrest():
    """Test Class for `src.hello.HelloWorld`."""

    def test_hello_world(self, capsys: CaptureFixture[Any]) -> None:
        """Test Method for `src.hello.HelloWorld.main`.

        This will test the main method with no arguments.

        Args:
            capsys: PyUnit fixture to capture output.
        """
        HelloWorld.main(["HelloWorld"])
        captured: CaptureResult[Any] = capsys.readouterr()
        assert_that(captured.out, is_("Hello World\n"), "Unexpected Output")

    def test_hello_world_arg(self, capsys: CaptureFixture[Any]) -> None:
        """Test Method for `src.hello.HelloWorld.main`.

        This will test the main method with 1 argument.

        Args:
            capsys: PyUnit fixture to capture output.
        """
        HelloWorld.main(["HelloWorld", "CC 410"])
        captured: CaptureResult[Any] = capsys.readouterr()
        assert_that(captured.out, is_("Hello CC 410\n"), "Unexpected Output")

```

The code is nearly identical to the other unit test class, but with two major changes:

1. There are a couple of new import statements at the top to include the `assert_that` and `is_` methods from Hamcrest. 
2. Instead of using `assert` the last line of each unit test uses `assert_that`. The order of the arguments and the basic idea is pretty much the same. Also, note the use of the `is_` method, which is simply stating that it should be equal. That method name includes an underscore to differentiate it from the `is` keyword in Python.

Of course, a simple test case such as this doesn't show the power of using Hamcrest instead of the built-in assertions in pyunit. If you want to know more about Hamcrest, feel free to check out the [Hamcrest documentation](https://pyhamcrest.readthedocs.io/en/v2.0.2/). We'll explore more about using Hamcrest in our unit tests later in this course.

## Running Tests

Now that we've created a new unit test class, let's go ahead and run it. Thankfully, we don't have to do anything else - pyunit will automatically find the new unit test class and execute it along with all the others. So, in a Linux terminal in the `python` directory, run the following command to execute those tests, along with the rest of our commands:

```java
tox -r
```

When the tests are complete, we can open the report and we should now see that there are 4 tests that executed successfully:

![Hamcrest Test Report](/images/e1/30tests.png)

While we're at it, since we added new code and unit tests we should also check to make sure that our code coverage is still good:

![Hamcrest Code Coverage](/images/e1/30cov.png)

As long as the tox command executes, we also know that the code passed all of our Flake8 style checks, and updated the documentation using pdoc3 as well.

![Hamcrest Flake](/images/e1/30flake.png)

If you run into any errors on any of those commands, now is a good time to get them resolved before moving on! This is the last step before we submit our code!

Click the link below to jump to the end where we submit our code.

[Create GitHub Release]({{< relref "../05-create-release.md" >}})