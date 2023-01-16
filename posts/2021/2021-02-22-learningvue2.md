---
aliases:
- /2021/02/22/learningvue2
categories:
- javascript
- frontend
- coding
date: '2021-02-22'
layout: post
readtime: true
title: Learning Vue.js Part 2

---

## Motivation

Learning frontend is a superpower. Even Eugene Yan wrote in his blog post [How to win a Data Hackathon](https://eugeneyan.com/writing/how-to-win-data-hackathon/) in
conclusion:

```
Training bespoke machine learning models wasn’t a differentiating factor at this hackathon. Instead, what made a difference was:

- Using readily available data via public datasets or APIs
- Using libraries / pre-trained models to speed up ML iteration
- Building UIs to make machine learning and insights easy to consume
- Deploying models and UIs so people can use them
```

![image](https://user-images.githubusercontent.com/24592806/108724626-889e3a00-754b-11eb-9a51-0c809b9f8867.png)

> Vue is a progressive framework for building user interfaces. Unlike other monolithic frameworks, Vue is designed from the ground up to be 
incrementally adoptable.

## Vue.js getting started guide

Last week we started by picking out a few basics of Javascript. I also recommended it would be a good idea to read Vue getting started guide.

Let's first look at Vue getting started guide:

[Follow this link](https://vuejs.org/v2/guide/)

The core library is focused on the view layer only and is easy to pick up and integrate with other libraries or 
existing projects. If you have read the getting started guide, you may have realised the following features:

1. Declarative render - the property of adding data elements
2. Then conditional statements using v-if and v-else
3. v-for for declaring all elements in the todo list
4. v-model to handle two-way input
5. Functions to call on click which can return the necessary functions as appropriately
6. Using components and using bind statements and passing prop
7. Vue components are similar to web components and are inspired and modelled with Slot API

The above points are a brief gist of the basic getting started guide about Vue.js. We made a small todo list with the above getting started guide:

## TODO list - based on Vue.js

[TODO list Code pen](https://codepen.io/kurianbenoy-aot/pen/poNWNpM)


If you look at the source code inside <script> tag:

```
export default {
  data() {
  .....
  },
  methods: {
  ....
    functions to be used for various use cases
  },
  computed: {
    ...
  }
```

- *data*: used for deciding properties of vue.js application
- *methods*: Used for various methods, like what functionality to occur when a button is to be clicked or calling APIs etc
- *computed*: Used for calculating values based on predefined data. There are both getters and setters functionality with this method


style - contains the functionality for using CSS to make your application look great
  
template - is the special place where all the Vue.js magic comes in place. In generally most of the folks use Vue.js with templates,
  even though there is [Vue render functions](https://vuejs.org/v2/guide/render-function.html) which I guess is mainly used React. In the case of templates, when you are using v-(suffix) it always is something special. It can be something like binding variables, methods, 
 loops, etc.
  
 ## Vue-cli to create Vue projects
 
Vue-cli is the best to initialize and get started with learning any new project the first time. This can be the equivalent of create-react-app in React world and the equivalent of [create-ml-app](https://github.com/shreyashankar/create-ml-app) build by Shreyas Shankar for ML projects.

It has multiple features like supporting various features of Babel, typescript, ESlint, etc. It does not require users to eject. It's very easy to customise and choose various features for our Vue project. Yet it's a good idea to remember all these are built on top of legends which are taken for granted often.

[Check out Vue CLI website to learn more about the project](https://cli.vuejs.org/)

The command to begin a project is:

`vue create <project name>`


## Side Note - about NPM packaging

[Article Link](https://dev.to/spartakyste/the-npm-guide-i-would-have-loved-as-a-beginner-4i07)

It talks about the basic NPM commands, how NPM acts as the package manager. It also tells about npm init -y command to create a project, and how to manage dependencies and devDependencies. 

Dependencies are vital features, while Dev dependencies like linters help in managing things not vital and are removed when productionizing with npm build. 

He also talks about the concept of scripts, which are used for determining commands to run like npm start in the case of React. 
Tips on managing dependencies, uninstalling packages and package-lock.json is mentioned in the article. 

I am signing off again, I will be back to share more of my learnings next week. Till then Bye.

~ Kurian

