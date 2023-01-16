---
aliases:
- /2021/01/21/pythonformatting
categories:
- coding
- Python
date: '2021-01-21'
layout: post
readtime: true
title: 3 Python libraries to make your code more pythonic

---

Python is one of the most used programming libraries. It is important to follow proper decorum while coding
in Python by following rules such as [PEP8](https://pep8.org/). Today I am going to introduce a few libraries
for formatting and making your code prettier in Python.

### black

It is an uncompromising python code formatter. The best thing about black is the project is built with a core goal 
to avoid any conflicts in the python coding formats over the time and act as a unifying interface for code formatting.
To use black, it's pretty easy:

```black {source_file or directory}```

By default, it's a bit intentional by only allowing double-quoted string, with a maximum line number by default set as 88 and
follow some more opinions which are PEP8-compliant. black is widely used in the python community. To check more options
about black, [look at the documentation](https://black.readthedocs.io/en/stable/). Thanks to ambv & PSF volunteers for this awesome library.

### isort

isort is a python library for sorting your imports in python. According to PEP8, there are few recommendations to order
when importing libraries:

1. standard library imports
2. related third party imports
3. local application/library specific imports

isort contains 12 possible settings for multiple line imports. Also, you can add comments, change the
import order and remove or append imports with the various setting in isort.

[Documentation](https://pycqa.github.io/isort/)

The default configuration of isort and black has a few style conflicts, which we will cover how to fix
in the latter part of this article.

### pip-chill

pip-chill is a library for fixing the ugly output of `pip-freeze` which lists all the packages and associated
sub-packages. Most of the people create their requirements based pip freeze output. This is where pip-chill 
to list just the packages you have installed with the command `pip-chill`. 

[Documentation](https://pip-chill.readthedocs.io/en/latest/)


### Inter-operability with black and isort

Let's look at how we can make both black and isort compatible with each other. The compatibility crisis can be solved by
two approaches:

**1. Using Scripts to run both black and isort**

*formatter.bat*
```
@ECHO OFF
isort --profile black .
black -S -t py38 .
ECHO Complete formatting code with black and isort
```

*formatter.sh*
```
#!/bin/bash
isort --profile black .
black -S -t py38 .
echo "Complete formatting code with black and isort"
```

**2. Integrating with pre-commit**

pre-commit is an awesome git hook to identify simple issues and autoformatting the code with black and isort before the project
is being run. Install pre-commit and create a .pre-commit-config.yaml file for setting up formatting with black and isort.


*.pre-commit-config.yaml*
```
repos:
-   repo: https://github.com/psf/black
    rev: 19.3b0
    hooks:
    -   id: black
-   repo: https://github.com/pycqa/isort
    rev: 5.6.4
    hooks:
      - id: isort
        args: ["--profile", "black", "--filter-files"]
```

Then run the git commit and the file gets added to git only if the tests for both black and isort are passed.

~ Kurian Benoy

