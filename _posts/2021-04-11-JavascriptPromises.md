---
title: Confusing part of Javascript promises
type: post
published: false
---


I was using axios library and another idiot stuff. 

I was defining a httpGETRequest which is used to sent with post request:

```javascript
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

Then using this I wanted to call an api and extract an attribute from the response.

but the:

export const getformHistoryApi = (ApiUrl: string, applicationId: string,  token: string) => {
  return httpGETRequest(ApiUrl+"/application/"+applicationId+"/history",{}, token)
}

I was thinnking of taking that idiot thing and then parse it. But on parsing with then it didn't work, why though


> An investment in knowledge always pays the best interest ~Benjamin Franklin

I am currently reading the book- The Pragmatic Programmer.

Building a knowledge portfolia is similar to managing financial journey:

- Serious investors inverst regularly as a habit
- DIverisification is key for long-term success
- Smart inverstors balance their porfolios between conservative and hig-risk
- Investors try to buy low and sell high for maximum return
- Portfolios should be reviewed and rebalanced periodically


Three links for this week -> :

- [History of linked list and why it's asked in interviews](https://www.hillelwayne.com/post/linked-lists/)
- [Why I write blogs by Sahil Dhiman](https://blog.sahilister.in/2020/10/why-i-write-blogs/)
- []()

