---
tags:
  - aws 
  - aws_alb 
  - nginx
  - networking 
---

# What's the difference between NGINX and ALB? 

NGINX is capable of doing Layer 7 *and* Layer 4 load balancing. ALB is AWS' Layer 7 load balancer. NLB is AWS' Layer 4 load balancer. [NGINX says themselves](https://www.nginx.com/blog/aws-alb-vs-nginx-plus/#compare) that "\[NGINX] works well in tandem with Amazon’s NLB." From this I gather that ALB and NGINX have a lot of overlap, where you probably only need one or the other.

As such, it might make more sense to just compare NGINX's L7 capabilities against ALB. NGINX is perhaps more fully featured, as it offers (at the time of writing) caching, rate limiting, multiple load balancing algorithms, and more out-of-the-box, which ALB does not.

However, being a managed AWS service, ALB can scale up and down to meet the demand of your services. As [this reddit-er put it](https://www.reddit.com/r/devops/comments/10875aa/comment/j3qi2tn/?utm_source=share&utm_medium=web2x&context=3), "ALB is \[really] just another common service like nginx under the hood. What they built is the automation." This can be huge, especially since, for example, if you have a single node running NGINX you have created a single point of failure.



