* AWS SDK - takes complexity out of coding by providing language-specific API for AWS services. E.g. API lifecycle considerations such as credential management, retries, data marshaling, etc. 
* AWS Management Console - It can help with using AWS Management Console - collection of web based user interface for exploring AWS
* AWS Command line interface - AWS CLI is a unified tool to manage AWS services. Can download and configure and control, multiple AWS services and automate through scripts. Cannot be used with language specific API
* Language specific integrated development environments - an integrated development environment which provides a set of coding productivity tools such as a source code editor, a debugger and build tools. Cloud 9 ide is an offering from AWS under IDEs
* AWS GuardDog is for AWS account level, not instance level management like an EC2 which is done by AWS Inspector. GuardDog cannot be used to check OS vulnerabilities which is done by AWS inspector
* AWS Infra event management is included in enterprise support plan and available ot business support customers for additional fee. AWS experts at side, AWS Infra event management helps you assess operational readiness, identify and mitigate risks and execute your event confidently
* Provides architectural and operational guidance for planned events using a prescriptive approach:
1. AWS helps understand success and desired business outcomes
2. AWS assess the readiness of your environments, help identify and mitigate risks and document your plan
3. You execute your events with AWS experts by your side
4. AWS helps analyze results after events and scale services to normal operating levels you can focus on planning your next event
(Event being application launch, data center migration, marketing event)
* Client side encryption using AWS encryption SDK 
1. Encrypting data before sending it o S3 is client-side encryption. AWS encryption SDK is a client side encryption library that is separately from the language-specific SDK. This can be used to easily implement encryption best practices in S3. Unlike the Amazon S3 encryption clients in the language -specific AWS SDKs, the AWS encryption is not tied to S3 and can be used to encrypt or decrypt data stored anywhere
* Security group acts as a virtual firewall for your instance to control inbound and outbound traffic. Security groups act at the instance level, not at the subnet level. You can specify allow rules but not deny rules. You can specify separate rules for inbound and outbound traffic.
* NACL (Network Access Control List)
1. Has inbound and outbound rules and each rule can either allow or deny traffic
* Most cost efficient option to purchase an EC2 reserved instance: as much upfront for longer period of time
* Fault tolerant: Instance store, physically attached to host computer. Low latency, used for non persistent data. Fault tolerant architecture
* Reliability pillar: Foundations, change management and failure management: CloudWatch, Config, CloudTrail
* AWS EFS is designed to be highly scalable, highly available and highly durable. Can store data and metadata across multiple AZ in the AWS Region. Can be mounted on instances across multiple AZ
* Mission critical systems: EBS volumes, very high performance, block storage designed for EC2 for throughput and transaction intensive workload at any scale
* Compute optimizer recommends optimal AWS resources for workload to reduce cost and improve performance by using ML to analyze historical metrics. Helps fit the resource provisioning to not under or over provision and pick optimal config for EC2 instances, EBS volumes and Lambda functions.
* How to remove an AWS account from AWS Organizations -> The AWS account must be able to operate as a standalone account. Only then it can be removed from AWS Organizations
* AWS support plan for guidance with setting up config, troubleshoot of AWS interoperability with 3rd party software. Business, Enterprise
