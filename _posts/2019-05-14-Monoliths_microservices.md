In this article, I will be talking about monoliths and microservice system 
architecture. Recently [Hrishikesh Bhaskaran](https://twitter.com/_stultus) gave
a talk on this topic at Facebook F8 meetup. This talk inspired me and changed
my thoughts about both. So I am going to highlight some of key takeways in this
blogpost.
(Still not completed)

Difference b/w monolith and microservice - user feed, photos, auth
Vertical scaling - increase RAM/My of CPU service
Horizontal scaling - more replicas

Why Monlith is easy?
- easy build time
- testing

Load balancers - imp for monoliths, Microservice is a buzz-word
(Monolith is easy for start and is a predated technology)

## Micoservices

- Testing all things when project increases, agile increases
- increase time for uptime
- Using new technologies is easy
- Language support is main thing like R, JS, Python

### Disadvantages:
- Different protocols, things lke that
- It's a distributed computing, so there is a lot of myths is here:
- All services has same IP, the network use VPC for various microservices. The UI if made network is reliable with both Photos and videos. Then broken it creates problem
- Assuming lattency is 0, stupid and create architecutre limitations
- Assume bandwidth is infinity,
- Assume network topologies are same, IP change when going to different Places the ping on further cases won't be available. Else use DNS server
- "" Network cordinators are same, IP mattan aale thapa;
- "" internal data cost is same
- Helps in architecturing team
- keeps differents Databases

Using Microservice for small 2 person teams is stupid
Familar things are using microservice

How microservice communicate each other, event-driven, request-driven , token-based
