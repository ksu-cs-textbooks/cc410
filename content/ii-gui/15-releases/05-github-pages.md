---
title: "GitHub Pages"
weight: 25
pre: "5. "
---

As part of the "Hello Real World" project in this course, we learned how to automatically generate documentation for our application based on the documentation comments included in our code. That documentation can be very valuable for anyone who wishes to use or modify our application, so we want to make it available for everyone. 

While it is possible for anyone to download our source code and generate this documentation themselves, many times we want to make this even easier by posting the documentation directly on the Internet. In this way, it is always available for anyone who needs it, without any extra steps. 

Thankfully, many code repository websites such as [GitHub](https://github.com/) make this process quick and easy. Let's explore how to make this content available on GitHub using a feature called [GitHub Pages](https://pages.github.com/)

## Preparing our Documents

First, we need to prepare our documents to be published on GitHub pages. Thankfully, this is a quick two-step process.

1. Generate an updated version of the documentation using either the `javadoc` or `pdoc3` tool. 
2. Copy the associated documentation to a folder named `docs` in our project.

Specifically, we want to copy the folder containing the `index.html` file, as well as any files and folders in that directory, to a new directory at the root of our project named `docs`. In general, this can easily be done with just a couple of commands on the terminal:

{{< tabs >}}

{{% tab name="Java" %}}

```bash
# get to the project folder (this may be different)
cd java
# remove existing docs, if any
rm -rf docs
# copy new docs to that folder
cp -r app/build/docs/javadoc/ docs/
```

{{% /tab %}}

{{% tab name="Python" %}}

```bash
# get to the project folder (this may be different)
cd python
# remove existing docs, if any
rm -rf docs
# copy new docs to that folder (this may be different)
cp -r reports/doc/python/ docs/
```

{{% /tab %}}

{{< /tabs >}}

Once that is done, we should now see a `docs` folder in our project, and within that folder we should find a file named `index.html`. We can right-click that file in Codio and choose **Preview Static** to make sure it is the correct file and that everything is working. 

Once we are satisfied, we should commit that docs folder to git, and then push our changes to our GitHub repository.

## Enabling GitHub Pages

To enable GitHub pages on our repository, we can follow the instructions on [this page](https://docs.github.com/en/github/working-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site) to use the newly created `docs` folder as the publishing source for our website:

1. In the repository on GitHub, go to the **Settings** page.
2. Find the "GitHub Pages" section, and choose the branch to use as the source. Typically, you'll want to choose the `main` or `master` branch.
3. Next to that, choose the `docs` folder as your publishing source.
4. Click the **Save** button.

![Github Pages](/cc410/images/15/gh-pages.png)

After a minute or so, you should be able to visit the URL listed there and you should see your documentation on the web! You can see some examples of what this looks like by reviewing the public repositories in the [K-State Computational Core](https://github.com/K-State-Computational-Core/) organization on GitHub and looking for the documentation links in each `README.md` file. 

On the next pages, we'll review how to build a Java JAR file and a Python wheel file. As always, feel free to skip to the page for your chosen programming language.

