In this article, I will be talking about monoliths and microservice system
architecture. Recently [Hrishikesh Bhaskaran](https://twitter.com/_stultus) gave
a talk on this topic at Facebook F8 meetup. This talk inspired me and changed my
thoughts about both. So I am going to highlight some of key takeways in this
blogpost.

## Monoliths

**Monoliths** can be defined as single tiered software user interface and data
access is combined together. So taking the example of Social media all
functionalities like userfeed, authentication, photos are all enclosed in a
single application.

In case of **Microservices**, all the functionalities are seperated whenever
required so we can use the best bleeding edge technology when required.

*Some basic terminologies*

```  Vertical scaling - increase RAM/My of CPU service
     Horizontal scaling - more replicas
     Loadbalancers - A load balancer is a device that distributes network
or application traffic across a cluster of servers. Load balancing improves
responsiveness and increases availability of applications. One of the 
easiest methods for scaling.
```

#### Why Monlith are easy to build?
- Less time for initial build
- Easy installation and deployment of services
- testing of service is very easy

Next we will discuss about `Microservices`. Now **microservices** has become a
buzz-word like *AI, Machine learning, blockchain, kubernetees*. Now docker,
kuberneetes and all have become popular. Thus making the microserice approach
very easy to use and a buzz word. As Hrishi said, please note `monolith is not a
out-dated technology` as many think about it. It still always recommended to use
monoliths when you are building a stack with no previous experience in it.

`Extras:`[DockervsKuberneetes:Not an or
question](https://www.youtube.com/watch?v=2vMEQ5zs1ko)

## Micoservices
Some of the characteristics of Microservices are:
- Per Martin Fowler and other experts, services in a microservice architecture
  (MSA) are often processes that communicate over a network to fulfill a goal
  using technology-agnostic protocols such as HTTP.
- Increased  uptime for servers, as only one service need to made down to scale
  a paricular component compared to monoliths which has downtime for entire
  services.
- Using new technologies is easy
- Various Database and Language support for each services is possible like R,
  JS, Python. You run backend both in flask, rust and golang for various
  microservices. This allows in using the best of everything.
- Helps in easy onboarding for new member and help in agile architecture of
  development, which is popular now.

#### Disadvantages:

 Microservices is a distributed computing, so there is a lot of problems are
 associated with it:
- All services should have same IP, the network use VPC for communication of
  various  microservices to each other.
- Assuming lattency is 0, stupid and create architecutre limitations
- Assume bandwidth is infinity,
- Assume network topologies are same, IP change when going to different Places
  the ping on further cases won't be available. Else use DNS server
- "" Network cordinators are same, IP mattan aale thapa;
- "" internal data cost is same

Using Microservice for small 2 person teams is stupid Familar things are using
microservice

## When to use Monoliths vs Microservices

This is actually a million dollar question according to me. Personally I had
 always used microservices as my defacto method of development and encountered
 lot of issues with it. Once I was developing a website for 1 day use purpose,
 to be used at-most maximum of 100 people. And using microservices made it a
 pain to deploy the service and eventually one of my friends solved the issue by
 using a static website with everything hard coded and was deployed in less than
 1 hour.

**Moral of story: Use adequate technology at adequate time**

*Monolith* is ideal for new projects which are meant to be served in a
low/medium scale with less knowledge on how to build it. 


*Microservices* are ideal for projects which you already have some domain
experience on and know what exactly are the services split up needed for
satisfying your requirement.


Thanks for reading the article and I hope it was not prolix and boring :).
