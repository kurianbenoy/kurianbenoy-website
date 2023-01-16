---
aliases:
- /c/python/2019/09/17/Precision_values
author: Kurian Benoy
categories:
- python
- c
date: '2019-09-17'
layout: post
title: Float/decimal points precision in C++ and python3

---

Manipulating and printing outut format with specific no of digits in precision
is necessary for many cases. This kind of questions are sometimes asked in Coding 
interviews and you find in weird case were you know answer, but don't know to 
format the output.

In C++ Float precision is implemented by the header `<iomanip>`. Note std::fixed input, will extend the digits even if
it does not exist

```
#include <iostream>     // std::cout, std::fixed
#include <iomanip>      // std::setprecision

int main () {
  double f =3.14159;
  std::cout << std::setprecision(5) << f << '\n';
  std::cout << std::setprecision(9) << f << '\n';
  std::cout << std::fixed;
  std::cout << std::setprecision(5) << f << '\n';
  std::cout << std::setprecision(9) << f << '\n';
  return 0;
}
```

While in languages like Python it follows Float point precision similar to C programming
formatter like:

```
f = 3.14159
print("%.5f" %f)
print("%.9f" %f)
print("%.5f" %f)
print("%.9f" %f)
```

#### Complement:
BIT Manipulation ie XOR(^) , Left Shift(<<), Right shift(>>)
