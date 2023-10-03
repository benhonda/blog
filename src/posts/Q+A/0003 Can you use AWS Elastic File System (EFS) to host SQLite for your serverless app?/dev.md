# Can you use AWS Elastic File System (EFS) to host SQLite for your serverless app?

**Short answer: yes, but.**

Yes, but the N+1 problem comes into play when you make requests over the network to your SQLite database.

Yes, but this would fall into the “inappropriate uses” category on the [official SQLite website](https://www.sqlite.org/whentouse.html)

Yes, but read this guys article: [https://paulbradley.dev/sqlite-efs-serverless-database/](https://paulbradley.dev/sqlite-efs-serverless-database/) and this guys article: [https://www.lambrospetrou.com/articles/aws-lambda-and-sqlite-over-efs/](https://www.lambrospetrou.com/articles/aws-lambda-and-sqlite-over-efs/)

Yes, AND costs can go to almost pennies.

Questions:

- does any distributed SQLite system suffer from this too? How the hell does LiteFS pull this off? Or do they not?
- Is this even true? Can EFS live ******with****** the lambda function and thus be like an embedded database