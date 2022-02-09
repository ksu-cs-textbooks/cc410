---
title: "Licenses"
pre: "2. "
weight: 20
date: 2020-03-06T00:53:26-05:00
hidden: true
---

{{< youtube -USMqm7lgXs >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

One major aspect of working with external software libraries is the license actually used by the library. A software license is a legal document that describes how the software can be used and what restrictions are placed on it. So, now is a great time to review that topic and discuss some of the more commonly used software licenses in the world today. However, before I do that, a quick disclaimer. I am not a lawyer, and software licenses are, by nature, legal documents. So, while I'm doing the best I can to give you the information you need, if you are ever unsure you should seek qualified advice. With that said, let's get started.

First, let's discuss the word free. In terms of software licensing, the word free can really have two different meanings. The first meaning is "without cost", typically referred to as "free as in food". So, in this sense, a free piece of software is one that can be obtained without cost, such as the Slack desktop application, Google Chrome web browser, or even Visual Studio Code. However, just because those programs are free doesn't mean that they don't come with restrictions. This is because the other definition of free is "without restrictions", typically referred to as "free as in speech". For software to be free according to this definition, you should be able to use it in any way, and even look at and change the source code if desired.

In short, free is a very difficult term to use for software licensing, and just because something is free doesn't mean that it is actually free. 

So, let's dive into software licenses. First, let's discuss copyright. In the United States, copyright is automatic and applied to any work, published or unpublished. So, if a piece of software doesn't have any license attached to it, it is assumed to be under copyright and it may not be legal to even download or use the software without permission from the author. GitHub gets around this a bit with their user agreement, which states that any code published in a public repository may be downloaded and viewed without violating copyright, but that's about it. So, if we actually want anyone to be able to legally use our software, we should attach a license to it.

One option is to release the software into the public domain. The public domain is the least restrictive of all software licenses, and it basically means that anyone can use the software for any purpose, including repackaging it and reselling it for a profit. In general, it is not recommended to apply a public domain license to software, but if you would like to do so the Creative Commons CC0 or GitHub Unlicense are two choices to go this route.

The next category of licenses are the permissive licenses. These are similar to the public domain licenses in that they place very few restrictions on who can use the code and how they can use it, but it does add some important protections. First, it usually specifies that the license must be attached to any copies of the source code itself, and that the original author of the software cannot be held liable for any use or misuse of the software or any damages caused by using the software. This protection is very important, since we can never really guarantee that our software won't cause issues when someone tries to run it. Finally software under this license can usually be repackaged and resold under a different license. Some common choices for permissive licenses are the MIT license, which is recommended by GitHub, as well as the similar BSD and Apache licenses. 

Another category of software license is the copyleft license, which is a play on the word "copyright". In effect, a copyleft license is used to make sure that the software always remains free and open, and so it prevents anyone from repackaging or reselling the software. Likewise, any derivative works of the software must also be licensed in the same way, so you cannot simply change it a bit and then call it your own. Finally, under a copyleft license, it is still a bit unclear if you are allowed to use it as a library within another piece of software under a different license, but generally that is accepted as OK even though it hasn't been tested in court yet. A great example of a copyleft license is the GNU General Public License, or GPL. 

Finally, there is an entire category of licenses for commercial software that we'll just call proprietary licenses. These define exactly who can use a program and what limits are placed on that use. Many times these are the "end user license agreements" or "EULA"s that you agree to each time you install or use a new piece of software. 

So, in short, there are a few basic cases to understand when dealing with software licenses. If there is no license attached, it is assumed to be copyrighted. Beyond that, if the software is in the public domain, then you'll find a license like the Unlicense or CC0 attached to it. For software that has few restrictions, look for the MIT, BSD, or Apache licenses attached. Software that has a copyleft license like the GNU GPL will always be free and open source, and finally any corporate software is most likely licensed under a unique proprietary license that you should read carefully in order to understand exactly how it can be used. 

Hopefully this overview of software licenses is helpful as you navigate the world of installing external libraries and possibly creating your own. 