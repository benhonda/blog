---
tags:
  - load_balancing 
  - networking 
---

# Is a load balancer a reverse proxy?

TLDR; IMO, all load balancers are reverse proxies but not all reverse proxies are load balancers. Load balancers are reverse proxies because they sit between the internet and backend services and to the client, they act as the "proxy" to the server. 

To answer this, I feel like I need to make some opinionated definitions. 

A load balancer, in networking, is anything that distributes a load across multiple services. These services can be containers, servers, whatever.

A forward proxy sits between clients and the internet. 

A reverse proxy sits between the internet and services. 


[![Forward vs. Reverse Proxy: Benefits & Use Cases in 2023](https://research.aimultiple.com/wp-content/uploads/2022/10/forward-proxies-vs.-reverse-proxies.png)





Analogy:

There are 100 people in line at Starbucks. The cashier is ultra fast and can take down orders in seconds. Once an order is placed, the cashier tells the workers behind her what to do (make coffee, prepare food, clean up, etc.). The workers do their job and give the cashier the order, then the cashier gives the order to the customer and the transaction is complete.

In this situation, the customer is the client, the cashier is the reverse proxy, and the workers are the services. 

Here's a load balancing one.

There are 100 people in line at Starbucks. The cashier is ultra fast and can take down orders in seconds. They only serve coffee at this Starbucks, so all the workers are manning coffee stations. Once an order is placed, the cashier tells which worker to start brewing the coffee. The cashier just goes from left to right picking the workers sequentially. Once a coffee is ready, the worker hands it to the cashier and the cashier gives it to the customer.

In this situation, the customer is the client, the cashier is the load balancer who is balancing the load using a round-robin algorithm, and the workers are the services.


But do all the services have to be the same????????????

See [In networking, does a load balancer ALWAYS balance load between services that do the exact same thing?](Q+A/0033%20In%20networking,%20does%20a%20load%20balancer%20ALWAYS%20balance%20load%20between%20services%20that%20do%20the%20exact%20same%20thing?/staging.md)

