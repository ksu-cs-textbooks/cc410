---
title: "Text Formats"
weight: 15
pre: "3. "
---
{{% youtube P1wM8NCV-ng %}}

So, now that we understand state, let's talk about how we can serialize it in a way that is easy to parse and understand. There are really two major options we can choose from: a **textual** representation of the data, and a **binary** representation. Let's look at text formats first.

## Text Data Formats

There are many different ways that we can serialize data into a textual format. In fact, we've already covered how to read data from and write data to text files many times throughout this curriculum, and it is probably one of first things most programmers learn how to do.

At its core, the concept of serialization to a text file is pretty much the same as writing any data to a text file. We simply must write all the data stored in the program to a text file in an organized way. Then, when we need to load that file back into our program's state, we can simply read and parse the data, storing it in objects and variables as needed.

## Example

So, let's look at a simple example and explore the various ways that we could store this data in a textual format. Consider a `Person` object that has a `name` and `age` attribute. In addition, that object stores an instance of `Pet`, which also has a `name`, a `breed` and an `age` attribute. 

![State Diagram](../../images/19/state.svg)

With that structure in mind, there are several different formats we could use to store the data. 

### Custom Format

For many novice programmers, the first choice might be to simply create a custom text format to store the data. Here is one possible approach:

```tex
Person
Name = Willie Wildcat
Age = 42
Pet
Name = Reggie
Age = 4
Breed = Shorkie
```

This format definitely stores all of the data in the program's state, and it looks like it can easily be read and parsed back into the program without too much work. However, such a custom text format has several disadvantages:

1) The code to create this text file and read it back into the program must be custom written for each type of object.
2) The format doesn't store any hierarchical structure - how do we know which pet belongs to which person?
3) What if a person can have multiple pets, or their name includes a newline character? 

Of course, all of these concerns can be addressed by adding either additional rules to the structure or additional complexity to the code for reading and writing these files. However, let's look at some other widely used formats that already address some of these concerns and see how they compare. Many of them also already have pre-written libraries we can use in our code as well.

### XML

The [Extensible Markup Language](https://en.wikipedia.org/wiki/XML), or XML, is a great choice for data serialization. XML uses a format very similar to HTML, and handles all sorts of data structures and formats very easily. Here's an example of the same state translated into an XML document:

```xml
<state>
    <person>
        <name>Willie Wildcat</name>
        <age>42</age>
        <pet>
            <name>Reggie</name>
            <age>4</age>
            <breed>Shorkie</breed>
        </pet>
    </person>
</state>
```

As we can see, each object and attribute becomes its own tag in XML. We can even place the `Pet` object directly inside of the `Person` object, showing the hierarchical structure of the data. 

XML also supports the use of a [document type definition](https://en.wikipedia.org/wiki/Document_type_definition), or DTD, which provide rules about the structure of the XML document itself. So, using XML along with a DTD will make sure that the document is structured exactly like it should be, and it will be very easy to parse and understand. 

In fact, most programming languages include libraries to easily create and parse XML documents, making them a great choice for data serialization. XML is also defined as a standard by the World Wide Web Consortium, or W3C, making it widely used on the internet. Many websites make use of [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)), short for asynchronous JavaScript and XML, to send and receive data between a web application and a web server. 

### JSON

Another option that is very popular today is [JavaScript Object Notation](https://en.wikipedia.org/wiki/JSON), or JSON. JSON originally started as a way to easily represent the state of objects in the JavaScript programming language, but it has since been adapted to a variety of different uses. Similar to XML, JSON is widely used on the internet today to share data between web applications and web servers, most notably as part of RESTful APIs. 

A JSON representation of the state shown earlier is shown below:

```json
{
    "Person": {
        "Name": "Willie Wildcat",
        "Age": 42,
        "Pet": {
            "Name": "Reggie",
            "Age": 4,
            "Breed": "Shorkie"
        }
    }
}
```

JSON and XML share many structural similarities, and in many cases it is very straightforward to convert data between XML and JSON representations. However, JSON tends to require less storage space than similar XML data, making it a good choice if storage space is limited or fast data transfer is required. Finally, JSON can be natively parsed by many programming languages such as JavaScript and Python, and libraries exist for most other languages such as Java.

### YAML

Another choice that is commonly used is [YAML](https://en.wikipedia.org/wiki/YAML), a [recursive acronym](https://en.wikipedia.org/wiki/Recursive_acronym) for "YAML Ain't Markup Language." YAML is very similar to JSON in many ways, and in fact JSON files can be considered valid YAML files themselves.

Here is a YAML representation of the same state:

```yaml
Person:
  Name: Willie Wildcat
  Age: 42
  Pet:
      Name: Reggie
      Age: 4
      Breed: Shorkie
```

YAML uses indentation to denote the hierarchical structure of the document, very similar to Python code. As we can see, the structure of a YAML document is very similar to the custom text format we saw earlier. 

However, while this YAML document seems very simple, the YAML specification includes many features that are omitted in JSON, such as the ability to include comments in the data. Unfortunately, YAML also suffers from many of the same problems as Python code, such as the difficulty of keeping track of the indentation when manually editing a file, and the fact that truncated files may be interpreted as complete since there are no termination markers. 


