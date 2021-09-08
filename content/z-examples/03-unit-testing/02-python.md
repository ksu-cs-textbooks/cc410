---
title: "Python"
pre: "2.P. "
weight: 25
---

{{% youtube RvMmtAZjnHo %}}

## Resources

* [pytest Assertions](https://docs.pytest.org/en/stable/assert.html)
* [Hamcrest Matchers](https://pyhamcrest.readthedocs.io/en/v2.0.2/library/)

## Tox Changes

In the `tox.ini` file, we added the following line under the `[testenv]` heading:

```ini
ignore_errors = True
```

This will allow the full Tox script to execute, even if there are errors earlier in the process.

## Steps

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

5. Confirm that project runs, all unit tests pass, no style errors, no type errors, and documentation generates properly. 

6. **Create New Unit Tests and Update Code as Needed.** Continuously commit to Git as changes are made!

7. **Add Documentation Comments.** Continuously commit to Git as changes are made!

8. Add `README.md` and discuss unit tests you feel should be added to adequately test the `GuessingGame` class.

9. Create a UML Class Diagram for the source code and include it in the project. 

10. Confirm that project runs, no style errors related to comments, and pydoc3 generates properly. 

11. When complete, use Git to commit and push updated code. 

```bash
git add .
git commit -m "Example Complete"
git push
```

12. On GitHub, create a release tag and submit URL to Canvas for grading. 