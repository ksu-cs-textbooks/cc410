---
title: "Elements"
weight: 35
pre: "7. "
---

{{% youtube GTkJYwpw4vQ %}}

[Video Materials]({{<relref "./video">}})

Once we've created a window, a panel, and selected our layout manager, we can finally start to add elements to our GUI. This page will list some of the common GUI elements that we can choose, and describe how they can be used best in our applications. Where possible, we'll also link to official documentation and some tutorial resources so we can learn how to use each of these in our programs. Refer to the links for screenshots and examples of how each of these elements can be used in our programs. Examples below are taken from the [TkDocs](https://tkdocs.com/tutorial/index.html) documentation site. 

## Panel

![Frame](/images/9/w_frame.png)[^1]

[^1]: https://tkdocs.com/tutorial/widgets.html

* Java: [JFrame](https://docs.oracle.com/javase/8/docs/api/javax/swing/JFrame.html) ([Tutorial](https://docs.oracle.com/javase/tutorial/uiswing/components/frame.html))
* Python: [Frame](https://tkdocs.com/tutorial/widgets.html#frame) ([Tutorial](https://www.geeksforgeeks.org/python-tkinter-frame-widget/?ref=lbp))

A panel is the container element in the GUI. It usually doesn't appear to have any graphical component, though it can be styled as shown in the screenshot above. Other elements are typically added to a panel, which uses a layout manager to determine how the elements are placed within the panel. 

## Label

![Label](/images/9/w_label.png)[^1]

* Java: [JLabel](https://docs.oracle.com/javase/8/docs/api/javax/swing/JLabel.html) ([Tutorial](https://docs.oracle.com/javase/tutorial/uiswing/components/label.html))
* Python: [Label](https://tkdocs.com/tutorial/widgets.html#label) ([Tutorial](https://www.geeksforgeeks.org/python-tkinter-label/))

A label is simply a piece of text added to the GUI that is not editable by the user. They are typically used to provide information to the user or "label" other controls, such as text boxes.

## Single Line Text Input

![Entry](/images/9/w_entry.png)[^1]

* Java: [JTextField](https://docs.oracle.com/javase/8/docs/api/javax/swing/JTextField.html) ([Tutorial](https://docs.oracle.com/javase/tutorial/uiswing/components/textfield.html))
* Python: [Entry](https://tkdocs.com/tutorial/widgets.html#entry) ([Tutorial](https://www.geeksforgeeks.org/python-tkinter-entry-widget/))

These controls are used for a single line of text input, such as a username or password field. 

## Multiple Line Text Input

![Text](/images/9/w_text.png)[^2]

[^2]: https://tkdocs.com/tutorial/morewidgets.html#text

* Java: [JTextArea](https://docs.oracle.com/javase/8/docs/api/javax/swing/JTextArea.html) ([Tutorial](https://docs.oracle.com/javase/tutorial/uiswing/components/textarea.html))
* Python: [Text](https://tkdocs.com/tutorial/text.html) ([Tutorial](https://www.geeksforgeeks.org/python-tkinter-text-widget/))

These controls handle multiple lines of text input, such as in a word processing program.

## Button

![Button](/images/9/w_button.png)[^1]

* Java [JButton](https://docs.oracle.com/javase/8/docs/api/javax/swing/JButton.html) ([Tutorial](https://docs.oracle.com/javase/tutorial/uiswing/components/button.html))
* Python [Button](https://tkdocs.com/tutorial/widgets.html#button) ([Tutorial](https://www.geeksforgeeks.org/python-creating-a-button-in-tkinter/))

A button is one of the simplest controls. When a user clicks on a button in our GUI, we can then call a function in our code to perform any action required.

## Checkbox

![Checkbutton](/images/9/w_checkbutton.png)[^1]

* Java [JCheckBox](https://docs.oracle.com/javase/8/docs/api/javax/swing/JCheckBox.html) ([Tutorial](https://docs.oracle.com/javase/tutorial/uiswing/components/button.html))
* Python [Checkbutton](https://tkdocs.com/tutorial/widgets.html#checkbutton) ([Tutorial](https://www.geeksforgeeks.org/python-tkinter-checkbutton-widget/?ref=lbp))

A checkbox, sometimes referred to as a toggle, allows the user to manipulate a boolean value, such as "on" and "off" by clicking it. Checkboxes typically include their own text label, and don't need to have a separate label added to them.

## Radio Button

![Radiobutton](/images/9/w_radiobutton.png)[^1]

* Java [JRadioButton](https://docs.oracle.com/javase/8/docs/api/javax/swing/JRadioButton.html) ([Tutorial](https://docs.oracle.com/javase/tutorial/uiswing/components/button.html))
* Python [Radiobutton](https://tkdocs.com/tutorial/widgets.html#radiobutton) ([Tutorial](https://www.geeksforgeeks.org/radiobutton-in-tkinter-python/?ref=lbp))

A radio button is part of a set of buttons that are similar to checkboxes, but only one option can be selected at a time. The name comes from old radios that had a set of buttons that could be used to recall stations, and pressing one button would cause any other button pressed to pop back out, such that only one button could be pressed at a time. 

## List Box

![Listbox](/images/9/w_listbox.png)[^2]

* Java [JList](https://docs.oracle.com/javase/8/docs/api/javax/swing/JList.html) ([Tutorial](https://docs.oracle.com/javase/tutorial/uiswing/components/list.html))
* Python [ListBox](https://tkdocs.com/tutorial/morewidgets.html#listbox) ([Tutorial](https://www.geeksforgeeks.org/python-tkinter-listbox-widget/?ref=lbp))

A list box displays a list of options to the user, and then the user can choose one or more options from the list, depending on how it is configured.

## Combo Box

![Combobox](/images/9/w_combobox.png)[^1]

* Java [JCombBox](https://docs.oracle.com/javase/8/docs/api/javax/swing/JComboBox.html) ([Tutorial](https://docs.oracle.com/javase/tutorial/uiswing/components/combobox.html))
* Python [Combobox](https://tkdocs.com/tutorial/morewidgets.html#listbox) ([Tutorial](https://www.geeksforgeeks.org/combobox-widget-in-tkinter-python/?ref=lbp))

A combo box, sometimes referred to as a drop-down menu, allows a user to select a single option from a list of options, or possibly enter their own option. It is really a combination of a list box and a text input field in one, hence why it is called a "combo" box. 

