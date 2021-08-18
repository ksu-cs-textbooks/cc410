---
title: "Licenses"
weight: 30
pre: "6. "
---
{{% youtube -USMqm7lgXs %}}

In the world of software, we use the term [**open-source**](https://en.wikipedia.org/wiki/Open_source) to refer to any software that has source code that is openly available. This is in contrast to [**proprietary**](https://en.wikipedia.org/wiki/Proprietary_software) software, sometimes referred to as **closed-source** software, which is software with source code that is not publicly available. The software itself may be sold, or even provided for free, but the actual source code is protected by the company. 

So, before we can use just any software library we find, we should consider what license it uses and how that impacts our ability to use that library. On this page, we'll briefly discuss some of the licenses and terminology used in industry today.

{{% notice tip %}}

# I Am Not A Lawyer

The information below is my best attempt to help simplify the vastly complex legal documents that make up a software license. However, this simple information may not be enough to fully understand all of the nuances of how a particular software license impacts your ability to use it or distribute it with your own software. 

In general, most software that is licensed under one of the more permissive licenses listed below can be safely used in your application, and many (but not all) of them allow you to distribute that software as part of your application as well. 

However, when in doubt, you should always read the documents carefully and seek competent legal advice if you are ever unsure. It is always best to make sure you are properly complying with the license of a piece of software you are using.

{{% / notice %}}

## Free Software

First, let's discuss **free software**. The term "free" has two different meanings, and they are sometimes applied to software interchangeably:

1. Without cost - as in "free food"
2. Without restrictions - as in "free speech"

So, when we say software is "free," it is always important to know which definition of "free" we are using. For example, the [Slack](https://slack.com/) messaging application is available for free, meaning no cost, but with some restrictions applied. Google's [Chrome](https://www.google.com/chrome/) web browser is also free, meaning no cost, and is based on the open source [Chromium](https://www.chromium.org/) project, but Chrome itself is not open source since it contains some proprietary software. These free programs are sometimes referred to as "freeware" - meaning that they are available without cost, but still use proprietary source code.

The [Linux Kernel](https://www.kernel.org/) is an example of a piece of software that is free and open source, however even it has some restrictions applied to it. Namely, the license of the Linux Kernel requires that any software built using the source code of the kernel (a [derivative work](https://en.wikipedia.org/wiki/Derivative_work)) must also be offered under the same license. 

In fact, the [Free Software Foundation](https://www.fsf.org/) has developed a set of four "freedoms" that are used to determine if a piece of software can truly be labelled "free":

* "Use: Free Software can be used for any purpose and is free of restrictions such as licence expiry or geographic limitations."
* "Study: Free Software and its code can be studied by anyone, without non‐disclosure agreements or similar restrictions."
* "Share: Free Software can be shared and copied at virtually no cost."
* "Improve: Free Software can be modified by anyone, and these improvements can be shared publicly."^[https://fsfe.org/freesoftware/]

Software that meets these four criteria sometimes use the term "libre" software, or FOSS ("Free Open Source Software") to differentiate themselves from the traditional definition of the word "free". 

So, as we can see, the term "free" really isn't a great way to discuss software licenses. Instead, we'll focus in on some more specific licenses and what they mean.

## Software Licenses

### Public Domain

The least restrictive license is the [public domain](https://en.wikipedia.org/wiki/Public_domain) license, meaning that the software can be used by anyone for any purpose, without any restrictions. However, the lack of a license does not mean that the software is in the public domain - quite the opposite in many cases. In the United States, any work, whether published or not, is automatically copyrighted to the original author^[https://copyright.cornell.edu/publicdomain] until 70 years after the author's death. So, to release software into the public domain, a proper license must be attached to the software.

One common public domain license is the [Creative Commons CC0](https://en.wikipedia.org/wiki/Creative_Commons_license#Zero_/_public_domain) license, with basically waives as many legal rights as possible on any work that the license is applied to. GitHub recommends a similar license called the [Unlicense](https://choosealicense.com/licenses/unlicense/). 

### Permissive Licenses

[Permissive licenses](https://en.wikipedia.org/wiki/Permissive_software_license) allow few restrictions on the use and distribution of the software.

A permissive license commonly used for software is the [MIT License](https://en.wikipedia.org/wiki/MIT_License), which grants very little restrictions on the use of the software other than that the license itself should be included in any copies or portions of the software. In addition to granting permission, it also includes a disclaimer stating that the software is offered without any warranty and the authors are not liable for any damages caused by use of the software. 

This license is used by a large number of open source projects, and typically is one of the easiest to use.

Some similar licenses are the [BSD](https://en.wikipedia.org/wiki/BSD_licenses) and [Apache](https://en.wikipedia.org/wiki/Apache_License) licenses. 

### Copyleft Licenses

The next level of licenses are the [copyleft](https://en.wikipedia.org/wiki/Copyleft) licenses. These licenses typically require that any [derivative works](https://en.wikipedia.org/wiki/Derivative_work) also be licensed with the same rights. So, if we include a software library that is using a copyleft license in our software, we cannot then make our software proprietary and sell it, as this would violate the copyleft license of that software library.

The most common copyleft license used in software is the [GNU General Public License](https://en.wikipedia.org/wiki/GNU_General_Public_License), or GPL, which is used by the Linux Kernel and many other applications typically included as part of a Linux distribution. This requires that any derivative works of the Linux Kernel also be made available under a copyleft license. 

{{% notice tip %}}

# Copyleft and Derivative Works

One major open question with copyleft licenses - if a piece of software uses a library that is licensed with a copyleft license, but doesn't distribute that library directly as part of its package, is it still considered a derivative work?

This is a hotly debated question with the [Wikipedia Article](https://en.wikipedia.org/wiki/GNU_General_Public_License#Linking_and_derived_works) for the GPL laying out many different points of view on the topic. For example, when a library is statically linked to an application, it is inseparable. However, does the same hold if the library is dynamically linked? Likewise, if a piece of software is just using the public API of a library without modifying the library's source code, is it a derivative work? 

These questions make licensing software that uses libraries under a copyleft license very confusing. Because of this, there is also a [GNU Lesser General Public License](https://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License) or GLPL that specifically addresses this issue by allowing other software to link to libraries licensed with the LGPL without it being considered a derivative work. 

{{% / notice %}}

### Proprietary Licenses

The last category of software licenses are the unique, proprietary licenses that are attached to software that is not open-source or free. Each one of these licenses can vary widely in the rights given to the users, so we should always read them carefully before using them.

## Impact of Licenses

In summary, the licenses of the libraries we use when building our software, as well as any tools or platforms, can all impact the eventual license we can assign to our application if we choose to distribute it. In most cases, we can freely use any open source software for personal use, but as soon as we wish to distribute, or possibly sell, our own software, then we will have to determine what license can be applied to our work. We'll review that in a later chapter. 
