# Do I do less maintenance on my EC2 instances if I run all my apps in Docker containers?

Since they will run with their own OS, I am just using the hardware of the instance, right? Or no…


Updated Oct 3:

You would still have to do the same maintenance on the server. However, with all your apps in containers, it would certainly be easier to decouple your apps from the server completely such that you could tear down and deploy new infrastructure instead of patching. This is an area where Infrastructure as Code (IaC) shines.