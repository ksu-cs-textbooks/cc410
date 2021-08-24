---
title: "Introduction"
weight: 5
pre: "1. "
---

Earlier in this course, we learned that an object-oriented program can be thought of as two different parts, the **state** of the program, and the **behavior** in the program. In this chapter, we're going to discuss ways that we can save the program's state while it is running. By doing so, we can then resume the program at a later time by simply loading that state back into memory.

This is a process generally known as **serialization**, though other languages may use other terms. Most notably, the process that Python uses is known as **pickling** in the Python documentation. Other documents may refer to this process as **marshalling**. 

At its core, this is simply the process of taking either the whole or a part of a program's state and converting it into a format that can be stored and/or transmitted, and then read back into memory to create a semantically identical state of the program. 

Thankfully, we don't have to worry about the **behavior** of the program, since that is already present in the program's source code and any associated files that are created by compiling or executing the code. As long as the code hasn't changed since the state was saved, we'll be able to completely reconstruct the program, including both **state** and **behavior**.
