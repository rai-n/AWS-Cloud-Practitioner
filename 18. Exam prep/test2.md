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