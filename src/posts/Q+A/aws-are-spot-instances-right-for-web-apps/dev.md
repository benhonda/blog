---
tags:
  - aws
  - aws_fargate
  - aws_ec2
---
# Are Spot instances right for web applications?

[What does "Spot" mean?](Q+A/aws-what-does-spot-mean-in-aws-land/dev.md)

Maybe...

- Since AWS can reclaim the server though, the web server must be stateless (i.e., no SQLite?????????????).
	- What if I'm using EBS??????
- Your web app should also be able to run on different instance types (like t3 vs. m5) such that you can replace interrupted instanced with instances from other *pools* (instance that have the same type, OS, and AZ).

Maybe not...

- EC2 Spot gives a 2-min heads-up when it's about to take your capacity away. If you're using ALB, you have to create your own hook to put the server in the "draining state" (also known as the deregistration delay) that lasts for 120 seconds or less (AWS recommends 90 seconds), which stops the ALB from routing requests there while allowing ongoing requests to complete. [In this blog post](https://aws.amazon.com/blogs/compute/running-web-applications-on-amazon-ec2-spot-instances/), AWS tells you how you can catch the interruption notice, put the affected instance into the draining state and tell the ASG to launch a replacement instance using EventBridge, Lambda, and AWS Systems Manager. 
	- EventBridge: Catch Spot Instance Interruption Notice and trigger Lambda
	- Lambda: Call DetachInstances API of EC2 Auto Scaling to put the instance into the draining state. If *ShouldDecrementDesiredCapacity* parameter is false, EC2 Auto Scaling attempts to launch replacement Spot Instance capacity according to your instance type selection and allocation strategy.
	- Systems Manager "Run" Command: Perform operations to gracefully stop your app, like closing DB connections etc.
	Here is how they do it: https://github.com/awslabs/ec2-spot-labs/tree/master/ec2-spot-interruption-handler 
  Seem like a lot of work? But I guess the savings are up to 90%.

## What is the downtime situation? Can I avoid it entirely?

My guess: Yes, well, mostly. I think some requests will drop when the ALB doesn't pick up on the dead server right away. Actually no, that is the whole point of the [deregistration delay](https://github.com/awslabs/ec2-spot-labs/tree/master/ec2-spot-interruption-handler)

From [this other blog post](https://aws.amazon.com/blogs/compute/best-practices-for-handling-ec2-spot-instance-interruptions/), 
>At the time of writing this blog post, less than 5% of Spot Instances are interrupted by EC2 before being terminated intentionally by a customer, because they are automatically handled through integrations with AWS services.

