---
title: "Python"
pre: "2.P. "
weight: 25
---

{{% notice warning "Start X Server" %}}

Starting in Fall 2026, Codio has been updated to not start the X display server until you try to connect to it the first time. So, before running your Python program, find the entry in the menu at the top of the Codio window to open the GUI viewer (sometimes it'll be called "X Server" or "Virtual Desktop") and click on it to open the GUI viewer, then leave it open while you run your code or tests.

{{% /notice %}}

{{< youtube hjMFAcxwJBU  >}}

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

6. **Create New GUI Classes.** Continuously commit to Git as changes are made!

7. **Update Main.py to use new GUI.** This is just for testing purposes. 

8. **Add GUI Panel for TheChoco.** You'll do this on your own.

9. When complete, use Git to commit and push updated code. 

```bash
git add .
git commit -m "Example Complete"
git push
```

10. On GitHub, create a release tag and submit URL to Canvas for grading. 

---

### Completed GUIs

##### Main Window with Order Panel

![Main Screen](/images/e6/tkinter_sample.png)

##### Main Window with Sundae Panel

![Main Screen](/images/e6/tkinter_sample2.png)
