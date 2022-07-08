---
title: "HTML Forms"
weight: 10
pre: "2. "
---

{{% notice info "Content Note" %}}

Much of the content in this page was adapted from Nathan Bean's [CIS 400](https://textbooks.cs.ksu.edu/cis400/3-web-development/03-web-data/02-http-forms/) course at K-State, with the author's permission. That content is licensed under a [Creative Commons BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.

{{% / notice %}}

{{% youtube b0SPMKu5o0A %}}

[Video Materials]({{<relref "./video">}})

One of the earliest (and still widely used) mechanisms for transferring data from a browser (client) to the server is a _form_.  The `<form>` is a specific HTML element that contains input fields and buttons the user can interact with.

### The `<input>` Element

Perhaps the most important - and versatile - of these is the [`<input>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input) element.  By setting its `type` attribute, we can represent a wide range of possible inputs, as is demonstrated by this table adapted from a similar one on the [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input):

| Type | Description | Basic Examples | 
| ---- | ----------- | -------------- | 
| [button](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/button) | 	A push button with no default behavior displaying the value of the [value](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#htmlattrdefvaluec) attribute, empty by default. | `<input type="button" name="button" value="Button" />` <br> <input type="button" name="button" value="Button" /> |
| [checkbox](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox) | 	A check box allowing single values to be selected/deselected. | `<input  type="checkbox" name="checkbox" />`<br>`<label for="checkbox" style="display: inline">Checkbox</label>` <br> <input  type="checkbox" name="checkbox" /> <label for="checkbox" style="display: inline">Checkbox</label> | | 
| [color](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/color) | A control for specifying a color; opening a color picker when active in supporting browsers. | `<input type="color" name="color" style="width: 40px; height: 40px;" />` <br> <input type="color" name="color" style="width: 40px; height: 40px;" /> |
| [date](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/date) | A control for entering a date (year, month, and day, with no time). Opens a date picker or numeric wheels for year, month, day when active in supporting browsers. | `<input  type="date" name="date"/>` <br> <input  type="date" name="date"/> |
| [datetime-local](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/datetime-local) | 	A control for entering a date and time, with no time zone. Opens a date picker or numeric wheels for date- and time-components when active in supporting browsers. | `<input  type="datetime-local" name="datetime-local"/>` <br> <input  type="datetime-local" name="datetime-local"/> |
| [email](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/email) | 	A field for editing an email address. Looks like a `text` input, but has validation parameters and relevant keyboard in supporting browsers and devices with dynamic keyboards. | `<input type="email" name="email"/>` <br> <input type="email" name="email"/> |
| [file](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/file) | A control that lets the user select a file. Use the [accept](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#htmlattrdefaccept) attribute to define the types of files that the control can select. | `<input type="file" accept="image/*, text/*" name="file"/>` <br> <input type="file" accept="image/*, text/*" name="file"/> |
| [hidden](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/hidden) | 	A control that is not displayed but whose value is submitted to the server. There is an example in the next column, but it's hidden! | `<input id="hidden_id" name="hidden_id" type="hidden" value="f0e1d2c3b4">` <br> <input id="hidden_id" name="hidden_id" type="hidden" value="f0e1d2c3b4"> &larr; It's here! |
| [image](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/image) | A graphical `submit` button. Displays an image defined by the `src` attribute. The [alt](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#htmlattrdefalt) attribute displays if the image [src](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#htmlattrdefsrc) is missing. | `<input type="image" name="image" style="height: 40px;" src="..." alt="Submit"/>` <br> <input type="image" name="image" style="height: 40px;" src="/images/core-logo-on-purple.svg" alt="Submit"/> |
| [month](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/month) | A control for entering a month and year, with no time zone. | `<input type="month" name="month"/>` <br> <input type="month" name="month"/> | 
| [number](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/number) | A control for entering a number. Displays a spinner and adds default validation when supported. Displays a numeric keypad in some devices with dynamic keypads. | `<input  type="number" name="number"/>` <br> <input  type="number" name="number"/> |
| [password](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/password) | A single-line text field whose value is obscured. Will alert user if site is not secure. | `<input  type="password" name="password"/>` <br> <input  type="password" name="password"/> | 
| [radio](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio) | 	A radio button, allowing a single value to be selected out of multiple choices with the same [name](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#htmlattrdefname) value. | `<input type="radio" name="radio"/>` <br> `<label style="display: inline" for="radio">Radio</label>` <br> <input type="radio" name="radio"/> <label style="display: inline" for="radio">Radio</label> |
| [range](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/range) | 	A control for entering a number whose exact value is not important. Displays as a range widget defaulting to the middle value. Used in conjunction with [min](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#htmlattrdefmin) and [max](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#htmlattrdefmax) to define the range of acceptable values. | `<input type="range" name="range" min="0" max="25"/>` <br> <input type="range" name="range" min="0" max="25"/> |
| [reset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/reset) | 	A button that resets the contents of the form to default values. Not recommended. | `<input  type="reset" name="reset"/>` <br> <input  type="reset" name="reset"/> |
| [search](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/search) | A single-line text field for entering search strings. Line-breaks are automatically removed from the input value. May include a delete icon in supporting browsers that can be used to clear the field. Displays a search icon instead of enter key on some devices with dynamic keypads. | `<input  type="search" name="search"/>` <br> <input  type="search" name="search"/> |
| [submit](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/submit) | A button that submits the form. | `<input type="submit" name="submit"/>` <br> <input type="submit" name="submit" style="border: 1px solid black"/> | 
| [tel](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/tel) | 	A control for entering a telephone number. Displays a telephone keypad in some devices with dynamic keypads. | `<input  type="tel" name="tel"/>` <br> <input  type="tel" name="tel"/> | 
| [text](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/text) | 	The default value. A single-line text field. Line-breaks are automatically removed from the input value. | `<input type="text" name="text"/>` <br> <input type="text" name="text"/> |
| [time](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/time) | A control for entering a time value with no time zone. | `<input  type="time" name="time"/>` <br> <input  type="time" name="time"/> |
| [url](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/url) | 	A field for entering a URL. Looks like a `text` input, but has validation parameters and relevant keyboard in supporting browsers and devices with dynamic keyboards. | `<input type="url" name="url"/>` <br> <input type="url" name="url"/> |
| [week](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/week) | A control for entering a date consisting of a week-year number and a week number with no time zone. | `<input type="week" name="week"/>` <br> <input type="week" name="week"/> |

Regardless of the type, the `<input>` element also has a `name` and `value` property.  The `name` is similar to a variable name, in that it is used to identify the input's value when we serialize the form (more about that later), and the `value` is the value the input currently is (this starts as the value you specify in the HTML, but it changes when the user edits it).

### The `<textarea>` Element

The [`<textarea>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea) element represents a multi-line text input.  Similar to terminal programs, this is represented by columns and rows, the numbers of which are set by the `cols` and `rows` attributes, respectively.  Thus:

```html
<textarea cols=40 rows=5></textarea>
```

Would look like:

<textarea cols=40 rows=5></textarea>

As with inputs, a `<textarea>` has a `name` and `value` attribute.

### The `<select>` Element

The [`<select>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select) element, along with `<option>` and `<optgroup>` make drop-down selection boxes.  The `<select>` takes a name attribute, while each `<option>` provides a different value.  The `<options>` can further be nested in `<optgroup>`s with their own labels.  The `<select>` also has a `multiple` attribute (to allow selecting multiple options), and `size` which determines how many options should be displayed at once (with scrolling if more are available).

For example:

```html
<select id="dino-select">
    <optgroup label="Theropods">
        <option>Tyrannosaurus</option>
        <option>Velociraptor</option>
        <option>Deinonychus</option>
    </optgroup>
    <optgroup label="Sauropods">
        <option>Diplodocus</option>
        <option>Saltasaurus</option>
        <option>Apatosaurus</option>
    </optgroup>
</select>
```

Displays as: 

<select id="dino-select">
    <optgroup label="Theropods">
        <option>Tyrannosaurus</option>
        <option>Velociraptor</option>
        <option>Deinonychus</option>
    </optgroup>
    <optgroup label="Sauropods">
        <option>Diplodocus</option>
        <option>Saltasaurus</option>
        <option>Apatosaurus</option>
    </optgroup>
</select>


### The `<label>` Element

A [`<label>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label) element represents a caption for an element in the form.  It can be tied to a specific input using its `for` attribute, by setting its value to the `id` attribute of the associated input.  This allows screen readers to identify the label as belonging to the input, and also allows browsers to give focus or activate the input element when the label is clicked.

For example, if you create a checkbox with a label:

```html
<fieldset style="display:flex; align-items:center;">
  <input type="checkbox" id="example"/>
  <label for="example">Is Checked</label>
</fieldset>
```

<fieldset style="display:flex; align-items:center;">
  <input type="checkbox" id="example"/>
  <label for="example">Is Checked</label>
</fieldset>

Clicking the label will toggle the checkbox!

### The `<fieldset>` Element

The `<fieldset>` element is used to group related form parts together, which can be captioned with a `<legend>`.  It also has a `for` attribute which can be set to the `id` of a form on the page to associate with, so that the fieldset will be serialized with the form (this is not necessary if the fieldset is inside the form).  Setting the fieldset's `disabled` attribute will also disable all elements inside of it.

For example:

```html
<fieldset>
  <legend>Who is your favorite muppet?</legend>
  <input type="radio" name="muppet" id="kermit">
    <label for="kermit">Kermit</label>
  </input>
  <input type="radio" name="muppet" id="animal">
    <label for="animal">Animal</label>
  </input>
  <input type="radio" name="muppet" id="piggy">
    <label for="piggy">Miss Piggy</label>
  </input>
  <input type="radio" name="muppet" id="gonzo">
    <label for="gonzo">Gonzo</label>
  </input>
</fieldset>
```

Would render:

<style>fieldset>label {display: inline; margin-right: 2rem;} </style>
<fieldset>
  <legend>Who is your favorite muppet?</legend>
  <input type="radio" name="muppet" id="kermit">
    <label for="kermit">Kermit</label>
  </input>
  <input type="radio" name="muppet" id="animal">
    <label for="animal">Animal</label>
  </input>
  <input type="radio" name="muppet" id="piggy">
    <label for="piggy">Miss Piggy</label>
  </input>
  <input type="radio" name="muppet" id="gonzo">
    <label for="gonzo">Gonzo</label>
  </input>
</fieldset>

### The `<form>` Element

Finally, the `<form>` element wraps around all the `<input>`, `<textarea>`, and `<select>` elements, and gathers them along with any contained within associated `<fieldset>`s to submit in a serialized form.  This is done when an `<input type="submit">` is clicked within the form, when the enter key is pressed and the form has focus, or by calling the `submit()` method on the form with JavaScript.

There are a couple of special attributes we should know for the `<form>` element:

* `action` - the URL this form should be submitted to.  Defaults to the URL the form was served from.
* `enctype` - the encoding strategy used, discussed in the next section.  Possible values are:
  * `application/x-www-form-urlencoded` - the default
  * `multipart/form-data` - must be used to submit files 
  * `text/plain` - useful for debugging
* `method` - the HTTP method to submit the form using, most often GET or POST

When the form is submitted, the form is serialized using the `enctype`, and submitted using the HTTP `method` to the URL specified by the `action` attribute.  Let's take a deeper look at this process next.
