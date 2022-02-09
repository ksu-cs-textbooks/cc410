---
title: "RESTful Routes"
weight: 30
pre: "6. "
---

{{% notice info info-1 "content note" %}}

Much of the content in this page was adapted from Nathan Bean's [CIS 400](https://textbooks.cs.ksu.edu/cis400/3-web-development/03-web-data/05-restful-routes/) course at K-State, with the author's permission. That content is licensed under a [Creative Commons BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.

{{% / notice %}}

{{% youtube VyEBbwUi6Co %}}

[Video Materials}({{<relref "./video">}})

Many web applications deal with some kind of _resource_, i.e. people, widgets, records.  Much like in object-orientation we have organized the program around objects, many web applications are organized around resources.  And as we have specialized ways to construct, access, and destroy objects, web applications need to create, read, update, and destroy resource records (we call these CRUD operations).

In his 2000 PhD. dissertation, Roy Fielding defined [Representational State Transfer (REST](https://en.wikipedia.org/wiki/Representational_state_transfer)), a way of mapping HTTP routes to the CRUD operations for a specific resource.  This practice came to be known as RESTful routing, and has become one common strategy for structuring a web application's routes.  Consider the case where we have an online directory of students.  The students would be our resource, and we would define routes to create, read, update and destroy them by a combination of HTTP action and route:

<table>
  <tr>
    <th>CRUD Operation</th>
    <th>HTTP Action</th>
    <th>Route</th>
  </tr>
  <tr>
    <td>Create</td>
    <td>POST</td>
    <td>/students</td>
  </tr>
  <tr>
    <td>Read (all)</td>
    <td>GET</td>
    <td>/students</td>
  </tr>
  <tr>
    <td>Read (one)</td>
    <td>GET</td>
    <td>/students/[ID]</td>
  </tr>
  <tr>
    <td>Update</td>
    <td>PUT or POST</td>
    <td>/students/[ID]</td>
  </tr>  
  <tr>
    <td>Destroy</td>
    <td>DELETE</td>
    <td>/students/[ID]</td>
  </tr>
</table>

Here the `[ID]` is a unique identifier for the individual student.  Note too that we have _two_ routes for reading - one for getting a list of _all_ students, and one for getting the details of an individual student.

REST is a remarkably straightforward implementation of very common functionality, no doubt driving its wide adoption.  Many web application frameworks support REST, either explicitly through special code structures or shortcuts, or implicitly through the use of route parameters. 

When we use a RESTful route to create or update new resources, we often want to take an additional step - _validating_ the supplied data.
