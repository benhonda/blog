# When is ECS Fargate cheaper than ECS EC2?

According to [this blog post](https://aws.amazon.com/blogs/containers/theoretical-cost-optimization-by-amazon-ecs-launch-type-fargate-vs-ec2/), which has been spread around the internet, “the greater the capacity utilization of the \[EC2] instance, the more cost effective the EC2-based launch.” In other words, when we can use an EC2 instance to its full capacity in terms of CPU and Memory, ECS EC2 is up to 30% cheaper than using ECS Fargate. The blog post notes that the cost analysis does not include the cost of the Elastic Block Storage (EBS), which is something we have to pay for with EC2.

At my company, we were hosting up to 10 web applications on a single t3.large EC2 instance. We were able to do this because most of them were hardly hit with requests—we’re talking maybe 100 requests per day. Based on my research, I don’t think this is an ideal situation to switch to Fargate. With Fargate, you run tasks or pods to run your application. For a web app, you probably want it to be accessible 24/7. Using the ever-confusing Fargate pricing calculator, it is estimated that running 1 task (the practical minimum for running 1 web app) with the cheapest configuration (ARM architecture, 0.25 vCPU and 0.5 GB memory allocated, 20 GB ephemeral storage) would cost 7.93 USD per month. We can probably bring this down about 33% cheaper with a 1-year commitment and paying up front. ~5.30 USD, not bad for a web app that can scale. With our 10 web app setup, we’d be running ourselves about 55 USD per month. But again, we’re running on the bare minimum configuration. Is this enough for my apps? How the hell should I know?

If you have a fat app, you’re going to need more vCPU and more memory. Going to 0.5 vCPU and 1 GB of memory (as required when we bump to 0.5 vCPU) doubles the cost of each task.

So what is the solution? Are requirements are as follows:

Questions generated from writing this:

- How much vCPU and Memory does my app need?
- Can I run my app in a single Fargate task or is it going to require more than one?/can I run a django app in a single fargate task?
- Can I use Fargate with SQLite?
- How does SQLite manage multiple writes?
    - Can I use celery to manage writes to my SQLite?
    - Is this what write-ahead logging (WAL) is?