---
title: "GitHub Releases"
weight: 40
pre: "8. "
---

Finally, we've completed creating our package, and we're ready to publish it. One of the easiest options is to include our package files directly in a GitHub release on GitHub.

In the "Hello Real World" example project, we learned how to create a release on GitHub using a tag. The only thing we'll do differently this time is upload our packages to the release. Unfortunately, there is no easy way to select them directly from the repository, so we may have to download the package files from the `dist` directory to our computer first before starting this step.

![Release Page](/images/15/release.png)

When creating a release on GitHub, there is a spot at the bottom of the page to upload binaries. So, we can upload the package files from our `dist` directory right here. In the screenshot, I've uploaded both a JAR and a wheel file, but we would just use each of the package files created in our `dist` folder for the current version of our package.

Once the release is published, we'll see our package files directly on the page ready for anyone to download and use in their own projects!

![Release Downloads](/images/15/release2.png)
