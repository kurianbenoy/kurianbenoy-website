---
aliases:
- /2021/04/07/statictyping
author:
- kurianbenoy
categories:
- code
date: '2021-04-07'
layout: post
readtime: true
title: Static type ecosystem - python types & Typescript

---

Many of the popular languages like Javascript and Python which are being used by millions of developers are dynamically typed language.
That is the code is check for correctness, type of variables only during the run times. This makes millions of developers prone to writing code with potential errors.

Most languages run dynamically and can point to just a few syntax errors. Yet almost most of the errors which programmers face are probably type errors or run time errors. This is where the need for static code analysis comes from. 

This is where tools for static code analysis becomes important and necessary. It's a necessary toolkit for any amateur programmer and helps in providing strict checking and help write programmers write fewer buggy code. In both Python and JavaScript, there are a few tools that help in providing static code analysis.

In the Python world, the standard library comes with typing modules and type hints. Python types are implemented as a series of PEP(Python enhancement proposals) and in the latest python version i.e. 3.9 it provides run time support for Python typing which doesn't require importing typing every time. With the latest PEP for type hinting generics in standard collections, you can now use built-in collection types such as list and dict as generic types instead of importing the corresponding typing module.

```
def greet_all(names: list[str]) -> None:
    for name in names:
        print("Hello", name)
```

Check out more in the below links 👇:
- https://docs.python.org/3/library/typing.html 
- https://youtu.be/H5CnZQDKfhU
- https://docs.python.org/3/whatsnew/3.9.html

For the JavaScript world, there is Typescript which is a very mature ecosystem. It is being built by Microsoft and is a static type-checker that provides greater clarity on top of things build on JavaScript. When using typescript, you can find potential bugs and support for almost 90% of common types used. For the rest of the cases, you can create interfaces to write associate types.

I will highly recommend you to check one of the Typescript get started guides and start reading the Typescript handbook as well. It's widely adopted in the JavaScript world and is used in various companies. Check out the below links  👇:

- https://www.typescriptlang.org/docs/handbook/intro.html#get-started
- https://www.typescriptlang.org/docs/handbook/intro.html
- https://www.typescriptlang.org/


**Three Links for this week 👉:**

- [Arya provides tips about Understanding your parents and making them aware of your decisions](https://aryamurali.com/2019/04/14/understanding-your-parents/)
- [TalkPython host, Michael Kennedy, and Eugene have a slightly more philosophical chat on the latest episode where they discussed about life lessons from machine learning](https://youtu.be/EE1u1dbPZWQ)
- [Susanshu encourages us to say yes to more scary decisions](https://www.susanshu.com/tough-decisions-do-what-scares-you)
