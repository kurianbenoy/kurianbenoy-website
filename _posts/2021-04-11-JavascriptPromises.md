---
title: Confusing part of Javascript promises
type: post
published: false
---

javascript


I was using axios library and another idiot stuff. 

I was defining a httpGETRequest which is used to sent with post request:

```
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


Three links for this week -> :

- [History of linked list and why it's asked in interviews](https://www.hillelwayne.com/post/linked-lists/)
- [Why I write blogs by Sahil Dhiman](https://blog.sahilister.in/2020/10/why-i-write-blogs/)
- []()

