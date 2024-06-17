---
title: "Python 3.9"
pre: "4. "
weight: 40
---

## Updating to Python 3.9

In Fall 2022, the Codio software stack was updated to Python 3.9. This requires several changes to be made to the projects, which are described below.

### For Projects Already Started using Python 3.6

1. Uninstall all Python packages:

```bash
pip3 uninstall -y -r requirements.txt
```

2. Update the stack by going to the **Project > Stack > Settings** menu option. 

![Menu Options](/images/errata/update1.png)

On that page, select the latest version of the CC 410 Stack, and click Save.

![Select Stack](/images/errata/update2.png)

The Codio box should update to the new stack. 

### For New Projects

1. Confirm that the current Python version is 3.9 and that Pip3 is updated as well:

```bash
python3 --version
pip3 --version
```

Current versions are shown below:

![Python Versions](/images/errata/update3.png)

2. Update `tox.ini` to use Python 3.9 instead of Python 3.6:

```ini
[tox]
envlist = py39
```

3. Install project requirements using `pip3`:

{{% notice warning %}}

Check the [errata page](03-errata) to see if any requirements must be updated.

{{% /notice %}}

```bash
pip3 install -r requirements.txt
```

If there are any errors, contact the instructor.

4. Test and run the project following the usual procedure. 