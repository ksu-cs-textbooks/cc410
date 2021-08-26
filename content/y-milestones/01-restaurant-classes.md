---
title: "Restaurant Classes"
pre: "1. "
weight: 20
date: 2021-08-17T00:53:26-05:00
---

This page lists the milestone requirements for **Milestone 1** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Hero Pizza_, celebrating the heroes from cartoons, comic books, movies, and more. 

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
  * Python: Use tox configured to use Python 3.6 and a requirements file to install libraries. You may include a main class in a separate package for testing purposes only.
* **All code must properly compile or be interpreted.**
  * Java: It must compile using Gradle.
  * Python: It must be interpreted using Python 3.6. Where specified, type hints should be included in the code, and all code should pass a strict Mypy type check.
* Submissions to Canvas should be tagged GitHub releases that are numbered according to [Semantic Versioning](https://semver.org/).

{{% expand "Unenforced requirements (click to expand):" %}}

The following requirements **ARE NOT** enforced for this milestone, but will be enforced in later milestones that use the same code. We will focus on learning to meet each of these requirements in future modules. However, you are welcome to "plan ahead" by minimizing the number of style errors in your code and adding some basic documentation where desired. 

{{% notice tip tip-0 "Naming Standards" %}}

You can make things easier on yourself by following proper naming standards for your language of choice, even though we aren't enforcing a style guide for this milestone.

* **Java** - All names are in CamelCase. Classes start with uppercase, like `ClassName`, methods and attributes start with lowercase like `methodName`. See the [Google Style Guide](https://google.github.io/styleguide/javaguide.html#s5-naming).
* **Python** - All names are lowercase with underscores like `method_name`, with the exception of classes, which are named in CamelCase starting with an uppercase letter like `ClassName`. See the [Google Style Guide](https://google.github.io/styleguide/pyguide.html#s3.16-naming).

It is easier to get this correct from the start, then having to refactor your code later. Of course, major refactoring is also a good lesson that guarantees you'll get it right in the future!

{{% /notice %}}

* **(Milestone 3) All code submitted must be free of style errors.** We will be using the [Google Style Guide](https://google.github.io/styleguide/) for each language. 
  * Java: Use Checkstyle 8.38+ and the [Google Style Configuration](https://raw.githubusercontent.com/checkstyle/checkstyle/checkstyle-8.38/src/main/resources/google_checks.xml). 
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

* Pizza classes - 7
  * Declared in the `heropizza.data.pizzas` package
* Side classes - 4
  * Declared in the `heropizza.data.sides` package
* Drink classes - 5
  * Declared in the `heropizza.data.drinks` package
* Enumeration classes - 3
  * Declared in the `heropizza.data.enums` package

See the [Hero Pizza Menu](#hero-pizza-menu) section below for descriptions of what each class should contain.

**Python** - these files should include complete type annotations and achieve a low imprecision percentage in Mypy using strict type checking.

{{% notice tip tip-1 "Python Type Checking" %}}

_In my testing, the only imprecision in type checking should be the first line of the `__eq__` method since it must accept an imprecise `object` type until the `isinstance()` method call. It will also mark the `@property.setter` annotations, but they don't count toward the imprecision total and can be ignored. The total imprecision should be less than 5% overall, and will probably be less than 2% in most cases. -Russ_

{{% /notice %}}
  
## Time Requirements

Completing this project is estimated to require 3-8 hours.

{{% notice note tip-2 "Expected Scope" %}}

_In my testing, this milestone requires around 1000-1500 lines of pure code without documentation, or around 2000-2500 lines including documentation comments that will be included as part of milestone 2. Much of the code can be carefully copy-pasted between files with similar attributes. My best suggestion is to do the enumerations first, then pick one of the complex pizzas and start there. Once you have the pizzas all working, the sides and drinks are pretty easy and use much of the same structure. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* Pizza classes - 40%
* Side classes - 20%
* Drink classes - 30%
* Enumeration classes - 10%

The following deductions apply:

* Any portion of the project which will not compile (Java), pass a strict type check (Python), or execute properly will be given a grade of 0.

This is not an exhaustive list of possible deductions. The instructors will strive to provide reasonable and fair grading, but we can't predict all possible defects. It is up to the student to ensure that the project is complete and correct before submission. 

## Submission

Submit this assignment by creating a release on GitHub and uploading the release URL to the assignment on Canvas. You **should not** submit this Codio project or mark it as complete in Codio, in case you need to come back to it and make changes later.

---
---
---

## Hero Pizza Menu

_our motto: eat like a hero - choose pizza!_

Each attribute described below should be implemented as a private variable within the class. Most attributes will also include a **getter** method, and sometimes a **setter** method, following this naming scheme (using **Price** as an example): 
  * **Java** - The private `price` attribute would have a `getPrice` getter and `setPrice` setter method.
  * **Python** - The private `__price` attribute would have a getter and setter named `price` implemented as a [Python Property](https://docs.python.org/3/library/functions.html#property). 

---

### Pizzas

Each pizza should be stored in an appropriately named class in the `heropizza.data.pizzas` package. Each pizza should include an attribute for the following data:
  * **Crust** - a `Crust` value (see below). It should have a **getter** and **setter** method.
  * **Veggies** - a Java [HashSet](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html) or a Python [set](https://docs.python.org/3.6/library/stdtypes.html#set) of `Veggie` values (see below). 
    * This attribute should have a **getter** method that returns a **shallow copy** of the set to prevent external modification. See [HashSet's Copy Constructor (Java)](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html#HashSet-java.util.Collection-) or [set.copy (Python)](https://docs.python.org/3.6/library/stdtypes.html#frozenset.copy). 
    * This attribute should also have methods for **Add Veggie** and **Remove Veggie** to modify the list of condiments. 

In addition, each entrée should have the ability to return the following data through an appropriate **getter** method. The data may be stored as attributes or hard coded directly into the method. 
  * **Price** - a Java `double` or Python `float` value representing the base price of the item plus any upcharge associated with the chosen **Crust** value. 
  * **Calories** - an `int` value representing the number of calories associated with the item.
  * **Modifications** - a Java [LinkedList](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html) of `String` values or a Python [list](https://docs.python.org/3.6/library/stdtypes.html#list) of `str` values. 
    * If stored as an attribute, it should return a **shallow copy** of the list to prevent external modification. See [LinkedList's Copy Constructor (Java)](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html#LinkedList-java.util.Collection-) or [list.copy (Python)](https://docs.python.org/3.6/library/stdtypes.html#typesseq-mutable). 

{{% notice warning %}}

Unfortunately, the Java `clone()` methods can cause an unchecked cast exception when used on Java Collections classes with generics. See [this StackOverflow question](https://stackoverflow.com/questions/9252803/how-to-avoid-unchecked-cast-warning-when-cloning-a-hashset) for a discussion of how to get around that using a copy constructor.

{{% /notice %}}

Each pizza class should also override the default string representation method (`toString()` in Java or `__str__()` in Python) and return a string that properly describes the pizza. The string should be formatted as "{pizza name} on {crust} Crust", such as "The Mikey on Thin Crust".

It should also override the default equality method (`equals()` in Java or `__eq__()` in Python). Two items should be considered equal **only if the values of all attributes** are equal. 

Each pizza description will include a list of toppings included on the pizza. Those toppings should be represented using Boolean attributes that are set to `true` by default, with appropriate **getter** and **setter** methods. Changing any of these to `false` will cause a "Hold {topping}" message, such as "Hold Ham", to be added to the **Modifications** list. Likewise, changing it back to `true` will remove the appropriate message. If all toppings are at their default values, the **Modifications** list should be empty. 

Each pizza will be served on **Thin Crust** by default, and will include a default set of **Veggies**. Those attributes should be populated appropriately in the constructor for the pizza. Changes to the **Crust** and **Veggies** attributes will not affect the **Modifications** attribute at this time (we'll add that later). 

The number of **Calories** for a pizza will remain constant, regardless of other attributes (we'll just pretend that changing the pizza doesn't change the number of calories).

The **Price** for a pizza will change based on the value selected for the **Crust**. Each pizza will have a base price listed for the **Thin** crust option. Other crusts include an associated upcharge, which must be added to the base price.

##### The Mikey (Ham, Cheese & Pineapple)

_just like the turtle himself, this sandwich "hams" it up and is super "cheesy"_

`heropizza.data.pizzas.TheMikey` - The price is **$8.25** and it is **986** calories. Toppings: **Ham** and **Cheese**. Veggies: **Pineapple**. 

##### The Jean Grey (Pork)

_a simple pizza for a complex hero_

`heropizza.data.pizzas.TheJeanGrey` - The price is **$10.25** and it is **850** calories. Toppings: **Pork** and **Cheese**. Veggies: **Mushrooms**, **Red Onions**, **Black Olives**, **Green Peppers**, **Banana Peppers** and **Roma Tomatoes**

##### The Wolverine (Meat)

_all the meat for a carnivorous feast_

`heropizza.data.pizzas.TheWolverine` - The price is **$9.35** and it is **950** calories. Toppings: **Sausage**, **Bacon**, **Ham** and **Pork**. Veggies: **Red Onions** and **Green Peppers**.

##### The She-Ra (Pepperoni)

_everyone "adora"s this classic_

`heropizza.data.pizzas.TheSheRa` - The price is **$8.75** and it is **1325** calories. Toppings: **Pepperoni** and **Cheese**. Veggies: none. 

##### The Jem (BBQ Chicken)

_a star studded treat that isn't a hologram_

`heropizza.data.pizzas.TheJem` - The price is **$9.65** and it is **1075** calories. Toppings: **Chicken**, **BBQ Sauce** and **Bacon**. Veggies: **Red Onions**

##### The He-Man (Nearly Everything)

_a pizza for a heroic appetite_

`heropizza.data.pizzas.TheHeMan` - The price is **$18.95** and it is **1986** calories. Toppings: **Ham**, **Sausage**, **Pepperoni**, **Bacon**, **Pork**, and **Cheese**. Veggies: **Mushrooms**, **Red Onions**, **Black Olives**, **Green Peppers**, **Banana Peppers** and **Jalapeno Peppers**

##### The Captain Planet (Vegetarian)

_by your powers combined_

`heropizza.data.pizzas.TheCaptainPlanet` - The price is **$6.50** and it is **745** calories. Toppings: **Cheese**. Veggies: **Mushrooms**, **Red Onions**, **Black Olives**, **Green Peppers**, **Banana Peppers**, **Jalapeno Peppers**, **Pineapple** and **Roma Tomatoes**

---

### Sides

Each side should be stored in an appropriately named class in the `heropizza.data.sides` package. Each side should include an attribute for the following data:
  * **Size** - a `Size` value (see below). It should have a **getter** and **setter** method.

In addition, each side should have the ability to return the following data through an appropriate **getter** method. The data may be stored as attributes or hard coded directly into the method. 
  * **Price** - a Java `double` or Python `float` value. 
  * **Calories** - an `int` value.

Each side class should also override the default string representation method (`toString()` in Java or `__str__()` in Python) and return a string that properly describes the side. The string should be formatted as "{size} {side name}", such as "Small Snarf Sticks".

It should also override the default equality method (`equals()` in Java or `__eq__()` in Python). Two items should be considered equal only if the values of all attributes are equal. 

Each side description will include a **Price** and number of **Calories** for each **Size**. The sides will have a default size of `Small`. 

##### Snarf Sticks (Breadsticks)

_soft breadsticks with a chewy bite_

`heropizza.data.sides.SnarfSticks` - Small: **$1.95** and **275** calories. Medium: **$3.25** and **450** calories. Hero: **$5.50** and **750 ** calories. 

##### Sailor Moon (Meatballs)

_meatballs inspired by a famous hairdo_

`heropizza.data.sides.SailorMoon` - Small: **$2.35** and **300** calories. Medium: **$4.85** and **550** calories. Hero: **$7.95** and **960** calories. 

##### Mjolnir (Mozzarella Sticks)

_do you have what it takes to wield Thor's hammer?_

`heropizza.data.sides.Mjolnir` - Small: **$2.95** and **425** calories. Medium: **$4.65** and **595** calories. Hero: **$6.95** and **840** calories. 

##### Batwings (Chicken Wings)

_Batman's trusty snack_

`heropizza.data.sides.Batwings` - Small: **$3.25** and **525** calories. Medium: **$5.25** and **765** calories. Hero: **$6.55** and **905** calories. 

---

### Drinks

Each drink should be stored in an appropriately named class in the `heropizza.data.drinks` package. Each drink should include an attribute for the following data:
  * **Size** - a `Size` value (see below). It should have a **getter** and **setter** method.

In addition, each drink should have the ability to return the following data through an appropriate **getter** method. The data may be stored as attributes or hard coded directly into the method. 
  * **Price** - a Java `double` or Python `float` value. 
  * **Calories** - an `int` value. It should have a **getter** method.
  * **Modifications** - a Java [LinkedList](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html) of `String` values or a Python [list](https://docs.python.org/3.6/library/stdtypes.html#list) of `str` values. 
    * If stored as an attribute, it should return a **shallow copy** of the list to prevent external modification. See [LinkedList's Copy Constructor (Java)](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html#LinkedList-java.util.Collection-) or [list.copy (Python)](https://docs.python.org/3.6/library/stdtypes.html#typesseq-mutable). 

Each drink class should also override the default string representation method (`toString()` in Java or `__str__()` in Python) and return a string that properly describes the drink. The string should be formatted as "{size} {drink name}", such as "Small Katara".

It should also override the default equality method (`equals()` in Java or `__eq__()` in Python). Two items should be considered equal only if the values of all attributes are equal. 

Each drink description may include a list of flavors that may be added. Those flavors should be represented using Boolean attributes that are set to `false` by default, with appropriate **getter** and **setter** methods. Changing any of these to `true` will cause a "Add {flavor}" message, such as "Add Cherry", to be added to the **Modifications** list. Likewise, changing it back to `false` will remove the appropriate message.

In addition, drinks may specify default flavors that should be represented using Boolean attributes that are set to `true` by default, with appropriate **getter** and **setter** methods. Changing any of these to `false` will cause a "Hold {flavor}" message, such as "Hold Coconut", to be added to the **Modifications** list. Likewise, changing it back to `true` will remove the appropriate message. 

If all flavors are at their default values, the **Special Instructions** list should be empty. 

Each side description will include a **Price** and number of **Calories** for each **Size**. The sides will have a default size of `Small`. Changes to the **Size** attribute will not affect the **Modification** attribute. 

##### Starfire (Cherry Soda)

_a titan of a drink_

`heropizza.data.drinks.Starfire` - Flavors: **Cherry** (default), **Vanilla**, **Orange** and **Grape**. Small: **$1.40** and **170** calories. Medium: **$3.75** and **255** calories. Hero: **$4.75** and **375** calories. 

##### Groot (Root Beer)

_a tasty drink made from strong roots_

`heropizza.data.drinks.Groot` - Flavors: **Caramel**, **Cinnamon**, and **Anise**. Small: **$3.55** and **320** calories. Medium: **$4.45** and **435** calories. Hero: **$5.05** and **540** calories.

##### Samurai Jack (Smoothie)

_a smooth drink to sooth a warrior's spirit_

`heropizza.data.drinks.SamuraiJack` - Flavors: **Jackfruit** (default), **Banana**, **Mango** and **Strawberry**. Small: **$4.25** and **650** calories. Medium: **$6.75** and **825** calories. Hero: **$9.55** and **1115** calories.

##### Bubbles (Boba Tea)

_a "powerpuff" of a drink with sugar and spice_

`heropizza.data.drinks.Bubbles` - Flavors: **Lychee**, **Passion Fruit**, and **Matcha**. Small: **$3.40** and **350** calories. Medium: **$4.45** and **425** calories. Hero: **$5.65** and **695** calories. 

##### Katara (Water)

_a simple water drink for an extraordinary water bender_

`heropizza.data.drinks.Katara` - Flavors: **Lemon** and **Coconut**. All sizes are **$1.00** and **0** calories. 

---

### Enumerations

Each enumeration should be stored in an appropriately named class in the `heropizza.data.enums` package. Each enumeration class should also override the default string representation method (`toString()` in Java or `__str__()` in Python) and return a string that properly describes the item. Python developers may also wish to override the `__repr__()` method to return this value as well.

##### Crust

_a solid base for a trustworthy pizza slice_

`heropizza.data.enums.Crust` - **Thin**, **Hand Tossed** (add $0.50), **Deep Dish** (add $1.00), **Cheese Stuffed** (add $2.00)

{{% notice tip tip-3 "Enums with Data" %}}

It is possible to create an enumeration that also stores additional data associated with each value, and then access that data through the enum value. You may be able to use this to simplify handling the upcharge for each crust type. Below are links to some sample code from later in this course that shows how to create such an enum and use that data.

**Java**: [Enum](https://github.com/K-State-Computational-Core/restaurantregister-java/blob/main/app/src/main/java/edu/ksu/cs/cc410/register/CashDenomination.java) [Usage](https://github.com/K-State-Computational-Core/restaurantregister-java/blob/main/app/src/main/java/edu/ksu/cs/cc410/register/CashDrawer.java#L69)  
**Python**: [Enum](https://github.com/K-State-Computational-Core/restaurantregister-python/blob/main/cc410/register/CashDenomination.py) [Usage](https://github.com/K-State-Computational-Core/restaurantregister-python/blob/main/cc410/register/CashDrawer.py#L61)

{{% /notice %}}

##### Size

_options to fit any heroic appetite_

`heropizza.data.enums.Size` - **Small**, **Medium**, **Hero**

##### Veggies

_an important part of a balanced meal_

`heropizza.data.enums.Veggie` - **Mushrooms**, **Red Onions**, **Black Olives**, **Green Peppers**, **Banana Peppers**, **Jalapeno Peppers**, **Pineapple**, **Roma Tomatoes** 

---

_Special thanks to friends and family for inspiration and menu suggestions!_