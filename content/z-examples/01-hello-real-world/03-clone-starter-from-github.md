---
title: "Clone Starter from GitHub"
weight: 30
pre: "3. "
---

{{< youtube mZIqb6OQYZg  >}}

Once we have accepted the assignment on GitHub classroom and have access to the repository, we can "clone" it in Codio, allowing us to access any starter code and then add our own code as we continue to work through this example project. This project doesn't include any starter code, but we'll go ahead and do this step first, just like we would with any other project.

## Find GitHub Repository URL

At this point, you should have access to a repository page that looks like this:

![GitHub Classroom Repository](/images/e1/32repo.png)

On that page, we need to get the SSH URL of this repository. We can find it by clicking the green **Code** button in the upper right. On the box that appears, make sure you select the SSH option to get the SSH URL. It should look similar to this:

![GitHub Classroom SSH URL](/images/e1/32sshurl.png)

The SSH URL should begin with `git@github.com:`. If it starts with `https://` then you need to select the SSH option. Once you have the correct URL, select it and **copy** it to your clipboard.

## Clone Project in Codio

Next, we need to open a Linux terminal in Codio and use the `git` command line tool to clone that repository in Codio. Make sure your terminal is in the `workspace` folder by running this command first:

```bash
cd ~/workspace
```

It should be in that folder by default, but it is always a good idea to check by either running the command above or looking at the end of the command prompt. 

Then, we will use a command structured like this to clone the repository. **do not run this command - keep reading**:

```bash
git clone <SSH URL> <language folder>
```

In that command, replace the `<SSH URL>` portion with the SSH URL you copied from GitHub above. Also, replace the `<language folder>` section with the name of the folder for the programming language you wish to use. 

For example, if I would like to complete this exercise using the Java programming language, my command would look like this:

```bash
git clone git@github.com:K-State-Computational-Core/example-1-hello-real-world-russfeld-student.git java
```

For Python, I would use:

```bash
git clone git@github.com:K-State-Computational-Core/example-1-hello-real-world-russfeld-student.git python
```

Of course, your SSH URL will be different, so you must adjust the required command above to meet your needs. Basically, just type `git clone`, then a space, then paste in your SSH URL, and then another space, followed by the name of the programming language that you'd like to use. That's all it takes!

When I run that command, I'll get output that looks like this:

![Git Clone Output](/images/e1/32clone.png)

If this is the first time you've used `git` in this Codio project, you'll have to type `yes` and press enter at the prompt to accept the key for `github.com`. Once you do that, then the rest of the command will complete and you'll see the following output:

![Git Clone Success](/images/e1/32clonedone.png)

Since I used `java` as the last part of that command, I should now see at least two new items in the `java` folder in the Codio file tree:

![Codio File Tree After Git](/images/e1/32filetree.png)

If you choose `python`, you'll probably see the same items inside of the `python` directory instead. The `.git` and `.github` folders contain information about the repository and the classroom assignment, and should be left alone. **DO NOT DELETE OR MODIFY THESE FOLDERS!** You may notice that they are not present in many of the screenshots in this assignment, just as a reminder to ignore them completely.

{{% notice info "Wrong Folder" %}}

If you accidentally forget to specify a folder at the end of the `git clone` command, or specify the wrong folder, your repository may not be in the `java` or `python` folder that already exists in Codio. In that case, there are a couple of remedies you may try:

1. Delete the folder that was created in error, and try the command again with the correct folder name.
2. Delete the existing `java` or `python` folder, and rename the new folder to the correct name. 

{{% /notice %}}

{{% notice info "Folder Not Empty" %}}

If you try to clone a repository into a folder that is not empty, you'll get an error message. In that case, it is best to completely delete the folder and try again. If the folder doesn't exist, the `git` command will create it for you.

{{% /notice %}}

{{% notice warning "Permission Errors" %}}

If you receive an error message stating "Could not read from remote repository," double-check your URL and try again. If it still doesn't work, let the instructor know. There is a chance that the instructor simply needs to authorize the Codio SSH keys on the new GitHub classroom instance. We have to do this each semester, and it can easily be forgotten. You may earn some bug bounty points for letting us know about this!

{{% /notice %}}

If you were able to successfully clone the project from GitHub Classroom into Codio, you are ready to begin coding! From here on out, the guide will refer to the `java` and `python` folders directly, assuming that you've properly cloned the assignment from GitHub correctly.

## Next Steps

The next parts of this project are different for Java and Python. Click the link below to jump to the correct section for your language. You can also use the links in the menu to the left. 

[Java](04-java/)  
[Python](04-python/)

