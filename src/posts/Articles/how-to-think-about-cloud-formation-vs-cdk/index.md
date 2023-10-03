---
deploy: false
research:
  - url: https://blog.shikisoft.com/aws-cdk-vs-cloudformation/ 
tags:
  - #IaC 
  - #DevOps 
---
# How to think about AWS CloudFormation versus AWS Cloud Development Kit

![](Screen%20Shot%202023-09-27%20at%209.24.13%20PM.png)


- CDK simplifies CloudFormation features
- Kinda-sorta, CDK is like Pulumi and CloudFormation is like Terraform.
	- Pulumi lets you code in your favourite programming language. So does CDK.
	- Terraform uses it's own language, HashiCorp Language (HCL). CloudFormation, though still utilizing JSON/YAML files, has its own strict configuration.
- By allowing you to code in a programming language, CDK allows you to write control flow statements like loops, whereas CloudFormation uses simple JSON/YAML so this is not possible.
- CDK provides default configuration for you via abstraction. "Therefore, even if you don’t know the AWS service well, you can still create resources following AWS best practices."
- 
- ### CDK is to CloudFormation what an ORM is to SQL. - I just came up with that - is it correct?

