---
title: "Summary"
weight: 40
pre: "8. "
---
In this section, we learned about UML class diagrams, a language-agnostic approach to visualizing the structure of an object-oriented software system.  We saw how individual classes are represented by boxes divided into three compartments; the first for the identity of the class, the second for its attributes, and the third for its operators. We learned that italics are used to indicate abstract classes and operators, and underlining static classes, attributes, and operators.

We also saw how associations between classes can be represented by arrows with specific characteristics, and examined four of these in detail: aggregation, composition, generalization, and realization.  We also learned how multiplicities can show the number of instances involved in these associations.

Finally, we saw how classes, interfaces, and enumerations are modeled using UML.  We saw how the stereotype can be used to indicate language-specific features like properties.  We also looked at creating UML class diagrams using Diagrams.net and Microsoft Visio.

{{< quizdown >}}

---
primaryColor: '#512888'
secondaryColor: '#cccccc'
textColor: black
shuffleQuestions: true
shuffleAnswers: true
locale: en
---

# UML

**UML** is the shortened version of what name?

1. [X] Unified Modeling Language
1. [ ] United Modality Language
1. [ ] United Modeling Language
1. [ ] Unified Modality Language

# Class Diagram

A **class diagram** is used to communicate what information about a program?

1. [X] Structure and relationships between classes
1. [ ] Links and communication between software components
1. [ ] Chronological sequence of object interactions
1. [ ] How the users will interact with the software

# Component Diagram

A **component diagram** is used to communicate what information about a program?

1. [ ] Structure and relationships between classes
1. [X] Links and communication between software components
1. [ ] Chronological sequence of object interactions
1. [ ] How the users will interact with the software

# Sequence Diagram

A **sequence diagram** is used to communicate what information about a program?

1. [ ] Structure and relationships between classes
1. [ ] Links and communication between software components
1. [X] Chronological sequence of object interactions
1. [ ] How the users will interact with the software

# Use-Case Diagram

A **use-case diagram** is used to communicate what information about a program?

1. [ ] Structure and relationships between classes
1. [ ] Links and communication between software components
1. [ ] Chronological sequence of object interactions
1. [X] How the users will interact with the software

# Boxes

In a class diagram, a **box** is used to represent what part of a program?

1. [X] A class, struct, or enum
1. [ ] A user
1. [ ] An association 
1. [ ] A message

# Stereotype

A **stereotype** in UML is used to convey what information on a diagram?

1. [X] Language-specific information
1. [ ] Associations
1. [ ] Inheritance
1. [ ] Users

# Typed Element

A **typed element** in UML is used to represent what information?

1. [X] A field or parameter
1. [ ] A method
1. [ ] An interface
1. [ ] A user

# Public

In a UML diagram, what symbol is used to indicate **public** visibility?

1. [X] `+`
1. [ ] `-`
1. [ ] `#`
1. [ ] `*`

# Private

In a UML diagram, what symbol is used to indicate **private** visibility?

1. [ ] `+`
1. [X] `-`
1. [ ] `#`
1. [ ] `*`

# Protected

In a UML diagram, what symbol is used to indicate **protected** visibility?

1. [ ] `+`
1. [ ] `-`
1. [X] `#`
1. [ ] `*`

# Constraint

A **constraint** in a UML diagram describes what?

1. [X] A restriction placed on the value of an element
1. [ ] A restriction on the instances of a class that can be created
1. [ ] The number of instances attached to an association
1. [ ] The size of the overall component

# Methods

In a UML class diagram, which compartment of a box representing a class contains the operations or **methods** of that class?

1. [X] The bottom compartment
1. [ ] The top compartment
1. [ ] The middle compartment
1. [ ] The rightmost compartment

# Languages

True or false: developers creating the same program in different programming languages would create identical UML diagrams to represent their program?

1. [X] False
2. [ ] True

# Attributes

In a UML class diagram, **attributes** are indicated using which UML element?

1. [X] Typed element
1. [ ] Classed element
1. [ ] Box element
1. [ ] Association element

# Accessor Methods

Consider the following typed element:

`+ age: int <<get,set>>`

The **accessor methods** indicated by the `<<get,set>>` portion are represented using what feature of UML?

1. [X] Stereotype
1. [ ] Association
1. [ ] Sequence Diagram
1. [ ] Generic

# Operations

Consider the following UML **operation**:

`+ volume(r: int, h: int, cone: boolean): float`

What is the **return type** of that operation:

1. [X] `float`
1. [ ] `int`
1. [ ] `boolean`
1. [ ] `volume`

# Static

Which text format is used to indicate a class or method is **static** in a UML diagram?

1. [X] Underline
1. [ ] Italics
1. [ ] Bold
1. [ ] Strikethrough

# Abstract

Which text format is used to indicate a class or method is **abstract** in a UML diagram?

1. [ ] Underline
1. [X] Italics
1. [ ] Bold
1. [ ] Strikethrough

# Associations

An **association** between two classes in a UML diagram is represented by which graphical element?

1. [X] Line
1. [ ] Triangle
1. [ ] Box
1. [ ] Circle

# Realization

The **realization** association is also known as what association type?

1. [X] Weak is-a
1. [ ] Strong is-a
1. [ ] Weak has-a
1. [ ] Strong has-a

# Generalization

The **generalization** association is also known as what association type?

1. [ ] Weak is-a
1. [X] Strong is-a
1. [ ] Weak has-a
1. [ ] Strong has-a

# Aggregation

The **aggregation** association is also known as what association type?

1. [ ] Weak is-a
1. [ ] Strong is-a
1. [X] Weak has-a
1. [ ] Strong has-a

# Composition

The **composition** association is also known as what association type?

1. [ ] Weak is-a
1. [ ] Strong is-a
1. [ ] Weak has-a
1. [X] Strong has-a

# Realization Arrow

The **realization** association is represented by which arrow?

1. [X] ![Dashed Line with Open Arrow](/cc410/images/5/arrow1.svg)
1. [ ] ![Solid Line with Open Arrow](/cc410/images/5/arrow2.svg)
1. [ ] ![Solid Line with Open Diamond](/cc410/images/5/arrow3.svg)
1. [ ] ![Solid Line with Solid Diamond](/cc410/images/5/arrow4.svg)

# Generalization Arrow

The **generalization** association is represented by which arrow?

1. [ ] ![Dashed Line with Open Arrow](/cc410/images/5/arrow1.svg)
1. [X] ![Solid Line with Open Arrow](/cc410/images/5/arrow2.svg)
1. [ ] ![Solid Line with Open Diamond](/cc410/images/5/arrow3.svg)
1. [ ] ![Solid Line with Solid Diamond](/cc410/images/5/arrow4.svg)

# Aggregation Arrow

The **aggregation** association is represented by which arrow?

1. [ ] ![Dashed Line with Open Arrow](/cc410/images/5/arrow1.svg)
1. [ ] ![Solid Line with Open Arrow](/cc410/images/5/arrow2.svg)
1. [X] ![Solid Line with Open Diamond](/cc410/images/5/arrow3.svg)
1. [ ] ![Solid Line with Solid Diamond](/cc410/images/5/arrow4.svg)

# Composition Arrow

The **composition** association is represented by which arrow?

1. [ ] ![Dashed Line with Open Arrow](/cc410/images/5/arrow1.svg)
1. [ ] ![Solid Line with Open Arrow](/cc410/images/5/arrow2.svg)
1. [ ] ![Solid Line with Open Diamond](/cc410/images/5/arrow3.svg)
1. [X] ![Solid Line with Solid Diamond](/cc410/images/5/arrow4.svg)

# Multiplicity

The **multiplicity** of an association in UML denotes what information?

1. [X] The number of objects involved
1. [ ] The size of each class
1. [ ] The code complexity of the package
1. [ ] The type of the association

{{< /quizdown >}}