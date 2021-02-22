---
title: Learning Vue.js Part 2
type: post
---

## Motivation

Learning frontend is a super power. Even Eugene Yan wrote on his blogpost [How to win a Data Hackathon](https://eugeneyan.com/writing/how-to-win-data-hackathon/) in
conclusion:

```
Training bespoke machine learning models wasn’t a differentiating factor at this hackathon. Instead, what made a difference was:

- Using readily available data via public datasets or APIs
- Using libraries / pre-trained models to speed up ML iteration
- Building UIs to make machine learning and insights easy to consume
- Deploying models and UIs so people can use them
```

Last week we started from picking out the a few basics of Javascript. I also recommended it would be a good to idea to read Vue getting started guide.

Let's first look at Vue getting started guide:

[Follow this link](https://vuejs.org/v2/guide/)

Vue is a progressive framework for building user interfaces. Unlike other monolithic frameworks, Vue is designed from the ground up to be 
incrementally adoptable. The core library is focused on the view layer only, and is easy to pick up and integrate with other libraries or 
existing projects. If you have read the getting started guide, you may have realised the following features:

1. Declarative render - the property of adding data elements
2. Then conditional statements using v-if and v-else
3. v-for for declaring all elements in todo list
4. v-model to handle two way input
5. Functions to call on click which can return the necessary functions as appropriately
6. Using components and using bind statements and passing prop
7. Vue components are similar to web components and is inpired and modelled with Slot APi

The above points are a brief gist of about getting started guide about Vue.js. We made a small todo list with the above getting started guide:

[TODO list Code pen](https://codepen.io/kurianbenoy-aot/pen/poNWNpM)


If you look at the source code inside <script> tag:

```
export default {
  data() {
  .....
  },
  methods: {
  ....
    functions to be used for Various usecases
  },
  computed: {
    ...
  }
```

- *data*: used for deciding properties of vue.js application
- *methods*: Used for various methods, like what functionality to occur when a button is click
- *computed*: Used for calculating values based on predefined data. There are both getters and setters functionality with this method

<style> contains the functionality for using CSS to make your application look great
  


