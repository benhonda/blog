# What is the database N+1 problem and why is SQLite immune to it?

Most of this information, including all graphics, is from the _[SQLite and the N+1 (no) problem](https://www.youtube.com/watch?v=qPfAQY_RahA)_ video by [Mycelial](https://www.youtube.com/@mycelial1653) on YouTube. Go watch that video.

The N+1 problem can be simplified to this:

> For a given query, we do N more queries. And queries are slow.

For example, say we are querying books in or database. For each of those books, we want to grab the reviews for them. We can query all our books in one query and then for each of these books, we query the reviews. N+1.


![](Screen%20Shot%202023-10-03%20at%209.40.04%20AM.png)
This snippet comes from ****SQLite and the N+1 (no) problem**** by [Mycelial](https://www.youtube.com/@mycelial1653) on YouTube

The N+1 problem really just says:

1. We are doing a lot of queries
2. Queries are expensive

For Problem 1, there are a lot of techniques to reduce the amount of queries we hit our database with. These range from simple to complicated and are not specific to any 1 database, so clearly this is not the source of SQLite’s immunity to the N+1 problem.

Problem 2 doesn’t exist in SQLite land. Why? Long story short, because SQLite is an embedded database as opposed to a client-server database, that is, requests to SQLite do not travel over the internet. Most of the query latency comes from network time. The [YouTube video](https://www.youtube.com/watch?v=qPfAQY_RahA) that inspired this post provides a simple graphic visualization of the time taken for a basic read request to a Postgres database, highlighting this fact:


![](Screen%20Shot%202023-10-03%20at%209.40.49%20AM.png)
In conclusion? Use SQLite and you can suck at database administration!

Read more about it here [https://sqlite.org/np1queryprob.html](https://sqlite.org/np1queryprob.html)

