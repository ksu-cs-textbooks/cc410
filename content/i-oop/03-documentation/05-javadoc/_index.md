---
title: "Javadoc"
weight: 25
pre: "5. "
---

{{% youtube QYAda6-2rVw %}}

[Video Materials]({{<relref "./video">}})

The Java software development kit (SDK) includes a tool called Javadoc, which can create documentation based on the documentation comments included in the code. Both the [Javadoc Documentation](https://www.oracle.com/technical-resources/articles/java/javadoc-tool.html) and the [Google Style Guide](https://google.github.io/styleguide/javaguide.html#s7-javadoc) include information about how those documentation comments should be structured and the information each should contain. This page will serve as a quick guide for the most common use cases, but you may wish to refer to the documentation linked above for more specific examples and information. The [Checkstyle](https://checkstyle.sourceforge.io/) tool is also a great way to check that the documentation comments are properly structured.

## General Structure

A properly structured Javadoc comment includes a few parts:

1. **A summary fragment**. This is the first part of the comment, ending with the first period. It should concisely describe the object being commented, but doesn't have to be a complete sentence.
2. **Additional Paragraphs**. Following the summary fragment, additional paragraphs may be included to further describe the object. The paragraphs should start with the `<p>` tag. However, unlike HTML, notice that there is no matching `</p>` closing tag required. 
3. **Tags**. Javadoc supports many tags. Here are the most common tags, listed in the order in which they should appear:
   * `@author` (classes and interfaces only)
   * `@version` (classes and interfaces only)
   * `@param` (methods and constructors only)
   * `@return` (methods only)
   * `@throws`
   * `@see`

When including multiple `@author`, `@param` or `@throws` tags, there are some rules governing the ordering of the tags as well. You can find much more information about the tags and how they can be used in the [Javadoc Documentation](https://www.oracle.com/technical-resources/articles/java/javadoc-tool.html#tag). 

### Class Comment

Let's begin by looking at the Javadoc comment for a class. Here's an example:

```java
/**
 * Represents a chessboard and moves chess pieces.
 *
 * <p>This class stores a chessboard in a 2D array and includes
 * methods to move various chess pieces across the board. Squares
 * are labelled using algebraic chess notation.
 *
 * @author Russell Feldhausen russfeld@ksu.edu
 * @version 0.1
 */
public class Chessboard {
```

This comment includes a summary fragment, and additional paragraph, and the two required tags for a class comment, `@author` and `@version`. At a minimum, each class we develop should include this information directly above the class declaration. 

This comment provides enough information for us to understand what the class is used for and a bit about how it works, even without seeing the code.

### Method Comment

Here's another example Javadoc comment, this time for a method:

```java
/**
 * Moves a knight from one square to another
 *
 * <p>If a knight is present on <code>source</code> and 
 * can make a legal move to <code>destination</code>, the method 
 * will perform the move. 
 *
 * @param source       the source square in algebraic chess notation
 * @param destination  the destination square in algebraic chess notation
 * @return             <code>true</code> if a piece was captured; 
 *                     <code>false</code> otherwise
 * @throws IllegalArgumentException     if a knight is not present on 
 *                                      <code>source</code> or if that knight 
 *                                      cannot move to <code>destination</code>
 */
public boolean moveKnight(String source, String destination) {
```

Similar to the comment above, this comment includes enough information for us to understand exactly what the method does. It tells us about the parameters it accepts and the format it expects, the return value, and any exceptions that could be thrown by this code. With this comment alone, we could probably write the code for the method itself!

### Other Comments

The two examples above cover most places where we would use Javadoc comments in our code. The only other example would be for any public attributes of a class, as in this example:

```java
/** The Student's Wildcat ID */
public int wid;
```

However, as we discussed in a previous module, if we follow the concepts of encapsulation and information hiding we shouldn't have any publicly-accessible attributes, only public accessor methods such as getters and setters, which can be documented as methods. So, we probably won't end up using this much in our own code.
