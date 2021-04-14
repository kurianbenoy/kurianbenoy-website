---
title: An Issue I had with fetching data with Axios
type: post
readtime: true
tags: [coding, javascript]
published: false
---


I was working on building [Camunda- formio Tasklist](https://github.com/kurianbenoy-aot/camunda-formio-tasklist-vue) as part of my work. In Javascript, lot of people use axios library to work with
fetching data from APIs. There are lot of other ways also to fetch data like Ajax calls, using fetch API etc.

So let me talk you about my problem. I wrote the below snipped to fetch a GET request data on passing the API url,
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

This solved my issue. But I was curious about the why part. Then I looked into the documentation of axios, and it starts with
the tagline:

> axios: Promise based HTTP client for the browser and node.js.

### What are Promises?

I am stealing this from [Chandelier Axels article on Promises](https://dev.to/spartakyste/the-promises-guide-i-would-have-loved-as-a-junior-developper-3621)

```
According to MDN web documentation definition for promises is the following :

A Promise is a proxy for a value not necessarily known when the promise 
is created. It allows you to associate handlers with an asynchronous
action's eventual success value or failure reason

It doesn't make sense to me at all. 

So what are promises?:

First, the basics. Javascript is a synchronous and mono-threaded language. It means that all your code will execute in the order it's write, and it only has one call stack. To keep it simple, we'll stand that JS is a language where eveything happen in order, without any external add-ons.

Promises are a way to execute certain pieces of code asynchronously, meaning they'll be executed behind the scenes, while the rest of the synchronous code is done.

Why do we need them ?

Let's take a real life exemple with two waiters. To keep it simple, our waiters are responsible from taking the orders, and delivering the dishes froms the kitchen to the clients.

Our first waiter will be the synchronous one (like if Javascript promises never existed). He would take the order, give it to the kitchen, wait for the dishes to be ready, and finally serve them, and so on. Kinda awkward and inefficient.

Our second waiter will handle things asynchronously. He'll take the orders from the clients and give it to the kitchen. By the time the dishes are ready, he will go do something else and come back later for the dishes whenever they are ready.

This is exactly what's happening in JS. The kitchen will give a promise to the waiter that the dishes will be ready sometime in the future.

A promise always take a function with two arguments : resolve and reject. When the promise must return the result, we call resolve with the results. If something wrong happened, let's say we're missing some ingredients, the whole promise is compromised, we must cancel the order and get something different from the client, this is where we call reject.

Why ? If we keep with our waiter exemple, we say to the kitchen : Hey, I have a new order, prepare it, and we didn't let the necessary preparation time, so the kitchen answer It's not ready ! We're still preparing it. The promise is pending.

How do we access the value then ?

Do you remember the MDN definition ? It allows you to associate handlers, the keywords here is handlers. Let's go back to our previous exemple, but let's get it to work for real this time.

const preparingDishes = new Promise((resolve, reject) => {
  // See the code above
});

// Now that our promise is created, let's trigger it, and then read the results
preparingDishes
  .then((dishes) => {
    // dishes is a arbitrary name, usually it's called result

    /* Within this function, we can access the result of the promise. The parameter will be the value you gave to the resolve.
    You are guaranted that anything you put in here, will execute when the promise is fullfilled (succesfull) */
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

    // For example, wether the kitchen succeed preparing the dishes or not, they'll have to start the next one
    prepareNextDishes();
  });

As you must have noticed by now, the .then, .catch and .finally are the handlers MDN is talking about. Each will execute under different circumstances as stated above.
Please take note that attaching all the handlers isn't mandatory, you could only attach a .then for exemple (but I wouldn't recommended it), or only a .then and a .catch, which is what you'll use most of the time.
```

If you look at MDN documentation, there are three states of promises that is:

1. Pending: initial state, neither fulfilled nor rejected.
2. Fulfilled: meaning that the operation was completed successfully.
3. Rejected: meaning that the operation failed.

I will also recommend you to check out the end section of Chandelier Axels article on Promises about the async/await methods.

----

I have started reading the Pragmatic Programmer and I am sharing few of the notes with you folks:

> An investment in knowledge always pays the best interest ~Benjamin Franklin

To build a knowledge portfolia is similar to managing financial journey:

- *Serious investors inverst regularly as a habit*: Like investing it is important to spend weekly a specific amount of time on what you are learning.
- *Diverisification is key for long-term success*: The more things you know you are more valuable. So learn ins and out of technology you are learning, maybe get deep into the layer which you have been work all throughout.
- *Smart inverstors balance their porfolios between conservative and high-risk*: Some languages which are already established are like already established and growth rate will be little less. It important to manage your technical risks and grow.
- *Investors try to buy low and sell high for maximum return*: While if you take a bet on some new cool technolgy which is just getting established, you become a established figure in that language. Imagine the first folks who tried Java and used it through out their life time.
- *Portfolios should be reviewed and rebalanced periodically*: Review you knowledge skills periodically and rebalance your strengths to stay relevant in the industry.

----

Three links for this week  👉:

- [History of linked list and why it's asked in interviews](https://www.hillelwayne.com/post/linked-lists/)
- [Why I write blogs by Sahil Dhiman](https://blog.sahilister.in/2020/10/why-i-write-blogs/)
- [Creating Streamlit dashboards using Python](https://youtu.be/tx6bT2Sh9R8)

