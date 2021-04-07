---
title: Static type ecosystem - python types & Typescript
type: post
readtime: true
author: [kurianbenoy]
tags: [code]
---

Most of languages which run dynamically and is able to point just a few syntax errors. Yet almost most of the errors which programmers face are probably type errors or run time errors. This is where the need of static code analysis comes from. In popular languages like JavaScript and Python which is being used by millions of developers this makes it more prone to writing bad code with potential for errors.

This is where tools for static code analysis becomes important and necessary. It's a necessary toolkit for any amateur programmer and helps in providing strict checking and help write programmers write fewer buggy code. In both Python and JavaScript there are a few tools which can help in providing static code analysis.

In Python world, the standard library comes with typing modules and type hints. Python types are implemented as a series of PEP(Python enhancement proposals) and in latest python version i.e. 3.9 it provides run time support for Python typing which doesn't require importing typing every time. With the latest PEP for type hinting generics in standard collections   you can now use built-in collection types such as list and dict as generic types instead of importing the corresponding typing module.

```
def greet_all(names: list[str]) -> None:
    for name in names:
        print("Hello", name)
```

Check out more in below links 👇:
- https://docs.python.org/3/library/typing.html 
- https://youtu.be/H5CnZQDKfhU
- https://docs.python.org/3/whatsnew/3.9.html

For JavaScript world, there  is Typescript which is a very mature ecosystem. It is being build by Microsoft and is a static type-checker which provides greater clarity on top of things build on JavaScript. When using typescript, almost 90% it is mainly giving type interference to the functions and values being passed. 

I will highly recommend you to check one of the Typescript get started guides and start reading the Typescript handbook as well. It's widely adopted in JavaScript world and is used in various companies. Check out the below links  👇:

- https://www.typescriptlang.org/docs/handbook/intro.html#get-started
- https://www.typescriptlang.org/docs/handbook/intro.html
- https://www.typescriptlang.org/


**Three Links for this week 👉:**

- Understanding your parents - https://aryamurali.com/2019/04/14/understanding-your-parents/
- what machine learning can teach about life - https://youtu.be/EE1u1dbPZWQ
- do more of scary decisions - https://www.susanshu.com/tough-decisions-do-what-scares-you
