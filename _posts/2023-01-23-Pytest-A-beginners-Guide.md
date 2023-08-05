---
layout: post
title:  "Pytest - A Guided Series - Part 1"
author: grim
categories: [ Python, Coding ]
comments: True
image: assets/images/PythonLogging/xxx
tags: [featured]
---

Testing is a major inevitable part of Software development. As the technology and standard gets updated every now and then, testing for such complex codes demanded a framework to ensure Software's quality. There are 'n' number of testing frameworks widely available in existence, but `Pytest` is a framework that proved to be simple yet handles testing complex software.

The beauty of Pytest is, you don't need to spend much time on understanding or coding the pre-requisites of collecting the test cases.

Major advantages of Pytest.

- Collects tests automatically. Naming of the test filename to be in format test_*name*.py or *name*_test.py and the test function to be named in the similar manner(test_*case name* or *case name*_test).
- Test validation is more staright forward & handled with the `assert` statement. 
- Setup and teardown operation handlings are more simpler with the help of fixtures.
- Fixtures provide more control. We can resolve dependencies or fetch a data which are needed for the test case even before test case starts execution.
- Parametrizing your test case prevents creating multiple test cases for different range of inputs and their respective results.
- Tagging test cases, skipping test cases, marking test cases with attributes are few of the additional things that adds more value.
  
These are some of the features that make pytest stand out of the other frameworks. It doesn't means that other frameworks are not effective/pytest is the best among all, rather it is very easy to start working with it and besides being simple to work, it can handle complex test scenarios.

# Pytest - a simple code example:

First we will start with the installation of pytest via cmd.

```shell
pip install pytest
pytest --version
```


```shell
# file test_add.py

def addition(a,b):
    return a+b

def test_add():
    assert addition(3, 3) == 5

```

You can execute this with `pytest test_add.p` command and you can see the below traces.

![Wireshark]({{ site.baseurl }}/assets/images/pytest/1.png)

From the traces you can see that one test case got **collected**. And it failed with an **AssertionEror**, because `3+3 != 5`. And at the end it shows a summary of the test session with the time taken for execution i.e, `1 failed in 0.19 seconds`.

So, we have written and tested our function `addition(a,b)`. In real world scenario/applications, tests are kept under separate directory from the source code - usually under a directory named test.

**Note - when test cases are written to be in a module i.e in a test class, the naming of the class to be done  as `Test_*` If the prefix of the class is not Test, then pytest skips the class**

Like all other test suites, `.` means test case has passed and `F` means test failed with pytest.

# Master the pytest CLI

 - Exiting on encountering the failure
    `pytest -x` this would stop the execution after facing the first failure.

 - Exiting after encountering 'N' number of failures
    `pytest --maxfail = 3` this stops the execution after facing three failures.

   To execute test cases based on name i.e lets say we have 5 test cases that has common string 'add' that validates a part of code, we can exeute all the 5 test cases by referencing them with below command,
    `pytest -k add` 

   Running a particular test case,
    `pytest test_add.py::test_function`

   If we have tagged the test cases with markers(we will see about marking in further posts, but for understanding this is similar to tagging)
    `pytest -m marker_name` - runs the test cases that are marked with specific name alone.
    The string mentioned in the **marker_name** acts like a condition. For instance, if we want to test cases marked with tag1 and not tag2, we can mention this in pytest command as, `pytest -m "tag1 and not tag2`

   There are lot of command line arguments for pytest. If we mention `pytest --collect-only`, it collects the test cases alone and no test execution takes place.

   Likewise adding `noconftest` with the pytest commands tells to not use/collect any conftest.py files. There are lot of CLI options available. To explore more about supported CLI arguments and other additional features, feed `pytest --help` in your Command prompt.

Now that we have glanced about the pytest framework, we will start to see its features to unveil more.

# Fixtures

Fixtures in pytest can be used for various purposes. On laymen terms, fixtures are again some functions, that will do a certian task. We can use this to fetch any data that are needed for the test case even before the test execution starts. In more simple terms, fixtures are like decorators and are passed to test functions like positional arguments.

They allow you to manage and share data, configuration and setup/teardown logic in your tests. Fixtures are defined with the `@pytest.fixture` decorator and can be referenced as function arguments in your test functions. 

We will cover this with a small example,

![Wireshark]({{ site.baseurl }}/assets/images/pytest/2.png)

here, we can created a function that holds a list. And we decorated this function as fixture with `@pytest.fixture`. Hence when pytest encounters this code segment, this will be treated as fixtures.

Let's use the fixture in our test function by passing it as an argument.

![Wireshark]({{ site.baseurl }}/assets/images/pytest/3.png)

On running the code, you can see that the fixture fetches the value of the list and assertion passes on the same.

![Wireshark]({{ site.baseurl }}/assets/images/pytest/4.png)

Fixtures are mostly used to execute preconditions or provide data for tests to run. They allow developers to encapsulate common setup and teardown code, leading to more maintainable and modular test suites.

# Conftest

For smaller projects, we can place the fixtures within the same test file. But when more number of fixtures, it is better to organize them in a seperate file. This is where `conftest` comes into picture.

By placing fixtures in a conftest.py file at the root of the test directory, pytest automatically discovers and makes these fixtures available to all test files in the same directory and its subdirectories.

![Wireshark]({{ site.baseurl }}/assets/images/pytest/5.png)

Execution of this will fetch same result as above.

The magic of conftest.py lies in its ability to create a hierarchy of fixtures, with local fixtures defined within specific test files, and shared fixtures residing in the conftest.py. This organization promotes reusability and ensures a clean separation between test logic and setup code, fostering easier collaboration within teams and enhancing code readability.

In short, in this post we have seen about 
1. Pytest and its efficiency
2. How to write a simple test case and some CLI tips
3. Fixtures and its purpose
4. Conftest and its usage.

Hope you find this useful. We will explore about more of the Pytest in upcoming posts.
