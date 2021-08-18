---
title: "Restaurant Classes"
pre: "1. "
weight: 20
date: 2020-12-29T00:53:26-05:00
---

This page lists the milestone requirements for **Milestone 1** of the **CC 410 Restaurant Project**. Read the requirements carefully and discuss any questions with the instructors or TAs. 

## Purpose

The **CC 410 Restaurant Project** project for this semester is centered around building a point of sale (POS) system for a fictional restaurant named _Starfleet Subs_, based in the [Star Trek](https://en.wikipedia.org/wiki/Star_Trek) universe. 

This first milestone involves building the classes that represent items on the restaurant's menu. In a traditional [Model-View-Controller](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) software design pattern, these classes would make up the core of the **model**. This content should be mostly review of concepts learned in prior CC courses with the addition of enumerations (enums). It should not be particularly difficult, but it may be repetitive and time consuming. 

Specifically, we'll focus primarily on **data encapsulation** by storing attributes about each menu item in the class. We'll also learn how to combine **state** and **behavior** by modifying the string representation of the object based on the current state, or the combined values stored in the attributes. 

{{% notice tip %}}

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

The following requirements **ARE NOT** enforced for this milestone, but will be enforced in later milestones that use the same code. We will focus on learning to meet each of these requirements in future modules. However, you are welcome to "plan ahead" by minimizing the number of style errors in your code and adding some basic documentation where desired. 

{{% notice tip %}}

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

## Assignment Requirements

This milestone should include the following features:

* Entrée classes - 7
  * Declared in the `starfleetsubs.data.entrees` package
* Side classes - 4
  * Declared in the `starfleetsubs.data.sides` package
* Drink classes - 5
  * Declared in the `starfleetsubs.data.drinks` package
* Enumeration classes - 3
  * Declared in the `starfleetsubs.data.enums` package

See the [Starfleet Subs Menu](#starfleet-subs-menu) section below for descriptions of what each class should contain.

**Python** - these files should include complete type annotations and achieve a low imprecision percentage in Mypy using strict type checking.

{{% notice tip %}}

_In my testing, the only imprecision in type checking should be the first line of the `__eq__` method since it must accept an imprecise `object` type until the `isinstance()` method call. It will also mark the `@property.setter` annotations, but they don't count toward the imprecision total and can be ignored. The total imprecision should be less than 5% overall, and will probably be less than 2% in most cases. -Russ_

{{% /notice %}}
  
## Time Requirements

Completing this project is estimated to require 3-8 hours.

{{% notice tip %}}

_In my testing, this milestone requires around 1000-1500 lines of pure code without documentation, or around 2000-2500 lines including documentation comments that will be included as part of milestone 2. Much of the code can be carefully copy-pasted between files with similar attributes. My best suggestion is to do the enumerations first, then pick one of the complex entrées like `TheRiker` and start there. Once you have the entrées all working, the sides and drinks are pretty easy and use much of the same structure. -Russ_

{{% /notice %}}

## Grading Rubric

This assignment will be graded based on the rubric below:

* Entrée classes - 30%
* Side classes - 30%
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

## Starfleet Subs Menu

_our motto: to boldly eat a sandwich where no sandwich has been eaten before_

Each attribute described below should be implemented as a private variable within the class. Most attributes will also include a **getter** method, and sometimes a **setter** method, following this naming scheme (using **Price** as an example): 
  * **Java** - The private `price` attribute would have a `getPrice` getter and `setPrice` setter method.
  * **Python** - The private `__price` attribute would have a getter and setter named `price` implemented as a [Python Property](https://docs.python.org/3/library/functions.html#property). 

---

### Entrées

Each entrée should be stored in an appropriately named class in the `starfleetsubs.data.entrees` package. Each entrée should include an attribute for the following data:
  * **Bread** - a `Bread` value (see below). It should have a **getter** and **setter** method.
  * **Condiments** - a Java [HashSet](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html) or a Python [set](https://docs.python.org/3.6/library/stdtypes.html#list) of `Condiment` values (see below). 
    * This attribute should have a **getter** method that returns a **shallow copy** of the set to prevent external modification. See [HashSet's Copy Constructor (Java)](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html#HashSet-java.util.Collection-) or [set.copy (Python)](https://docs.python.org/3.6/library/stdtypes.html#frozenset.copy). 
    * This attribute should also have methods for **Add Condiment** and **Remove Condiment** to modify the list of condiments. 

In addition, each entrée should have the ability to return the following data through an appropriate **getter** method. The data may be stored as attributes or hard coded directly into the method. 
  * **Price** - a Java `double` or Python `float` value. 
  * **Calories** - an `int` value. It should have a **getter** method.
  * **Special Instructions** - a Java [LinkedList](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html) of `String` values or a Python [list](https://docs.python.org/3.6/library/stdtypes.html#list) of `str` values. 
    * If stored as an attribute, it should return a **shallow copy** of the list to prevent external modification. See [LinkedList's Copy Constructor (Java)](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html#LinkedList-java.util.Collection-) or [list.copy (Python)](https://docs.python.org/3.6/library/stdtypes.html#typesseq-mutable). 

{{% notice info %}}

Unfortunately, the Java `clone()` methods can cause an unchecked cast exception when used on Java Collections classes with generics. See [this StackOverflow question](https://stackoverflow.com/questions/9252803/how-to-avoid-unchecked-cast-warning-when-cloning-a-hashset) for a discussion of how to get around that using a copy constructor.

{{% /notice %}}

Each entrée class should also override the default string representation method (`toString()` in Java or `__str__()` in Python) and return a string that properly describes the entrée. The string should be formatted as "{sandwich name} on {bread}", such as "The Kirk on White Bread".

It should also override the default equality method (`equals()` in Java or `__eq__()` in Python). Two items should be considered equal only if the values of all attributes are equal. 

Each entrée description will include a list of ingredients included on the sandwich. Those ingredients should be represented using Boolean attributes that are set to `true` by default, with appropriate **getter** and **setter** methods. Changing any of these to `false` will cause a "Hold {ingredient}" message, such as "Hold Ham", to be added to the **Special Instructions** list. Likewise, changing it back to `true` will remove the appropriate message. If all ingredients are at their default values, the **Special Instructions** list should be empty. 

Likewise, each entrée description will include a **Price**, number of **Calories**, a default value for **Bread** and a default set of **Condiments**. Those attributes should be populated appropriately in the constructor for the entrée. Changes to the **Bread** and **Condiments** attributes will not affect the **Special Instructions** attribute. Likewise, the **Price** and number of **Calories** will remain constant, regardless of other attributes. 

##### The Kirk (Ham & Cheese)

_just like the man himself, this sandwich "hams" it up and is super "cheesy"_

`starfleetsubs.data.entrees.TheKirk` - The price is **$6.35** and it is **650** calories. Served on **White Bread** with **Ham** and **Cheese**. Comes with **Lettuce, Tomato, and Mayo**. 

##### The Scotty (Ham, Turkey, Bacon & Cheese)

_a heartier sandwich, with turkey and bacon to keep your ship in top shape_

`starfleetsubs.data.entrees.TheScotty` - The price is **$7.65** and it is **800** calories. Served on **Wheat Bread** with **Ham**, **Turkey**, **Bacon** and **Cheese**. Comes with **Lettuce, Tomato, Onion, Mustard and Mayo**. 

##### The Janeway (Italian)

_a sandwich tasty enough for any "voyager" to enjoy_

`starfleetsubs.data.entrees.TheJaneway` - The price is **$9.35** and it is **950** calories. Served on **White Bread** with **Ham**, **Pepperoni**, **Salami** and **Cheese**. Comes with **Lettuce, Tomato, Onion, Pickles, Peppers, and Mayo**. 

##### The Q (BBQ)

_the ultimate judgement of humanity, a "continuum" of meats_

`starfleetsubs.data.entrees.TheQ` - The price is **$11.25** and it is **1375** calories. Served on **White Bread** with **Brisket**, **Pulled Pork**, **Sausage**, and **Bacon**. Comes with **Onion, Pickles, and BBQ Sauce**. 

##### The Gagh (Meatball)

_a Klingon delicacy to feed a true warrior's hunger_

`starfleetsubs.data.entrees.TheGagh` - The price is **$8.45** and it is **1020** calories. Served on **Sourdough Bread** with **Meatballs**, **Marinara** and **Cheese**. Comes with no condiments by default.

##### The Riker (Nearly Everything)

_our "number one" sandwich_

`starfleetsubs.data.entrees.TheRiker` - The price is **$17.01** and it is **1701** calories. Served on **Wheat Bread** with **Ham**, **Turkey**, **Pepperoni**, **Salami**, **Brisket**, **Pulled Pork**, **Bacon** and **Cheese**. Comes with **Lettuce, Tomato, Onion, Pickles, Peppers, Olives, Mayo, Mustard, and BBQ Sauce**

##### The Spock (Vegetarian)

_a most logical choice_

`starfleetsubs.data.entrees.TheSpock` - The price is **$5.50** and it is **700** calories. Served on **Wheat Bread** with **Cheese**. Comes with **Lettuce, Tomato, Onion, Pickles, Peppers, Olives, and Mayo**. 

---

### Sides

Each side should be stored in an appropriately named class in the `starfleetsubs.data.sides` package. Each side should include an attribute for the following data:
  * **Size** - a `Size` value (see below). It should have a **getter** and **setter** method.

In addition, each side should have the ability to return the following data through an appropriate **getter** method. The data may be stored as attributes or hard coded directly into the method. 
  * **Price** - a Java `double` or Python `float` value. 
  * **Calories** - an `int` value. It should have a **getter** method.

Each side class should also override the default string representation method (`toString()` in Java or `__str__()` in Python) and return a string that properly describes the side. The string should be formatted as "{size} {side name}", such as "Small Data Chips".

It should also override the default equality method (`equals()` in Java or `__eq__()` in Python). Two items should be considered equal only if the values of all attributes are equal. 

Each side description will include a **Price** and number of **Calories** for each **Size**. The sides will have a default size of `Small`. Those attributes should be populated appropriately in the constructor for the side, and should be updated if the **Size** attribute changes.

##### Data Chips (Potato Chips)

_crispy, crunchy potato chips seeking to understand human emotions_

`starfleetsubs.data.sides.DataChips` - Small: **$1.75** and **250** calories. Medium: **$2.25** and **350** calories. Large: **$3.50** and **550** calories. 

##### Enterprise (Cookie & 2 Pickles)

_a round cookie and two gherkin "nacelles" in honor of the best ship in the fleet_

`starfleetsubs.data.sides.Enterprise` - Small: **$1.98** and **170** calories. Medium: **$3.77** and **340** calories. Large: **$5.55** and **510** calories. 

##### Borg (Pretzel Bites)

_it is "futile" to "resist" these identical square pretzel bites wrapped in foil_

`starfleetsubs.data.sides.Borg` - Small: **$2.55** and **375** calories. Medium: **$4.15** and **565** calories. Large: **$6.65** and **780** calories. 

##### Bones McCoy (Chicken Wings)

_these wings are the best "bones" in the galaxy_

`starfleetsubs.data.sides.BonesMcCoy` - Small: **$3.75** and **545** calories. Medium: **$5.45** and **785** calories. Large: **$6.75** and **925** calories. 

---

### Drinks

Each drink should be stored in an appropriately named class in the `starfleetsubs.data.drinks` package. Each drink should include an attribute for the following data:
  * **Size** - a `Size` value (see below). It should have a **getter** and **setter** method.

In addition, each drink should have the ability to return the following data through an appropriate **getter** method. The data may be stored as attributes or hard coded directly into the method. 
  * **Price** - a Java `double` or Python `float` value. 
  * **Calories** - an `int` value. It should have a **getter** method.
  * **Special Instructions** - a Java [LinkedList](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html) of `String` values or a Python [list](https://docs.python.org/3.6/library/stdtypes.html#list) of `str` values. 
    * If stored as an attribute, it should return a **shallow copy** of the list to prevent external modification. See [LinkedList's Copy Constructor (Java)](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html#LinkedList-java.util.Collection-) or [list.copy (Python)](https://docs.python.org/3.6/library/stdtypes.html#typesseq-mutable). 

Each drink class should also override the default string representation method (`toString()` in Java or `__str__()` in Python) and return a string that properly describes the drink. The string should be formatted as "{size} {drink name}", such as "Small Picard".

It should also override the default equality method (`equals()` in Java or `__eq__()` in Python). Two items should be considered equal only if the values of all attributes are equal. 

Each drink description may include a list of ingredients it includes by default. Those ingredients should be represented using Boolean attributes that are set to `true` by default, with appropriate **getter** and **setter** methods. Changing any of these to `false` will cause a "Hold {ingredient}" message, such as "Hold Whipped Cream", to be added to the **Special Instructions** list. Likewise, changing it back to `true` will remove the appropriate message. 

In addition, drinks may include optional ingredients that should be represented using Boolean attributes that are set to `false` by default, with appropriate **getter** and **setter** methods. Changing any of these to `true` will cause a "Add {ingredient}" message, such as "Add Ice", to be added to the **Special Instructions** list. Likewise, changing it back to `false` will remove the appropriate message. If all ingredients are at their default values, the **Special Instructions** list should be empty. 

Each drink description will include a **Price** and number of **Calories** for each **Size**. The drinks will have a default size of `Small`. Those attributes should be populated appropriately in the constructor for that class, and should be updated if the **Size** attribute changes. Changes to the **Size** attribute will not affect the **Special Instructions** attribute. 

##### The Picard (Hot Tea)

_tea, Earl Grey, hot_

`starfleetsubs.data.drinks.ThePicard` - Tea served with **Lemon**. Can optionally add **Ice**. Small: **$0.95** and **5** calories. Medium: **$1.65** and **10** calories. Large: **$2.25** and **15** calories.

##### The Troi (Latte/Mocha)

_the ultimate comfort drink inspired by a chocolate sundae_

`starfleetsubs.data.drinks.TheTroi` - Espresso served with **Chocolate**,  **Whipped Cream** and a **Cherry**. Can optionally add **Extra Espresso Shot**. Small: **$3.75** and **300** calories. Medium: **$4.35** and **425** calories. Large: **$5.25** and **600** calories.

##### The Worf (Prune Juice)

_a warrior's drink_

`starfleetsubs.data.drinks.TheWorf` - Prune Juice. Can optionally add **Ice**. Small: **$1.25** and **150** calories. Medium: **$1.75** and **225** calories. Large: **$2.55** and **415** calories.

##### The Guinan (Lemonade)

_a refreshing drink for a mysterious connoisseur_

`starfleetsubs.data.drinks.TheGuinan` - Lemonade served with **Ice**. Can optionally add **Strawberry** and/or **Cherry**. Small: **$2.30** and **150** calories. Medium: **$3.45** and **225** calories. Large: **$4.65** and **395** calories. 

##### Altair Water

_the ultimate in hydration, direct from Altair IV_

`starfleetsubs.data.drinks.AltairWater` - Can optionally add **Ice** and/or **Lemon**. All sizes are **$0.50** and **0** calories. 

---

### Enumerations

Each enumeration should be stored in an appropriately named class in the `starfleetsubs.data.emnums` package. Each enumeration class should also override the default string representation method (`toString()` in Java or `__str__()` in Python) and return a string that properly describes the item. Python developers may also wish to override the `__repr__()` method to return this value as well.

##### Bread

_an upper deck and a lower deck is important for any sub_

`starfleetsubs.data.enums.Bread` - **White Bread**, **Wheat Bread**, **Sourdough Bread**

##### Size

_options to fit any appetite_

`starfleetsubs.data.enums.Size` - **Small**, **Medium**, **Large**

##### Condiments

_don't forget your KHAAAAAANNNNN!-diments_

`starfleetsubs.data.enums.Condiment` - **Lettuce**, **Tomato**, **Onion**, **Pickles**, **Peppers**, **Olives**, **Mayo**, **Mustard**, **BBQ Sauce**

---

_Special thanks to Nathan, Stephen, Sarah, Kellie, Dan, Jack, Josh, Pascal, Beth, and Vince for inspiration and menu suggestions!_