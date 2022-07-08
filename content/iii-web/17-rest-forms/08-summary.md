---
title: "Summary"
weight: 40
pre: "8. "
---

In this chapter we looked at how data is handled in web applications.  We saw how forms can be used to submit data to our server, and examined several common encoding strategies.  We also saw how we can retrieve this data in our web application by examining the routes or the form data submitted.  We also explored the concept of RESTful routes.  Finally, we discussed validating submitted values, on both the client and server side of a HTTP request.

You should now be able to handle creating web forms and processing the submitted data.

{{% notice info "Web APIs" %}}

Not all web applications are built to be viewed in a browser.  Many are built to be used by other programs.  We call these web applications APIs (Application Programming Interfaces).  These also make HTTP or HTTPS requests against our applications, but usually instead of serving HTML, we serve some form of serialized data instead - most commonly XML or JSON.

{{% / notice %}}

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

# Forms

An **HTML form** is used to perform what task on a webpage? 

1. [X] Collect data from a user and send it back to the server
1. [ ] Provide a list of links for the user to click on
1. [ ] Help the user navigate the structure of a website
1. [ ] Send data from the server directly to a user's computer

# Form Elements

Most elements in an **HTML form** use which HTML element type? 

1. [X] `&lt;input>`
1. [ ] `&lt;a>`
1. [ ] `&lt;span>`
1. [ ] `&lt;field>`

# Dropdown Box

Which HTML element is used to create a **drop-down box**, similar to a combo box element on a traditional GUI?

1. [X] `&lt;select>`
1. [ ] `&lt;input>`
1. [ ] `&lt;textarea>`
1. [ ] `&lt;listbox>`

# Informational Text

Which HTML element is used to provide additional information, such as the name or requirements, for an element that collects data in a form?

1. [X] `&lt;label>`
1. [ ] `&lt;text>`
1. [ ] `&lt;info>`
1. [ ] `&lt;radio>`

# Form Data

Data from a form is an encoded set of entries that use which data format?

1. [X] Key/Value Pairs
1. [ ] Arrays
1. [ ] Integers
1. [ ] Strings

# REST

The **REST** method of mapping routes to operations is a shortened form of what name?

1. [X] Representational State Transfer
1. [ ] Resource Extensive Status Technology
1. [ ] Routing Engaged System Tree
1. [ ] Routed Escaped String Transmission

# Routes

Following a RESTful routing strategy, which HTTP action and route would most likely be used to remove an entry in a list of courses with the course ID of 42?

1. [X] `DELETE` `/courses/42`
1. [ ] `POST` `/courses/42`
1. [ ] `GET` `/courses/42`
1. [ ] `PUT` `/courses/42`

# Validation

In an HTML form, the process of **validation** is best described by which statement?

1. [X] Verifying the user submitted values that meet certain criteria
1. [ ] Determining if the form was created by the website itself
1. [ ] Preventing users from deleting data without permission
1. [ ] Controlling which form entries can be edited by the user

{{< /quizdown >}}
