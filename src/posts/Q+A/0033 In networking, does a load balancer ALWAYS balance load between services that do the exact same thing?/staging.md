---
tags:
  - load_balancing 
  - networking 
---

# In networking, does a load balancer ALWAYS balance load between services that do the exact same thing?

This may be an opinionated question - so to me...

Yes, the act of load balancing means distributing load across replicas of services. 

Perhaps the greyest area here is when dealing with L7 load balancers, which are capable of routing requests based on path, content type, cookies, and a bunch of other application layer things. 

In my view, however, the load balancing doesn't occur until *after* the L7 load balancer does its parsing. Here's what I mean:

[L7 Load Balancer diagram](L7%20Load%20Balancer%20diagram.md)

In this example, the requests bound for the App1 server are not even technically being load balanced at all. In fact, from the clients perspective, you could say that the load balancer is just acting as a reverse proxy for the App1 server. 

Now, you might be wondering; [is a load balancer just a reverse proxy?](Q+A/0034%20Is%20a%20load%20balancer%20a%20reverse%20proxy?/dev.md)
