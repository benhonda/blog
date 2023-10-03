# Storage in Docker containers - how does it all work?

Research

- [https://www.youtube.com/watch?v=OAeVsjwRVe8&list=PLTk5ZYSbd9Mg51szw21_75Hs1xUpGObDm&index=12](https://www.youtube.com/watch?v=OAeVsjwRVe8&list=PLTk5ZYSbd9Mg51szw21_75Hs1xUpGObDm&index=12)

Reminder:

![Screen Shot 2023-10-03 at 10.02.29 AM](Screen%20Shot%202023-10-03%20at%2010.02.29%20AM.png)

1. Writable layers

![](Screen%20Shot%202023-10-03%20at%2010.04.54%20AM.png)

1. tmpfs (in-memory)

![](Screen%20Shot%202023-10-03%20at%2010.05.10%20AM.png)

1. Bind mounts
    1. Mount to a dir on host filesystem… that is, if I mount to `srv/` on my local computer and that dir does not exist on my remote server, it won’t work
    2. 🚨  this may be what we want for our SQLite implementation!

![](Screen%20Shot%202023-10-03%20at%2010.05.29%20AM.png)

1. Volumes (like bind mounts but managed by docker)
    1. No file locking! i.e. not good for SQLite

![](Screen%20Shot%202023-10-03%20at%2010.05.43%20AM.png)

![Screen Shot 2023-10-03 at 10.03.12 AM](Screen%20Shot%202023-10-03%20at%2010.03.12%20AM.png)

