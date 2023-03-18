## Cloud formation 

* Cloud formation is a declarative way of outlining your AWS infrastructure, for any resources (most of them are supported)
* For a Cloud Formation template you can say:
1. I want a security group
2. I want two EC2 instance using this group
3. I want S3 bucket
4. I want a load balancer (ELB) for these machines
* Infrastructure as code (no more manual resources to be created), good for repeating an architecture in different environments, regions or AWS accounts.
* Changes to infrastructure are reviewed through code
* Cost (Each resource within the stack is tagged with an identifier so u can breakdown how much a stack costs you)
* You can estimate the cost using Cloud Formation template
* Savings strategy. In dev, you could automate deletion of templates at 5 PM and recrate at 8 AM safely
* Productivity 
1. CAn destroy or recrate an infrastructure on cloud on the fly 
2. Automated generation of diagram for templates
3. Declarative programming (no need to figure out ordering and orchestration, cloud formation will automatically figure out the order)
* Can use existing templates on the web
* Leverage documentation
* Supports almost all AWS resources, and "custom resources" for resources that are not supported

* Cloud formation Stack Designer shows the resources for an infrastructure ure as well as the relations between the components

## AWS Cloud Development Kit (CDK)
* Define cloud infrastructure using familiar language like JS/TS, Python, Java, etc. 
* Code is compiled into Cloud Formation template (YAML OR JSON)
* Can deploy infrastructure and application runtime together
1. Good for lambda functions and docker containers in ECS/ EKS