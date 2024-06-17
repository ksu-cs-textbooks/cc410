---
title: "Java"
pre: "2.J. "
weight: 20
---

###### Part 1

{{< youtube m3o877yvd1M  >}}

###### Part 2

{{< youtube EP9CzJ-mCkw  >}}

## Gradle Changes

The `build.gradle` file includes the library for JUnit5 parameterized tests:

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
gradle check
```

6. Confirm that project runs and has no style errors. 

7. **Handle Save Events** 
8. **Handle Cancel Events** 
9. **Switch Listbox to Tree in Sidebar**
10. **Populate Tree with Elements**
11. **Handle Edit Events**
12. **Handle Delete Events**
13. **Create Unit Tests**

14. When complete, use Git to commit and push updated code. 

```bash
git add .
git commit -m "Example Complete"
git push
```

15. On GitHub, create a release tag and submit URL to Canvas for grading. 