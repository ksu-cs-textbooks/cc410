---
title: "Spring and Form Data"
weight: 20
pre: "4. "
---
Once we've built a website that can send form data using an HTTP `POST` request to our web application, we need some way to access that information in our controller. Let's look at how we would accomplish this in Spring.

## Spring Path Variables

In a previous example, we saw how we can create a route that includes variables directly in the path itself:

```java
@GetMapping("/greeting/{name}")
public String greetingWithName(@PathVariable String name, Model model) {
    model.addAttribute("name", name);
    return "greeting";
}
```

In this example, we include the annotation `@PathVariable` before one of the parameters in our method. Spring will automatically match the name of that parameter to the name of one of the path variables in the route, and fill in the value when it calls the function.

## Spring Request Parameters

When dealing with data sent in a `POST` request via an HTML form, we can use a similar method to add those variables to our method. In this case, we'll use the `@RequestParam` annotation, which includes some options we can configure as well:

```java
@PostMapping("/advancedsearch")
public String advancedSearchResults(
        @RequestParam(name = "text", required = true, defaultValue = "") String text,
        @RequestParam(name = "checkbox", defaultValue = "false") boolean checkbox,
        @RequestParam(name = "value", required = true, defaultValue = "-1") double value,
        Model model) {
    model.addAttribute("text", text);
    model.addAttribute("checkbox", checkbox);
    model.addAttribute("value", value);
}
```

The example above shows three different types of request parameters: `String` values from text entry fields, `boolean` values from checkboxes, and numerical values from number input fields. Spring will automatically convert the data to the requested type if possible, making it easy to use.

One thing to note is that the value of a checkbox will only be included along with the form if it is checked. If the checkbox is unchecked, that value will not be present in the form data. So, for `boolean` values, we don't want to list them as required but should always include a default value of `"false"` in case they are not included in the form data. 

## Filling In Form Data

Spring also includes some handy methods for filling out form data based on the values in the template model. This is really helpful for times when we want to allow a user to submit a form but immediately redirect the user back to the same page with the form already completed, as well as some additional data. In addition, as we'll see in a later chapter, if we have any form validation issues, we can help the user by making it easy to fix the error without having to restart filling out the form.

```html
<input type="text" name="text" placeholder="Enter text here..." th:value="${text}">
<input type="checkbox" name="checkbox" th:checked="${checkbox}">
<input type="number" name="value" placeholder="Number" step="0.1" min="0" max="10" th:value="${value}">
```

In our HTML templates, we can use the `th:value` attribute in our `input` tags to fill the form input based on the given value. For checkboxes, we can use a special `th:checked` attribute, which will set the `checked` attribute on the checkbox if the value is present in the model and set to `true`.
