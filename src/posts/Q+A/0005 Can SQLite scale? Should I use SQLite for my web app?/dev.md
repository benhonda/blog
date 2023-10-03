# Can SQLite scale?/Should I use SQLite?

Resources:

- [https://blog.wesleyac.com/posts/consider-sqlite](https://blog.wesleyac.com/posts/consider-sqlite)
- [https://fly.io/blog/all-in-on-sqlite-litestream/](https://fly.io/blog/all-in-on-sqlite-litestream/)

Yup, another “Should I use SQLite” blog. There are some good articles out there making a strong case for SQLite in production and its capability to handle your shitty web app. The question of if SQLite can scale is a tricky one (and one that I am certainly not qualified to answer) because, as always, it depends. There are tradeoffs. Here are some tradeoffs and why I am ok with them.

| Negative |Justification|
|---|---|
|Using SQLite means you can’t go serverless—at least not without sacrificing some of the features that make embedded databases like SQLite so attractive.|So I can’t go serverless. At least, not totally serverless (See my article on what the hell a serverless even is). I’m probably going to end up paying more for my infrastructure and now I have a server to patch/upgrade/maintain/scale. But hey, I can keep it as simple as I like.|
| ||

Questions:

- When is the right time to geographically shard?
- Is serverless right for web apps?