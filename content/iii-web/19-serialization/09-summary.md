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

# Preparation

When preparing for a release, what is one reason given for **reviewing and reducing dependencies** of our application?

1. [X] Fewer dependencies are easier to manage and install
1. [ ] Dependencies make running om multiple platforms more difficult
1. [ ] Dependencies can store sensitive information
1. [ ] More dependencies make the application more attractive to potential users

{{< /quizdown >}}