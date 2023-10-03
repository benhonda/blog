# What the hell is even a serverless?

Resources:

- [https://www.trek10.com/blog/is-fargate-serverless](https://www.trek10.com/blog/is-fargate-serverless)

Serverless means different things to different people. Here’s how I conceptualize it.

“Serverless is a spectrum”

From [Ben Kehoe of iRobot](https://aws.amazon.com/heroes/usa/ben-kehoe/) via Way back machine ([https://web.archive.org/web/20180108070250/https://read.acloud.guru/fargate-serverless-and-the-difference-between-managed-infrastructure-and-managed-code-e72f5f0d5ea](https://web.archive.org/web/20180108070250/https://read.acloud.guru/fargate-serverless-and-the-difference-between-managed-infrastructure-and-managed-code-e72f5f0d5ea))

Containers are orthogonal to serverless-ness. They are, from a high-level application architecture perspective, VMs — just extremely lightweight VMs. If you have a container that is active when it is not handling data, it is a server.

Their ability to be started and stopped, created and thrown away is one of the things that _enables_ many implementations of serverless platforms. But if you start one up and run a Node process that listens for requests, handles multiple requests simultaneously in the same process, and sits idle if no requests are made — _that’s a server_.

Part of the problem is that people are conflating the _application notion_ of a server which is about software — with the _infrastructure notion_ of a server which is about instances and/or heavyweight proper VMs.

Serverless is about having _neither_. Not having VMs in EC2 is not sufficient to be serverless. Azure Container Instances demonstrate this well — containers are really not that different from instances.

Not having VMs is about _managed infrastructure_ — not having application-level servers is about _managed code_. If you have neither, you’re serverless.

Fargate is running application-level servers on completely managed infrastructure. So, kinda serverless.

Cool from [Ben Kahoe’s twitter](https://twitter.com/ben11kehoe):

Living the serverless dream: Christmas Day 2021, when everybody who has bought a Roomba since Black Friday opens them in about a four hour window on Christmas morning, was completely hands off keyboard for us. Literally nothing needed to handle the massive influx of traffic.