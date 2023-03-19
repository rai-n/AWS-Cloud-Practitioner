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

## Beanstalk
* As a AWS developer, you don't want to manage infrastructure, but deploy code 
* E.g. You don't want to configure databases, load balances, scaling concerns, etc
* Developer centric view of developing an application on AWS using EC2, ASG, ELB, RDS, etc
* Beanstalk is all of above services in one view that's easy to make sense of
* Full control of configuration is still available
* Beanstalk is platform as a service
* Beanstalk itself is free but costs are associated with underlying instances
* Beanstalk is a managed service
* instance configuration is configurable, but handled by Beanstalk
* Beanstalk has capacity provisioning (automatically specifying number of data reads and writes per second), load balancing and auto-scaling
* Beanstalk takes care of health monitoring and responsiveness
* Architecture models
1. Single instance deployment (Good for dev)
2. LB + ASG (Good for production web applications)
3. ASG only (Great for non-web workers in production - workers, etc)
* Beanstalk Health monitoring
1. Health agent pushes metrics to CloudWatch
2. Checks for app health, pushes to health events

### Difference between Beanstalk and Cloud formation
* Beanstalk is application focused and upload your code and beanstalk will find a way to run the code and do it for you. Cloud formation is infrastructure focused and allows system engineers to create infrastructure as code. E.g. they can create templates for an infrastructure which can be repeatable in different regions or accounts.

## CodeDeploy
* Use to deploy application automatically
* Works with EC2 instances and on-premise servers from v1 to v2, etc
* Hybrid service (both EC2 and on-premise servers)
* Servers must be provisioned and configured ahead of time with CodeDeploy agent

## CodeCommit
* Before pushing code to servers it has to be stored and usually this is done using Git. 
* CodeCommit is AWS's competing product 
1. Source control service that hosts git-based repositories
2. Makes it easy to collaborate with others
3. Code changes are automatically versioned
* Fully managed 
* Scalable and highly available 
* Private, secured and integrated with AWS

## CodeBuild
* Code building service in the cloud
* Compiles the source code, run tests and produces packages that are ready to be deployed (E.g. by CodeDeploy)
* CodeCommit <- (Retrieves Code) Code Build -> Ready to deploy artifact
* Fully managed and serverless
* Continuously scalable & highly available
* Secure
* Pay as you go pricing, only pay for build time

## CodePipeline
* This orchestrates the steps to automatically push code to production
* Code => Build => Test => Provision => Deploy
* Basis for CI/CD (Continuous integration and continuous delivery)
* E.g. CodeCommit -> CodeBuild -> CodeDeploy -> Elastic Beanstalk
* Fully managed, compatible with CodeCommit, CodeBuild,CodeDeploy, ElasticBeanstalk, CloudFormation, GitHub, 3rd party services, custom plugins, etc
* Fast delivery & rapid updates

## CodeArtifact
* Software packages depend on each other to be built (dependency)
* Storing/ retrieving these dependencies is called artifact management
* CodeArtifact is secure, scalable, cost-efficient artifact management for software development
* Works with all common dependency management tools such as Maven, Gradle, npm, yarn, twine, pip, nuget, etc
* Developers and CodeBuild can retrieve dependencies straight from CodeArtifact instead of creating own artifact management system

## CodeStar
* Unified UI to easily management software development activities in one place
* Start a project and CodeStar will give dashboard and provides a quick way to get started with setting up CodeCommit, CodeBuild, CodeDeploy, CodePipeline, Elastic Beanstalk, EC2, etc

## Cloud9
* It is a cloud IDE for writing, running and debugging code
* Cloud9 IDE can be used within a web browser from anywhere through the internet
* Allows pair programming in real time

## Systems Manager
* Helps manage EC2 and on premise systems at scale (Hybrid service)
* Get operational insights about state of infrastructure
* Most important features:
1. Patching automation for compliance on all servers/ instances
2. Run commands across entire fleet of servers
3. Store parameter config with the SSM Parameter Store
* Works with Windows and Linux OS servers
* How to make it work?
1. Install SSM agent onto EC2 instance or on premise VM (installed by default on Amazon Linux AMI & some Ubuntu AMI)
2. With SSM agent, we can run commands, patch & configure fleet of servers

## SSM Session Manager
* Allows you to start a secure shell on EC2 or on-premise servers (hybrid service)
* No SSH access, bastion hosts, or SSH keys needed
* No port 22 needed (better security)
* How it works?
1. EC2 instance or on-premise server has an SSM agent which is connected to the Session Manager service and executes command on it 
* Supports Linux, macOS and Windows
* Send session log data to S3 or CloudWatch logs
// continue later

## OpsWorks
* OpsWorks was made to get a managed "Chef" and "Puppet" service for server configuration automatically, or repetitive actions in the cloud
* It's an alternative to SSM
* Can only provision standard AWS resources such as EC2 instances, DB, LB, EBS, etc 
* If "Chef" and "Puppet" needed, then OpsWorks
* If migrating from "Chef" and "Puppet" templates then it can easily work on AWS using OpsWorks which has the ELB (ALB), Application layer (EC2), Database layer (RDS) and application information is fetched from Cookbook repository and application information from application repository
  Q: How is AWS OpsWorks Stacks different than AWS Elastic Beanstalk?

> AWS OpsWorks Stacks is a configuration management platform while AWS Elastic Beanstalk is an application management platform.
  AWS Elastic Beanstalk is an easy-to-use service for deploying and scaling web applications and services developed with Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker. Customers upload their code and Elastic Beanstalk automatically does the rest.

> AWS OpsWorks Stacks and AWS Elastic Beanstalk both automate operations but serve different needs and purposes. AWS Elastic Beanstalk is designed for developers who want to deploy web applications without worrying about operations. Developers simply upload their code and Elastic Beanstalk automatically handles the deployment, from capacity provisioning, load balancing, auto-scaling to application health monitoring. The application will be ready to use without any infrastructure or resource configuration work on the developer’s part.

> In contrast, AWS OpsWorks Stacks is an integrated configuration management platform for IT administrators and DevOps engineers who want a high degree of customization and control over operations. AWS OpsWorks Stacks users leverage Chef recipes to automate operations like software configurations, package installations, database setups, server scaling, and code deployment.