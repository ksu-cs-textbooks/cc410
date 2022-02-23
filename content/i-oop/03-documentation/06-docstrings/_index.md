---
title: "Python Docstrings"
weight: 30
pre: "6. "
---

{{% youtube -aX1FAMnlgw %}}

[Video Materials]({{<relref "./video">}})

Many Python developers have standardized on the use of docstrings as documentation comments. Both [PEP 257](https://www.python.org/dev/peps/pep-0257/) and the [Google Style Guide](https://google.github.io/styleguide/pyguide.html#s3.8-comments-and-docstrings) include information about how those documentation comments should be structured and the information each should contain. This page will serve as a quick guide for the most common use cases, but you may wish to refer to the documentation linked above for more specific examples and information. The [flake8](https://flake8.pycqa.org/en/latest/index.html) tool along with the [flake8-docstrings](https://pypi.org/project/flake8-docstrings/) plugin is also a great way to check that the documentation comments are properly structured.

## General Structure

A properly structured docstring comment includes a few parts:

1. **A summary line**. This is the first part of the comment, ending with the first period. It should concisely describe the object being commented, but doesn't have to be a complete sentence.
2. **Additional Paragraphs**. Following the summary fragment, additional paragraphs may be included to further describe the object. The paragraphs should start at the same indentation as the first quotation mark. Paragraphs are separated by blank lines.
3. **Optional Sections**. While not explicitly required by the standard, there are several optional sections that could be included as part of a docstring. For this course, we'll use the following sections:
   * `Author` (files only)
   * `Version` (files only)
   * `Attributes` (classes with public attributes only)
   * `Args` (methods and constructors only)
   * `Returns` (methods only)
   * `Raises`

You can find more information about the structure of docstrings in the [Google Style Guide](https://google.github.io/styleguide/pyguide.html#38-comments-and-docstrings).

### File Comment

Let's begin by looking at the docstring comment for a file. Here's an example:

```python
"""Implements a simple chessboard.

This file contains a class to represent a chessboard.

Author: Russell Feldhausen russfeld@ksu.edu
Version: 0.1
"""
```

The file docstring gives information about the contents of the file. For object-oriented programs where each file contains a single class, this can be a bit redundant, but it is useful information nonetheless. For other Python files, this may be the only comment included in the file. 

While the Python documentation format does not require listing the author or the version, it is a nice convention from the Javadoc format that we can carry over into our Python docstrings as well.

### Class Comment

Next, let's look at the docstring comment for a class. Here's an example:

```python
class Chessboard:
    """Represents a chessboard and moves chess pieces.
    
    This class stores a chessboard in a 2D array and includes
    methods to move various chess pieces across the board. Squares
    are labelled using algebraic chess notation.
    """
```

This comment includes a summary fragment, and an additional paragraph. Since the class doesn't include any public attributes, we omit that section. Instead, we'll document the accessor methods, or getters and setters, as part of the Python property that is used to access or modify private attributes.  

This comment provides enough information for us to understand what the class is used for and a bit about how it works, even without seeing the code.

### Method Comment

Here's another example docstring comment, this time for a method:

```python
def move_knight(self, source: str, destination: str) -> bool:
    """Moves a knight from one square to another
    
    If a knight is present on source and 
    can make a legal move to destination, the method 
    will perform the move. 
    
    Args:
        source: the source square in algebraic chess notation
        destination: the destination square in algebraic chess notation
        
    Returns:
        True if a piece was captured; False otherwise
 
    Raises:
        ValueError: if a knight is not present on source or 
          if that knight cannot move to destination
    """
```

Similar to the comment above, this comment includes enough information for us to understand exactly what the method does. It tells us about the parameters it accepts and the format it expects, the return value, and any exceptions that could be thrown by this code. With this comment alone, we could probably write the code for the method itself!
