---
layout: post
title: Swift installation & programming language
---

> Picking up a new language, every 2 months - Kushal Das

So I decided to pickup swift and blog my experiences with that. 

## Promise of Swift

1. Infinetely Hackable language - we can go and change even the lowest level in the language,
and use these above the hood to get best performance
2. Similar to Python
3. Can reach C level speed for programming


## Installation 

Before hacking a new language, it's always necessary to setup your working environment for 
the language. The installation instructions are covered in [Swift
docs](https://swift.org/getting-started/#installing-swift). Swift can be installed in 
MacOS and Linux.

Since my operating system is Debian10, as I found the local installation a bit tricky, I installed
with Docker.

Docker installation is pretty straightword:

```
docker pull swift
docker run --security-opt seccomp=unconfined -it swift
```

(Points - from talk in Tensorworld brett and Paige)
- why awesome,
- running TPU specific operations with swift for bfloat16
- directly connecting with tensorflow
- importing C libraries directly
- using C and combining d/dx with sqrt
