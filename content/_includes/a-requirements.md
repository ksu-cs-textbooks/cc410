* **All code must be object-oriented.**
  * All executable code must be within a class
    * Python package files such as `__init__.py` and `__main__.py` are exempt.
  * Classes must be organized into packages based on common usage.
* **All projects must include automation for testing, style checking, and documentation generation.**
  * Java: Use Gradle with the `application`, `jacoco`, and `checkstyle` plugins.
  * Python: Use tox configured to use Python 3.10 and a requirements file to install libraries.
* **All code must properly compile and be executable.**
  * Java: It must compile and execute using Gradle.
  * Python: It must execute using Python 3.10. Where specified, type hints should be included in the code, and all code should pass a strict Mypy type check.
* **All code submitted must be free of style errors.** We will be using the [Google Style Guide](https://google.github.io/styleguide/) for each language. 
  * Java: Use Checkstyle 10.6.0+ and the [Google Style Configuration](https://raw.githubusercontent.com/checkstyle/checkstyle/checkstyle-10.6.0/src/main/resources/google_checks.xml). 
    * You may modify the configuration to allow 4 space indentations instead of 2 space indentations.
  * Python: Use Flake8 with the `flake8-docstrings` and `pep8-naming` plugins. Code should conform to PEP 8 style with Google style docstrings. 
* **Where specified, code should contain appropriate unit tests that achieve the specified level of code coverage.**
  * Java: Use JUnit 5. You may choose to use Hamcrest for assertions.
  * Python: Use pytest. You may choose to use Hamcrest for assertions.
* **Where specified, code should contain appropriate documentation comments following the language's style guide.**
  * In any class that should be documented, **every method in that class should have complete documentation comments.**
  * Java: Use javadoc to generate documentation.
  * Python: Use pdoc3 to generate documentation.
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).