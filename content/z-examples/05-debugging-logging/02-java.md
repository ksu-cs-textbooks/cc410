---
title: "Java"
pre: "2.J. "
weight: 20
---

{{% youtube RoMqkzZiDfI %}}

## Resources

* [Codio Debugger](https://docs.codio.com/project/ide/features/#debugging)
* [Java Logging API Tutorial](https://www.vogella.com/tutorials/Logging/article.html)

## Configuring Codio Debugger

![Java](/cc410/images/e5/java.png)

![Java 2](/cc410/images/e5/java2.png)

Make sure the `application` section of `build.gradle` is set to the correct application.

Can copy unit test code to a test `main` function for testing. Codio doesn't have a good way to individually debug a single unit test, but some IDEs do.

## Gradle Changes

Added entries in the `application` section for both programs. Can comment/uncomment as needed.

```groovy
application {
    // Define the main class for the application.
    mainClass = 'tictactoe.TicTacToe'
    // mainClass = 'sudoku.SudokuFourModel'
}
```

## Outline

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
```

6. Confirm that project runs, no style errors, and tests execute (some tests will fail). 

7. **Fix Code to Pass Unit Tests**. Use Codio debugger and/or Logging

8. Add logging to both files

9. Add `README.md` and discuss how you solved the errors.

10. Confirm that project runs and all tests pass.

11. When complete, use Git to commit and push updated code. 

```bash
git add .
git commit -m "Example Complete"
git push
```

12. On GitHub, create a release tag and submit URL to Canvas for grading. 