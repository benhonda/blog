# Sharing SQLite across Docker containers - is it realistic and why the hell would you do that?

Research

- From this: [https://rbranson.medium.com/sharing-sqlite-databases-across-containers-is-surprisingly-brilliant-bacb8d753054](https://rbranson.medium.com/sharing-sqlite-databases-across-containers-is-surprisingly-brilliant-bacb8d753054)
    - “For all practical purposes, there is precisely one solution: SQLite. It turns out that multi-process concurrency is one of the things that separates SQLite from the other best-of-breed embedded databases. It is a practically unique feature — its raison d’être, at least from this perspective.”
    - “_Containers are just processes_, and SQLite is _really good_ at sharing a database across processes.”

For simplicity of course! Is it realistic? We need to test that of course. The idea is that each container has the same volume mounted to it where the SQLite file lives.

- Does this allow us to scale horizontally?
- Will we run into concurrency issues with this setup?

About container storage - [see my Storage in Docker containers article](https://www.notion.so/Storage-in-Docker-containers-how-does-it-all-work-b98f217f474347f8b61685a95a9774d2?pvs=21) - we would need to use bind mounts and NOT volumes because volumes don’y have file locking, which (I think?) is required for SQLite to work properly.

[Aside: this is what [our research article does](https://rbranson.medium.com/sharing-sqlite-databases-across-containers-is-surprisingly-brilliant-bacb8d753054), so check ✅]


![](Screen%20Shot%202023-10-03%20at%2010.03.12%20AM.png)
From [https://docs.docker.com/storage/bind-mounts/](https://docs.docker.com/storage/bind-mounts/)
