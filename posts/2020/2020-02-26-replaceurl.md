---
aliases:
- /2020/02/26/replaceurl
date: '2020-02-26'
layout: post
readtime: true
title: Replace one host name with another host name in Javascript

---

Problem: You are given a host name, and from it you want to replace host name of one website with another which follows the exact Url pattern

eg: Url = https://github.com/kurianbenoy-aot/Learning

In the above url we need to replace github with gitlab because I have a clone repo in gitlab also with same domain name.

I am going to show how to do it with Javascript.

```
Url = "https://github.com/kurianbenoy-aot/Learning"
replaceUrl = "https://gitlab.com"

 Urlextract= (Url.split('://')[1]).split('/')[0]
 replaceUrlextract = replaceUrl.split("//")[1]
 
//answer is: "https://gitlab.com/kurianbenoy-aot/Learning"
console.log(Url.replace(Urlextract, replaceUrlextract))
```

What if we just wanted to extract the domain name from Url:

```
ans = Url.replace("https://", "").replace("http://", "").split('/')[0]
console.log(ans)
```

