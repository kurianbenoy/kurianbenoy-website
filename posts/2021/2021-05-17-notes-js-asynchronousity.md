---
aliases:
- /2021/05/17/notes-js-asynchronousity
author: Kurian Benoy
date: '2021-05-17'
layout: post
title: Notes on Javascript Asynchronicity

---

A few points to remember about JavaScript:

- JavaScript runtime is a single threaded. What it means is when a given program's code runs straight along, with only one thing happening at once. If a function relies on the result of another function, it has to wait for the other function to finish and return, and until that happens, the entire program is essentially stopped from the perspective of the user.
- **What are you Javascript?**

I am single-threaded non-block asynchronous concurrent language. I have a call stack, an event loop, a callback queue and some other APIs.

- On of the frusturating parts of synchronous programming is in an era of computers with multiple cores available. There is no sense waiting for something
to be completed when my work is being done. It is up to the programming environment you are using (web browsers, in the case of web development) to provide you with APIs that allow you to run such tasks asynchronously.
- An example program for waiting for processes in UI is shown in below example link:

[Example Link](https://mdn.github.io/learning-area/javascript/asynchronous/introducing/simple-sync-ui-blocking.html)

1. The first button for clicking Fill button and then on clicking button for alert. 
2. It won't function, as the operation to fill canvas is still running, and only on completion the alert button is shown.

- JavaScript also has threads with Web Workers for using threads. It can help when you have a computer with multiple cores.
- The issue with threads comes when one task you run depends on another, so multiple threads needn't help always to improve speed.
- In such situations there is a system like Promises in JavaScript language construct.

Main thread: Task A                   Task B
    Promise:      |__async operation__|

- In case of JavaScript to implement asynchronous programming, it is usually implemented with the help of concept **Event Loop**:

Coming on that topic of Event Loop, there is an excellent talk by Phillip Roberts about "What the heck is event loop
anyways?". It's the most watched video for a particular reason.

<iframe width="560" height="315" src="https://www.youtube.com/embed/8aGhZQkoFbQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Rough Notes from that talk
----
- In v8, there is a stack, heap. Javascript is single threaded, with single call stack.
- blowing stack(MAximum call stack exceeded)
- What if browser were synchronous. In browser, we can't do anything during program running, so browsers
should be ideally asynchronous
- Simplest solution is asynchronous callbacks. In call stack how is behavious happening? After 5 seconds 
on Set time out function is printed again.
- JavaScript Runtime can do just one time, browser can do multiple times like WebAPIs. In case of NodeJS, there is C APIs instead of webapis.
- In Stack, webAPIs, task Queue.
- The event loop elements in queue is only pushed when the stack is clear.
- Time out is minimum guaranteed time which is promised by Event loop

According to him JS was build for web, so any web time instance is build not just merely with 
JavaScript runtime, but under the hood their is queues, Web APIs to implement the event loop.
All this is because javascript is used in application for billions of people daily, because it 
should be used real time. Just when something is running, our browser can't freeze to wait for another
instance to be loaded right.


Now after watching that 25 minute long talk. Let's look more into asynchronousity in JavaScript

There are two types of asynchronous code style you will come across in JavaScript code:
- Old style callbacks
- Newer promise style codes

In case of promises and callbacks they are different in many ways:

a) Promises helps in ordered execution of statements with then statements
b) better error handling in case of promises
c) In case of failure in callbacks it causes the call back hell, which can
be pretty difficult to fix the issue
d) Callbacks loose full control of how functions are executed when passing
to a third party library.

Now as [MDN concludes](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Introducing):

*In its most basic form, JavaScript is a synchronous, blocking, single-threaded language, in which only one operation can be in progress at a time. But web browsers define functions and APIs that allow us to register functions that should not be executed synchronously, and should instead be invoked asynchronously when some kind of event occurs (the passage of time, the user's interaction with the mouse, or the arrival of data over the network, for example). This means that you can let your code do several things at the same time without stopping or blocking your main thread.*

Also before concluding the link of this week:

1. Did you know that [switch/case statements are not available in Python?](https://docs.python.org/3/faq/design.html?highlight=case%20switch#why-isn-t-there-a-switch-or-case-statement-in-python)
2. [How to implement Sorting in Python, an excellent tutorial by Andrew Dalke and Raymond Hettinger](https://docs.python.org/3/howto/sorting.html)
3. [Did you hear about the latest library Icream to never use print and log again](https://github.com/gruns/icecream)

**References:**

- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Introducing
- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Concepts
- https://mixstersite.wordpress.com/2020/10/20/javascripts-asynchronicity/
- https://javascript.info/async-await
