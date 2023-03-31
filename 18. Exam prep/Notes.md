## Interesting notes

* Active passive failover, when you want a primary resource to be available most of the time and secondary resource on standard in case all primary resources become unavailable
* Active active failover, when all resources are active until a resource becomes unhealthy it is not used
* AWS inspector is an automated, security assessment service that helps you check for unintended network accessibility of your EC2 instances and for vulnerabilities there. Inspector assessments are offered as pre-defined rules packages mapped to common security best practices and vulnerabilities
* AWS customers can carry out penetration test
* AWS Cost Explorer lets you visualize understand and manage AWS costs and usage over time. It gives you a detailed breakdown of cost going back 12 months and also allows you to forecast future costs
* AWS Cost and Usage Reports - contains the most comprehensive set of data available, provides raw data which can be sent to S3 and then processed with Athena
* AWS Budgets give the ability to set custom budgets that alert when the cost or usage (or are forecasted to exceed) budget amount. Can also be used when utilization drops below a target. Can be created at monthly, quarterly or yearly level
* AWS Pricing calculator lets you check out AWS services and find the cost of services on AWS. E.g. modelling the infra before building them to see how much it will cost
* AWS Personal Health Dashboard provides alerts and remediation guidance when AWS is experiencing events that might affect you. It is not used to get operational insights of AWS resources.
* EBS is high performant block storage service, cannot be accessed by multiple EC2 instances simultaneously
* You can create Snapshots to back up EBS since data is divided into blocks. You have to use AWS backup to create backups for storing backups of EFS 
* An Amazon Machine Image (AMI) is basically a copy of the disk that will be attached to a newly-launched instance. It is normally just the boot disk, but an AMI can actually contain multiple disk images.
* AWS provides a number of AMIs with pre-loaded operating systems such as Windows, Amazon Linux and Ubuntu. Some of them contain additional software, such as Windows with SQL Server.
* There are also community AMIs that are created by somebody other than AMI, but shared to all users. For example, a company might load a demo version of their software onto the AMI, so customers can simply launch an Amazon EC2 instance and it will have all software already loaded and configured.
* AWS OpsWorks - Chef and Puppet 
* AWS Systems Manager - can control infra on AWS, interface for checking out operational data from many AWS services and also lets you automate operational tasks across the resources. E.g. you can group resources like EC2 instance, S3 bucket, RDS instances by application, check out their operation data for monitoring and troubleshooting
* AWS Systems Manager lets devops teams manage the system by grouping different resources, can patch, update and distribute software on all machines
* ECS and EKS are container orchestration services. ECS for docker and EKS for kubernetes. Fargate is a container runtime environment. You run contains by telling ECS or EKS to deploy the containers on either Fargate or EC2 instances.
* ECS and EKS can pull container images from ECR or any image registry they have access to such as DockerHub
* Instance store, performant temporary block-level storage physically attached to your EC2 instance. Good for cache, buffers, and temporary content or for data that is replicated across a fleet of instances such as a load-balanced pool of web servers. Data is lost if instance experiences failure or terminates. 
* Can create tags for each department
* AWS Pricing calculator: explore AWS services and estimate the cost of infra by adding cost of individual resources
* AWS Trusted advisor: recommendation for AWS best practices to optimize the infra, improve security, performance, cost, etc
* AWS Cost Explorer: Has default report for visualization the costs and usage of top give cost-accruing AWS services. Can check historical data from 12 months ago
* AWS budgets: set custom budgets alerts that alert you when your cost or usage (or forecasted) to exceed amount
* AWS System manager allows you to centralize operational data from multiple AWS services and automate tasks across your AWS resources. You can create logical groups of resources such as applications, different layers of an application stack, or production versus development environment
* DynamoDB Accelerator is a in-memory cache that delivers fast read performance for your tables at scale by enabled you to use a fully managed in-memory cache. 10x faster reads. DAX does not support active-active cross-region config but DynamoDB global tables do support active active cross-region support
* All multi master clusters in Aurora DB must be in the same region, you can't enable cross-region replicas with multi-master clusters
* AWS trusted advisor provides provisioning guidance, best practices in cost optimization, performance, security, fault tolerance, security limits
* AWS Glue is a fully managed, extract, transform and load (ETL) service that makes it easy for customers to prepare and load their data for analytics. AWS Glue is meant ot be used for batch ETL data processing
* AWS Secrets manager helps you protect secrets needed to access your app, services and IT resources. The service enables you to easily rotate, manage and retrieve db credentials, API keys and other secrets throughout their lifecycle. Users and applications retrieve secrets with a call to Secrets Manager APIs, eliminating need to hardcore sensitive information in plain text
* Compliance and user audit on who accessed what: CloudTrail
* CodeDeploy is a service that automates code deployments to any instances, including EC2 instances EC2 instances and ones running on-premise. Unlike CloudFormation, it does nto deal with infra config and orchestration
* AWS Directory Service - AWS Directory Service for MS Active Discovery, aka AWS Managed Microsoft AD, enabled your directory-aware workloads and AWS resources to use managed ACtive Directory in the Cloud
* Site to Site VPN - Creates a secured connection between data center/ branch and AWS cloud resources. Goes over the public internet. Site to Site VPN cannot be used to interconnect VPCs.
* AWS Direct Connect - AWS DC creates a dedicated private connection from your AWS VPC to a remote location. Does not use the public internet and takes a month to establish
* VPC Endpoint - Enables you to connect your VPC to supported AWS services using a VPC endpoint powered by PrivateLink without requiring an Internet Gateway, NAT device, VPN connection or AWS direct connection
* AWS SSO is an AWS service that enables you to centrally manage access to multiple AWS accounts and business applications and provide users with single sign-on access to their assigned accounts and applications from one place. With SSO, you can easily manage SSO access and suer permissions to all your accounts in AWS organizations centrally. AWS SSo allows you to create and mange user identities in AWS SSO's identity store, or easily connect to your existing identity source including MS Active directory, Azure AD, Okta Universal directory. You can use AWS SSO to quickly and easily assign and manage your employees' access to multiple AWS accounts, SAML-enabled cloud applications (such as Salesforce, Office 376 and Box), and custom-build in-house applications all from a central place
* AWS Cognito - Cognito lets you add user auth with form or social identity provider. 
* AWS identity and access management - IAM enables you to securely control access to AWS services and resources for users. You can create and manage users and groups and use permissions to allow or deny access to resources
* AWS CLI is a unified tool to mange AWS services. With one tool to download and configure, you can control multiple AWS services from the command line and automate them through scripts
* AWS Inspector is an automated vulnerability management service that continually scans AWS workloads for software vulnerabilities and unintended network exposure. Inspector provides security assessments of your application settings and configurations on your EC2 instances while GuardDuty helps with analyzing your entire AWS environment for threats. Also checks running OS for known vulnerabilities
* AWS Config, all configs for a region is shown. You can track configuration changes for services. You can apply predefined rules by custom rules defined through AWS Lambda for checking compliance with the rules