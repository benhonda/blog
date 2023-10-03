---
tags:
  - networking 
  - load_balancing
---
# Load balancing with K8s

[What is the difference between Load Balancer and Reverse Proxy?](https://serverfault.com/questions/127021/what-is-the-difference-between-load-balancer-and-reverse-proxy)

From https://www.nginx.com/resources/glossary/layer-7-load-balancing/, A device that performs Layer 7 load balancing is often referred to as a _[reverse‑proxy server](https://www.nginx.com/resources/glossary/reverse-proxy-server/)_.



- [https://stackoverflow.com/questions/40601012/distributed-application-is-load-balancer-single-point-of-failure](https://stackoverflow.com/posts/70074723/timeline)
	- I'm also looking into this now in 2021. Although the easy options like NGINX are really convenient they do seem to provide a single point of failure.
	- The solution today is to use a Kubernetes or Docker Swarm approach it seems which become very complex, but have load balancing built into every node or at least a master which fails over.
	- Failing that, a cloud based load balancer from one of the big boys like Google, AWS or Azure might give the necessary uptime.

