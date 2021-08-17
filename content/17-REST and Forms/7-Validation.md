---
title: "Validation"
weight: 35
pre: "7. "
---
{{% notice note %}}

# Content Note

Much of the content in this page was adapted from Nathan Bean's [CIS 400](https://textbooks.cs.ksu.edu/cis400/3-web-development/03-web-data/06-validation/) course at K-State, with the author's permission. That content is licensed under a [Creative Commons BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.

{{% / notice %}}

Validation refers to the process of making sure the submitted data matches our expectations.  Validation can be done client-side or server-side.  For example, we can use the built-in HTML form validation properties to enforce rules, like a number that must be positive:

```html
<input type="number" min="0" name="Age" required>
```

If a user attempts to submit a form containing this input is submitted, and the value is less than 0, the browser will display an error message instead of submitting.  In addition, the psuedo-css class `:invalid` will be applied to the element.

We can also mark inputs as required using the `required` attribute.  The browser will refuse to submit the form until all required inputs are completed. Inputs with a `required` attribute also receive the `:required` pseudo-class, allowing you to assign specific styles to them.

You can read more about HTML Form validation on [MDN](https://developer.mozilla.org/en-US/docs/Learn/Forms/Form_validation).

Client-side validation is a good idea, because is minimizes invalid requests against our web application.  However, we cannot always depend on it, so we _also_ need to implement server-side validation.  We can write custom logic for doing this, but many web application frameworks also have built-in support for validation.
