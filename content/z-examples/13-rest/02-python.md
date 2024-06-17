---
title: "Python"
pre: "2.P. "
weight: 25
---

{{% notice warning "Errata" %}}

This video uses the `html5` widget module in WTForms, which is no longer present. See below the video for a fix!

{{% /notice %}}

{{< youtube 1b1x94AOO-k  >}}

{{% notice note "Widget Fix" %}}

Since this video was recorded, Flask-WTF updated and is now using a newer version of the underlying WTForms library. That library has since deprecated the `html5` widgets module and moved them into the main `widgets` module.

When running the code as shown in the video, you may receive this error:

![Example 13 Import Error](/images/e13/ex13error.png)

To resolve this, in `MovieForm.py` we can simply change the import to be `from wtforms.widgets import NumberInput` and then remove the `html5` in front of each instance where we use `NumberInput` in the code. See the screenshot below for a corrected version:

![Example 13 Corrected Code](/images/e13/ex13corrected.png)

For more information, check out the [relevant pull request](https://github.com/wtforms/flask-wtf/pull/484) and the [WTForms Widgets Documentation](https://wtforms.readthedocs.io/en/3.0.x/widgets/).

{{% /notice %}}

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

6. Follow along with the video to update the project.

7. When complete, use Git to commit and push updated code. 

```bash
git add .
git commit -m "Example Complete"
git push
```

8. On GitHub, create a release tag and submit URL to Canvas for grading. 
