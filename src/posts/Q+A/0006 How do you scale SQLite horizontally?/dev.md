# How do you scale SQLite horizontally?

Resources:

- [https://blog.wesleyac.com/posts/consider-sqlite](https://blog.wesleyac.com/posts/consider-sqlite)

First of all, what is horizontal scaling? Briefly:

- Scaling out, not up
- Like going from 1x Toyota Camry, to 2, to 3, etc. Versus vertical scaling, which would be going from 1x Toyota Camry to 1x 458 Ferrari
- In tech terms, you add more machines to your fleet instead of just adding more compute or memory to you machine(s).

When people talk about autoscaling, they are usually talking about horizontal autoscaling, which involves automatically adjusting the number of machines (virtual machines, containers, etc.) that are running your application. For instance, if you package your web application into containers, you can deploy it on ECS Fargate in AWS. This way, your application becomes "scalable", as ECS can horizontally scale it by controlling the number of instances running your application based on traffic.

That’s horizontal scaling as it pertains to your application. But what about your database? Traditionally, horizontal scaling of databases involves a concept called sharding, where you break down your data into smaller chunks and you run it on multiple machines (it’s similar to application-level horizontal scaling in this way). Spreading related data across nodes is difficult with relational databases, so businesses will typically opt for vertical scaling of their database servers first unless their traffic becomes too much for their machines or they have alternative business reasons to scale out. I don’t have a solution for horizontal scaling. It’s hard, and you probably need a team to manage and maintain it (but, similarly, you’d have to have a team to manage a really really large database running on a fat server, [see how Expensify does it here](https://blog.expensify.com/2018/01/08/scaling-sqlite-to-4m-qps-on-a-single-server/))

But WAIT! You may have noticed I said “database server”, which SQLite is not. SQLite lives with your application, which means that to horizontally scale your application, you’d need to horizontally scale your database, which, as we just mentioned, is not a trivial thing to do. So really it’s not so much a question of “How do you scale SQLite horizontally?”, it’s more a question of “How do you scale an application horizontally with an SQLite database?”

My answer to this, as of today (August 2023) and in my limited experience, is that if you really need to horizontally scale it’s probably a better idea to decouple your application from your database, which doesn’t mean you ****have**** to leave SQLite, but it does mean that you would be using SQLite in what would be classified as an “inappropriate use-case”, [as defined by the SQLite documentation](https://www.sqlite.org/whentouse.html). I think if you’re at the point where it is necessary to scale SQLite horizontally, you should probably be using a quote-unquote “real” database like Postgres or MySQL. Again, keep in mind, I don’t know much.