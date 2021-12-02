---
title: "Summary"
weight: 45
pre: "9. "
---

In this chapter, we learned about how to serialize the state of our applications into a file for storage, and then how to read that state back into memory.

We explored different formats we can use, including JSON, XML, and a binary format. Each of those comes with various pros and cons, so we have to choose wisely.

Then, we saw some examples of how to work with each format in our chosen programming language. In each case, it isn't too difficult to do. 

Finally, we discussed some of the things we might not want to serialize, and the fact that, in practice, we might want to use a database instead of a text file for storing large amounts of data, especially in a web application.

Thankfully, we'll be able to put this skill to use as we wrap up our semester project. 

## Review Quiz

Check your understanding of the new content introduced in this chapter below - this quiz is not graded and you can retake it as many times as you want.

{{< quizdown >}}

---
primaryColor: '#512888'
secondaryColor: '#cccccc'
textColor: black
shuffleQuestions: true
shuffleAnswers: true
locale: en
---

# State

In an object-oriented program, the **state** of a program contains what information?

1. [X] All variables and objects stored in memory
1. [ ] Messages passed between objects
1. [ ] Publicly accessible methods
1. [ ] How the information is encoded in memory

# Serialization

In programming, **serialization** refers to what process?

1. [X] Converting data in memory to long-term storage on disk
1. [ ] Sending messages between web servers
1. [ ] Casting data between data types in memory
1. [ ] Duplicating data to multiple areas

# XML

Which of the following is an example of data stored in the **XML** format?
<br><br>
**Option 1**:
```xml
<student>
  <name>Test Person</name>
  <id>12345</id>
</student>
```
**Option 2**:
```json
{
    "Student": {
        "Name" : " Test Person",
        "id": 12345
    }
}
```
**Option 3**:
```yml
Student:
  Name: Test Person
  id: 12345
```
**Option 4**:
```ini
Student
Name = Test Person
id = 12345
```

1. [X] Option 1
1. [ ] Option 2
1. [ ] Option 3
1. [ ] Option 4

# YAML

Which of the following is an example of data stored in the **YAML** format?
<br><br>
**Option 1**:
```xml
<student>
  <name>Test Person</name>
  <id>12345</id>
</student>
```
**Option 2**:
```json
{
    "Student": {
        "Name" : " Test Person",
        "id": 12345
    }
}
```
**Option 3**:
```yml
Student:
  Name: Test Person
  id: 12345
```
**Option 4**:
```ini
Student
Name = Test Person
id = 12345
```

1. [ ] Option 1
1. [ ] Option 2
1. [X] Option 3
1. [ ] Option 4

# JSON

Which of the following is an example of data stored in the **JSON** format?
<br><br>
**Option 1**:
```xml
<student>
  <name>Test Person</name>
  <id>12345</id>
</student>
```
**Option 2**:
```json
{
    "Student": {
        "Name" : " Test Person",
        "id": 12345
    }
}
```
**Option 3**:
```yml
Student:
  Name: Test Person
  id: 12345
```
**Option 4**:
```ini
Student
Name = Test Person
id = 12345
```

1. [ ] Option 1
1. [X] Option 2
1. [ ] Option 3
1. [ ] Option 4

# Unstructured Test

Which of the following is an example of data that is **NOT** stored in a common text format (JSON, XML, YAML)?
<br><br>
**Option 1**:
```xml
<student>
  <name>Test Person</name>
  <id>12345</id>
</student>
```
**Option 2**:
```json
{
    "Student": {
        "Name" : " Test Person",
        "id": 12345
    }
}
```
**Option 3**:
```yml
Student:
  Name: Test Person
  id: 12345
```
**Option 4**:
```ini
Student
Name = Test Person
id = 12345
```

1. [ ] Option 1
1. [ ] Option 2
1. [ ] Option 3
1. [X] Option 4

# Binary - Pros

Which of the following is **NOT** listed as an **advantage** of storing serialized data in a binary format?

1. [X] Binary files are readable by any programming language
1. [ ] Binary files are smaller
1. [ ] Binary files are more efficient
1. [ ] Binary files are not editable by humans

# Binary - Cons

Which of the following is **NOT** listed as a **disadvantage** of storing serialized data in a binary format?

1. [X] Binary files require special hard drive storage systems
1. [ ] Binary files are only readable by the language that crated them
1. [ ] Binary files cannot be easily read or edited by a 
1. [ ] Binary files are often locked to particular versions of a program

# Excluded Data

According to the textbook, which of the following data items **should be excluded** when serializing data? 

1. [X] Data that is dependent on other data
1. [ ] Data that is very small
1. [ ] Numerical data
1. [ ] Textual data

# Real World Data

At the end of the chapter, we discuss what real-world piece of software that would typically be used to **store serialized data in practice**?

1. [X] Database
1. [ ] Spreadsheet
1. [ ] Word Processor
1. [ ] Log File

{{< /quizdown >}}