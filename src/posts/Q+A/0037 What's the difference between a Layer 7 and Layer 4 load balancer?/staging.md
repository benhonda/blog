---
tags:
  - load_balancing 
  - networking 
references:
  - https://www.youtube.com/watch?v=aKMLgFVxZYk
---


# What's the difference between a Layer 7 and Layer 4 load balancer?

To understand the difference we must first understand what Layer 7 and Layer 4 are. I assume you know of the TCP/IP and OSI models (where these layers come from).

I find the best way to explain this is to look at what each layer can "see", instead of what it does in networking terms. 

In Layer 4, the Transport Layer, we have access to transport layer protocols and port number. The transport layer protocols are TCP (requires connection) and UDP (connection-less). Since we don't have any extra information, a Layer 4 load balancer uses load balancing algorithms (some you might have heard of like round robin or least connections) to direct requests to the servers it is proxying. [Here is a great tool to visualize these algorithms in action](https://samwho.dev/load-balancing/)

[L4 Load Balancer diagram](L4%20Load%20Balancer%20diagram.md)

In Layer 7, the Application Layer, we have access to the data that is being sent. So in an HTTP request, that would include HTTP headers, cookies, content type. A layer 7 LB may also use load balancing algorithms, but that would come *after* the request has been "parsed" and the LB knows what direction it should go.

[L7 Load Balancer diagram](L7%20Load%20Balancer%20diagram.md)

So...
Layer 4 LB, simple, dumb, fast. 
Layer 7 LB, more granular, smarter. 