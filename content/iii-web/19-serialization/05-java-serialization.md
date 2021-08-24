---
title: "Java Serialization"
weight: 25
pre: "5. "
---

There are many different methods for serializing data in Java. We'll quickly look at three of them. 

## XML via JAXB

Java includes a special API known as the [Java Architecture for XML Binding](https://www.oracle.com/technical-resources/articles/javase/jaxb.html), or JAXB, for mapping Java objects to XML. 

To use it, we can add a few annotations to our objects:

```java
import javax.xml.bind.annotation.*;

@XmlRootElement
public class Person {

    // other code omitted
    
}
```

In the simplest form, we simply add the `@XmlRootElement` annotation above the class to denote that it can be treated as a root element. If the class contains any lists or other collections, there are a few annotations that are needed for those element as well. The `Pet` class is similar.

With these annotations in place, reading and writing the XML file is very simple:

```java
import java.io.*;
import javax.xml.bind.*;

public class SaveXml {
    
    public static void main(String[] args) throws Exception {
        
        Person person = new Person("Willie Wildcat", 42, new Pet("Reggie", 4, "Shorkie"));
        System.out.println("Saving person:");
        System.out.println(person);
        
        File file = new File("person.xml");
        
        JAXBContext jaxbContext = JAXBContext.newInstance(Person.class);
        Marshaller jaxbMarshaller = jaxbContext.createMarshaller();
        jaxbMarshaller.setProperty(Marshaller.JAXB_FORMATTED_OUTPUT, true);
        jaxbMarshaller.marshal(person, file);
        
    }
}
```

To write an XML file, we create a `JAXBContext` based on the `Person` class, and then create a `Marshaller` that actually handles converting the Java data to XML. We can then simply write it's output to a file.

```java
import java.io.*;
import javax.xml.bind.*;

public class LoadXml {
    
    public static void main(String[] args) throws Exception {
        
        File file = new File("person.xml");
        
        JAXBContext jaxbContext = JAXBContext.newInstance(Person.class);
        Unmarshaller jaxbUnmarshaller = jaxbContext.createUnmarshaller();
        Person person = (Person) jaxbUnmarshaller.unmarshal(file);
        
        System.out.println("Loading person:");
        System.out.println(person);
        
    }
}
```

Reading an XML file is very similar. The only major difference is that we use an `Unmarshaller` in place of the `Marshaller`. 

For more information on using JAXB, refer to these resources. The full source code can be found on [GitHub](https://github.com/K-State-Computational-Core/serialization-examples-java/tree/main/xml):

* [Java Architecture for XML Binding (JAXB)](https://www.oracle.com/technical-resources/articles/javase/jaxb.html) from Oracle
* [Reading and Writing XML in Java](https://stackabuse.com/reading-and-writing-xml-in-java/) from StackAbuse

## JSON via Jackson

To handle JSON data in Java, we can use the [Jackson](https://github.com/FasterXML/jackson) library. It can be installed in Gradle by adding a few items to `build.gradle`:

```groovy
// Required to match Jackson versions in Spring
ext['jackson.version'] = '2.12.2'

dependencies {
    // other sections omitted
    
    implementation 'com.fasterxml.jackson.core:jackson-databind:2.12.2'
}
```

Then, the process for saving and loading JSON data is very similar to working with XML:

```java
import java.io.*;
import com.fasterxml.jackson.databind.ObjectMapper;

public class SaveJson {
    
    public static void main(String[] args) throws Exception {
        
        Person person = new Person("Willie Wildcat", 42, new Pet("Reggie", 4, "Shorkie"));
        System.out.println("Saving person:");
        System.out.println(person);
        
        File file = new File("person.json");
        
        ObjectMapper mapper = new ObjectMapper();
        mapper.writeValue(file, person);
        
    }
}
```

```java
import java.io.*;
import com.fasterxml.jackson.core.type.TypeReference;
import com.fasterxml.jackson.databind.ObjectMapper;

public class LoadJson {
    
    public static void main(String[] args) throws Exception {
        
        File file = new File("person.json");
        
        ObjectMapper mapper = new ObjectMapper();
        Person person = mapper.readValue(file, new TypeReference<Person>(){});       
        
        System.out.println("Loading person:");
        System.out.println(person);
        
    }
}
```

In both cases, we simply create an `ObjectMapper` class from Jackson, and then use it to read and write the JSON data. It's that simple.

For more information on using Jackson, refer to these resources. The full source code can be found on [GitHub](https://github.com/K-State-Computational-Core/serialization-examples-java/tree/main/json):

* [Jackson Project Home](https://github.com/FasterXML/jackson) on GitHub
* [Intro to the Jackson ObjectMapper](https://www.baeldung.com/jackson-object-mapper-tutorial) from Baeldung

## Binary Using Java Serialization

Java also includes a built-in mechanism for serialization. All that is really required is to implement the [`Serializable`](https://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html) interface on any objects to be serialized. 

```java
import java.io.*;

public class Person implements Serializable {

    // other code omitted
    
}
```

The `Pet` class is similarly updated. Once that is done, we can use the built-in `ObjectInputStream` and `ObjectOutputStream` to read and write objects just like we do any other data types in Java.

```java
import java.io.*;

public class SaveBinary {
    
    public static void main(String[] args) throws Exception {
        
        Person person = new Person("Willie Wildcat", 42, new Pet("Reggie", 4, "Shorkie"));
        System.out.println("Saving person:");
        System.out.println(person);
        
        File file = new File("person.ser");
        
        ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream(file));
        out.writeObject(person);
        
    }
}
```

```java
import java.io.*;

public class LoadBinary {
    
    public static void main(String[] args) throws Exception {
        
        File file = new File("person.ser");
        
        ObjectInputStream in = new ObjectInputStream(new FileInputStream(file));
        Person person = (Person) in.readObject();
        
        System.out.println("Loading person:");
        System.out.println(person);
        
    }
}
```

By convention, we use the `.ser` file extension for serialized data from Java. 

For more information on Java serialization, refer to these resources. The full source code can be found on [GitHub](https://github.com/K-State-Computational-Core/serialization-examples-java/tree/main/binary):

* [Java - Serialization](https://www.tutorialspoint.com/java/java_serialization.htm) from TutorialsPoint
* [Serialization in Java](https://www.geeksforgeeks.org/serialization-in-java/) from GeeksforGeeks

