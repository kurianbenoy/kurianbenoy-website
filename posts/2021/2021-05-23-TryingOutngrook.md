---
aliases:
- /2021/05/23/TryingOutngrook
author: Kurian Benoy
date: '2021-05-23'
layout: post
readtime: true
title: Trying out ngrok

---

[ngrok](https://ngrok.com/) is a cross-platform application software for enabling developers to deploy or expose their web applications from locally with 
a associated website url. This works due to the SSH tunnelling.

So this weekend I was trying out ngrok with few of the projects I have worked:

- [Project 1: Cartoonizer](https://github.com/Toon-It/Cartoonizer)

Hosting Cartoonizer is a long pending issue for me. The cartoonizer to use with ngrok. I downloaded the package: `flask-ngrok`. Just making a few 
changes as [mentioned in the below article](https://www.geeksforgeeks.org/how-to-run-python-flask-app-online-using-ngrok/) got the application up and running
with a https url. The application was up and running, yet when I tried uploading an image to cartoonize, it failed to work due to the usage of os module in
my library to fetch and cartoonize image.

- [Project 2: Camunda-formio-tasklist-vue](https://github.com/AOT-Technologies/forms-flow-ai-extensions/tree/master/camunda-formio-tasklist-vue)

Since this is a Vue application, I was expecting to easily use along ngrok. Instead of using any packages this time, [I created an account
in ngrok](https://ngrok.com/) and downloaded the client for the operating system. Then on authenicating with my token and running the command:

`ngrok http 3000`

I was expecting my application to be up. Yet, I faced an error message:

> Invalid Host Header 

On googling a bit, I stumbled upon a solution once I ran the command: 

`ngrok http 3000 -host-header="localhost:3000`

So my application was up and running after a 20-30 seconds page delay(which I  am curious why though?)

- [Project 3: Augmentation Web App library](https://github.com/kurianbenoy/Augmentation-web-app-library)

Since this was a streamlit application. When I tried installing in windows, it gave me some SocketIO connection error, which didn't run my application.
So then I used wsl to run the project and on running it up, it was not getting pointed to an internal IP address instead of localhost. So when I ran ngrok,
like the previous approach. It was not working in associated port. I need to see how can I point an internal IP to ngrok or get this application running in 
localhost.


So I am winding off by sharing how [ngrok works](https://ngrok.com/product). Also some good news 🌼, after nearly 5 months - I have contributed to 
Shahul's latest [open source project- Twitter Emotion](https://github.com/shahules786/twitter-emotions). The project given an input tweet, extracts the phrase in
the tweet associated to express a particular sentiment.

>:wq
