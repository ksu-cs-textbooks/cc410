---
title: "Python Serialization"
weight: 30
pre: "6. "
---
There are many different methods for serializing data in Python. We'll quickly look at three of them. 

## XML 

Python includes the [ElementTree](https://docs.python.org/3/library/xml.etree.elementtree.html) library for processing XML. Unfortunately, due to the way that Python handles objects, we have to write some of the processing ourselves. There are some external libraries that will automatically explore Python objects and build the XML based on its attributes. 

To write an XML file in Python, we can use code similar to this:

```python
import xml.etree.ElementTree as ET


person = Person("Willie Wildcat", 42, Pet("Reggie", 4, "Shorkie"))
print("Saving person:")
print(person)

person_elem = ET.Element("person")
ET.SubElement(person_elem, "name").text = person.name
ET.SubElement(person_elem, "age").text = str(person.age)
pet_elem = ET.SubElement(person_elem, "pet")
ET.SubElement(pet_elem, "name").text = person.pet.name
ET.SubElement(pet_elem, "age").text = str(person.pet.age)
ET.SubElement(pet_elem, "breed").text = person.pet.breed

with open("person.xml", "w") as file:
    file.write(ET.tostring(person_elem, encoding="unicode"))

```

To construct an XML document, we simply must construct each element and set the parent element, tag, and data of each element, as shown in the example above.

```python
import xml.etree.ElementTree as ET


xml_tree = ET.parse("person.xml")
person_elem = xml_tree.getroot()

for child in person_elem:
    if child.tag == "name":
        name = child.text
    if child.tag == "age":
        age = child.text
    if child.tag == "pet":
        for subchild in child:
            if subchild.tag == "name":
                pet_name = subchild.text
            if subchild.tag == "age":
                pet_age = subchild.text
            if subchild.tag == "breed":
                pet_breed =subchild.text

person = Person(name, age, Pet(pet_name, pet_age, pet_breed))

print("Loading person:")
print(person)
```

Then, to parse that data, we can simply iterate through the tree structure and find each tag, loading the text data into a variable and using those variables to reconstruct our objects.

For more information on using UML, refer to these resources. The full source code can be found on [GitHub](https://github.com/K-State-Computational-Core/serialization-examples-python/tree/main/xml):

* [ElementTree](https://docs.python.org/3/library/xml.etree.elementtree.html) in Python Documentation

## JSON

To handle JSON data in Python, 

Then, the process for saving and loading JSON data is very similar to working with XML:

```python
import json


person = Person("Willie Wildcat", 42, Pet("Reggie", 4, "Shorkie"))
print("Saving person:")
print(person)

person_dict = dict()
person_dict['name'] = person.name
person_dict['age'] = person.age
person_dict['pet'] = dict()
person_dict['pet']['name'] = person.pet.name
person_dict['pet']['age'] = person.pet.age
person_dict['pet']['breed'] = person.pet.breed

with open("person.json", "w") as file:
    json.dump(person_dict, file)

```

For JSON, it is easiest to construct a dictionary containing the structure and data to be serialized. This could easily be done as a method within the class itself, but this example shows it outside the class just to demonstrate how it works.

To read the serialized data, we can do the reverse:

```python
import json


with open("person.json") as file:
    person_dict = json.load(file)

person = Person(
    person_dict['name'],
    person_dict['age'],
    Pet(
        person_dict['pet']['name'],
        person_dict['pet']['age'],
        person_dict['pet']['breed']))

print("Loading person:")
print(person)
```

For more information on using JSON in Python, refer to these resources. The full source code can be found on [GitHub](https://github.com/K-State-Computational-Core/serialization-examples-python/tree/main/json):

* [JSON Library](https://docs.python.org/3/library/json.html) from Python Documentation

## Binary using Pickle

Python also includes a built-in mechanism for serialization. All that is required is the [Pickle](https://docs.python.org/3/library/pickle.html) library. 

```python
person = Person("Willie Wildcat", 42, Pet("Reggie", 4, "Shorkie"))
print("Saving person:")
print(person)

with open("person.p", "wb") as file:
    pickle.dump(person, file)

```

```python
with open("person.p", "rb") as file:
    person = pickle.load(file)

print("Loading person:")
print(person)

```

All we have to do is open the file in a binary format by adding `b` to the `open` command.

For more information on Java serialization, refer to these resources. The full source code can be found on [GitHub](https://github.com/K-State-Computational-Core/serialization-examples-python/tree/main/binary):

* [Pickle](https://docs.python.org/3/library/pickle.html) from Python Documentation
* [Using Pickle](https://wiki.python.org/moin/UsingPickle) from Python Wiki
