---
title: "Access Modifiers"
weight: 45
pre: "9. "
---

{{% youtube a1oUEgvW09Y %}}

[Video Materials}({{<relref "./video">}})

{{% notice note note-0 "Access Modifiers in Python" %}}

Most of the content below will apply to the Java language only. Python does not directly support information hiding through access modifiers, but simulates it by allowing developers to prefix variables with underscores to indicate that they are "protected" and should be left alone. Likewise, prefixing a Python variable or method name with two underscores will make it appear private to the class, but a developer can simply add the class name to the variable or method name in order to access it. So, in places below where we state that an external class "cannot" access a private attribute, keep in mind that in Python it is always possible and "should not" is a better term to use. 

Thankfully, the concepts are mostly the same, so this is good information for both Java and Python developers to understand.

{{% / notice %}}

Now let's return to the concept of [information hiding](https://en.wikipedia.org/wiki/Information_hiding), and how it applies in object-oriented languages.

Unanticipated changes in state are a major source of errors in programs. Again, think back to the EPIC source code we looked at earlier. It may have seemed unusual now, but it used a common pattern from the early days of programming, where _all_ the variables the program used were declared in one spot, and were _global_ in scope (i.e. any part of the program could reassign any of those variables).

If we consider the program as a state machine, that means that any part of the program code could change any part of the program's state.  Provided those changes were intended, everything works fine. But if the _wrong_ part of the state was changed, problems would ensue.

For example, if we were to make a typo in the part of the program dealing with water run-off in a field, which ends up assigning a new value to a variable that was supposed to be used for crop growth, we've just introduced a very subtle and difficult to find error.  When the crop growth modeling functionality fails to work properly, we'll probably spend serious time and effort looking for a problem in the crop growth portion of the code, but the problem doesn't lie in that code at all!

Java, along with many other object-oriented languages, use [access modifiers](https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html) to implement data hiding. Consider a class representing a student:

{{< tabs >}}

{{% tab name="Java" %}}

```java
public class Student{
    private String first;
    private String last;
    private int wid;
    
    public Student(String first, String last, int wid){
        this.first = first;
        this.last = last;
        this.wid = wid;
    }
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
class Student:
    
    def __init__(self, first: str, last: str, wid: int) -> None:
        self.__first = first
        self.__last = last
        self.__wid = wid
```

{{% /tab %}}

{{< /tabs >}}

By using the access modifier `private` in Java, or prefixing the attributes with two underscores in Python, we have indicated that our fields `first`, `last`, and `wid` cannot be accessed (seen or assigned) outside of this code.  For example, if we were to create a specific student:

{{< tabs >}}

{{% tab name="Java" %}}


```java
Student willie = new Student("Willie", "Wildcat", 888888888);
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
willie: Student = Student("Willie", "Wildcat", 888888888)
```

{{% /tab %}}

{{< /tabs >}}

We would not be able to change that student's name. The statement `willie.first = "Bob"` would fail, because the field `first` is private. In fact, we cannot even see his name, so trying to print that value would also fail.  

If we want to allow a field or method to be accessible _outside_ of the object, we must declare it `public` in Java, or remove the underscores in Python.  While we _can_ declare fields public, this violates the core principles of encapsulation, as any outside code can modify our object's state in uncontrolled ways. This is definitely not what we want.

Instead, in a true object-oriented approach we would write public  **_accessor methods_**, a.k.a. **getters** and **setters**.  These are methods that allow us to see and change field values _in a controlled way_.  Adding accessors to our Student class might look like:

{{< tabs >}}

{{% tab name="Java" %}}

```java
public class Student{
    private String first;
    private String last;
    private int wid;
    
    public Student(String first, String last, int wid){
        this.first = first;
        this.last = last;
        this.wid = wid;
    }
    
    public String getFirst(){
        return this.first;
    }
    
    public void setFirst(String value){
        if(value.length() > 0){
            this.first = value;
        }
    }
    
    public String getLast(){
        return this.last;
    }
    
    public void setLast(String value){
        if(value.length() > 0){
            this.last = value;
        }
    }
    
    public int getWid(){
        return this.wid;
    }
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
class Student:
    
    def __init__(self, first: str, last: str, wid: int) -> None:
        self.__first = first
        self.__last = last
        self.__wid = wid
        
    @property
    def first(self) -> str:
        return self.__first
    @first.setter
    def first(self, value: str) -> None:
        if len(value) > 0:
            self.__first = value
    
    @property
    def last(self) -> str:
        return self.__last
    @last.setter
    def last(self, value: str) -> None:
        if len(value) > 0:
            self.__last = value
            
    @property
    def wid(self) -> int:
        return self.__wid
```

{{% /tab %}}

{{< /tabs >}}

Notice how the `setFirst()` and `setLast()` setters in Java, and the `first()` and `last()` setters in Python, check that the provided name has at least one character?  We can use setters to make sure that we never allow the object state to be set to something that makes no sense.

Also, notice that the `wid` field only has a getter. This effectively means once a student's wid is set by the constructor, it cannot be changed (it's read only).  This allows us to share data without allowing it to be changed outside of the class.

{{% notice info info-1 "Getters and Setters vs. Properties" %}}

Notice that Java uses methods called `getFirst` and `setFirst` as getters and setters, while Python uses the `@property` decorator and methods that share the same name. These **properties** in Python simplify the use of getters and setters in code. 

For example, in Java, if we want to use a getter or setter, we must call them by the function name:

```java
willie.setFirst("William");
System.out.println(willie.getFirst());
```

Through the use of properties in Python, we can refer to the field directly by name, as if it were a public field, and our getter or setter will be called automatically:

```python
willie.first = "William"
print(willie.first)
```

Unfortunately, Java does not support the use of properties at this time.

{{% / notice %}}
