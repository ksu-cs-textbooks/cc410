---
title: "Boxes"
weight: 15
pre: "3. "
---
UML class diagrams are largely composed of _boxes_ - basically a rectangular border containing text. UML class diagrams use boxes to represent units of code - i.e. classes, structs, and enumerations.  These boxes are broken into compartments.  For example, an `Enum` is broken into two compartments:

![A UML Enum representation](/cc410/images/5/umlbox.png)

### Stereotypes 

UML is intended to be language-agnostic.  But we often find ourselves in situations where we want to convey language-specific ideas, and the UML specification leaves room for this with  _stereotypes_. Stereotypes consist of text enclosed in double less than and greater than symbols.  In the example above, we indicate the box represents an enumeration with the `<<enum>>` stereotype.
