---
title: "Flask and Form Data"
weight: 25
pre: "5. "
---

Once we've built a website that can send form data using an HTTP `POST` request to our web application, we need some way to access that information in our controller. Let's look at how we would accomplish this in Flask.

## Flask Path Variables

In a previous example, we saw how we can create a route that includes variables directly in the path itself:

```python
@route('/greeting/<name>/')
def greeting_with_name(self, name):
    """Display greeting with name."""
    return render_template("greeting.html", name=name)
```

In this example, we simply include the path variable `<name` in the route, and a corresponding parameter in our controller function. Flask will automatically match the name of that parameter to the name of one of the path variables in the route, and fill in the value when it calls the function.

## Flask Request Parameters

When dealing with data sent in a `POST` request via an HTML form, Flask uses a slightly different approach. Part of the Flask library is the `requests` object, which can be used to access information about the request sent to the server. Part of that object is a `dict` named `form`, which includes all of the form data. So, we can access the data from an HTML form by accessing the elements in the `form` dictionary:

```python
@route("/advancedsearch/", methods=['POST'])
def advanced_search_results(self):
    """Search results page."""
    # don't use request.form['text'] - raises exceptions!
    text: str = request.form.get('text', None)
    checkbox: bool = bool(request.form.get('checkbox', False))
    try:
        value: float = float(request.form.get('value', "-1"))
    except ValueError:
        value = -1
    return render_template(
        "advanced_search.html",
        text=text,
        checkbox=checkbox,
        value=value)
```

The example above shows three different types of request parameters: `String` values from text entry fields, `boolean` values from checkboxes, and numerical values from number input fields. Since they are all sent as text, we have to use the various methods in Python to convert them to the data type we need.

However, there are a few important things to note in this code. First, instead of directly accessing the elements in the `form` dictionary, as in `request.form['text']`, we are using the `get()` method as described in the [Python documentation](https://docs.python.org/3/library/stdtypes.html#dict.get). This is because directly accessing the elements will raise an exception if they are not present, which we'll have to handle. Instead, we can use the `get` method to access them if they are present. If not, we can provide a second parameter which will be the "default" value used if no value is present. This makes it much easier to handle situations where we can't guarantee that all values would be present in the form.

Likewise, for some numerical values, we may still need to use a `try-except` statement to safely convert them, as shown in the example above. We are using a default value of `-1` in the case that the value is not provided, but also in the `except` clause if the value provided cannot be properly converted to a numerical value. 

Finally, one thing to note is that the value of a checkbox will only be included along with the form if it is checked. If the checkbox is unchecked, that value will not be present in the form data. So, for `boolean` values, we should always include a default value of `"false"` in case they are not included in the form data. 

## Filling In Form Data

Flask also includes some handy methods for filling out form data based on the values in the template model. This is really helpful for times when we want to allow a user to submit a form but immediately redirect the user back to the same page with the form already completed, as well as some additional data. In addition, as we'll see in a later chapter, if we have any form validation issues, we can help the user by making it easy to fix the error without having to restart filling out the form.

```html
<input type="text" name="text" placeholder="Enter text here..." value="{{ text }}}">
<input type="checkbox" name="checkbox" {{ "checked" if checkbox else "" }}>
<input type="number" name="value" placeholder="Number" step="0.1" min="0" max="10" value="{{ value }}">
```

In our HTML templates, we can use the `value` attribute in our `input` tags to fill the form input based on the given value. For checkboxes, we can use a short Python ternary `if` statement, which will set the `checked` attribute on the checkbox if the value is present in the model and set to `true`.
