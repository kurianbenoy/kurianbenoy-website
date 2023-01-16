---
aliases:
- /2021/04/11/JavascriptPromises
categories:
- coding
- javascript
date: '2021-04-11'
layout: post
readtime: true
title: An Issue I had with fetching data with Axios

---

I was working on building [Camunda- formio Tasklist](https://github.com/kurianbenoy-aot/camunda-formio-tasklist-vue) as part of my work. In the Javascript ecosystem, a lot of folks
use the Axios library to work with fetching data from APIs. There are a lot of other ways also to fetch data like Ajax calls, using fetch API etc as well.

So let me talk to you about my problem. I wrote the below snipped to fetch a GET request API data on passing the API URL,
parametrised data, token which I am passing will return the data.

```javascript
 import axios from 'axios';

export const httpGETRequest = (url: string, data: any, token: string, isBearer = true) => {
  return axios.get(url, {
    params: data,
    headers: {
      Authorization: isBearer
        ? `Bearer ${token}`
        : token,
    },
  });
};
```

Now I am going to call this method to pas the associated ApiUrl, applicationId, token etc to fetch a specific API to get
the history on passing a particular applicationID. I was expecting that it was going to on using then() method, I can extract the value
from the API, like this way:

```javascript
export const getformHistoryApi = (ApiUrl: string, applicationId: string,  token: string) => {
  httpGETRequest(ApiUrl+"/application/"+applicationId+"/history",{}, token).then((result) => {
      //fetching necessary data
  }
}
```

Yet it doesn't work. On realising why it doesn't work is because bought me to look at the previous works realise instead of working on that method, I called the following: 

```javascript
export const getformHistoryApi = (ApiUrl: string, applicationId: string,  token: string) => {
  return httpGETRequest(ApiUrl+"/application/"+applicationId+"/history",{}, token)
  
}


getformHistoryApi("https://kurianbenoy.com", 250, alasdfjadf). then((result) => {
// fetch API data object
})
.catch((error)=> {
//in case of any errors
}
```

This solved my issue. But I was curious about the why part. Then I looked into the documentation of Axios, and it starts with
the tagline:

> axios: Promise based HTTP client for the browser and node.js. It was not knowing axios used promises which caused me the issue.

### What are Promises?

I am stealing this from [Chandelier Axels article on Promises](https://dev.to/spartakyste/the-promises-guide-i-would-have-loved-as-a-junior-developper-3621)

```
According to MDN web documentation definition for promises is the following :

A Promise is a proxy for a value not necessarily known when the promise is created. It allows you to associate handlers with an asynchronous
action's eventual success value or failure reason

It doesn't make sense to me at all. 

So what are promises?:

First, the basics. Javascript is a synchronous and mono-threaded language. It means that all your code will execute in the order it's written, and it only has one call stack. To keep it simple, we'll stand that JS is a language where everything happens in order, without any external add-ons.

Promises are a way to execute certain pieces of code asynchronously, meaning they'll be executed behind the scenes, while the rest of the synchronous code is done.

Why do we need them?

Let's take a real-life example with two waiters. To keep it simple, our waiters are responsible for taking the orders and delivering the dishes from the kitchen to the clients.

Our first waiter will be the synchronous one (like if Javascript promises never existed). He would take the order, give it to the kitchen, wait for the dishes to be ready, and finally serve them, and so on. Kinda awkward and inefficient.

Our second waiter will handle things asynchronously. He'll take the orders from the clients and give them to the kitchen. By the time the dishes are ready, he will go do something else and come back later for the dishes whenever they are ready.

This is exactly what's happening in JS. The kitchen will give a promise to the waiter that the dishes will be ready sometime in the future.

A promise always takes a function with two arguments: resolve and reject. When the promise must return the result, we call resolve with the results. If something wrong happened, let's say we're missing some ingredients, the whole promise is compromised, we must cancel the order and get something different from the client, this is where we call reject.

How do we access the value then?

It allows you to associate handlers, the keywords here are handlers. Let's go back to our previous example, but let's get it to work for real this time.

const preparingDishes = new Promise((resolve, reject) => {
  // See the code above
});

// Now that our promise is created, let's trigger it, and then read the results
preparingDishes
  .then((dishes) => {
    // dishes is a arbitrary name, usually it's called result

    /* Within this function, we can access the result of the promise. The parameter will be the value you gave to the resolve.
    You are guaranteed that anything you put in here, will execute when the promise is fulfilled (successful) */
    callWaiter(dishes);
  })
  .catch((error) => {
    // In case an error happened, this handler will catch the return value inside your above reject or any error that could happen in your promise code
    if (error === 'An ingredient is missing !') {
      sendWaiterBacktoClients();
    }
  })
  .finally(() => {
    // This one will execute anything that you put inside, either the promise succeed or not

    // For example, whether the kitchen succeed in preparing the dishes or not, they'll have to start the next one
    prepareNextDishes();
  });

As you must have noticed by now, the .then, .catch and .finally are the handlers MDN is talking about. Each will execute under different circumstances as stated above.
Please take note that attaching all the handlers isn't mandatory, you could only attach a .then for example (but I wouldn't recommend it), or only a .then and a .catch, which is what you'll use most of the time.
```

If you look at MDN documentation, there are three states of promises that are:

1. Pending: initial state, neither fulfilled nor rejected.
2. Fulfilled: meaning that the operation was completed successfully.
3. Rejected: meaning that the operation failed.

I will also recommend you to check out the end section of Chandelier Axels article on Promises about the async/await methods.

----
I and my Tux have started reading the Pragmatic Programmer and I am sharing a few of the notes from the book with you folks:

![pexels-kurian-benoy-7499104](https://user-images.githubusercontent.com/24592806/114697081-17088e00-9d3b-11eb-87ee-96b52374a7d9.jpg)


> An investment in knowledge always pays the best interest ~Benjamin Franklin

Building a knowledge portfolio is similar to managing a financial journey:

- *Serious investors invest regularly as a habit*: Like investing it is important to spend weekly a specific amount of time on what you are learning.
- *Diversification is key for long-term success*: The more things you know you are more valuable. So learn ins and out of the technology you are learning, maybe get deep into the layer which you have been working throughout the years.
- *Smart investors balance their portfolios between conservative and high-risk*: Some languages which are already established and the growth rate will be a little less. It is important to manage your technical risks and grow.
- *Investors try to buy low and sell high for maximum return*: While if you take a bet on some new cool technology that is just getting established, you become an established figure in that language. Imagine the first folks who tried Java and used it throughout their lifetime.
- *Portfolios should be reviewed and rebalanced periodically*: Review your knowledge skills periodically and rebalance your strengths to stay relevant in the industry.

----

Three links for this week  👉:

- [History of linked list and why it's asked in interviews](https://www.hillelwayne.com/post/linked-lists/)
- [Why I write blogs by Sahil Dhiman](https://blog.sahilister.in/2020/10/why-i-write-blogs/)
- [Creating Streamlit dashboards using Python](https://youtu.be/tx6bT2Sh9R8)



