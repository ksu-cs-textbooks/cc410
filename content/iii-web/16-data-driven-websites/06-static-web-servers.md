---
title: "Static Web Servers"
weight: 30
pre: "6. "
---

{{% notice info info-1 "content note" %}}

Much of the content in this page was adapted from Nathan Bean's [CIS 400](https://textbooks.cs.ksu.edu/cis400/3-web-development/02-aspdotnet/02-static-webservers/) course at K-State, with the author's permission. That content is licensed under a [Creative Commons BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.

{{% / notice %}}

Now that we've learned about all of the core technologies used to create and deliver webpages, let's take a deeper look at the software that runs on the servers that are responsible for receiving HTTP requests and responding to them. We typically call these programs **web servers**.

The earliest web servers simply served files held in a directory, and in fact many web servers today are still capable of doing exactly that. For example, K-State Computer Science provides a basic web server that can be used to host a personal web page for any faculty, staff, or students in the department. According to the [instructions](https://support.cs.ksu.edu/CISDocs/wiki/Personal_Web_Pages), all you have to do is place the files in a special folder named `public_html` on the central `cslinux.cs.ksu.edu` server, and then they can be accessed at the address `http://people.cs.ksu.edu/~[eid]/` where `[eid]` is your K-State eID.

[Apache](https://www.apache.org/) is one of the oldest and most popular open-source web servers in the world.  Microsoft introduced their own web server, [Internet Information Services (IIS)](https://www.iis.net/) around the same time.  Unlike Apache, which can be installed on most operating systems, IIS only runs on the Windows Server operating system. More recently, the [nginx](https://www.nginx.com/) server has become very popular due to its focus on high performance.  

As the web grew in popularity, there was tremendous demand to supplement these static pages with pages created on the fly in response to requests - allowing pages to be customized for a particular user, or displaying the most up-to-date information from a database.  In other words, _dynamic_ pages.  We'll take a look at these next.
