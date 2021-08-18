---
title: "Module Outline & Notes"
pre: "1. "
weight: 10
date: 2019-12-17T10:53:26-05:00
---

## Notes

#### Python Project 1

* Good discussion of PyTest vs. UnitTest: https://blog.j-labs.pl/2019/02/Pytest-why-its-more-popular-than-unittest
* Flake8 Intro on Medium: https://medium.com/python-pandemonium/what-is-flake8-and-why-we-should-use-it-b89bd78073f2
* Code Linters: https://github.com/collections/clean-code-linters
* Python Running PyTest with Src Directory: 
* Discussion on src folder for Python: https://hynek.me/articles/testing-packaging/
* Running PyTest with Src:
  * https://stackoverflow.com/questions/1896918/running-unittest-with-typical-test-directory-structure
  * https://stackoverflow.com/questions/50155464/using-pytest-with-a-src-layer
  * https://stackoverflow.com/questions/49589082/pytest-python-src-layout 
  * https://docs.pytest.org/en/stable/pythonpath.html (Conftest.py hack)

* Using __main__ in Python: https://www.geeksforgeeks.org/usage-of-__main__-py-in-python/

* Running Coverage: https://coverage.readthedocs.io/en/coverage-5.3/source.html#source

* Flake8 Plugins: https://stackoverflow.com/questions/60403545/flake8-not-giving-errors-warnings-on-missing-docstring-or-code-not-following-pep

* PyTest
  * https://docs.pytest.org/en/stable/getting-started.html
  * https://docs.pytest.org/en/stable/goodpractices.html#test-discovery
  * https://docs.pytest.org/en/stable/mark.html#mark
  * https://docs.pytest.org/en/stable/capture.html

* PyDocStyle: https://github.com/pycqa/pydocstyle


```bash
python3 src
pip3 install pytest
pip3 install pytest-html
python3 -m pytest
python3 -m pytest --html=report.html
pip3 install coverage
python3 -m coverage run --source src -m pytest --html=report.html
python3 -m coverage html
pip3 install flake8
pip3 install pep8-naming
pip3 install flake8-docstrings
pip3 install flake8-html
python3 -m flake8 --docstring-convention google --format=html --htmldir=flake
```

https://realpython.com/python-testing/

* Java CheckStyle Docs: https://checkstyle.org/cmdline.html


