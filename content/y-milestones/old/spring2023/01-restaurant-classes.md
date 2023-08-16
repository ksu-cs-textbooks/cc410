---
title: "Restaurant Classes"
pre: "1. "
weight: 20
---

This page lists the milestone requirements for **Milestone 1** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Game Grub_, offering food of all kinds to celebrate our love of games of all kinds. 

This first milestone involves building the classes that represent items on the restaurant's menu. In a traditional [Model-View-Controller](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) software design pattern, these classes would make up the core of the **model**. This content should be mostly review of concepts learned in prior CC courses with the addition of enumerations (enums). It should not be particularly difficult, but it may be repetitive and time consuming. 

Specifically, we'll focus primarily on **data encapsulation** by storing attributes about each menu item in the class. We'll also learn how to combine **state** and **behavior** by modifying the string representation of the object based on the current state, or the combined values stored in the attributes. 

{{% notice note %}}

In future milestones, we'll focus on adding **inheritance** to simplify the code and structure in these classes. We'll also add proper **unit tests** and **documentation** to these classes. For now, our only focus is on building the classes themselves. 

{{% /notice %}}

## General Requirements

{{% notice warning %}}

The first couple of milestones only require a subset of the general requirements introduced in the "Hello Real World" project. Read this section carefully to see what is required for this particular milestone.

{{% /notice %}}

This milestone must follow these professional coding standards:

* **All code must be object-oriented.**
  * All executable code must be within a class
    * Python package files such as `__init__.py` and `__main__.py` are exempt.
  * Classes must be organized into packages based on common usage.
* **This project must include automation for compilation and execution.**
  * Java: Use Gradle with the `application` plugin. The project should compile without errors. You may include a main class in a separate package for testing purposes only.
  * Python: Use tox configured to use Python 3.10 and a requirements file to install libraries. You may include a main class in a separate package for testing purposes only.
* **All code must properly compile or be interpreted.**
  * Java: It must compile using Gradle.
  * Python: It must be interpreted using Python 3.10. Where specified, type hints should be included in the code, and all code should pass a strict Mypy type check.
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).

{{% expand "Unenforced requirements (click to expand):" %}}

The following requirements **ARE NOT** enforced for this milestone, but will be enforced in later milestones that use the same code. We will focus on learning to meet each of these requirements in future modules. However, you are welcome to "plan ahead" by minimizing the number of style errors in your code and adding some basic documentation where desired. 

{{% notice tip "Naming Standards" %}}

You can make things easier on yourself by following proper naming standards for your language of choice, even though we aren't enforcing a style guide for this milestone.

* **Java** - All names are in CamelCase. Classes start with uppercase, like `ClassName`, methods and attributes start with lowercase like `methodName`. See the [Google Style Guide](https://google.github.io/styleguide/javaguide.html#s5-naming).
* **Python** - All names are lowercase with underscores like `method_name`, with the exception of classes, which are named in CamelCase starting with an uppercase letter like `ClassName`. See the [Google Style Guide](https://google.github.io/styleguide/pyguide.html#s3.16-naming).

It is easier to get this correct from the start, then having to refactor your code later. Of course, major refactoring is also a good lesson that guarantees you'll get it right in the future!

{{% /notice %}}

* **(Milestone 3) All code submitted must be free of style errors.** We will be using the [Google Style Guide](https://google.github.io/styleguide/) for each language. 
  * Java: Use Checkstyle 10.6.0+ and the [Google Style Configuration](https://raw.githubusercontent.com/checkstyle/checkstyle/checkstyle-10.6.0/src/main/resources/google_checks.xml). 
    * You may modify the configuration to allow 4 space indentations instead of 2 space indentations.
  * Python: Use Flake8 with the `flake8-docstrings` and `pep8-naming` plugins. Code should conform to PEP 8 style with Google style docstrings. 
* **(Milestone 2) Where specified, code should contain appropriate unit tests that achieve the specified level of code coverage.**
  * Java: Use JUnit 5. You may choose to use Hamcrest for assertions.
  * Python: Use pytest. You may choose to use Hamcrest for assertions.
* **(Milestone 2) Where specified, code should contain appropriate documentation comments following the language's style guide.**
  * Java: Use javadoc to generate documentation.
  * Python: Use pdoc3 to generate documentation.

{{% /expand %}}

## Assignment Requirements

This milestone should include the following features:

* Entree classes - 5
  * Declared in the `gamegrub.data.entrees` package
* Side classes - 3
  * Declared in the `gamegrub.data.sides` package
* Drink classes - 3
  * Declared in the `gamegrub.data.drinks` package
* Enumeration classes - 3
  * Declared in the `gamegrub.data.enums` package

See the [Game Grub Menu](#game-grub-menu) section below for descriptions of what each class should contain.

**Python** - these files should include complete type annotations and achieve a low imprecision percentage in Mypy using strict type checking.

{{% notice tip "Python Type Checking" %}}

_In my testing, the only imprecision in type checking should be the first line of the `__eq__` method since it must accept an imprecise `object` type until the `isinstance()` method call. It will also mark the `@property.setter` annotations, but they don't count toward the imprecision total and can be ignored. The total imprecision should be less than 5% overall, and will probably be less than 2% in most cases. -Russ_

{{% /notice %}}
  
## Time Requirements

Completing this project is estimated to require 3-8 hours.

{{% notice note "Expected Scope" %}}

_In my testing, this milestone requires around 1000-1500 lines of pure code without documentation, or around 2000-2500 lines including documentation comments that will be included as part of milestone 2. Much of the code can be carefully copy-pasted between files with similar attributes. My best suggestion is to do the enumerations first, then pick one of the complex entrees and start there. Once you have the entrees all working, the sides and drinks are pretty easy and use much of the same structure. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* Entree classes - 40%
* Side classes - 20%
* Drink classes - 30%
* Enumeration classes - 10%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.
* Any portion of the project which does not meet the general requirements listed above will have a commensurate amount of points deducted.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

{{% notice note "Code Review" %}}

_As part of the grading of all assignments in this course, I will be doing a deep dive into a few classes in your code. This will include leaving detailed comments on code style and format in GitHub. I will usually choose various classes to review at random, and any issues found in that class will be verified in other classes of the same type. - Russ_

{{% /notice %}}

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.

---
---
---

## Game Grub Menu

_our motto: play fair, eat well_

Each attribute described below should be implemented as a private variable within the class. Most attributes will also include a **getter** method, and sometimes a **setter** method, following this naming scheme (using **Price** as an example): 
  * **Java** - The private `price` attribute would have a `getPrice` getter and `setPrice` setter method.
  * **Python** - The private `__price` attribute would have a getter and setter named `price` implemented as a [Python Property](https://docs.python.org/3/library/functions.html#property). 

---

### Entrees

Each entree should be stored in an appropriately named class in the `gamegrub.data.entrees` package. Each entree should include an attribute for the following data:
  * **Base** - a `Base` value (see below). It should have a **getter** and **setter** method.
  * **Topping** - a Java [HashSet](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/HashSet.html) or a Python [set](https://docs.python.org/3.10/library/stdtypes.html#set) of `Topping` values (see below). 
    * This attribute should have a **getter** method that returns a **shallow copy** of the set to prevent external modification. See [HashSet's Copy Constructor (Java)](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/HashSet.html#%3Cinit%3E(java.util.Collection)) or [set.copy (Python)](https://docs.python.org/3.10/library/stdtypes.html#frozenset.copy). 
    * This attribute should also have methods for **Add Topping** and **Remove Topping** to modify the list of toppings. 

In addition, each entree should have the ability to return the following data through an appropriate **getter** method. The data may be stored as attributes or hard coded directly into the method. 
  * **Price** - a Java `double` or Python `float` value representing the base price of the item plus any upcharge associated with the chosen **Base** value. 
  * **Calories** - an `int` value representing the number of calories associated with the item.
  * **Instructions** - a Java [LinkedList](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/LinkedList.html) of `String` values or a Python [list](https://docs.python.org/3.10/library/stdtypes.html#list) of `str` values. 
    * If stored as an attribute, it should return a **shallow copy** of the list to prevent external modification. See [LinkedList's Copy Constructor (Java)](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/LinkedList.html#%3Cinit%3E(java.util.Collection)) or [list.copy (Python)](https://docs.python.org/3.10/library/stdtypes.html#typesseq-mutable). 

{{% notice warning %}}

Unfortunately, the Java `clone()` methods can cause an unchecked cast exception when used on Java Collections classes with generics. See [this StackOverflow question](https://stackoverflow.com/questions/9252803/how-to-avoid-unchecked-cast-warning-when-cloning-a-hashset) for a discussion of how to get around that using a copy constructor.

{{% /notice %}}

Each entree class should also override the default string representation method (`toString()` in Java or `__str__()` in Python) and return a string that properly describes the entree. The string should be formatted as "{entree name} on {base}", such as "Clue Chili on Spaghetti".

It should also override the default equality method (`equals()` in Java or `__eq__()` in Python). Two items should be considered equal **only if the values of all attributes** are equal. 

Each entree description will include a list of ingredients included on the entree. Those ingredients should be represented using Boolean attributes that are set to `true` by default, with appropriate **getter** and **setter** methods. Changing any of these to `false` will cause a "Hold {ingredient}" message, such as "Hold Sauce", to be added to the **Instructions** list. Likewise, changing it back to `true` will remove the appropriate message. If all ingredients are at their default values, the **Instructions** list should be empty. 

Each entree will be served on a particular **Default Base**, and will include a default set of **Toppings**. Those attributes should be populated appropriately in the constructor for the entree. Changes to the **Base** and **Toppings** attributes will not affect the **Instructions** attribute at this time (we'll add that later). 

The number of **Calories** for a entree will remain constant, regardless of other attributes (we'll just pretend that changing the base or toppings doesn't change the number of calories).

The **Price** for a entree will change based on the value selected for the **Base**. Each entree will have a base price listed for the **Default Base** option. Other bases include an associated upcharge or discount, which must be adjusted.

{{% notice tip "Base Prices" %}}

This means that the prices shown on the menu already include the upcharge for the given default base. You may want to calculate and store a base price for the item by removing the upcharge from the menu price. 

{{% /notice %}}

##### Clue Chili

_you'll have to discover "whodunit" and created this twist on a classic_

`gamegrub.data.entrees.Clue` - The price is **$10.45** and it is **1165** calories. Served on a **Spaghetti Base**. Ingredients: **Spicy Beef**, **Chili**, **Red Sauce** and **Beans**. Toppings: **Onion**, **Cheese** and **Hot Sauce**

##### Jenga Nachos

_stack them higher and higher until it all falls down_

`gamegrub.data.entrees.Jenga` - The price is **$11.85** and it is **1470** calories. Served on a **Chips Base**. Ingredients: **Spicy Beef**, and **Beans**. Toppings: **Onion**, **Cheese**, **Sour Cream**, **Hot Sauce** and **Guacamole**

##### Yahtzee Poké

_a refreshing dish perfect for a day on the water_

`gamegrub.data.entrees.Yahtzee` - The price is **$15.25** and it is **785** calories. Served on a **Rice Base**. Ingredients: **Tuna**, **Veggies**, and **Seaweed**. Toppings:  **Guacamole**, **Soy Sauce**, **Hot Sauce** and **Crispy Strips**

##### Chess Chicken Parmesan

_a hearty dish to checkmate any hunger_

`gamegrub.data.entrees.Chess` - The price is **$13.65** and it is **1555** calories. Served on a **Spaghetti Base**. Ingredients: **Crispy Chicken**, and **Red Sauce**. Toppings: **Cheese** and **Fresh Herbs**

##### Monopoly Bowl

_a true winner takes home everything_

`gamegrub.data.entrees.Monopoly` - The price is **$18.65** and it is **1685** calories. Served on a **Rice Base**. Ingredients: **Spicy Beef**, **Crispy Chicken**, **Beans**, and **Veggies**. Toppings: **Onion**, **Cheese**, **Hot Sauce**, **Sour Cream**, **Guacamole**, and **Crispy Strips**

---

### Sides

Each side should be stored in an appropriately named class in the `gamegrub.data.sides` package. Each side should include an attribute for the following data:
  * **Size** - a `Size` value (see below). It should have a **getter** and **setter** method.

In addition, each side should have the ability to return the following data through an appropriate **getter** method. The data may be stored as attributes or hard coded directly into the method. 
  * **Price** - a Java `double` or Python `float` value. 
  * **Calories** - an `int` value.

Each side class should also override the default string representation method (`toString()` in Java or `__str__()` in Python) and return a string that properly describes the side. The string should be formatted as "{size} {side name}", such as "Junior Potato Dice".

It should also override the default equality method (`equals()` in Java or `__eq__()` in Python). Two items should be considered equal only if the values of all attributes are equal. 

Each side description will include a **Price** and number of **Calories** for each **Size**. The sides will have a default size of `Junior`. 

##### Potato Dice

_a pile of d6 shaped taters, deep fried and tasty_

`gamegrub.data.sides.Dice` - Junior: **$2.75** and **350** calories. Classic: **$3.85** and **475** calories. Winner: **$5.35** and **795** calories. 

##### Catan Skewers

_wheat breaded lamb skewers, baked in a wood-fired clay oven and sprinkled with salt ore - every resource in the game!_

`gamegrub.data.sides.Catan` - Junior: **$4.45** and **530** calories. Classic: **$6.85** and **815** calories. Winner: **$8.65** and **1045** calories. 

##### Risk Bites

_deep fried mac & cheese balls, but one has a spicy surprise - are you brave enough to risk it?_

`gamegrub.data.sides.Risk` - Junior: **$3.95** and **480** calories. Classic: **$5.15** and **755** calories. Winner: **$6.95** and **940** calories.

---

### Drinks

Each drink should be stored in an appropriately named class in the `gamegrub.data.drinks` package. Each drink should include an attribute for the following data:
  * **Size** - a `Size` value (see below). It should have a **getter** and **setter** method.

In addition, each drink should have the ability to return the following data through an appropriate **getter** method. The data may be stored as attributes or hard coded directly into the method. 
  * **Price** - a Java `double` or Python `float` value. 
  * **Calories** - an `int` value. It should have a **getter** method.
  * **Instructions** - a Java [LinkedList](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/LinkedList.html) of `String` values or a Python [list](https://docs.python.org/3.10/library/stdtypes.html#list) of `str` values. 
    * If stored as an attribute, it should return a **shallow copy** of the list to prevent external modification. See [LinkedList's Copy Constructor (Java)](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/LinkedList.html#%3Cinit%3E(java.util.Collection)) or [list.copy (Python)](https://docs.python.org/3.10/library/stdtypes.html#typesseq-mutable). 

Each drink class should also override the default string representation method (`toString()` in Java or `__str__()` in Python) and return a string that properly describes the drink. The string should be formatted as "{size} {drink name}", such as "Junior Candy Land Shake".

It should also override the default equality method (`equals()` in Java or `__eq__()` in Python). Two items should be considered equal only if the values of all attributes are equal. 

Each drink description may include a list of flavors that may be added. Those flavors should be represented using Boolean attributes that are set to `false` by default, with appropriate **getter** and **setter** methods. Changing any of these to `true` will cause a "Add {flavor}" message, such as "Add Cherry", to be added to the **Instructions** list. Likewise, changing it back to `false` will remove the appropriate message.

In addition, drinks may specify default flavors that should be represented using Boolean attributes that are set to `true` by default, with appropriate **getter** and **setter** methods. Changing any of these to `false` will cause a "Hold {flavor}" message, such as "Hold Coconut", to be added to the **Instructions** list. Likewise, changing it back to `true` will remove the appropriate message. 

If all flavors are at their default values, the **Instructions** list should be empty. 

Each drink description will include a **Price** and number of **Calories** for each **Size**. The drinks will have a default size of `Junior`. Changes to the **Size** attribute will not affect the **Instructions** attribute. 

##### Candy Land Shake

_a classic shake with all the candy!_

`gamegrub.data.drinks.Candy` - Flavors: **Chocolate** (default), **Vanilla**, and **Strawberry**. Junior: **$5.75** and **770** calories. Classic: **$7.45** and **1215** calories. Winner: **$9.55** and **1465** calories.

##### Sorry Soda

_soda fountain for all, no apologies needed_

`gamegrub.data.drinks.Sorry` - Flavors: **Cola** (default), **Cherry**, **Grape**, and **Orange**. Junior: **$2.55** and **370** calories. Classic: **$3.85** and **535** calories. Winner: **$5.35** and **765** calories.

##### Cranium Coffee

_fuel for the brain to win the game_

`gamegrub.data.drinks.Cranium` - Flavors: **Milk** (default), **Caramel**, **Chocolate**, and **Mint**. Junior: **$4.35** and **380** calories. Classic: **$5.25** and **495** calories. Winner: **$6.00** and **585** calories.

---

### Enumerations

Each enumeration should be stored in an appropriately named class in the `gamegrub.data.enums` package. Each enumeration class should also override the default string representation method (`toString()` in Java or `__str__()` in Python) and return a string that properly describes the item. Python developers may also wish to override the `__repr__()` method to return this value as well.

##### Base

_an excellent start for a delicious meal_

`gamegrub.data.enums.Base` - **Rice** (add $1.00), **Spaghetti** (add $1.50) or **Chips** (add $2.00)

{{% notice tip "Enums with Data" %}}

It is possible to create an enumeration that also stores additional data associated with each value, and then access that data through the enum value. You may be able to use this to simplify handling the upcharge for each base. Below are links to some sample code from later in this course that shows how to create such an enum and use that data.

**Java**: [Enum](https://github.com/K-State-Computational-Core/restaurantregister-java/blob/main/app/src/main/java/edu/ksu/cs/cc410/register/CashDenomination.java) [Usage](https://github.com/K-State-Computational-Core/restaurantregister-java/blob/main/app/src/main/java/edu/ksu/cs/cc410/register/CashDrawer.java#L69)  
**Python**: [Enum](https://github.com/K-State-Computational-Core/restaurantregister-python/blob/main/cc410/register/CashDenomination.py) [Usage](https://github.com/K-State-Computational-Core/restaurantregister-python/blob/main/cc410/register/CashDrawer.py#L61)

{{% /notice %}}

##### Size

_strategies to win any game and fulfill your hunger_

`gamegrub.data.enums.Size` - **Junior** (Small), **Classic** (Medium), **Winner** (Large)

##### Toppings

_complete your meal and win the day_

`gamegrub.data.enums.Toppings` - **Onions**, **Cheese**, **Hot Sauce**, **Sour Cream**, **Guacamole**, **Soy Sauce**, **Crispy Strips**, **Fresh Herbs**

---

_Special thanks to friends and family for inspiration and menu suggestions!_