---
layout: post
title:  "Debugging in Python - Logging module"
author: grim
categories: [ Python, Coding ]
comments: True
image: assets/images/PythonLogging/BG.png
tags: [featured]
---

Whenever we do programming, `print` statements are very helpful for debugging/conveying the code status to the user. Let's say now our code is in production and all these print statements would be redundant. We need to comment them out if not needed. We cannot filter the print statements as high priority or so on. We also might need these debugging information in a file format.

The in-built python `logging` module is the one-stop solution to fulfill the above said criteria and even more in our python code.

# Installation - is it needed?

The logging module comes in-built with the python packages. Hence, it is not needed to separately install it again.
Anyhow, installation can be done with the command `pip3 install logging`.

So now let's start learning about this module!

Logging module has five different logging types with increasing severity level 
- Debug
- Info 
- Warning
- Critical
- Error

By default, the severity level is Warning. Let us see a small example to understand this,

![Logging]({{ site.baseurl }}/assets/images/PythonLogging/1.png)

The default logging level is "warning". Debugging statements of this level and above levels will be considered and rest of them will be ignored.

![Logging]({{ site.baseurl }}/assets/images/PythonLogging/2.png)

The default debugging statements got three segments. `Logging level : name: message`.

We can tweak the default behavior of the logging module. 

## Tweaking the Logging module

In order to use the logging module to its fullest, it's vital to have control over the method, 
`basicConfig(**kwargs`). Besides, to tweak the behavior of default logging behavior, we need to pass certain arguments as needed.

First, will have a short look at few arguments that this method support and then will start with how we can save the log file.

Changing logger level - `level`
Saving log in a file(name of the file passed in this argument) -  `filename`
Mentioning the mode of handling this file - `filemode`
Modifying the format of debugger statement - `format`

### Saving log file

![Logging]({{ site.baseurl }}/assets/images/PythonLogging/3.png)

Running this would have no signs on output console. But, you can see a new file has been created with name `debuglog.log` gets created in the current directory.

You can also choose to append the debug logs that are collected from multiple runs by mentioning `filemode` as `a (a - append)`

- Changing the default logging mode

![Logging]({{ site.baseurl }}/assets/images/PythonLogging/4.png)

By mentioning the logging level in `level` argument, we can modify the default 'Warning' level of logging. Note that the level mentioned is in **CAPITAL letters**, rather than the usual way of representation. From this you can understand that both are different type of parameters. In background, "logging.DEBUG" will correlate to an enum value that represents `Debug level - logging.debug()`.

-  Changing the format of debugging message

We saw that all the logging messages were recorded with this three segments and in order - Level : Name : Message.
We can modify this format to a different sequence. 

```shell
logging.basicConfig(level = logging.INFO, format = '%(message)s - %(name)s - %(levelname)s')
logging.warning("a warning message")
logging.info("just a info message")
logging.error("alert. an error message is recorded")
```

Output for this code will be,
```shell
a warning message - root - WARNING
just a info message - root - INFO
alert. an error message is recorded - root - ERROR

** Process exited - Return Code: 0 **
Press Enter to exit terminal
```

We can take control of the format by removing certain fields or by adding certian fields. The most useful one is adding timestamp to our log trace, which makes it more meaningful.

```shell
logging.basicConfig(format = '%(asctime)s - %(message)s', datefmt = '%d-%b-%y %H:%M:%S')
```
Above modification in basicConfig method prints the logging time in the modified format,

```shell
18-Oct-22 02:39:30 - a warning message
18-Oct-22 02:39:30 - alert. an error message is recorded

** Process exited - Return Code: 0 **
Press Enter to exit terminal
```

- Using F-strings with logging

We can include variables in our logging statements also. A simple demonstration is given below.

```shell
import logging

i = 5
while(i<10):
   cycle_counter = 1
   logging.info(f"We are in the cycle - {cycle_counter} now")
   cycle_counter = cycle_counter + 1
   i = i+1
```

The concepts that we have covered in this post is enough to set up a logging functionality for a real time application. We will cover deeper horizons of logging module such as capturing Exceptions, working with loggers and handlers etc in our further post.

Hope the information shared in this post is helpful! You can refer the documentation for deeper understanding.
Python documentation of the logging module can be found [here](https://docs.python.org/3/library/logging.html)