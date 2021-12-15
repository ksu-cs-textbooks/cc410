---
title: "GUI Basics"
pre: "4. "
weight: 50
date: 2021-02-09T00:53:26-05:00
---

This page lists the milestone requirements for **Milestone 4** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Hero Pizza_, celebrating the heroes from cartoons, comic books, movies, and more. 

The fourth milestone involves creating the various GUI windows and panels required for this project. The next milestone will involve adding functionality to these GUI elements beyond the ability to load different panels into the main window area.

## General Requirements

{{% expand "All projects must follow the professional coding standards listed here (click to expand):" %}}

{{% include-local "./_includes/a-requirements.md" %}}

{{% /expand %}}

## Assignment Requirements

This milestone should include the following features:

* A `heropizza.Main` class that properly loads and displays the program's GUI.
* A `heropizza.gui.MainWindow` class that represents the main GUI window.
  * It should contain two panels - a **main panel** and a **sidebar panel**.
  * It should also contain **two methods**: one to load a particular panel into the main panel, and another to load the order screen into the main panel.
* A `heropizza.gui.OrderPanel` class to represent the main order screen panel.
  * It should contain **three panels of buttons**, one each for pizzas, sides, and desserts. They may be automatically generated from the menu.
  * Each pizza will be listed **once**, but each side and drink will have **three buttons** - one for each size.
  * When clicked, those buttons should call a method to load the appropriate panel in to the main panel. 
* A `heropizza.gui.SidebarPanel` class to represent the sidebar panel.
  * It should contain labels for **order number, subtotal, tax, and total**. 
  * It should contain an **Edit** button that does nothing when clicked.
  * It should also include a **list box** as a placeholder that can be used to keep track of the order. The list box should expand to **fill all remaining vertical space** in the window.
* A panel class in the `heropizza.gui.pizzas` package for each pizza.
  * It should include appropriate controls for modifying the **ingredients, crust, and toppings**.
  * **When given an instance of the item** as a parameter to the constructor, the values of the controls should be **set to match the values** in the instance.
  * It should include a **Save** button that, when clicked, will replace the main panel with the order screen. We will handle actually saving the item in a future milestone.
  * _You may include a parent `PizzaPanel` class to reduce the amount of duplicate code._
* A **SINGLE** panel class `SidePanel` in the `heropizza.gui.sides` package.
  * It should include appropriate controls for modifying the **size** of the item.
  * **When given an instance of the item** as a parameter to the constructor, the values of the controls should be **set to match the values** in the instance.
  * It should include a **Save** button that, when clicked, will replace the main panel with the order screen. We will handle actually saving the item in a future milestone.
  * _Since each side only has a single option, this panel can be generalized to work with the parent `Side` class. However, when buttons on the OrderPanel are clicked, you'll need to make sure an instance of the correct item is generated._
* A panel class in the `heropizza.gui.drinks` package for each drink item.
  * It should include appropriate controls for modifying the **ingredients and size**.
  * **When given an instance of the item** as a parameter to the constructor, the values of the controls should be **set to match the values** in the instance.
  * It should include a **Save** button that, when clicked, will replace the main panel with the order screen. We will handle actually saving the item in a future milestone.
  * _You may include a parent `DrinkPanel` class to reduce the amount of duplicate code._
* Classes in the `heropizza.gui` package **do not require** unit tests.
* Classes in the `heropizza.gui` package **do not require** type hints in Python, though you may continue to use them if they are helpful. Any errors from Mypy originating in these classes will be ignored.
* Classes in the `heropizza.gui` package **do require** all appropriate documentation comments, and must be free of style errors.
* **Update the UML Diagram Contained in this project to match the updated structure of the project.**

You are welcome to add additional methods to the existing content in the `heropizza.data` package. If so, make sure you include appropriate type checking and unit tests.

See below for a few sketches of what your GUI might look like.

{{% notice note %}}

You are encouraged to use the code from Example 6 as a basis for this GUI, or you may create a different design. There are no set requirements for the design other than what is listed above, and the overall focus in this milestone is on simply getting the content on the screen and the ability to move between the various panels. You are welcome to spend additional time on the design if desired, but focus on getting the the content on the screen before doing any design work.

{{% /notice %}}
  
## Time Requirements

Completing this project is estimated to require 3-8 hours.

{{% notice tip %}}

_A rough estimate for this milestone would be around 1500 lines of new code. It could vary widely based on how you choose to implement the various portions of the GUI. I was able to reuse many portions of the example project and expand on them to build this milestone. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* `Main` class - 2%
* `MainWindow` class - 4%
* `SidebarPanel` class - 4%
* `OrderPanel` class - 20%
* Pizza Panel classes - 40%
* `SidePanel` class - 5%
* Drink Panel classes - 15%
* Updated UML diagram - 10%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.

---
---
---

## GUI Sketches

Below are some GUI sketches to help you visualize one possible GUI for a previous version of this project. You do not have to match this design at all, but this is at least a good starting point that you can reach based on what you learned in Example 6. 

{{% notice note %}}

_I chose to increase the default size of my GUI to 1024x740 pixels, as that made the buttons fit better into the window. - Russ_
 
{{% /notice %}}

##### Main Window

![Main Window](/cc410/images/m4/410_m6_gui1.svg)

##### Pizza Panel

![Main Window](/cc410/images/m4/410_m6_gui2.svg)

##### Side Panel

![Main Window](/cc410/images/m4/410_m6_gui4.svg)

##### Drink Panel

![Main Window](/cc410/images/m4/410_m6_gui3.svg)

## Helpful Hints & Code

Here are a couple of helpful pieces of code that you may wish to use in your project. 

##### Java

In many cases, I found it easiest to create private or protected methods that will construct my `GridBagConstraints` objects, either within the class I was working in or in a parent class in the case of pizza and drink panels. Here's an example:

```java
/**
  * Construct a GridBagConstraints object.
  *
  * @param y the y coordinate of the object
  * @param start set anchor to LINE_START
  * @return the constructed GridBagConstraints object
  */
protected GridBagConstraints makeGbc(int y, boolean start) {
    GridBagConstraints gbc = new GridBagConstraints();
    gbc.gridx = 0;
    gbc.gridy = y;
    if (start) {
        gbc.anchor = GridBagConstraints.LINE_START;
    }
    gbc.insets = new Insets(2, 2, 2, 2);
    return gbc;
}
```

Then, when I want to place something in my layout using a `GridBagConstraints` object build from this method, I can use this:

```java
this.add(check, this.makeGbc(i++, true));
```

The biggest benefit to this approach is that I can easily adjust **all** of the buttons by changing this one method. This is a great example of the "Don't Repeat Yourself" or [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) principle.

##### Python

In many cases, I found it helpful to create a dictionary of settings that I'd like use with the `grid()` method, and then pass that entire dictionary as keyword arguments to the method. I usually did this either in a helper method within the class itself, or in a parent class in the case of pizza and drink panels. Here's an example:

```python
def _grid_dict(self, row: int, sticky: str) -> Mapping[str, Any]:
    """Create a dictionary of settings.

    Args:
        row: the row for the item
        sticky: the sticky settings
    """
    settings: Dict[str, Union[str, int]] = dict()
    settings["row"] = row
    settings["column"] = 1
    settings["padx"] = 2
    settings["pady"] = 2
    settings["sticky"] = sticky
    return settings
```

Then, when I want to place something in my layout using the `grid()` method with these settings, I can use this:

```python
checkbutton.grid(**self._grid_dict(i, "W"))
```

Notice that I have to place two asterisks `**` before the method. That tells Python to "unpack" the dictionary returned by that method so that it can be read as individual keyword parameters. A deeper explanation is found [here](https://www.geeksforgeeks.org/packing-and-unpacking-arguments-in-python/). 

The biggest benefit to this approach is that I can easily adjust **all** of the buttons by changing this one method. This is a great example of the "Don't Repeat Yourself" or [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) principle.

I also had to tell Mypy to ignore the lambda expressions used in the `OrderPanel` class, as it cannot properly determine the type of the lambda. You can do this by adding a `# type: ignore` comment at the end of the offending line. 

```python
button = Button(master=side_frame, text=str(side),
                command=lambda x=str(side):  # type: ignore
                self.action_performed(x))
```

If anyone is able to figure out exactly how to properly get Mypy to handle this, there are major Bug Bounty points available!
