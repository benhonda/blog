---
tags:
  - aws
  - aws_fargate
  - aws_ec2
---
# What does "Spot" mean in AWS land? (i.e. EC2 Spot, Fargate Spot)

From: https://saturncloud.io/blog/what-sort-of-workloads-would-be-appropriate-for-use-on-amazon-ec2-spot-instances/
>Amazon EC2 Spot Instances are a type of Amazon Elastic Compute Cloud (EC2) instance that allows you to bid on unused EC2 capacity. This unused capacity is made available to you at a lower price than the regular On-Demand price, allowing you to run your workloads at a reduced cost.
>
>The catch is that Amazon can reclaim these instances at any time if the Spot price goes above your bid price. When this happens, your instance will be terminated and any workloads running on it will be interrupted. However, if your application is fault-tolerant and can handle interruptions, you can save a significant amount of money by using Spot Instances.

When you hear "Spot", think "spare", as in, "spare resources". AWS has provisioned these machines for clients and clients aren't using all of the resources in it. So you can borrow some of those resources (until the person whose machine you're using needs the resource, then you get kicked off). 