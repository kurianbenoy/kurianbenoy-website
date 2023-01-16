---
aliases:
- /2020/11/16/Various_python_distributions
date: '2020-11-16'
layout: post
title: Various Python Distributions

---

## Various Python Distributions

Python is infamous for being slow usualy. A lot of people with other language backgrounds complain Python is
notoriously slow. And to be honest there is some merit in there argument too and some may have heard about GIL
being the issue causing this lock mechanism. There is always a convenience vs speed drift being discussed at
the core of issue. Yet most of this issue is always talked about CPython, which is a variant of Python developed
by PSF and maintained by various Python core developers.


Yet it's not just CPython alone. There are various other distribution implementations of Python.
Even though for beginners and almost 90% percentage of folks out there might be using CPython
for their use case. I created a twitter poll recently and almost 74% have never used any other Python
distribution other than CPython.

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Have you used any Python Distribution other than CPython(normal Python)?</p>&mdash; Kurian Benoy (@kurianbenoy2) <a href="https://twitter.com/kurianbenoy2/status/1326523758606131200?ref_src=twsrc%5Etfw">November 11, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

So let's look at some of  distributions out there in the Python world like which are build for specific purposes like:

### IronPython

Iron Python is a python written for .NET platform. It was used in lot of .NET libraries libraries where we
need a glue language without the boiler plate then IronPython is a good fit. Also since it did not have a
GIL, it could multithread quite effectively. Used in Tibco Statistica as default Python version.[Thanks @Arocks](https://twitter.com/arocks/status/1327497282648907776)

## Cython

It's a version which is responsible for all weird Python errors like missing headers file if you
have received it. It's widely used and mature with numpy support. It requires thorough knowledge of
C. 

You need to write your operators and types in C like fashion with cint and others as example. The obvious
advantage on writing your code in Cython is it runs faster in almost 90% of the cases.

## PyPy

A Python based interpreter, which is being used in competitive coding a lot. It also more faster and
supports all the features of Python standard. Guido recommends using PyPy for speeding python code

According to PyPy docs:

PyPy has been used to mean two things. The first is the RPython translation toolchain for generating interpreters for dynamic programming languages. And the second is one particular implementation of Python produced with it. Because RPython uses the same syntax as Python, this generated version became known as Python interpreter written in Python. It is designed to be flexible and easy to experiment with.

There are even more which Victor Stenner mentioned in his Pycon India talk. The most commonly used are Cython which
cause C like errors in python usually.

I can promise to update this article soon.

