---
title: "Choosing a License"
weight: 15
pre: "3. "
---
The next major step in releasing a piece of software is to choose a license. Adding a license to your software allows you to specify what the software can be used for, who can use it, and how they can make use of it either within their own applications or by possibly distributing and building derivative works. 

In the previous chapter, we discussed various software licenses and what they mean when we try to use a library under that license. Now, let's look at what it means to release our software using those licenses.

{{% notice warning "I Am Not A Lawyer" %}}

The information below is my best attempt to help simplify the vastly complex legal documents that make up a software license. However, this simple information may not be enough to fully understand all of the nuances of how a particular software license impacts other users' ability to interact with your software, and your liabilities when it comes to that use.

In general, choosing to license your software under one of the more permissive licenses listed below will generally make the application available to all users and protect you from any liability. However, it does not give you any control over how the application may be used by others, including commercial use. 

However, when in doubt, you should always read the documents carefully and seek competent legal advice if you are ever unsure. It is always best to make sure you understand the consequences of choosing a particular software license.

{{% / notice %}}

## Choosing a License

To help choose a software license that fits your project, GitHub helpfully maintains the site [choosealicense.com](https://choosealicense.com/). It helps developers choose an applicable license by asking a few simple questions. We'll discuss some of those questions below and the various licenses they lead to.

### Community License

For starters, if your project is meant to be part of a larger community of projects, consider using the license that is used by other projects in that community. For example, if we are building a library that is meant to be an add-on for an existing application, it makes sense to choose the license that the application is distributed under. In that way, we can guarantee that our project is available to anyone who can use the application it is meant for.

Likewise, if you are working for a company or with a group of developers, they may already have a preferred license for you to use. In those cases, consulting with others in your group is a valuable way to learn what licenses are being used by the group and how your application may fit in.

### Public Domain

The first major choice is whether we'd like to place any limitations on how our software is used at all. If the answer is no, then most likely we'll want to choose one of the **public domain** licenses available. This is the most open license, which allows anyone the ability to use our application in any way they wish. 

GitHub recommends using the [Unlicense](https://choosealicense.com/licenses/unlicense/) for this, which effectively will release the software into the public domain and absolve the creator of any liability or warranty concerns related to the software. Similarly, many creative works may also choose to use the Creative Commons [CC0](https://creativecommons.org/share-your-work/public-domain/cc0/) license to release the content into the public comain. 

### Permissive License

A **permissive license** is another common choice for software that we'd like to make freely available to users with a minimum set of limitations. Typically, the only limitation we place on software using these licenses is that the original source code itself must be distributed using this license, but derivative works may be licensed under different terms.

By far the most common permissive license for software on GitHub is the [MIT License](https://choosealicense.com/licenses/mit/). This license is used by many open-source projects that wish to keep their code as open as possible, while still allowing users to repackage and redistribute the software as part of a larger commercial package.

### Copyleft License

A **copyleft license** is a good choice when we want to make sure that our software remains freely available to users, including any major modifications or derivative works. In general, a copyleft license requires any modifications to our application, or any application that makes major use of our application and source code, to be released under the same license. 

The most common choice for a copyleft license is the [GNU General Public License](https://choosealicense.com/licenses/gpl-3.0/) (GPL), which is used by many projects related to the Linux operating system. Any software licensed using the GPL includes the limitation that any derivative works are also licensed under the GPL. In this way, a commercial entity couldn't take our application and repackage it or resell it commercially.

A similar choice is the [GNU Lesser General Public License](https://choosealicense.com/licenses/lgpl-3.0/) (LGPL), which modifies the GPL to explicitly allow software that only make use of the public interface of our software to be distributed under a different license. Put another way, a commercial application that makes use of our library's API could still be sold, but our library must be distributed with its license intact. Any derivative works will still require licensing under the LGPL. 

### No Choice - Default Copyright

Of course, if we choose not to include a license with our software, it will be copyrighted by default, at least in the United States. This means that, even though our source code may be available on the Internet, anyone who chooses to use it could be violating our copyright and subject to legal action. This is further complicated by other agreements such as the [GitHub Terms of Service](https://docs.github.com/en/github/site-policy/github-terms-of-service), which allows users on that site to view and "fork" any repository available publicly, regardless of the underlying license or lack thereof. 

GitHub provides a good [overview](https://choosealicense.com/no-permission/) of what happens when you choose to publish software without a license. That said, it is highly recommended to either choose an open-source license listed above, or make the code private until we are ready to choose a license. 

{{% notice note "Case Study" %}}

#### The CC 410 Course Materials

Now that we've discussed the various software licenses available, this is a good time to dig deeper into this course and talk about the license attached to various portions of the course. As stated earlier, I am not a lawyer and this is not meant to be a substitute for reading and exploring the licenses yourself, but here is a quick overview of the various licenses used in this course.

* **Course Textbook, Videos, Slides, and Milestones** - Much of the textbook content in this course is licensed using the [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/) license. This is similar to a copyleft license and it states that this content may be used and reused freely, but any derivative works must be attributed to the original source, may not be commercially used or sold, and must also be available under a similar license. Basically, we want anyone to be able to use our materials, but we don't want someone else reselling it as their own, and we want it to always be publicly available, including any enhancements or updates. See the [License & Attribution](https://core.cs.ksu.edu/license/) page on our website. 
* **Course Quizzes, Exams, Model Solutions, and Project Starters** - Any content not explicitly listed above is considered to be copyrighted, and cannot be shared or used outside of this class. Most of this content is stored either in private repositories on GitHub or our internal GitLab server, or is only a part of the course on Canvas or Codio. By enrolling in this course, we are giving you permission to access and use these resources for your own education, but you may not share or distribute them without our permission. See the [Copyright Notice](https://core.cs.ksu.edu/5-cc410/00-introduction/06-syllabus-410/#copyright-notice) on the course syllabus. 
* **Publicly Available Software Libraries** - There are a few publicly available software libraries created for this course, which can be found on the course's [GitHub Organization](https://github.com/K-State-Computational-Core/). These repositories each include their own license, and mostly use the [MIT License](https://choosealicense.com/licenses/mit/). So, you can freely use, reuse, and adapt the code there as you wish. 
* **Student Work** - In the United States, students maintain the copyright on any work they produce as a student as part of their regular academic career. This means that any code you produce in this course, including in the final project, ongoing course project, and your portions of the example projects are yours to do what you want with. In most cases, the school also maintains the right to modify, mark on, and retain those works (basically, this is what allows me as an instructor to review and grade your work, and also to use your solutions to help improve my own solutions for future students). 

The last bullet point above is tricky, because this legally allows you as a student to post your project solutions on GitHub and share them publicly. This is great, as it allows you to use this project as part of your portfolio that you can share with others, and maybe even include it in your resume as you apply for jobs. However, it also means that other students can see your code and possibly submit it as their own, violating the [K-State Honor Code](https://www.k-state.edu/honor/basics/pledge.html). This is made even more difficult because the student sharing a solution could be considered liable in addition to the student who chooses to use it. 

While we cannot prevent you from posting these solutions, at least on copyright grounds, here is my recommendation for the best way to protect yourself and others from running into issues:

1. While in the course, keep your solutions private and do not share them with others. This will protect you from possible K-State Honor Code violations during the course and allow you to complete your work without worrying about other students using it.
2. Once you've completed the course, you may choose to publicly post any materials you hold the copyright to, including your ongoing milestone project and the final project. You may also post the portions of the example projects that you wrote, but the original starter files should not be posted as they are copyrighted at this point.  

In this course, we use some tools for detecting plagiarized code, and we also update the projects from time to time to prevent reuse of entire solutions between semesters. In general, a student found to be using a solution that was published online by a previous student will be held liable for violating the K-State Honor Code, but not the student who chose to exercise their rights to publish that solution after the conclusion of the course. 

{{% / notice %}}
