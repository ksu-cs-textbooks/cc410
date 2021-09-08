---
title: "Python"
pre: "2.P. "
weight: 25
---

###### Part 1

{{% youtube -nGEixsWd2I %}}

###### Part 2

{{% youtube K4E6duybPMo %}}

## Tox Changes

The `tox.ini` file has been updated to allow testing with a display, and will now run the full unit test suite.

```ini
[testenv]
deps = -rrequirements.txt
ignore_errors = True
passenv = DISPLAY
commands = python3 -m mypy -p src --html-report reports/mypy
           python3 -m coverage run --source src -m pytest --html=reports/pytest/index.html
           python3 -m coverage html -d reports/coverage
           python3 -m flake8 --docstring-convention google --format=html --htmldir=reports/flake
```

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

5. Confirm that project runs and has no style errors. 

6. **Handle Save Events** 
7. **Handle Cancel Events** 
8. **Switch Listbox to Tree in Sidebar**
9. **Populate Tree with Elements**
10. **Handle Edit Events**
11. **Handle Delete Events**
12. **Create Unit Tests**

13. When complete, use Git to commit and push updated code. 

```bash
git add .
git commit -m "Example Complete"
git push
```

14. On GitHub, create a release tag and submit URL to Canvas for grading. 