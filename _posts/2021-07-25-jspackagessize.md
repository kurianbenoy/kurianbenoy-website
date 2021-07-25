---
title: Why are popular npm packages are very small in sizes like less than 1MB?
type: post
tags: [TIL, JavaScript]
show-avatar: false
---

Most of the NPM packages are of very small size, as it's a crucial thing
which affects the npm packages. Let's look at why it's a crucial things.

One is the performance factor of the applications you are building. Most
of the applications you are working on are to be highly performant, and should
work even in low bandwidth settings.

At the end of the day, imagine if your npm package is say 10 MB in size. I don't expect
99% of users in India to never use your application in web or mobile. Why?
Because loading your application will easily take 5-10 seconds, while an average application
is expected to return a meaningful content load usually in milliseconds. This is why it's very
important to keep your application small in size, and easily usable for lot of folks.

This is why popular NPM packages like React are just Kbs in size. One of the most common complaint, I heard
from other folks was why to use React for a TodoList App with 3MB size when you can do same things
easily with vanilla JS + CSS in a very performant reaason. Any frontend framework has it's own pros and
cons.

Yet as people making packages, it's very important to make your packages as small as possible
to be highly reliable. So some of simplest things we can do is to Reduce dependencies as much as possible.
This can be done by not trying install third party dependency when we are working on something which a stack
overflow answer recommends. Adam Polak recommends how to reduce your
[size of node modules for Cost and performance reasons](https://tsh.io/blog/reduce-node-modules-for-better-performance/).

Also generally the loading time is not so slow even though there are dependencies, as most of
common dependencies like JQuery which are commonly used in multiple websites are cached if they come from CDN 
in users browser itself.

I would like to thank [Faiz Shabeeb](http://shabeebk.com/blog/) for sharing this knowledge.

