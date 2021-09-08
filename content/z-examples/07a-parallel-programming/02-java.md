---
title: "Java"
pre: "2.J. "
weight: 20
---

{{% youtube LqhMZyx9GnA %}}

Here is a basic outline of the steps to follow to complete this example.

1. Clone Starter Code from GitHub

```bash
git clone <url> java
```

2. **Update `ParallelOne` to use 4 threads.**
3. **Take a screenshot showing a race condition.**
4. **Update `ParallelOne` to use a lock.**
5. **Take a screenshot showing no race condition.**
6. **Update `ParallelTwo` to use blocking and an arbitrary number of threads.**
7. **Run several times with different number of threads (1 - 10) and graph results.**
8. **Write in `README.md` to answer two questions**

9. When complete, use Git to commit and push updated code. 

```bash
git add .
git commit -m "Example Complete"
git push
```

10. On GitHub, create a release tag and submit URL to Canvas for grading. 

---

## Compiling and Running Java

Recall that you can compile a Java program using `javac`:

```bash
javac ParallelOne.java
```

You can then run it using `java`:

```bash
java ParallelOne
```