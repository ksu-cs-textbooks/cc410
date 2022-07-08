---
title: "Write Hello World"
weight: 20
pre: "4.P.2. "
---

{{% youtube Gx_nV1Y-0ek %}}

Now that we've created a package for our code, let's write the code for our "Hello Real World" application. Traditionally, a Python "Hello World" program is a single line of code, but for this example we'll follow all of the object-oriented standards by creating a class and a method. 

## Create a Class

First, we need to create a source code file for our application. We'll place this code inside of the `src/hello` package we've already created. So, let's create a file called `HelloWorld.py` in that directory. Once it is created, we should see the following structure:

![Python Hello File](/images/e1/22hellostruct.png)

Then, inside of that file, we can place the following code:

```python
class HelloWorld:
    @staticmethod
    def main(args):
        print("Hello World")
```

This code should be pretty familiar at this point. The one thing to notice is that this file does not include a main guard. We do this for a couple of reasons:

1. If the class is executed directly, it will simply load the class but there isn't any code outside of the class that would actually be executed.
2. We will use a different process to start our entire application, which we will detail below.

So, by using this structure, we can actually simplify our code a bit by omitting the main guard!

## Make an Application

Next, we'll need to create a couple more files in order to make our application easily executable. In fact, what we'll end up doing is making the entire `src` folder act like a "meta package" that includes all of the packages in the application. 

To do this, we'll need to create two more files directly inside of the `src` folder:

* `__init__.py` - this will make Python treat the entire `src` directory as a package
* `__main__.py` - this will allow Python to execute that package directly as an application

Once those files are created, we should have a structure similar to this image:

![Python Meta Package](/images/e1/22meta.png)

Then, we need to populate those files with some code. So, in the `__init__.py` file in `src`, enter the following code:

```python
print("In /src/__init__.py")
```

As before, this will just allow us to see when the package is loaded to help us understand how everything works together.

In the `__main__.py` file, we'll put the following code:

```python
import sys
from src.hello.HelloWorld import HelloWorld
print("In /src/__main__.py")
HelloWorld.main(sys.argv)
```

Hopefully this code is also pretty easy to understand. We'll import the `sys` library so we can access the command line arguments, and then we'll also import our `HelloWorld` class from the `src.hello` meta package we created. Finally, we'll print a message stating which file we are in, and then call the main method of our application, passing along the command line arguments. 

The `__main__.py` file is described in the [Python Documentation](https://docs.python.org/3/library/__main__.html).

## Run Our Application

That's all we need to make our application usable. Now, let's see if we can execute it.

To use our application, we'll need to use the Linux terminal from within the `python` folder. So, let's open the Linux terminal and change our directory to that location:

```bash
cd ~/workspace/python
```

Of course, if you are already in the `~/workspace` folder, you can just use `cd python` to get there. In the code above, we include the whole path so that it will always work, regardless of the current working directory. 

Once we are in that directory, we can execute our application using the following command:

```bash
python3 -m src
```

That will tell Python to execute the application stored in our `src` folder as a Python module, or meta package. When we do that, we should receive output like this:

![Python Output](/images/e1/22output.png)

As we can see, our application actually goes through a few steps before it is able to run the `main` function:

1. First, Python finds the `src` meta package, which will reach the print statement in `__init__.py`. It will then find `__main__.py` and execute it to run the meta package as a program.
2. Then, the `src.hello` package is loaded on line 2 of `__main__.py`. So, the `__init__.py` file in that package will be loaded and executed.
3. Next, we reach the print statement on line 3 `__main__.py`.
4. Finally, line 4 of `__main__.py` executes the `main` function of our `HelloWorld` class

There we go! We've successfully built and run our application using Python! If you want, you can test different messages in `HelloWorld.py` to make sure the program is working correctly.

{{% notice info "Pycache Folders" %}}

When Python code is executed, the Python interpreter creates a "compiled" version of the code and stores it in a folder called `__pycache__`. Those folders can be safely ignored, but they may appear in various directories as you develop and test your application. Later in this module we'll discuss how to omit those directories from version control applications such as Git. 

You can read more about this process in the [Python Documentation](https://docs.python.org/3/tutorial/modules.html#compiled-python-files).

{{% /notice %}}