---
tags:
  - load_balancing 
  - aws
  - aws_alb
  - aws_api_gateway
---


# How to think about Application Load Balancer vs API Gateway

- ALB is a load balancer (layer 7 load balancer, hence "application" LB)
- API Gateway does many things, including load balancing

- ALB can have cold start
- API Gateway has no cold start

- "API gateways are typically single-point-deployment proxies, designed to create a coherent public interface out of a disparate group of services." - [hackernews](https://news.ycombinator.com/item?id=21589508)

- API Gateway has a 30s timeout, versus 4000s for ALB. So long requests are a no go

- The ALB has one primary job - balance the load amongst backend services.
- APIGW is really just deploying an API - just serverless-ly - which may be more than what you need (?)

- "API Gateway can manage and balance out network traffic just as a Load Balancer, just in a different way. Instead of distributing requests evenly to a set of backend resources (e.g. a cluster of servers), an API Gateway can be configured to direct requests to specific resources based on the endpoints being requested" - [dashbird](https://dashbird.io/blog/can-api-gateway-act-load-balancer/)


Maybe a better question is: [when is ALB a better choice that API Gateway?](Q+A/when%20is%20ALB%20a%20better%20choice%20that%20API%20Gateway/dev.md)

![ALB vs API GW|100%](ALB%20vs%20API%20GW%20drawing.md)
