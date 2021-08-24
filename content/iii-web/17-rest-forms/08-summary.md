---
title: "Summary"
weight: 40
pre: "8. "
---

In this chapter we looked at how data is handled in web applications.  We saw how forms can be used to submit data to our server, and examined several common encoding strategies.  We also saw how we can retrieve this data in our web application by examining the routes or the form data submitted.  We also explored the concept of RESTful routes.  Finally, we discussed validating submitted values, on both the client and server side of a HTTP request.

You should now be able to handle creating web forms and processing the submitted data.

{{% notice info info-1 "Web APIs" %}}

Not all web applications are built to be viewed in a browser.  Many are built to be used by other programs.  We call these web applications APIs (Application Programming Interfaces).  These also make HTTP or HTTPS requests against our applications, but usually instead of serving HTML, we serve some form of serialized data instead - most commonly XML or JSON.

{{% / notice %}}
