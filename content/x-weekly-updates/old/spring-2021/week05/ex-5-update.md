---
title: "Update to Example 5 Python"
pre: "5.A "
weight: 55
date: 2021-02-22T00:53:26-05:00
---

It appears that I missed an interesting error when developing Example 5 for Python. It is a bit complex, so I'm relying on the advanced formatting of this webpage to help explain it better than I can via email or in a short post to the class. I'll start with a short version, and then include a longer discussion of the problem and how I came to a solution that I feel is very helpful reading for anyone learning to program and solve these issues in their own work.

## tl;dr - The Short Version

Currently pytest has a [bug](https://github.com/pytest-dev/pytest/issues/5502) that causes errors when logging to `sys.stderr` when running code inside of `pytest`. 

As best I can tell, `pytest` tries to capture all output being printed to `sys.stderr` by redirecting it to a buffer (a virtual file) when running the tests. Once it is done, it will close the buffer and redirect output back to `sys.stderr`. Unfortunately, our logger does not realize this, and it may continue to try and write data to the buffer that is now closed, resulting in the `ValueError: I/O operation on closed file` error message seen in the output.

There are several [methods](https://stackoverflow.com/questions/25188119/test-if-code-is-executed-from-within-a-py-test-session/44595269#44595269) to determine if code is running under `pytest` and disable logging in that case. 

I recommend [this method](https://stackoverflow.com/a/44595269):

```python
import sys

# get the root logger
logger = logging.getLogger()
# disable if pytest is running
if "pytest" in sys.modules:
    logger.disabled = True
```

You will need to add this code to any file that you add logging to, in order to prevent errors from `pytest`. Alternatively, you can disable the handler that prints to `sys.stderr` and instead just use a file handler.

## The Long Version

Since this is an advanced programming course, I figure that it is worth a bit of a "deep dive" into this situation so you can understand what I found, the efforts I went through to solve it, and how things are really working behind the scenes.

This is a bit of [cognitive apprenticeship](https://en.wikipedia.org/wiki/Cognitive_apprenticeship), where I attempt to show you my thought processes and how I go about solving a problem like this. My hope is that you'll be able to learn from this process and possibly use this knowledge to help you solve your own problems in the future. 

Unfortunately, in the world of higher education, we spend way too much time focusing on narrowly-scoped, previously-solved problems, to allow you to learn in an environment where we know a solution is possible in a set amount of time. In the real world, however, you'll be constantly presented with broadly-scoped, open-ended problems like this one, where you'll have to do some exploration to find possible causes and solutions, and then use your own background and knowledge to determine what solutions, if any, are available.

So, here goes.

### The Error

When you run `pytest` in Example 5 after adding some logging code as directed in the video, you will see many pages of errors printed to the terminal. In my testing, the terminal in Codio printed errors for several minutes before finally stopping. A screenshot of a small portion of those errors is below.

![Errors](/images/410_e5_errors.png)

When this happens, you may be able to use <kbd>CTRL</kbd> + <kbd>C</kbd> to stop the output, but in many cases I simply had to close the terminal tab in Codio.

### What Happened

When I developed this example, I focused on the debugging portion first, and then later added the logging code. However, I neglected to run `pytest` after adding the logging code to my model solution, and did not encounter this error in my initial testing. That was an oversight on my part.  

As you work on this project, you may end up adding the logging code first while still working on debugging the errors in the project. In that case, you will most likely run `tox` or `pytest` to run the unit tests contained in the project with the logging code in place. That will cause the error to appear. As soon as I ran `tox` in my existing model solution, my code presented this error.

### How I solved the problem

The process of finding a solution for this problem went in three phases.

###### Phase 1 - Searching

First, I attempted to Google some of the error message and a few things that I suspected were at play. I already had a hunch that the error itself was coming from the logging code, since I had added that to my model solution last. After reproducing the bug in my solution, I set out to solve it. Some Google search phrases I used:

1. `pytest logging stderr write to closed file` - Including keywords `pytest` and `logging` as well as the `stderr` stream and a bit of the error message.
2. `pytest stream.write(msg) I/O operation on closed file` - adding more details such as the line of code causing the error and the exact error messages.
3. `"pytest" stream.write(msg) I/O operation on closed file` - putting `"pytest"` in quotes will find results that always include that keyword

There were others, but this was the most fruitful. 

###### Phase 2 - Isolate the Error

In several of those searches, I came across a few bug reports on GitHub, specifically within the `pytest` project's repository. Bug reports and discussions on GitHub are usually very fruitful when looking for technical errors that include code and error messages, so I looked into a few of them. 

1. [ValueError: I/O Operation on closed file (#14)](https://github.com/pytest-dev/pytest/issues/14) - this was the first one I found. However, I quickly ruled it out, as it was first posted in 2010 and mainly seemed to use Python 2 instead of Python 3. After scrolling through the discussion, nothing really seemed to fit the situation I was in, so I ignored it and moved on. However, it did reference the next issue...
2. [Improve error message when tests use closed stdout/stderr (capture) (#5743)](https://github.com/pytest-dev/pytest/issues/5743) - this one felt like it was a bit closer. In this report, they discuss the fact that pytest will redirect and close system streams such as `sys.stderr` as part of the test. It was also much more recent, and some of the error messages they were running into were similar to what I was seeing.
3. [pytest 4.5 floods the output with logging errors when logging from atexit handlers (#5282)](https://github.com/pytest-dev/pytest/issues/5282) - similar to the one above, this one was getting closer to the issue I was seeing, though it wasn't an exact match. By reading these three thread, I was starting to get a feel for the crux of the error - if our logger is trying to write to any of the output streams, like `sys.stderr` or `sys.stdout`, then most likely `pytest` would interfere with that and cause this error. Thankfully, the last two issues both referenced this issue...
4. [pytest capture logging error still happening (#5502)](https://github.com/pytest-dev/pytest/issues/5502) - this report had a lot of discussion on it, but pretty much sealed the deal for me. One of the core `pytest` developers posted [a message](https://github.com/pytest-dev/pytest/issues/5502#issuecomment-526348052) that included this text:

> What I believe is happening is:
> 1. pytest changes `sys.stdout` and `sys.stderr` to a buffer while importing test modules.
> 1. If there's user code setting up logging and/or creating a `logging.StreamHandler` at the import level, it will attach itself to pytest's buffer.
> 1. When pytest is about to finish the test session, it will restore `sys.stdout` and `sys.stderr` to the original values, and close the "capture" buffer.
> 1. Here the problem happens: if any message is emitted at this point, the `StreamHandler` will try to attach itself to the buffer, hence the error.

So, we've now found what we suspect is the error. All we have to do is figure out how to resolve it. 

###### Phase 3 - The Fix

Unfortunately, [issue #5502]((https://github.com/pytest-dev/pytest/issues/5502)) is still open as of this writing, so we needed a way to get around this error. With some quick testing, I was able to confirm the error went away if I removed the `StreamHandler` from the existing logging code. So, I decided that the best way to deal with this was to find some way to disable logging while the code is running as part of a unit test. This is a somewhat common, though discouraged, trick in programming. Ideally you don't want to hide any code from the unit tests, but in some instances you want to make sure that the unit tests don't actually change live data, such as the actual database used by this program. So, you can "protect" the code that connects to the database and make sure it cannot run as part of a unit test.

A quick Google search for `determine if code is running under pytest python` quickly lead me to a [StackOverflow post](https://stackoverflow.com/questions/25188119/test-if-code-is-executed-from-within-a-py-test-session) discussing this very issue. Great! I had quickly found a pretty good resource that might lead me to a solution.

Within the discussion, there are a few solutions suggested, and helpfully ranked by the upvotes from other users.

1. [Solution 1](https://stackoverflow.com/a/44595269) - simply check `if "pytest" in sys.modules:` since the `pytest` application will always be loaded when running a test. This solution seemed pretty simple and didn't have many obvious side effects, provided your application didn't load `pytest` as part of its normal execution. 
2. [Solution 2](https://stackoverflow.com/a/25188424) - a solution that points to a section of the [pytest Manual](http://doc.pytest.org/en/latest/example/simple.html#detect-if-running-from-within-a-pytest-run) that shows the preferred way of doing this. In short, we place some code in the `conftest.py` file, which is only executed as part of a unit test, to update a value in our code, and then check that value where needed. This looks promising, and is probably the correct answer that would work in all cases, but also requires significantly more code and adds a structural dependency between our code and the `conftest.py` file.
3. [Solution 3](https://stackoverflow.com/a/58866220) - a third solution suggests checking for the existence of the `PYTEST_CURRENT_TEST` environment variable, which is set when pytest is running. This may also work, but has the side effect of being outside of our control - any other application on our system could also set that variable, including another instance of `pytest`, so it may not work as reliably as the other two. 

In the end, I chose [Solution 1](https://stackoverflow.com/a/44595269), and updated the code at the top of my `main()` method in `TicTacToe.py` to the following:

```python
import sys

# get the root logger
logger = logging.getLogger()
# disable if pytest is running
if "pytest" in sys.modules:
    logger.disabled = True
```

That code will simply load the logger, and immediately check if the `"pytest"` module is loaded. If so, it will disable the logger globally in my program.

An alternative solution would be to just disable the `StreamHandler` and allow the `FileHandler` to remain enabled, but I felt that logging from unit tests is not helpful and chose to disable it entirely.

### Summary

I hope this discussion is helpful - I've found that sometimes the best opportunities for [cognitive apprenticeship](https://en.wikipedia.org/wiki/Cognitive_apprenticeship) happen directly as a result of the class, so I wanted to take this chance and share a bit of my own problem solving process here. 

If you have any follow up questions about this, please let me know!
