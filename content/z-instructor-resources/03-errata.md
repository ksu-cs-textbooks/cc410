---
title: "Errata"
pre: "3. "
weight: 30
date: 2022-04-27T00:53:26-05:00
---

## Errata

This page is a quick reference for any known errata that have yet to be resolved.

### Flake 8 and HTML Plugin - 2022-08-25

Currently the `flake8-html` plugin has not been updated to work with Flake 8 version 5.0.0.  

The bug report is here: https://github.com/lordmauve/flake8-html/issues/30. 

In the meantime, you can fix this by locking `flake8` to a version below 5.0.0 in the `requirements.txt` file by updating the entry for `flake8` to the following:

```ini
# Lock flake8 to <5.0.0
# https://github.com/lordmauve/flake8-html/issues/30
flake8<5.0.0
```


### Flake 8 - 2022-04-05

{{% notice note %}}

This error may have been resolved by moving Python to version 3.9 in Fall 2022. It has not been tested yet; this will be updated once it is tested and confirmed working.

{{% /notice %}}

In Python, you may get some errors when running Flake8 due to a bug. The error message references the "Markup" class as part of "Jinja2" which is used by the Flake8-html plugin.

The bug report and pull request to fix it is here: https://github.com/lordmauve/flake8-html/pull/24. It has yet to be included in a new release.

In the meantime, you can fix this by adding the following information to your requirements.txt file:

```ini
# fix for broken jinja
# https://github.com/lordmauve/flake8-html/pull/24
jinja2==3.0.*
```

### Testing with Tox - 2023-03-29

Running tests that include a graphical interface via Tox may cause issues with x11 permissions.

This can be resolved by installing this PyTest plugin: https://github.com/The-Compiler/pytest-xvfb

Documentation has not been updated to note this.

<!-- TODO Update Documentation  -->