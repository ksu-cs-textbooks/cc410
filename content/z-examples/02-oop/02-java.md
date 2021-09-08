---
title: "Java"
pre: "2.J. "
weight: 20
---

{{% youtube D-203mVSLkU %}}

Here is a basic outline of the steps to follow to complete this example.

1. Clone Starter Code from GitHub

```bash
git clone <url> java
```

2. Install SDKMAN

[Instructions](https://sdkman.io/install)

```bash
curl -s "https://get.sdkman.io" | bash
```

3. Close and Reopen Terminal to load SDK Man
4. Install Gradle

```bash
sdk install gradle
```

5. Compile, Run & Test Existing Project

```bash
cd java
gradle run
gradle test
gradle check
gradle javadoc
```

6. Confirm that project runs, all unit tests pass with 100% coverage, no style errors, and Javadoc generates properly. 

7. **Create New Packages, Classes, and Enums.** Continuously commit to Git as changes are made!

8. **Update HelloWorld.java to use new classes (optional).** This is just for testing purposes. 

9. When complete, use Git to commit and push updated code. 

```bash
git add .
git commit -m "Example Complete"
git push
```

10. On GitHub, create a release tag and submit URL to Canvas for grading. 