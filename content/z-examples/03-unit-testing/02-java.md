---
title: "Java"
pre: "2.J. "
weight: 20
---

{{< youtube qail9GqR3gY  >}}

## Resources

* [JUnit 5 Assertions](https://junit.org/junit5/docs/5.6.2/api/org.junit.jupiter.api/org/junit/jupiter/api/Assertions.html)
* [Hamcrest Matchers](http://hamcrest.org/JavaHamcrest/javadoc/2.2/)

## Gradle Changes

In the `build.gradle` file, the JUnit 5 parameters library was added:

```groovy
dependencies {
    // Use JUnit Jupiter API for testing.
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.6.2', 'org.hamcrest:hamcrest:2.2', 'org.junit.jupiter:junit-jupiter-params'

    // Use JUnit Jupiter Engine for testing.
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine'

    // This dependency is used by the application.
    implementation 'com.google.guava:guava:29.0-jre'
}
```

Also, we added a quick section at the bottom to allow Gradle tasks to read input from `System.in`:

```groovy
// Allow run to read from System.in
run{
    standardInput = System.in
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
sdk install gradle 7.6
```

5. Compile, Run & Test Existing Project

```bash
cd java
gradle run
gradle test
gradle check
gradle javadoc
```

6. Confirm that project runs, no style errors, and Javadoc generates properly. 

7. **Create New Unit Tests and Update Code as Needed.** Continuously commit to Git as changes are made!

8. **Add Documentation Comments.** Continuously commit to Git as changes are made!

9. Add `README.md` and discuss unit tests you feel should be added to adequately test the `GuessingGame` class.

10. Create a UML Class Diagram for the source code and include it in the project. 

11. Confirm that project runs, no style errors related to comments, and Javadoc generates properly. 

12. When complete, use Git to commit and push updated code. 

```bash
git add .
git commit -m "Example Complete"
git push
```

13. On GitHub, create a release tag and submit URL to Canvas for grading. 