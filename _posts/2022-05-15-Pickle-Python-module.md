---
layout: post
title:  "Pickle your Python Code"
author: grim
categories: [ Python, Coding ]
comments: True
image: assets/images/pickle/pickle.png
tags: [featured]
---

Pickling is one of the modules in python that helps us in serialization and de-serialization process.
In this post, we are going to talk in detail about this module and glance on some other related modules.

# What is Serialization ?

Serialization is the process of converting the data to a linear format, which can be shared to some other instances(code) or even to some other computer via network.
For instance, you might need to save your state of code(value of objects after execution), just like we do in Video games. Such that you can resume your code execution from the instance where you left. 

As we are speaking in "Python" now, we shall see this with an example code for easier understanding.

```shell
class test():
	t_int = 10
	t_list = [ 1, 2, 'hello']
	
t_object = test()

```
Above is a simple code that has a class named `test` with two members. With pickle module we can convert this object structures(in python datatypes are handled as objects) into a linear stream of data in byte format.

```shell
import pickle
class test():
	t_int = 10
	t_list = [ 1, 2, 'hello']
	
t_object = test()
pickle_string = pickle.dumps(t_object)
print(pickle_string)
```

On executing of the above code, you can see the ```b'\x80\x04\x95\x18\x00\x00\x00\x00\x00\x00\x00\x8c\x08__main__\x94\x8c\x04test\x94\x93\x94)\x81\x94.``` binary conversion.

Basically, this is what the pickling module does. With this stream of converted data, we can transmit them via a network or can be used for saving the instances of the objects. The use cases are only limited to one's coding needs . Now let's dig more about this module.

Official Documentation - click [here](https://docs.python.org/3/library/pickle.html)

In python, we can accomplish the serialization process in number of ways. There are three major modules, 

1. Marshal 
2. Pickle
3. JSON 

that supports us to do serialization. We will take about these towards the end. Noe lets see about the pickle module.

# Pickle module:

Pickle provides 4 methods for serialization and de-serialization process. 

- pickle.dump()
- pickle.dumps()
- pickle.load()
- pickle.loads()

# Pickling or Serialization or flattening:

With pickling, we convert the complex object structures of our code either in to a file or a string. `pickle.dump` saves the input object in a file(binary format). For this, we need to create and open a file in `wb` format(write in binary format), as given below,

```shell
	with open("\usr\bin\code_state", "wb") as state:
	pickle.dump(object, state)
```

Whereas, `pickle.dumps()` returns a string, which can be easily viewed with a `print` command.

![Pickle]({{ site.baseurl }}/assets/images/pickle/pickle1.png)

## Parameters in Serialization:

`pickle.dump(obj, file, protocol=None, *, fix_imports=True, buffer_callback=None)`

**Object** - refers the object to be serialized.
**file** - denotes the file where serialized data need to be written
**protocol** - there are six protocol version supported in pickle module now. 
The protocol version affects the way of serialization to be done and also compatibiity to the python version.

  - *Version 0* - Lowest version. Outputs in Human readable format.
  - *Version 1* - Compatable with older versions of python. Outputs in Binary format.
  - *Version 2* - was introduced with Python version 2.3.
  - *Version 3* - added with Python 3.0. This is the default pickle protocol version for 
     python 3.0   3.7 versions. Also, serialization done with this protocol cannto be deserialized by Python 2.x versions.
  - *Version 4*- introduced with Python 3.4. Extended support for wider range of object types 
     for pickling. Default version from Python 3.8.
  - *Version 5* - added with Python 3.8. Added support for out-of-band data and increased speed 
     for in-band data.

**Fix imports** - if fix imports is True and proocol version is less that 3, pickle will try to map the imports names to the old Python 2.x module names. Such that the pickled data can be unpickled for Python 2.x versions too.

**buffer_callback** - by default False. This is introduced with python 3.8 and is used when there is a need to transfer a huge serialized data.

`pickle.dumps()` has no file parameter, as it returns a string.

The following types can be pickled:

  * None, True, and False;
  * integers, floating-point numbers, complex numbers
  * strings, bytes, bytearrays
  * tuples, lists, sets, and dictionaries containing only picklable objects
  * functions (built-in and user-defined) defined at the top level of a module (using def, 
	  not lambda)
  * classes defined at the top level of a module

Note the few python features are not pickelable. For e.g, if your code has a `lambda function`, then directly attempting to pickle would throw an exception.
A work around for this is using `__getstate__` and `__setstate__` function. We have to manually delete the attributes that cannot be pickled.
Another workaround would be, using third party modules like `dill` to extend pickling capacity. 

Eventhough with these additional work arounds, not all python fields can be pickled. Things such as network connection or database connection related programs cannot be pickled as they are much more complex.

# Unpickling or Deserializaion:

Unpickling of pickled objects can be easily done with `pickle.load()`, to unpickle a file, or with `pickle.loads()` to unpickle a pickled string.

## Optional parameters in Unpickling:

The parameters in unpickling mostly defines how to unpickle data generated from Python 2.x.

If **fix_imports **is true, pickle will try to map the old Python 2 names to the new names used in Python 3.

The **encoding** and **errors** tell pickle how to decode 8-bit string instances pickled by Python 2; these default to ‘ASCII’ and ‘strict’, respectively. The encoding can be ‘bytes’ to read these 8-bit string instances as bytes objects. Using encoding='latin1' is required for unpickling NumPy arrays and instances of datetime, date and time pickled by Python 2.

These are the major features of pickle module. Now let us look in short on other alternates for serialization.

# Marshal 

```shell
import marshall
```
This is an old/ancient package. We can use this with our latest python version too. But it is not advised to do so, due to non-backward compatibiity and the fact that it is used by the interpreter to decode .pyc files. 

# JSON

```shell
import json
```
JSON is the widely known format and the python module provides platform independent form of serialization and deserialization. Besides, we can accomplish this with XML format files too. One major difference is that JSON is human-readable format. Also when compared to pickle module, JSON is a bit slower.

# **Thing to be aware of:**

While using Pickle module, there are plenty of open loops which could terrible impact. In its official page also, it has been mentioned ***not to deserialize data from unknown sources***. This could potentially break your system or open door for hacking.

Just in case, if you need your serialized data to be secure, we can include the usage of **hmac** module. This prevents unwanted tampering in pickled data.
Also using zipping modules, reduces the size of pickled data upto some extent.

**Regardless, unpickling data from unknown source is strictly not advised.**


With this brief coverage, we reach the concusion. We have seen about how to serialize and deserialize the python objects, alternate modules for the same, and the problems that lies in this module.

Hope the information I have gathered and conveyed in this post is useful!

Do explore this package and share the knowledge. If you have any comments/questions leave a message below.