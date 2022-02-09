---
title: "Class Diagrams"
pre: "2. "
weight: 20
date: 2020-01-15T00:53:26-05:00
hidden: true
---

{{< youtube fKuJNhMIQUE >}}

#### Resources

* <a href="{{<relref "./slides">}}" target="_blank">Slides</a>

#### Video Script

Let's dive into UML class diagrams a bit. First, we can talk about the basic building block of a Class diagram - the box. Each class in the diagram is represented by a box, and that box has three sections. At the top, we see the name of the class. We may also see a stereotype in the first box if there is something we need to know about the class that is language specific. For example, it could be an enumeration or an interface, and we'd indicate that by adding a stereotype to the first box. The second box contains the attributes of the class. These are typed items, so they will include, at the very least, a name and a type. Most UML diagrams also include the visibility information here, so we would typically see a plus or minus sign at the front of each attribute. Finally, attributes can also include some constraints placed in curly braces at the end of the element. For example, we could place a constraint on an `age` attribute that it must be greater than 0. Finally, at the bottom, we have the operations, or methods, of the class. For these, we typically include the method's signature, which encompasses the method name, parameters and their types, and the return type of the method. We may also include the visibility at the front as well. 

So, let's look at a quick example of a class element in a class diagram. This is the `Square` class that we've seen in several of our examples throughout this course. That class includes one private attribute, the length, which is a floating point value. After that, we've included the stereotype `get, set` which tells us that we should create a getter and a setter accessor method for this attribute, following whatever our language's standard is for those methods. The class also defines one public method, the `areaDifference` method, which accepts one `Circle` object as a parameter, and it returns a floating point value as well. 

So, as we can see, it is very easy to create the classes for our UML class diagrams, either by just looking at the code if it is already written, or ideally by thinking about what the structure of the class should be before we ever start writing it.