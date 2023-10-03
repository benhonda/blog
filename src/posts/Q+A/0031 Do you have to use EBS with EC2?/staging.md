---
tags:
  - aws
  - aws_ec2
  - aws_ebs
---
# Do you have to use EBS with EC2?

No, you do not have to attach an external EBS volume when you deploy an EC2 instance. This is because EC2 has it's own built-in storage that it can use. This storage option, however, is ephemeral, meaning that it will be destroyed when the instance is terminated. 

For web applications, you might want to attach an EBS volume so that you can design your systems with the intention of tearing down old servers and bringing up new ones. The serverless people will tell you to "treat servers like cattle, not pets."

However, given that EBS storage is network-based, it's [probably not suitable for SQLite](Q+A/0032%20Is%20EBS%20Suitable%20for%20SQLite?/staging.md) (which I use a lot). In these cases, you can use the onboard EC2 instance storage and something like [Litestream](https://litestream.io/) to continuously stream backups to S3 (minimizing the data-loss window).

However (again), since you'll be using instance storage, you can't horizontally scale your apps on this architecture without horizontally scaling SQLite (not trivial to do).