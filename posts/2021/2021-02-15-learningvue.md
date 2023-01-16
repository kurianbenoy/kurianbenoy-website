---
aliases:
- /2021/02/15/learningvue
categories:
- javascript
- frontend
- coding
date: '2021-02-15'
layout: post
readtime: true
title: Learning Vue.js Part1

---

*Why learning Vue.js?*

JavaScript is a language which I always wanted to learn. Yet recently when I was asked to learn as part of my day job, that's when I started thinking about learning it seriously. It is always important to learn some new languages/frameworks from time to time. Since it's a new year, let's plan to learn more tech topics in this year.

*Before Learning Vue.js - learn JS first*

To learn the Vue.js, first, it is essential to learn the basics of JavaScript, HTML, CSS etc. 
It is very important to get the fundamentals of JavaScript right.
Read what Nadia has to say 👇

![image](https://user-images.githubusercontent.com/24592806/107968479-6dc04880-6fd4-11eb-89d1-c3fba9c88b01.png)


Let's explore a few Javascript concepts which Nadia mentioned in her tweet.

*Promises*

Promises consist of both producers and consumers. The producers can consist of resolve and reject statements. While consumers can consist of statements with then, finally and catch statements embedded in it. Check the below article to learn more:

- [https://dev.to/spartakyste/the-promises-guide-i-would-have-loved-as-a-junior-developper-3621](https://dev.to/spartakyste/the-promises-guide-i-would-have-loved-as-a-junior-developper-3621)

- [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)

- [https://javascript.info/promise-basics](https://javascript.info/promise-basics)


*Arrow function*

This is an easy hack designed in ES6 and is a widely used feature in most of the codebases.
{% highlight javascript linenos %}
test = (a,b) => {
// Return function details
}
{% endhighlight %}

*Nullish Coalescing Operator*

The nullish coalescing operator (??) is a logical operator that returns its right-hand side operand when its left-hand side operand is null or undefined and otherwise returns its left-hand side operand.

Taken from MDN Docs

Consider the expression `a ?? b`.

> This evaluates to b if a is null or undefined, otherwise, it evaluates to a


*Destructing*

It's a short way to get elements of an array into variables or get properties of an object into variables.

{% highlight javascript linenos %}
const user = {
    name: 'Bhanu Teja',
    blogs: 3,
    timeSpan: 2.
}

const {name, blogs, timeSpan} = user
console.log(name);
console.log(blogs);
console.log(timeSpan);
{}
{% endhighlight %}

*Arrays*


Like any languages, a list of like elements is represented using Arrays which are equivalent to lists in Python. Some of the common array operators which are a bit unique are:

> map - The process of transforming an existing array to some other new form. 

{% highlight javascript linenos %}
const names = [
    { firstName: 'Casey ', lastName: 'Jones' },
    { firstName: 'Phil', lastName: 'Lesh'},
    { firstName: 'Brad', lastName: 'Traversy'},
    { firstName: 'August', lastName: 'West'}
]

names.map(name=> `${name.firstName} ${name.lastName}`)
{% endhighlight %}

> Reduce - The array reduce method reduces the array of values into a single value. It executes the callback function for each value of the array.

```
const values = [2, 4, 6, 7, 8]

const initialValue = 0
values.reduce((total, currentValue) => total + currentValue, initialValue)
```

> Splice - This method is used to add or remove elements in an array.

*Fetching APIs*

To fetch we usually use libraries like axios to do API request manipulation. It would be a good idea to learn more about it and let me share how to use these APIs in case of Vue.js in the below cookbook example.

[Using Axios to Consume APIs](https://vuejs.org/v2/cookbook/using-axios-to-consume-apis.html)


*Event Loops*

continuously running programs without waiting, so the web browser won't' be waiting infinitely long for a process to end. The concept of Javascript concept - Event loop.

{% highlight javascript linenos %}
let a = true

setTimeout(() => {
    a = false;
}, 2000);

while(a) {
    console.log(a);
    }
{% endhighlight %}

The reason why it continuously runs the code even after 2 seconds is because of the concept of event loops since javascript is single-threaded language and setTimeout runs in a separate thread, the value of a as false can't be replaced as the while loop is still getting run.

A very interesting talk on this topic is by Phillip Roberts titled - What the heck is the event loop anyway?

[![](http://img.youtube.com/vi/8aGhZQkoFbQ/0.jpg)](http://www.youtube.com/watch?v=8aGhZQkoFbQ "")


*setTimeout and setIntreval*

setTimeout is a function to run a specific function once for a period of milliseconds specified.
setIntreval is a function which runs periodically during a time interval
clearIntreval is a function to exit from this set interval on passing the function

*We haven't started Vue yet*

We haven't even touched the meat of our matter where we want to learn VUEJS. I would highly suggest you do yourself a favour by reading Vue.js getting started guide for this week and check out the sample project which we have created. We will continue our VueJs series for next week as well.

[Sample Vuejs application](https://github.com/kurianbenoy-aot/vuejs-101)


Signing Off, 

~ Kurian
