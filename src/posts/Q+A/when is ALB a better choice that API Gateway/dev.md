---
tags:
  - q_and_a
  - aws_alb
  - aws_api_gateway 
---
# When is ALB a better choice that API Gateway

ALB may be a better choice than API Gateway when:

- You have a monolith app running (on servers?)
	- Then you can just plop ALB in front of your servers 
	- ALB can integrate into your stack near seamlessly (is this true?), whereas API Gateway may require refactoring of your stack
	- 
- You have consistent traffic and only want a load balancer (because of cold starts on APIGW?)



When what you need is purely a load balancer, of course!