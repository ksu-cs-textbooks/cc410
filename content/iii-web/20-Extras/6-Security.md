---
title: "Security"
weight: 30
pre: "6. "
---
Another major concept to be aware of as a programmer is security. Computer systems today store large amounts of sensitive data, and hackers are always trying to access data and resources they should not have access to. Many times, their ability to access that data is due to a mistake or oversight on the part of a programmer, sometimes made months or even years prior. It could even have been due to some completely new situation that wasn't at all a concern when the program was originally written.

Therefore, programmers should also have a basic understanding of some of the concerns related to computer security and how they can do their best to avoid them.

## Defensive Programming

A major area of study is [Defensive Programming](https://en.wikipedia.org/wiki/Defensive_programming). In effect, defensive programming involves writing programs that will behave in expected ways, even if it receives unexpected or malicious inputs from the user. By learning to write programs in a defensive way, developers can limit the number of vulnerabilities a program has, while easily detecting or preventing malicious input from actually causing a problem.

### Secure Coding

In some programming languages, such as C and C++, the memory for storing data is handled directly by the user, and misuse of this can lead to all sorts of vulnerabilities in the code. We won't cover those here, but if you do decide to learn to program in those languages, it is definitely recommended to also build a strong understanding of how to properly manage memory and avoid these problems. This is known as [secure coding](https://en.wikipedia.org/wiki/Secure_coding)

Thankfully, both Java and Python generally handle memory for us, and are much less susceptible to these issues. That doesn't mean that they are immune, and there are situations where a developer can inadvertently expose data, but generally it is difficult to do so.

### Handling Errors

As we already learned throughout this course, we can write code to carefully handle errors as they arise. For example, if the input to this function should be a string that must be at least 1 character and no longer than 10 characters, we could do something like this in our code:

###### Java

```java
public void getString(String input) {
    if (input == null) {
        throw new NullPointerException();
    }
    if (input.length < 1 || input.length > 10) {
        throw new IllegalArgumentException();
    }
    // more code here
}
```

###### Python

```python
def get_string(self, input: str) -> None:
    if input is None or not isinstance(input, str):
        raise TypeError()
    if len(input) < 1 or len(input) > 10:
        raise ValueError()
    # more code here
```

In both of these examples, we carefully check the `input` variable to make sure that it is properly instantiated and that it meets the criteria we expect, before ever actually using it in our code. We are raising exceptions here, but we could also include some logging code to track these errors. In addition, we should write unit tests that test each of these checks and make sure they are working properly, and these tests will help us make sure we don't accidentally remove this code in a later version.

### Fail Safe

Another important concept in security is writing programs and designing systems that will fail in a safe manner. This can be especially important for software that controls parts of our physical environment, such as medical device software.

For example, if we are writing software that is used to lock a safe, what should happen when the software fails to recognize the input? Should it allow the door to be opened? In this case, probably not, since we want the items in the safe to be protected even if the software fails.

On the other hand, if the software is used to lock the doors on a car, it should probably be programmed to unlock the doors in certain situations, such as when an accident occurs. In that case, it could be more important to allow emergency responders to open the door than protecting the occupants of the car. 

There are many more techniques and concepts related to security and defensive programming. See the resources listed below for more information.

### References

* [Defensive Programming](https://en.wikipedia.org/wiki/Defensive_programming) on Wikipedia
* [Secure Coding](https://en.wikipedia.org/wiki/Secure_coding) on Wikipedia
* [Top 10 Secure Coding Practices](https://wiki.sei.cmu.edu/confluence/display/seccode/Top+10+Secure+Coding+Practices) from the Software Engineering Institute
* [Defensive Coding Guide](http://redhat-crypto.gitlab.io/defensive-coding-guide/) from Fedora (Covers Many Languages!)
