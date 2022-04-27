---
title: "Errata"
pre: "3. "
weight: 30
date: 2022-04-27T00:53:26-05:00
---

## Errata

This page is a quick reference for any known errata that have yet to be resolved. Last Updated April 27, 2022.

### Flake 8 - 2022-04-05

In Python, you may get some errors when running Flake8 due to a bug. The error message references the "Markup" class as part of "Jinja2" which is used by the Flake8-html plugin.

The bug report and pull request to fix it is here: https://github.com/lordmauve/flake8-html/pull/24. It has yet to be included in a new release.

In the meantime, you can fix this by adding the following information to your requirements.txt file:

```ini
# fix for broken jinja
# https://github.com/lordmauve/flake8-html/pull/24
jinja2==3.0.*
```