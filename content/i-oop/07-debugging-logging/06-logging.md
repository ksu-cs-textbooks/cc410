---
title: "Logging"
weight: 30
pre: "6. "
---

The last major concept we'll introduce around debugging is the use of a formal **logger** in our code. A logger allows us to collect debugging information throughout our program in a way that is lightweight, highly configurable, and surprisingly easy to use. Both Java and Python include some standard ways to create a simple log file.

{{< tabs >}}

{{% tab name="Java" %}}

###### Java Logger

The Java language includes the [Logger](https://docs.oracle.com/javase/8/docs/api/java/util/logging/Logger.html) class that can be used to create a logger within the code. Then, we can define what [Level](https://docs.oracle.com/javase/8/docs/api/java/util/logging/Level.html) of items we'd like to log, and how we'd like to store it. Typically, it'll either be stored in a file or just printed to the terminal.

Here's a very simple example of using a logger in our code:

```java
import java.util.logging.FileHandler;
import java.util.logging.Level;
import java.util.logging.Logger;

public class LogTest {
    
    
    private final static Logger LOGGER = Logger.getLogger(Logger.GLOBAL_LOGGER_NAME);
    
    public static void main(String[] args){
        // Levels INFO, WARNING, and SEVERE will be printed
        LOGGER.setLevel(Level.INFO);
        // Add a file logger
        LOGGER.addHandler(new FileHandler("log.xml"));
        LOGGER.info("This is an info log.");
        LOGGER.warning("This is a warning, but not too bad.");
        LOGGER.severe("This is a severe message, THIS IS BAD!");
    }
}
```

When this program is executed, we see the following output in the terminal:

```
Jan 21, 2021 10:14:46 PM LogTest main
INFO: This is an info log.
Jan 21, 2021 10:14:46 PM LogTest main
WARNING: This is a warning, but not too bad.
Jan 21, 2021 10:14:46 PM LogTest main
SEVERE: This is a severe message, THIS IS BAD!
```

We should also see a new file named `log.xml` in our current working directory, which contains an XML version of the log information printed to the terminal:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE log SYSTEM "logger.dtd">
<log>
<record>
  <date>2021-01-21T22:14:46</date>
  <millis>1611267286120</millis>
  <sequence>0</sequence>
  <logger>global</logger>
  <level>INFO</level>
  <class>LogTest</class>
  <method>main</method>
  <thread>1</thread>
  <message>This is an info log.</message>
</record>
<record>
  <date>2021-01-21T22:14:46</date>
  <millis>1611267286139</millis>
  <sequence>1</sequence>
  <logger>global</logger>
  <level>WARNING</level>
  <class>LogTest</class>
  <method>main</method>
  <thread>1</thread>
  <message>This is a warning, but not too bad.</message>
</record>
<record>
  <date>2021-01-21T22:14:46</date>
  <millis>1611267286139</millis>
  <sequence>2</sequence>
  <logger>global</logger>
  <level>SEVERE</level>
  <class>LogTest</class>
  <method>main</method>
  <thread>1</thread>
  <message>This is a severe message, THIS IS BAD!</message>
</record>
</log>
```

Of course, if we change the level to `Level.SEVERE`, then only the last message will be printed. We can even turn the log off completely. So, in this way, we can include the logging messages in our code wherever they are needed, and then configure the logger to only print the messages we want, or no messages at all. This is **much** more flexible than our earlier method of just using print statements, since we don't have to worry about removing them from our code later on.


{{% /tab %}}

{{% tab name="Python" %}}


###### Python Logger

The Java language includes the [logging](https://docs.python.org/3.9/library/logging.html) library that can be used to create a logger within the code. It includes several common [Logging Levels](https://docs.python.org/3.9/library/logging.html#logging-levels) that we can use, and we can easily configure it to log items to the terminal or a file.

Here's a very simple example of using a logger in our code, adapted from the [Logging HOWTO](https://docs.python.org/3.9/howto/logging.html) in the Python documentation:

```python
import logging
import sys

class LogTest:
    
    @staticmethod
    def main():
        # get the root logger
        logger = logging.getLogger()
        # set the log level
        logger.setLevel(logging.INFO)
        # add a terminal logger
        stream_handler = logging.StreamHandler(sys.stderr)
        stream_handler.setFormatter(logging.Formatter("%(asctime)s - %(name)s\n%(levelname)s: %(message)s"))
        logger.addHandler(stream_handler)
        # add a file logger
        file_handler = logging.FileHandler("log.txt")
        file_handler.setFormatter(logging.Formatter("%(asctime)s - %(name)s\n%(levelname)s: %(message)s"))
        logger.addHandler(file_handler)
        logger.info("This is an info log.")
        logger.warning("This is a warning, but not too bad.")
        logger.critical("This is a critical message, THIS IS BAD!")
                          
if __name__ == "__main__":
    LogTest.main()
```

When this program is executed, we see the following output in the terminal:

```
2021-01-21 22:33:53,224 - root
INFO: This is an info log.
2021-01-21 22:33:53,224 - root
WARNING: This is a warning, but not too bad.
2021-01-21 22:33:53,225 - root
CRITICAL: This is a critical message, THIS IS BAD!
```

We should also see a new file named `log.txt` in our current working directory, which contains the same content.

Of course, if we change the level to `logging.CRITICAL`, then only the last message will be printed. We can even turn the log off completely. So, in this way, we can include the logging messages in our code wherever they are needed, and then configure the logger to only print the messages we want, or no messages at all. This is **much** more flexible than our earlier method of just using print statements, since we don't have to worry about removing them from our code later on.

{{% /tab %}}

{{< /tabs >}}

## From Print Statements to Log Statements

Now that we know how to create a logger for our program, it should be really simple to convert any existing print statements to logging statements. Then, in the main class of our program, we can simply configure the desired level of logging - we would typically turn it completely off or only allow severe errors to be logged when the application is deployed, but for testing we may want the log to include more information. 

This gives us a quick and flexible way to gain information from our code through the use of logging. 
