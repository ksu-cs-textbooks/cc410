---
title: "Building Python Wheel"
weight: 35
pre: "7. "
---

Building a Python wheel file is super simple using the `setuptools` library - it handles almost all of the heavy lifting for us. The basic steps are outlined in the [Packaging Python Projects](https://packaging.python.org/tutorials/packaging-projects/) guide in the Python documentation. Below, we'll go through the steps we'll need to follow for most of the applications we've created in this course.

## Create Pyproject.toml

First, we'll need to create a file named `pyproject.toml` in the root our project directory. This file is responsible for defining the exact tools needed to build this package. We're just going to use the default file provided in the documentation for now:

```toml
[build-system]
requires = [
    "setuptools>=42",
    "wheel"
]
build-backend = "setuptools.build_meta"
```

## Create README.md

If we haven't already done this, now is a great time to create a `README.md` file in the root directory of our project and include some basic information about our project. Once it is published, we can come back to this file and update it with links to the documentation hosted in GitHub pages.

## Create a LICENSE file

In addition, we may wish to add a license to our project at this step, before packaging it. We can use the [choosealicense.com](https://choosealicense.com/) website to help find a license. We can also easily add a license to an existing GitHub repository following the [Adding a license to a repository](https://docs.github.com/en/github/building-a-strong-community/adding-a-license-to-a-repository) guide from GitHub, then using the `git pull` command to pull that license file into v0.1.0r local copy of the project. 

In either case, make sure we have a file in the root of our project named `LICENSE` before continuing. 

## Add Typing Files

If our code contains proper typing information that can be used by Mypy, we need to mark that by placing a blank file named `py.typed` in each package that contains type annotations. So, wherever we see an `__init__.py` file, we should also add a `py.typed` file to the same directory.

## Configure Metadata

Next, we need to set some metadata for our project. There are a couple of ways to do this, but the simplest is to create a static `setup.cfg` file that contains all of the information for our project. Once again, we'll place this file in the root of our project directory.

The [Packaging Python Projects](https://packaging.python.org/tutorials/packaging-projects/) tutorial provides a sample file that we can easily adapt for our needs. We've made a few changes below to that file to match our project:

```toml
[metadata]
name = <ourprojectname>
version = <0.1.0>
author = <Your Name>
author_email = <your_email@example.com>
description = <A description of our project>
long_description = file: README.md
long_description_content_type = text/markdown
url = https://github.com/<username>/<repo>
    Bug Tracker = https://github.com/<username>/<repo>/issues
classifiers =
    Programming Language :: Python :: 3
    License :: OSI Approved :: <MIT License>
    Operating System :: OS Independent

[options]
packages = find:
python_requires = >=3.9
include-package-data = True

[options.package_data]
<ourprojectname> = py.typed
```

The portions marked with angle brackets `<>` should be updated to match our project information. The tutorial linked above provides a great explanation of how to configure these items in our project. We can also refer to one of the [public repositories](https://github.com/K-State-Computational-Core/restaurantregister-python/blob/main/setup.cfg) for this course for another example.

Finally, we've included a couple of items at the bottom that aren't included in the tutorial to allow our package to be compliant with [PEP 561](https://www.python.org/dev/peps/pep-0561/) so that Mypy can make use of the typing information included in our package. This will include the `py.typed` files we added earlier to our eventual package. See the [Mypy Documentation](https://mypy.readthedocs.io/en/stable/installed_packages.html#making-pep-561-compatible-packages) for details.

## Adding Test Files

One thing we may want to do is include our test files in the output. To do that, we must simply add a `__init__.py` file to the `test` directory and any subdirectories of that folder in our project. The Python build process will automatically find those and include them in our package!

## Installing the Build Library

When we are ready to create our package, we must first make sure we have the latest version of the `build` library on our system. So, we can use the `pip3` command to install it:

```bash
pip3 install --upgrade build
```

## Create the Package

Once we are ready, we can run the following command from within our project directory to actually create our packages:

```bash
python3 -m build
```

If all goes well, we should see it create a new folder named `dist` that contains both a `.whl` file as well as a `.tar.gz` file that include our project. That command will also produce a long list of output that contains all of the files that are included in our package. We should review that output closely and make sure it includes all of the correct files.

## Updating Tox Configuration

If we want to automate this process, there are a few things we can do in our `tox.ini` file to make this process go a bit smoother:

* We can add the `build` package to our `requirements.txt` file so it will be available when we run `tox`.
* Right now, our program uses the top level package name `src` based on the `src` directory in our project. If we want, we can change that to any other name we wish. If we do, we'll need to update it throughout our source code and also in a few places in our `tox.ini` file. **You may want to do this before publishing a package so it doesn't use the name `src` as the base of the package path.
* When publishing a package, we probably don't want to include the documentation from our tests in our published documentation. So, instead of a period `.` at the end of our `pdoc` command, we can replace it with `src` or the new name of our top-level package.
* We can automate moving the documentation generated by `pdoc` to the `docs` folder by adding a few commands to our `tox.ini` file to copy the generated documentation. To do this, we need to add an `allowlist_externals` entry that lists the commands we'd like to use.
* Finally, we can add the `python3 -m build` command at the very end of our commands in `tox.ini` to automatically update our package each time we successfully run `tox`.
* Once we are ready to publish, it is a good practice to remove the `ignore_errors` line from our `tox.ini` file. In that way, we'll only create our package if all of the commands succeed.

Below is an updated `tox.ini` file showing these changes. 

```ini
[tox]
envlist = py39
skipsdist = True

[testenv]
deps = -rrequirements.txt
allowlist_externals = rm
                      cp
commands = python3 -m mypy -p src --html-report reports/mypy
           python3 -m coverage run --source src -m pytest --html=reports/pytest/index.html
           python3 -m coverage html -d reports/coverage
           python3 -m flake8 --docstring-convention google --format=html --htmldir=reports/flake
           rm -rvf reports/doc
           python3 -m pdoc --html --force --output-dir reports/doc src
           rm -rvf docs
           cp -rv reports/doc/src docs/
           python3 -m build
```

With everything in place, we can run our `tox` command to build our project. If we recently changed our `requirements.txt` file, we'll need to run `tox -r` at least once to install the new requirements. If everything works correctly, it should place our built packages in the `dist` folder and copy our documentation to the `docs` folder for us. 

## Update Git Ignore file

Finally, before we commit these changes, we may wish to update our git configuration to ignore a few new files or folders created by the build process. Here's the new `.gitignore` file that we can use:

```txt
__pycache__/
.tox
reports/
.coverage
build
*.egg-info/
```

It now ignores the `build` and any `.egg-info` folders. 

If everything looks good, we can save and commit our changes to the git repository for this project.

{{% notice info "Carefully Check Commit" %}}

In this commit, we'll want to carefully check the output of the `git status` command to make sure we are only committing the files we want to the repository. Ideally, the only changes should be to the `tox.ini` and `requirements.txt` files, the new `pyproject.toml` and `setup.cfg` files, as well as all the contents of the new `dist` and `docs` directories.

{{% / notice %}}

## Making a New Version

Now, with all of this automation in place, all we have to do to create a new version of our package is update the version number in our `setup.cfg` file, and then run `tox`. It will automatically create a new set of package files using the new version, and update our documentation to match. 

On the following pages, we'll discuss the steps for creating a release on GitHub that includes these package files for download, and also how to publish these to a repository!
