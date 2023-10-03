---
tags:
  - networking
  - load_balancing 
---
# When do you use the AWS Application Load Balancer?

AWS ALB is just another hosted [Layer 7 load balancer](Q+A/whats-the-difference-between-layer-4-and-layer-7-load-balancers/staging.md). So when do you need a hosted L7 LB? When your app is designed with High Availability in mind, and thus your servers are distributed. In this case, the traffic needs to be directed to your machines. ALB sits in front of your machines and directs traffic. By using a *hosted* LB, you get the HA that comes with that, so your LB doesn't become a single point of failure.

Note that here, ALB is acting as an external or internet-facing load balancer. I mention this because ALB can also be launched as an internal-facing load balancer, too.

Also note: ALB MUST be deployed in a minimum of 2 availability zones!

Related:
- [What's the difference between the load balancing that Kubernetes or Docker Swarm does and the AWS ALB](Q+A/load-balancing-with-k8s-or-swarm-versus-alb/index.md)?
- [What's the difference between Nginx and ALB?](Q+A/whats-the-difference-between-nginx-and-alb/staging.md)
- [What is the difference between a Layer 4 and Layer 7 load balancer? What is Nginx/ALB?](Q+A/whats-the-difference-between-layer-4-and-layer-7-load-balancers/staging.md)

