---
title: "Summary"
weight: 40
pre: "8. "
---

In this chapter, we examined the need for software documentation aimed at both end-users and developers (_user documentation_ and _developer documentation_, respectively). We also examined some formats this documentation can be presented in: HTML, Markdown, and XML.  We also discussed _documentation generation_ tools, which generate developer documentation from specially-formatted comments in our code files.  

We examined the both the Java and Python approach to documentation comments, helping other developers understand our code. For this reason, as well as the ability to produce HTML-based documentation using a documentation generator tool, it is best practice to use documentation comments in all our programs.

{{< quizdown >}}

---
primaryColor: '#512888'
secondaryColor: '#cccccc'
textColor: black
shuffleQuestions: true
shuffleAnswers: true
locale: en
---

# Documentation

Broadly speaking, **documentation** refers to what?

1. [X] Written materials that accompany program code
1. [ ] The number of times a program is executed
1. [ ] Log file outputs from a program
1. [ ] The list of authorized users of a program

# User Documentation

**User documentation** is meant for whom?

1. [X] End-users of the software
1. [ ] Developers of the software

# Developer Documentation

**Developer documentation** is meant for whom?

1. [ ] End-users of the software
1. [X] Developers of the software

# HTML

**HTML** documentation uses what marker to denote a block of code?

1. [X] The `<code>` tag
1. [ ] Three backticks ` ``` `

# Markdown

**Markdown** documentation uses what marker to denote a block of code?

1. [ ] The `<code>` tag
1. [X] Three backticks ` ``` `

# Uses Markdown

Which of the following tools use or support Markdown? **Choose all that are correct.**

- [X] GitHub
- [X] Codio
- [X] Hugo
- [X] Discord

# Code Comments

**Code comments** are best defined by what statement?

1. [X] Extra text in the source code ignored by the compiler or interpreter
1. [ ] Output from a linting tool
1. [ ] List of developers who modified each line of code
1. [ ] GitHub issues impacted by a code commit

# Literate Programming

**Literate programming** is best described by what statement?

1. [X] Writing complete explanations of the program’s logic in comments
1. [ ] Developing code only using English keywords
1. [ ] Writing code that rhymes internally
1. [ ] Correctly following a company's style guide

# Self-Documenting Code

In theory, **self-documenting code** requires how much additional documentation beyond the code itself?

1. [X] None
2. [ ] One comment per file
3. [ ] One comment per method
4. [ ] One comment per line

# Java Comments

Comments in **Java** may be denoted using which of the following formats? **Choose all that are correct.**

- [X] Two slashes `//`
- [X] Slash asterisk `/*` followed by asterisk slash `*/`
- [X] Slash two asterisks `/**` followed by asterisk slash `*/`
- [ ] Hash symbol `#`

# Python Comments

Comments in **Python** may be denoted using which of the following formats? **Choose all that are correct.**

- [ ] Two slashes `//`
- [ ] Slash asterisk `/*` followed by asterisk slash `*/`
- [X] Three double quotes `"""` followed by three double quotes `"""`
- [X] Hash symbol `#`

# Documentation Generators

Which of the following programs are examples of **documentation generators**? **Choose all that are correct.**

- [X] Javadoc
- [X] pdoc3
- [ ] Flake8
- [ ] Checkstyle

{{< /quizdown >}}