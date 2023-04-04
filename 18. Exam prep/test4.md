* Which AWS service will you use to privately connect VPC to S3
(connect the network to S3) - network to an AWS service -> VPC Endpoint Gateway
* A VPC endpoint enables you to privately connect your VPC to supported AWS services powered by AWS PrivateLink without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. Instances win your VPC do not require public IP addresses to communicate with resources in the service. Traffic between your VPC and the other service does not leave the AWS network.

There are two types of VPC endpoints, gateway and interface gateway. Gateway is for S3 and DynamoDB. S3 and DynamoDB support VPC Endpoint gateway. All other services support VPC endpoints use a VPC endpoint interface. Gateway endpoints are free but interface endpoints are charged per hour and per GB processed. Interface endpoints can be accessed outside the VPC, but gateway endpoints can be accessed only from resources inside the VPC

* Transit gateway -- simplify complex peering through central hub
* AWS direct connect - establish private virtual interface from your on-premise network directly to Amazon VPC
* API gateway - fully managed service that makes it easy for devs to create, publish, maintain, monitor and secure API at any scale.
* Detailed report - AWS cost and usage reports
* AWS services in regional scope: AWS Lambda, AWS Rekognition
* WAF you can configure web access control lists on your CloudFront distributions or Application Load balances to filter and block reqeustsd based on signatures
* A Network access control list contains a numbered list of rules and evaluates these rule sin increasing order while deciding where to allow traffic
* A security group is stateful, that is, it automatically allows the return traffic. Security group is instance level
* Amazon Kendra: fully managed ML enabled searching
* Amazon Personalize: real-time personalized recommendations
* Amazon comprehend - NLP to uncover information in unstructured data: find key phrases, entities sentiments, type of language being used, sensitive data, etc
* Amazon LEx - speech recognition for converting speech to text and natural language understanding to recognize the intent of the text to enable ot build apps with highly engaging user experience and lifelike conversational interactions
* AWS site-to-site VPN: customer gateway, virtual private gateway
AWS site-to-site VPN enables you to securely connect your on-premises network or branch office site to your Amazon Virtual Private Cloud (VPC). VPN connections are a good solution if you have an immediate ned, and have low to modest bandwidth requirements. The connections goes over the public internet. TVirtual Private Gateway (or a transit gateway) and customer gateway are components of a VPC. A virtual private gateway is the VPN concentrator on the Amazon side of the site-to-site vpn connection. A customer gateway is a resource in AWS that provides info to AWS About your customer gateway device
* Site-to-site vpn connection offers two VPN tunnels between a virtual private gateway or transit gateway on the AWS side and customer gateway on the remote on-premise customer side
Site-to-site VPN connection consists of:
1. Virtual private gateway
2. Transit gateway
3. Customer gateway
4. Customer gateway device

* IAM policies: EFFECT, ACTION are mandatory
* Most policies are stored in AWS as JSON documents. Identify-based policies and policies used to set

* S3 bucket for improving global performance -> use CloudFront to improve the performance of your website. CF makes website files like html, images and videos available from edge locations around the world. CF automatically redirects a request to copy a file at a nearest edge location. Results in faster download times
* S3 transfer acceleration enables secure, fast and easy transfers of files over long distances between client and S3 bucket. It uses CloudFront's edge locations. AS the data arrives at the edge location, data is routed to S3 over an optimized network path. You will be charged for transferring data into the bucket while normally a PutObject API call does not incur any costs. You will also pay more to retrieve objects since they got through the edge network
* Agility - agility refers to ability of cloud to give you easy access to broad range of techs that helps you innovate faster and build nearly anything that you can imagine. You can quickly spin up resources as you need them - from infra services, such as compute, storage, and databases, to iot, ml, data lakes, analytics and much more
* Elasticity- you don't have to over-provision resource upfront to meet peak hour demands. Instead provision the number of resources you need and scale these resources up or down instantly to grow and shrink capacity
* Org maintains separate VPC for each departments, they want to connect all of the VPC for better collaboration. Use transit gateway for complex VPC connections through a central hub and puts an end to complex peering relationships. It is like a cloud router - each connection is only made once. AS you expand globally, inter-region peering connects AWS transit gateways using the AWS global network. Your data is automatically encrypted and never travels over the public internet
* VPC peering to connect two VPC, direct connect to connect a remote network to your VPC
* Every AWS account provides it own invoice in the end of the month. You can get separate invoices for dev and prod by setting up separate accounts
* You cannot create separate invoices based on tags
* Scale down/ up means vertically scaling up or down CPU/ memory, etc
* Support plan for general architectural guidance: Developer. For more specific infrastructure event management you need Business
* To move entire AWS data and application to another region, best solution is that the company should start creating new resources in the designation AWS region and then migrate relevant data and apps into the AWS region. Database migration service cannot help with the entire IT resource migration
* True about cost allocation tags
1. For each resource, each tag key must be unique and each tag key can only have one value
2. You must activate both AWS generated tags and user-defined tags separately before they can appear in Cost Explorer or on a cost allocation report
* Read replica improves database scalability. You can place read replica in different AWS region closer to your users for better performance as horizontal scaling
Important:
1. Multi-AZ -> purpose of high availability. This is where non-aurora: synchronous replication occurs.  Spans at least two A-Z within a single region.
2. Multi-region ->  purpose of diaster recovery and local performance, asynchronous replication. Each region can have a multi-az deployment
3. Read replicas -> Main purpose is scalability. Asynchronous replication. Can be within an A-Z, cross-az or cross region
* Data encryption is automatically enabled for which AWS services:
1. CloudTrail logs
2. AWS storage gateway, hybrid cloud storage service which gives you on-premise access to virtually unlimited storage. All data transferred between gateway and AWS storage is encrypted using SSL for all type of gateways - File, Volume and Tape
3. AWS S3 glacier 
* Amazon EBS snapshots are stored incrementally, which means you are billed only for the changed blocks stored
* You will pay a fee each time you read from or write data stored on the EFS - infrequent access storage class. AWS EBS snapshots are a point in the time copy of your block data. For the first snapshot of a volume, EBS saves a full copy of data to S3. EBS snapshots are stored incrementally, which means you are billed only for the changed blocks stored
* 