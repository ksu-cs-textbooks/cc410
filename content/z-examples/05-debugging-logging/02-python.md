---
title: "Python"
pre: "2.P. "
weight: 25
---

{{% youtube 2nHWIJ1wUDA %}}

## Resources

* [Codio Debugger](https://docs.codio.com/project/ide/features/#debugging)
* [Logging HOWTO](https://docs.python.org/3/howto/logging.html)

## Configuring Codio Debugger

![Python](/images/e5/python.png)

![Python 2](/images/e5/python2.png)

Edit `src/__main__.py` to set Python path:

```python
import sys
sys.path.append("/home/codio/workspace/python/")
```

Make sure `src/__main__.py` imports and calls correct `main` method. 

Can copy unit test code to a test `main` function for testing. Codio doesn't have a good way to individually debug a single unit test, but some IDEs do.

## Tox Changes

In the `tox.ini` file, we added the following line under the `[testenv]` heading:

```ini
ignore_errors = True
```

This will allow the full Tox script to execute, even if there are errors earlier in the process.

We also removed the line to generate documentation, as it is not needed.
## Outline

Here is a basic outline of the steps to follow to complete this example.

1. Clone Starter Code from GitHub

```bash
git clone <url> python
```

2. Run Project

```bash
cd python
python3 -m src
```

3. Install Tox

```bash
pip3 install tox
```

4. Check & Test Existing Project

```bash
python3 -m tox
```

5. Confirm that project runs, no style errors, and tests execute (some tests will fail). 

6. **Fix Code to Pass Unit Tests**. Use Codio debugger and/or Logging

7. Add logging to both files

8. Add `README.md` and discuss how you solved the errors.

9. Confirm that project runs and all tests pass.

10. When complete, use Git to commit and push updated code. 

```bash
git add .
git commit -m "Example Complete"
git push
```

11. On GitHub, create a release tag and submit URL to Canvas for grading. 