---
title: An Issue I had with fetching data with Axios
type: post
readtime: true
tags: [coding, javascript]
published: false
---


I was working on building Camunda- formio Tasklist as part of my work. In Javascript, lot of people use axios library to work with
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

Yet it doesn't work. On realising why it doesn't work is because bought me 
me to look at the previous works realise instead of working on that method, I called th
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

This solved my issue. But I was curious about the why part. Then I looked into the documentatio of axios, and it starts with
the tagline:

> axios: Promise based HTTP client for the browser and node.js

https://axios-http.com/docs/post_example/
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
learn more about promise and explain it.
then , catch methods, nested chaining ,
Promise all example
What are prototypes?

----

I have started reading the Pragmatic Programmer and I am sharing few of the notes with you folks:

> An investment in knowledge always pays the best interest ~Benjamin Franklin

To build a knowledge portfolia is similar to managing financial journey:

- Serious investors inverst regularly as a habit
- DIverisification is key for long-term success
- Smart inverstors balance their porfolios between conservative and hig-risk
- Investors try to buy low and sell high for maximum return
- Portfolios should be reviewed and rebalanced periodically


Three links for this week  👉:

- [History of linked list and why it's asked in interviews](https://www.hillelwayne.com/post/linked-lists/)
- [Why I write blogs by Sahil Dhiman](https://blog.sahilister.in/2020/10/why-i-write-blogs/)
- [Creating Streamlit dashboards using Python](https://youtu.be/tx6bT2Sh9R8)

