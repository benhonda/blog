# How is Amazon EBS affected by installing dependencies inside my EC2 instance with something like pip install or npm install?

- EBS deep dive: [https://www.youtube.com/watch?v=kaWzAEVZ6k8](https://www.youtube.com/watch?v=kaWzAEVZ6k8)

An EBS volume (just an SSD or HDD, usually SSD unless we are storing massive amounts of data and don’t need I/O speed) is mounted to a path inside EC2. For example, this might be `/var/www/`. In this case, all of the data inside `/var/www/` lives on our EBS volume. When we run `pip install` or `npm install` we are downloading dependencies into a virtual env folder or `node_modules/` folder, respectively. Therefore, all the dependencies' "weight" is downloaded onto our attached EBS volume and occupies space there, similar to how the `node_modules/` directory occupies space on our computer during development.

See this video for more info: [https://www.youtube.com/watch?v=EdRE1EH_G-4](https://www.youtube.com/watch?v=EdRE1EH_G-4)