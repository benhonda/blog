# What are the disadvantages to running an app on a single instance?

A single server can take you very far. If you are optimizing for simplicity, then a single server architecture might be your best bet. But what is simplicity worth to you?

Here's what to watch out for:

- When you build your apps to run on a single node, it can take a lot of rework to make it work across multiple nodes (note: I'm using the word "node" and "server" synonymously here). You probably don't have to worry about this yet though.
- Single point of failure (SPOF). This is peoples primary concern it seems, and for good reason. This ties into High Availability (HA), which a single-server architecture would not fall into the category of. However, many would argue (including myself) that it's easier to just have a quick and dirty failover procedure than to architect this highly available thing with multiple nodes that takes some serious brain work to understand.
- Limited continuous deployment options. No blue/green deployments. You can have a staging server set up, but when it's time to flip it to production it's all or nothing.
- Not able to use Spot instances (not without a potential for downtime, at least). Maybe this is too specific to AWS, however a single-server architecture prevents you from the (potentially) huge cost savings of EC2 spot instances, since they can take your server away from you at a 2-minutes' notice. 