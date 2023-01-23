---
layout: post
title:  "Pytest - A beginners Guide Series - Part 1"
author: grim
categories: [ Python, Coding ]
comments: True
image: assets/images/PythonLogging/xxx
tags: [featured]
---

Testing is a major inevitable part of Software development. As the technology and standard gets updated every now and then, the testing for such complex codes demanded a framework to ensure the Software's quality. There are 'n' number of testing frameworks widely available in existence, but `Pytest` is one such framework that proved to be simple yet ensures to hanlde and test ay complex software.

The beauty of Pytest is, you don't need to spend much time on understanding or coding the pre-requisites of collecting the test cases.

Major advantages of Pytest.

- Collects tests automatically. Naming of the test filename to be in format test_*name*.py or *name*_test.py and the test function to be named in the similar manner(test_*case name* or *case name*_test).
- Test validation is more decided & handled with the `assert` statement. And no need to define anything more on the `assert`. 
- Setup and teardown operation handlings are more simpler with the help of fixtures.
- Fixtures provide more control. We can resolve dependencies or fetch a data which are needed for the test case even before test case starts execution.
- Parametrizing your test case prevents creating multiple test cases for different range of inputs and their respective results.
- Tagging test cases, skipping test cases, marking test cases with attributes are few of the additional things to be considered.
- Test cases can be written as functions are within a module.
  
These are some of the features that make pytest stand out of the other frameworks. It doesn't means that other frameworks are not effective/pytest is the best among all, rather is very easy to start working with it and besides being simple to work, it can handle evaluating complex scenarios too.

# Pytest - a simple code example:

First we will start with the installation of pytest via cmd.

```shell
pip install pytest
pytest --version
```


```shell
# inside file test_add.py

def addition(a,b):
    return a+b

def test_add():
    assert addition(3, 3) == 5

```

Execute this with `pytest test_add.p` command and you can see the below traces.

< image here pytest--1>

From the traces you can see that one test case got **collected**. And it fails with an **AssertionEror**, because `3+3 != 5`. And at the end it shows a summary of the test session with the time taken for execution i.e, `1 failed in 0.19 seconds`.

Thus we have written and tested our function `addition(a,b)`.
Here, I had the file name saved as main.py. But pytest is robust enough to collect and recognize the test cases alone with `test_*` or `*_test` naming sequence. In real world scenario/applications, tests are kept under separate directory from the source code - usually under a directory named test.

**Note - when test cases are written to be in a module i.e in a test class, the naming of the class to be done  as `Test_*` If the prefix of the class is not Test, then pytest skips the class**

Like all other test suites, `.` means test case has passed and `F` means test failed with pytest.



