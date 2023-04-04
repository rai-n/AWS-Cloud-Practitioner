* EFS is cheaper than FSx
* Some AWS Services only support EFS e.g. ECS, Lambda
* Some AWS services only support using FSx (Windows ECS containers)
* Protect against SQL injection and cross-site scripting: AWS Web application firewall
* Driver of AWS Costs: computer, storage, outbound  data transfer
* VPC and subnet: VPC spans entire AZ in region, subnet spans one AZ in the region
* Multi AZ - high availability
* AWS service for global availability and performance using AWS global network: cloud accelerator/ edge network = cloudfront
* GA is a service that improves the availability and performance of your application with local or global users. It provides static IP addresses which acts as a fixed entry point to application endpoints in a single or multiple regions, such as application load balancers, network load balancers, or EC2 instances. AWS GA uses the AWS global network to optimize the path from your users to your application, improving the performance of your traffic as much as 60%
* GA improves performance for a wide range of apps over tcp or udp by proxying packets at the edge to apps running 1 or more aws regions. It is a good fit for non-http use cases suc has gaming (udp), iot, voip or http use cases that specifically require static ip addresses ir deterministic fast regional failover
* CloudFront in the other hand is good for improving performance on caching content like images and videos and dynamic content such as API acceleration or dynamic site delivery
* AWS developer: one contact can open unlimited cases
* AWS business & enterprise: unlimited contact unlimited cases
* Security group acts as a firewall at the instance level whereas network access control list acts as a firewall at the subnet level
* A security group acts as a virtual firewall for your instance to control inbound and outbound traffic. When you launch an instance, in a VPC, you can assign up to 5 security groups to that instance. Security groups act at the instance level, not the subnet level. A network access control list NACL is optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets (i.i. it works on the subnet level)
* Reliability pillar of well architected framework
1. AWS Service Quotas (maximum value for AWS resources)
2. AWS Trusted advisor (tool for guidance to provision with best practices on cost optimization, security, fault tolerance, server limits and performance improvements)
* AWS Storage gateway is a hybrid cloud storage service that connects existing on-premise environments within the AWS cloud. Customers use SG to simplify storage management and reduce costs for key hybrid cloud storage use cases. These include moving tape backups to the cloud, reducing on premise storage with cloud-backed file shares, providing low latency access to data in AWS for on-premise applications as well as migration, archiving, processing and DR use cases.
* AWS SG services provide three different types of gateways - Tape gateway, file gateway and volume gateway that seamlessly connect on-premises apps to cloud storage, caching data locally for low-latency access