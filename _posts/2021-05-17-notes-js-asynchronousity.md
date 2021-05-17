---
title: Notes #1 - Javascript Asynchronicity
type: post
author: Kurian Benoy
---

Notes from [Asynchronous Concepts](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Concepts)

```
Normally, a given program's code runs straight along, with only one thing happening at once. If a function relies on the result of another function, it has to wait for the other function to finish and return, and until that happens, the entire program is essentially stopped from the perspective of the user.

This is a frustrating experience and isn't a good use of computer processing power — especially in an era in which computers have multiple processor cores available. There's no sense sitting there waiting for something when you could let the other task chug along on another processor core and let you know when it's done. This lets you get other work done in the meantime, which is the basis of asynchronous programming. It is up to the programming environment you are using (web browsers, in the case of web development) to provide you with APIs that allow you to run such tasks asynchronously.

A few points to remember always is:

- Javascript is a single threaded lanaguage
- It runs things one after another
- Yet about the browser(not sure)??
- So the issue with blocking code, is other processes need to wait until something is completed
- Examples like waiting for processes can be annoying like:

https://mdn.github.io/learning-area/javascript/asynchronous/introducing/simple-sync-ui-blocking.html

1. The first button for clicking Fill button and then on clicking button for alert. 
2. It won't function, as the operation to fill canvas is still running, and only on completion the alert button is shown.

- JavaScript also has threads with Web Workers for using threads. It can help use the multiple 
cores in JavaScript.
- The issue with threads comes when one task you run depends on another, so multiple threads needn't 
help.
- In such situations there is a system like Promises as based on the language construct.
Main thread: Task A                   Task B
    Promise:      |__async operation__|
```

- In case of JavaScript to implement asynchronous programming, it is usually implemented
with the help of concept Event Loop:

Coming on that topic, there is an excellent talk by Phillip Roberts about "What the heck is event loop
anyways?". It's the most watched video for a particular reason.

https://youtu.be/8aGhZQkoFbQ

In v8, there is a stack, heap. Javascript is single threaded, with single call stack.
- blowing stack(MAximum call stack exceeded)
- What happens when things are slow?
- We are loading code, in browsers. In browser, we can't do anything during program running, so browsers
should be ideally asynchronous

- Simplest solution is asynchronous callbacks. In call stack how is behavious happening? After 5 seconds 
on Set time out function is printed again.
- JavaScript Runtime can do just one time, browser can do multiple times like WebAPIs. `

- In Stack, webAPIs, task Queue.
- The event loop elements in queue is only pushed when the stack is clear.
- Time out is minimum guaranteed time which is promised by Event loop

According to him JS was build for web, so any web time instance is build not just merely with 
JavaScript runtime, but under the hood their is queues, Web APIs to implement the event loop.
All this is because javascript is used in application for billions of people daily, because it 
should be used real time. Just when something is running, our browser can't freeze to wait for another
instance to be loaded right.

<!-- But, the really important point. We understand once and for all why Javascript has to be asynchronous in the first place. It all comes around to when things in your code take or needs time, then you can’t freeze up your entire browser instance to wait for that one resource to load”. It isn’t efficient nor is it useful. Which something very important we forget because JS was built for the web first and then the other million use cases came along. -->

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


References:

- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Introducing
- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Concepts
- https://mixstersite.wordpress.com/2020/10/20/javascripts-asynchronicity/
- https://javascript.info/async-await
