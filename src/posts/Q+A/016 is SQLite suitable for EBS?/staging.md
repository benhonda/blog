---
tags:
  - sqlite
  - aws
  - aws_ebs
---
# Is EBS Suitable for SQLite?


## Concurrency

[ECS Best Practices - Persistent storage](https://docs.aws.amazon.com/AmazonECS/latest/bestpracticesguide/storage.html) says 
>The most distinctive difference between Amazon EFS and Amazon EBS is that you can simultaneously mount an Amazon EFS file system on thousands of Amazon ECS tasks. In contrast, Amazon EBS volumes don't support concurrent access. Given this, Amazon EFS is the recommended storage option for containerized applications that scale horizontally. This is because it supports concurrency.

However, [Attach a volume to multiple instances with Amazon EBS Multi-Attach](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volumes-multi.html) says
> Amazon EBS Multi-Attach makes it easier for you to achieve higher application availability in clustered Linux applications that manage concurrent write operations.

So... does concurrency work? I think so. More tests are needed.

## Network

One of the main drivers to use SQLite for your web apps is the lack of network hops to read and write from the DB. Take this away, and traditional client-server database servers are more appealing. 

EBS drives are attached over the network \[1]. However, many EBS types are optimized for sub-millisecond latency. So maybe it's not a "true" network hop? (I don't know the underlying infrastructure). Also, AWS talks about [Storage Area Networks (SANs)](https://aws.amazon.com/ebs/features/). 

## High Availability (HA)

Since SQLite would be decoupled from our servers, using SQLite on EBS with multi-attach means we can horizontally scale our servers without having to deal with the complexity that comes with horizontally scaling SQLite. 

This isn't just HA though - decoupling our database from the server gives us the ability to do a lot more things, like:
- Tear down and deploy EC2 instances as we please, thereby also making spot EC2 instances a viable option
- Attach Auto Scaling Groups to manage CPU/RAM usage. 


## Data Durability

[EBS promises 99.999% durability](https://aws.amazon.com/ebs/features/) (1 in 100,000 go bad).


## Conclusion

Despite all this, is EBS suitable for SQLite? I think so - but more research is needed. Like, what bottlenecks will EBS impose, if any?


## References

1.  [On the SQLite forum, this guy](https://sqlite.org/forum/info/248a387085e10557ee71af2af27fd3a2e049a63436f50471d201f99a159e444c) says that EBS drives are attached over the network. [From this Quora discussion](https://www.quora.com/Does-AWS-really-keep-EBS-volumes-and-EC2-instances-on-the-same-physical-host-or-is-EBS-volume-at-a-remote-location-like-a-NAS-or-SAN), he appears to be right. It makes sense though. How could AWS afford to attach these volumes directly to the instances.


## Appendix

On a Fargate note:
> Support for Amazon EBS volumes isn't available for tasks on Fargate


