---
title: "Java"
pre: "2.J. "
weight: 20
---

{{< youtube y6qQS3bdmzk  >}}

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

7. Follow along with the video to create the project.

8. Add the `about` page yourself!

9. When complete, use Git to commit and push updated code. 

```bash
git add .
git commit -m "Example Complete"
git push
```

10. On GitHub, create a release tag and submit URL to Canvas for grading. 

---

When using [Spring Initializr](https://start.spring.io/), below is a screenshot showing what it should look like.

![Spring Initializr](/images/e11/spring.png)

The generated `build.gradle` file looks like this as of Spring 2021:

```groovy
plugins {
	id 'org.springframework.boot' version '2.4.4'
	id 'io.spring.dependency-management' version '1.0.11.RELEASE'
	id 'java'
}

group = 'web'
version = '0.0.1-SNAPSHOT'
sourceCompatibility = '1.8'

repositories {
	mavenCentral()
}

dependencies {
	implementation 'org.springframework.boot:spring-boot-starter-thymeleaf'
	implementation 'org.springframework.boot:spring-boot-starter-web'
	developmentOnly 'org.springframework.boot:spring-boot-devtools'
	testImplementation 'org.springframework.boot:spring-boot-starter-test'
}

test {
	useJUnitPlatform()
}
```