In this article, I will be talking about monoliths and microservice system 
architecture. Recently [Hrishikesh Bhaskaran](https://twitter.com/_stultus) gave
a talk on this topic at Facebook F8 meetup. This talk inspired me and changed
my thoughts about both. So I am going to highlight some of key takeways in this
blogpost.

## Monoliths

**Monoliths** can be defined as single tiered software user interface and data
access is combined together. So taking the example of Social media all
functionalities like userfeed, authentication, photos are all enclosed in a 
single application.

In case of **Microservices**, all the functionalities are seperated whenever 
required so we can use the best bleeding edge technology when required.

`Some basic terminologies`
> Note: Vertical scaling - increase RAM/My of CPU service

>       Horizontal scaling - more replicas

>		 Loadbalancers - A load balancer is a device that distributes network
or application traffic across a cluster of servers. Load balancing improves
responsiveness and increases availability of applications. One of the 
easiest methods for scaling.

#### Why Monlith are easy to build?
- Less time for initial build
- Easy installation and deployment of services
- testing of service is very easy

Next we will discuss about `Microservices`. Now **microservices** has become a
buzz-word like *AI, Machine learning, blockchain, kubernetees*. Now docker, 
kuberneetes and all have become popular. Thus making the microserice approach
very easy to use and a buzz word. As Hrishi said, please note `monolith is not 
a out-dated technology` as many think about it. It still always recommended to
use monoliths when you are building a stack with no previous experience in it.

`Extras:`[DockervsKuberneetes:Not an or question](https://www.youtube.com/watch?v=2vMEQ5zs1ko)
(Monolith is easy for start and is a predated technology)

## Micoservices
Some of the characteristics of Microservices are:
- Per Martin Fowler and other experts, services in a microservice architecture (MSA) are often processes that communicate over a network to fulfill a goal using technology-agnostic protocols such as HTTP.jj
- Increased  uptime for servers, as only one service need to made down compared to entire services.
- Using new technologies is easy
- Various Database and Language support for each services is possible like R, JS, Python. You run backend both in flask, rust and golang for various microservices.
- Helps in easy onboarding for new member and help in agile architecture of development.

### Disadvantages:
 Microservices is a distributed computing, so there is a lot of myths is here:
- All services has same IP, the network use VPC for various microservices. The UI if made network is reliable with both Photos and videos. Then broken it creates problem
- Assuming lattency is 0, stupid and create architecutre limitations
- Assume bandwidth is infinity,
- Assume network topologies are same, IP change when going to different Places the ping on further cases won't be available. Else use DNS server
- "" Network cordinators are same, IP mattan aale thapa;
- "" internal data cost is same

Using Microservice for small 2 person teams is stupid
Familar things are using microservice

How microservice communicate each other, event-driven, request-driven , token-based
