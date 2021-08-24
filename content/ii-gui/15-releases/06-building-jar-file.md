---
title: "Building Java JAR File"
weight: 30
pre: "6. "
---

Building a JAR file using Gradle is super simple - it handles almost all of the heavy lifting for us. The basic steps are outlined in the [Building Java Libraries Simple](https://docs.gradle.org/current/samples/sample_building_java_libraries.html) guide in the Gradle documentation. Below, we'll go through the steps we'll need to follow for most of the applications we've created in this course.

## Run the Build Task

If we haven't already, we should first run the Gradle `build` task. This will automatically create a JAR file for our project, as well as any other required files.

```bash
# Change directory to the project directory (this may be different)
cd java
gradle build
```

Once we've done that, we can find our `app.jar` JAR file in the `app/build/libs` directory. That's really all there is to it, but there are a few more things we can add to make it even better.

## Create README.md

If we haven't already done this, now is a great time to create a `README.md` file in the root directory of our project and include some basic information about our project. Once it is published, we can come back to this file and update it with links to the documentation hosted in GitHub pages.

## Create a LICENSE file

In addition, we may wish to add a license to our project at this step, before packaging it. We can use the [choosealicense.com](https://choosealicense.com/) website to help find a license. We can also easily add a license to an existing GitHub repository following the [Adding a license to a repository](https://docs.github.com/en/github/building-a-strong-community/adding-a-license-to-a-repository) guide from GitHub, then using the `git pull` command to pull that license file into our local copy of the project. 

In either case, make sure we have a file in the root of our project named `LICENSE` before continuing. 

## Adding Metadata

One major thing we may wish to do in our projects is add some metadata to the project. We can do that by adding various entries to our `build.gradle` file. 

### Version

In our `build.gradle` file, we can define the version of our application by simply adding the following line outside of any other section in that file:

```groovy
version = 'v0.1.0'
```

When we set the version, we should see the version number appended to the end of our JAR file. If we are following [Semantic Versioning](https://semver.org/) in our project, we'll need to remember to update this version number in our `build.gradle` file each time we are ready to create a package for release. 

### Project Name

We may also wish to set the overall project name. For Gradle, this is in the `settings.gradle` file, which can be found at the top level of our project. In that document, we should see a setting named `rootProject.name`, which we can update with our project's name. For a single project application like the ones we've been building, we can set the name of that project as well:

```groovy
rootProject.name = 'ourprojectname'
include('app')
project(":app").name = 'ourprojectname'
```

We can also achieve a similar result by simply renaming the `app` directory in our project to match the name we'd like to use. Either method works well. 

### Add Name and Version to Manifest

Once we've set the project name and version in our various Gradle files, we can configure Gradle to include that information in our JAR file. We also need to add the name of the main class to this information if we want our JAR file to be directly executable. To do this, we simply add the following section to our `build.gradle` file:

```groovy
tasks.named('jar') {
    manifest {
        attributes('Implementation-Title': project.name,
                   'Implementation-Version': project.version,
                   'Main-Class': 'ourprojectname.Main')
    }
    archivesBaseName = project.name
}
```

We should replace `ourprojectname.Main` with the correct name and path to our main class. If we've been using Gradle to run our project, it is probably already in the `mainClass` attribute of the `application` section of the file.

Notice that we also can add an `archivesBaseName` setting here to change the base filename of our project's JAR file to match our project name. With all of this in place, we should now be able to run the `gradle build` command and find a JAR file named `ourprojectname-v0.1.0.jar` in the `app/build/libs` directory. 

We can also check that our `MANIFEST` file contains the correct information by extracting it:

```bash
jar xf lib/build/libs/ourprojectname-v0.1.0.jar META-INF/MANIFEST.MF
```

Then, we can open the file named `MANIFEST.MF` can is found in the `META-INF` directory and confirm that everything is correct:

```txt
Manifest-Version: 1.0
Implementation-Title: ourprojectname
Implementation-Version: v0.1.0
```

Once we've verified that our manifest is correct, we can delete the `META-INF` directory so it isn't included in our project. 

## Create a Source and Javadoc JAR

Sometimes, we may want to publish our original source code in a JAR file. That allows developers to easily download and modify our source code, or they can just explore it and see how it works. 

Likewise, in addition to posting our generated Javadoc on the Internet using GitHub Pages, we can also create a JAR file that contains our Javadoc documentation. This JAR file can be imported into many Java IDEs, such as Eclipse, NetBeans, and IntelliJ to allow the IDE to automatically show relevant portions of our documentation to developers as they use our library. To do this, we just need to add the following section to our `build.gradle` file:

```groovy
java {
    withSourcesJar()
    withJavadocJar()
}
```

We'll also need to add sections to configure those JAR files. These are exactly the same as the one created above, but with different task names:


```groovy
tasks.named('sourcesJar') {
    manifest {
        attributes('Implementation-Title': project.name,
                   'Implementation-Version': project.version)
    }
    archivesBaseName = project.name
}

tasks.named('javadocJar') {
    manifest {
        attributes('Implementation-Title': project.name,
                   'Implementation-Version': project.version)
    }
    archivesBaseName = project.name
}
```

Now, when we execute our `gradle build` command, we should see `ourprojectname-v0.1.0.jar` as well as both `ourprojectname-v0.1.0-sources.jar` and `ourprojectname-v0.1.0-javadoc.jar`. So, when we publish our package, we can also publish these JAR files as well.

## Automate Creation of Docs and Dist Artifacts

There are a few other changes we can make to our project to make everything quick and easy to assemble. Let's review them now:

### Customize Javadoc

Originally, we configured our project to include the Javadoc from our test files in the Javadoc for our entire project. While that may be useful for us internally as we are developing our code, we may not want to include that in our final Javadoc output. So, we can uncomment those lines in our `build.gradle` file.

In addition, as we saw on a previous page, we can move our Javadoc output to a folder named `docs` in our root project folder, and then GitHub Pages can automatically publish that documentation along with our project. Thankfully, we can configure our `build.gradle` file to automatically output the Javadoc files directly to that folder.

With those updates in place, the `javadoc` section of our `build.gradle` file may look something like this:

```groovy
javadoc {
    // classpath += project.sourceSets.test.compileClasspath
    // source += project.sourceSets.test.allJava
    destinationDir = file("${rootDir}/docs/")
}
```

Now, when we run the `gradle build` command, we should see our generated Javadoc documentation appear in the `docs` folder, right where it needs to be.

### Create Dist Folder

We'd also like to make sure our generated JAR files are easy for users to find in our repository. It is a common practice to create a folder named `dist` in our project directory to contain any distributable packages we create and publish. So, we can easily update our `build.gradle` file to place any JAR files there. We'll need to do this in all three of the JAR tasks:

```groovy
tasks.named('jar') {
    manifest {
        attributes('Implementation-Title': project.name,
                   'Implementation-Version': project.version,
                   'Main-Class': 'ourprojectname.Main')
    }
    archivesBaseName = project.name
    destinationDirectory = file("${rootDir}/dist/")
}

tasks.named('sourcesJar') {
    manifest {
        attributes('Implementation-Title': project.name,
                   'Implementation-Version': project.version)
    }
    archivesBaseName = project.name
    destinationDirectory = file("${rootDir}/dist/")
}

tasks.named('javadocJar') {
    manifest {
        attributes('Implementation-Title': project.name,
                   'Implementation-Version': project.version)
    }
    archivesBaseName = project.name
    destinationDirectory = file("${rootDir}/dist/")
}
```

As before, we can test this by running `gradle build` and seeing that our JAR files are now placed in the `dist` directory in our project.

## Summary

So, in summary, we updated our project configuration in the following ways:

* The `settings.gradle` file now includes our root project's name and updates the name of our single project:

```groovy
rootProject.name = 'ourprojectname'
include('app')
project(":app").name = 'ourprojectname'
```

* We updated `build.gradle` to:
  * Set the version number
  * Remove test file comments from the Javadoc
  * Redirect the Javadoc output to the `docs` folder
  * Create a JAR file for both the source code and Javadoc
  * Set the metadata in each JAR file
  * Output each JAR file to the `dist` folder
  
```groovy
javadoc {
    // classpath += project.sourceSets.test.compileClasspath
    // source += project.sourceSets.test.allJava
    destinationDir = file("${rootDir}/docs/")
}

version = 'v0.1.0'

java {
    withSourcesJar()
    withJavadocJar()
}

tasks.named('jar') {
    manifest {
        attributes('Implementation-Title': project.name,
                   'Implementation-Version': project.version)
    }
    archivesBaseName = project.name
    destinationDirectory = file("${rootDir}/dist/")
}

tasks.named('sourcesJar') {
    manifest {
        attributes('Implementation-Title': project.name,
                   'Implementation-Version': project.version)
    }
    archivesBaseName = project.name
    destinationDirectory = file("${rootDir}/dist/")
}

tasks.named('javadocJar') {
    manifest {
        attributes('Implementation-Title': project.name,
                   'Implementation-Version': project.version)
    }
    archivesBaseName = project.name
    destinationDirectory = file("${rootDir}/dist/")
}
```

Finally, we can run `gradle build` one more time, and then commit our changes to our repository. 

{{% notice info info-1 "Carefully Check Commit" %}}

In this commit, we'll want to carefully check the output of the `git status` command to make sure we are only committing the files we want to the repository. Ideally, the only changes should be to the `build.gradle` and `settings.gradle` files, as well as all the contents of the new `dist` and `docs` directories.

{{% / notice %}}

## Making a New Version

Now, with all of this automation in place, all we have to do to create a new version of our package is update the version number in our `build.gradle` file, and then run `gradle build`. It will automatically create a new set of JAR files using the new version, and update our documentation to match. 

On the following pages, we'll discuss the steps for creating a release on GitHub that includes these JAR files for download, and also how to publish these to a repository!
