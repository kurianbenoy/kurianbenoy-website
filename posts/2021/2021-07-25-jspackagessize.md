---
aliases:
- /2021/07/25/jspackagessize
categories:
- TIL
- JavaScript
date: '2021-07-25'
layout: post
show-avatar: false
title: Why should NPM packages be as small as possible?

---

Most of the popular NPM packages are very small in size, as it's a crucial thing
that affects the npm packages. Let's look at why it's a crucial thing:

One is the performance factor of the applications you are building. Most
of the applications you are working on are to be highly performant, and should
work even in low bandwidth settings.

Imagine if your npm package let's say is 10 MB in size. I don't expect
99% of users in India never load your application in web or mobile build with node_modules. But Why?

It's because loading your application will easily take 5-10 seconds, while an average application
is expected to return a meaningful content load usually in milliseconds. This is why it's very
important to keep your application small in size, and easily usable for a lot of folks. This is why popular
NPM packages like React, moment.js are just Kbs in size.

One of the most common complaints, I heard
from other folks was why to use React for a TodoList App with 3MB size when you can do the same thing
easily with vanilla JS + CSS(which is in a few KBs) for a very performant reason. Any frontend framework has its pros and
cons.

Also, it's very important to make your packages as small as possible to be highly reliable and cost less
cost for computing required for hosting. So one of the simplest things we can do is to reduce dependencies
as much as possible.

This can be done by not trying to install third-party dependencies when we are working on any application. 
Even though I agree a lot of stack-overflow answers recommends this approach. Yet generally the loading time is
not so slow even though there are dependencies, as most of the common dependencies like JQuery which are commonly
used in multiple websites are cached in the users' browser itself if they come from CDN.

Adam Polak recommends how to reduce [size of node modules for Cost and performance reasons](https://tsh.io/blog/reduce-node-modules-for-better-performance/).

I would like to thank [Faiz Shabeeb](http://shabeebk.com/blog/) for sharing this knowledge.
