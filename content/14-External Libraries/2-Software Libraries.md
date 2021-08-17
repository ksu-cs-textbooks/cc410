---
title: "Software Libraries"
weight: 10
pre: "2. "
---
{{% youtube 9hdiuaZ2wRY %}}

The term **software library** can actually mean several things. In essence, a [software library](https://en.wikipedia.org/wiki/Library_(computing)) is a collection of resources that can be used by computer program, either while it is running or while it is being developed. As we've learned so far in this course, it makes sense to think of a large software program as a few smaller packages or subsystems that work together. With that view in mind, a software library simply is a subsystem or package that is **developed outside of our application**. In most cases, it is meant to be reused by many different programs.

In fact, one of the major benefits of writing our software in a modular format is to enable this exact kind of [code reuse](https://en.wikipedia.org/wiki/Code_reuse). A program developed for one task may include code that could easily be repurposed for a similar task. A great example is a system for ordering food online at a restaurant. That same system includes many of the same components that would be required for any other e-commerce website, such as one that sells handmade arts and crafts. So, many portions of that software could be turned into general-purpose libraries that can be reused. 

![Playing an Ogg Vorbis File](../../images/14/ogg_vorbis.svg)^[https://commons.wikimedia.org/w/index.php?title=File:Ogg_vorbis_libs_and_application_dia.svg&oldid=456091091]

The diagram above shows an example of what it might look like for an application to use an external library to handle playing an [Ogg Vorbis](https://en.wikipedia.org/wiki/Vorbis) file, which is an audio file format similar to an MP3. It makes no sense for use to "reinvent the wheel" for playing an Ogg Vorbis file, even though the entire format is published online. Instead, we can find a compatible library for the language we are using, such as the `libvorbisfile` library shown in this diagram, and include that library in our software.

To play the file, we can call the functions in the library's [API](https://en.wikipedia.org/wiki/API) that accomplish that task. When we do, we can provide the Ogg Vorbis file as input, and we'll receive a decoded audio stream that we can send to yet another library that handles playing audio on our system. So, we can see these libraries as just another set of subsystems that our code interacts with in order to achieve its intended goal.

### References

* [Library (computing)](https://en.wikipedia.org/wiki/Library_(computing)) on Wikipedia
* [Ogg Vorbis](https://en.wikipedia.org/wiki/Vorbis) on Wikipedia
* [API](https://en.wikipedia.org/wiki/API) on Wikipedia
