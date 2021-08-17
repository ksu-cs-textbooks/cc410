---
title: "Python Wheels"
weight: 50
pre: "10. "
---
Python typically uses a special type of file called a [Wheel](https://realpython.com/python-wheels/) to create a downloadable package that contains Python source code and any additional resources or bundled libraries required for the package. Wheel files replaced the older ["egg" file format](https://packaging.python.org/discussions/wheel-vs-egg/) that Python used for distribution.

Most software libraries for Python are distributed as wheel files, including from the major repositories such as [PyPi](https://pypi.org/). 

A wheel file itself is built using the same format as the [ZIP](https://en.wikipedia.org/wiki/ZIP_(file_format)) file format. Typically, wheel files themselves are built by the [setuptools](https://setuptools.readthedocs.io/en/latest/) library, which is not itself part of the core Python language but can be quickly installed as a package using `pip3`. 

Finally, a wheel file can include additional information about the software, giving the details such as the version of the software and the developer.

## Installing a Wheel File.

Thankfully, installing a Python wheel file is very simple. Most recent versions of the `pip3` tool will handle this automatically via one of two methods.

1. We can use `pip3 install <packagename>` to find and download the package from [PyPi](https://pypi.org/). Most package entries on PyPi give the exact command needed to install them.
2. We can install a downloaded wheel file using `pip3 install <file>`, where `<file>` is the path and name of a wheel file we downloaded manually.

In either case, `pip3` will handle downloading, extracting and installing the Python wheel file on our system so it is ready for us to use in our Python applications.

As we learned in the "Hello Real World" project, we can also list these requirements in a `requirements.txt` file to have them automatically installed by `pip3` when we use the `tox` command to automate checking and testing our application. In that case, we typically store any manually downloaded wheel files in a folder named `lib` inside of our package directory, and then we can add entries to `tox.ini` that look like `lib/<filename>.whl` to make sure the wheel file is installed properly in the virtual environment as well.

### References

* [PEP 427 - The Wheel Binary Package Format 1.0](https://www.python.org/dev/peps/pep-0427/)
* [What are Python Wheels and Why Should You Care?](https://realpython.com/python-wheels/) from Real Python
* [Python Wheels](https://pythonwheels.com/) - lists the most common Python packages and whether they support installation from wheel files
