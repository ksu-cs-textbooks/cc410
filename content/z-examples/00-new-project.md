---
title: "New Project Checklist"
pre: "0. "
weight: 5
---

Steps to follow when setting up a new project in this course. 

## Java

### New Project

1. Clone empty GitHub repository into `java` folder:
```bash
git clone <url> java
```
2. [Install SDKMAN](https://sdkman.io/install)
```bash
curl -s "https://get.sdkman.io" | bash
```
3. Close and Reopen Terminal
4. Install Gradle
```bash
sdk install gradle
```
5. Change directory to `java` folder:
```bash
cd java
```
6. Initialize Gradle Project
```bash
gradle init
```
Recommended options:
    1. Type of project - `2: application`
    1. Implementation language - `3: Java`
    1. Split functionality across multiple subprojects - `1: no - only one application project`
    1. Build script DSL - `1: Groovy`
    1. Generate build using new APIs and behavior - `no`
    1. Test Framework - `4: JUnit Jupiter`
    1. Project name - `<name>`
    1. Source package - `<name>`
7. Add JaCoCo Plugin to `build.gradle`
```groovy
plugins {
    // Apply the application plugin to add support for building a CLI application in Java.
    id 'application'
    // JaCoCo plugin for code coverage
    id 'jacoco'
}

// ... rest of file here

// Configure Jacoco plugin
test {
    finalizedBy jacocoTestReport // report is always generated after tests run
}

jacocoTestReport {
    dependsOn test // tests are required to run before generating the report
    reports {
        xml.enabled false
        csv.enabled false
        html.destination file("${buildDir}/reports/jacoco")
    }
}
```
8. Configure JavaDoc in `build.gradle`
```groovy
// .. rest of file here

// Add tests to Javadoc
javadoc {
  classpath += project.sourceSets.test.compileClasspath
  source += project.sourceSets.test.allJava
}
```
9. Add Checkstyle to `build.gradle`
```groovy
plugins {
    // Apply the application plugin to add support for building a CLI application in Java.
    id 'application'
    // JaCoCo plugin for code coverage
    id 'jacoco'
    // Checkstyle plugin for linting
    id 'checkstyle'
}

// ... rest of file here

// Force Checkstyle to be more current version
checkstyle {
    toolVersion '10.6.0'
}
```
10. Store [Google Checkstyle XML](https://raw.githubusercontent.com/checkstyle/checkstyle/checkstyle-10.6.0/src/main/resources/google_checks.xml) at `config/checkstyle/checkstyle.xml`
    1. Optionally update `Indentation` section to match Codio values:
```xml
    <module name="Indentation">
      <property name="basicOffset" value="4"/>
      <property name="braceAdjustment" value="4"/>
      <property name="caseIndent" value="4"/>
      <property name="throwsIndent" value="8"/>
      <property name="lineWrappingIndentation" value="8"/>
      <property name="arrayInitIndent" value="4"/>
    </module>
```
11. Add additional libraries to `build.gradle` as needed (Hamcrest, JUnit Parameters, etc.)

### Existing Project or Example Project

1. Clone existing project into `java` folder: 
```bash
git clone <url> java
```
2. [Install SDKMAN](https://sdkman.io/install)
```bash
curl -s "https://get.sdkman.io" | bash
```
3. Close and Reopen Terminal
4. Install Gradle
```bash
sdk install gradle
```
5. Change directory to `java` folder:
```bash
cd java
```
6. Compile and Test Existing Project
```bash
gradle run
gradle check
```

## Python

### New Project

1. Clone empty GitHub repository into `python` folder:
```bash
git clone <url> python
```
2. Change directory to `python` folder:
```bash
cd python
```
3. Check Python Version:
```bash
python3 --version
```
4. Create `requirements.txt` file
```ini
coverage
flake8<5.0.0
flake8-docstrings
flake8-html
lxml
mypy
pdoc3
pep8-naming
pyhamcrest
pytest
pytest-html
tox
```
5. Install Python Libraries
```bash
pip3 install -r requirements.txt
```
6. Create `tox.ini` file
```ini

[tox]
envlist = py39
skipsdist = True

[testenv]
deps = -rrequirements.txt
ignore_errors = true
commands = python3 -m mypy -p src --html-report reports/mypy
           python3 -m coverage run --source src -m pytest --html=reports/pytest/index.html
           python3 -m coverage html -d reports/coverage
           python3 -m flake8 --docstring-convention google --format=html --htmldir=reports/flake
           python3 -m pdoc --html --force --output-dir reports/doc .
```
7. Create `.gitignore` file
```ini
__pycache__/
.tox
reports/
.coverage
```
8. Create `src` and `test` directories
```bash
mkdir src
mkdir test
```
9. Add empty `conftest.py` to `src` directory
10. Add empty `__init__.py` to `src` and `test` directory to make them packages
11. Create additional packages as needed
12. Add `__main__.py` to `src` and include code to call main method

### Existing Project

1. Clone existing project into `python` folder: 
```bash
git clone <url> python
```
2. Change directory to `python` folder:
```bash
cd python
```
3. Check Python Version:
```bash
python3 --version
```
4. Confirm Python Version matches the `envlist` entry in `tox.ini`
   1. Python 3.6.x - `py36`
   2. Python 3.9.x - `py39`
   3. Python 3.10.x - `py310`
5. [Update Packages](https://textbooks.cs.ksu.edu/cc410/z-instructor-resources/03-errata/) in `requirements.txt`
   1. Lock `flake8` to version before 5.0: `flake8<5.0.0`
5. Install Python Libraries
```bash
pip3 install -r requirements.txt
```
6. Run Existing Project
```bash
python3 -m src
```
or (For flask projects)
```bash
python3 -m flask run
```
6. Run `tox` using Recreate Option To Test Existing Project
```bash
tox -r
```

## GitHub Commit and Release

1. Git Commit and Push
```bash
git add .
git commit -m "Message"
git push
```
2. On GitHub Site, create [Release]({{< relref "/z-examples/01-hello-real-world/05-create-release/_index.md" >}})