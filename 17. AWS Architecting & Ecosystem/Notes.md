## Well Architected Framework, General Guiding Principles
* Stop guessing your capacity need, instead use auto scaling
* Test systems at production scale, AWS device farm
* Automate to make architectural experimentation easier or platform as a service such as Beanstalk
* Allow for evolutionary architecture based on changing requirements
* Drive architectures using data based on what you need
* Improve through game days, simulate app for flash sale day. E.g. stress test

## Design principles
* Scalability: vertical & horizontal
* Disposable resources: servers should be disposable and easily configured, back up data and configuration and should be done quickly
* Automation: Serverless, Infrastructure as a service, auto scaling
* Loose coupling: 
1. Monolith, gets bigger, avoid this as it is difficult to maintain and scale
2. Break it down into smaller, loosely coupled components. E.g. microservices or SQS
3. Change in or failure in one component should not cascade to other components
* Think in Services, not Servers
* What Managed services, databases, serverless can i use?


## Well Architecture Framework, 6 pillars
1. Operational Excellence
2. Security
3. Reliable
4. Performance efficiency
5. Cost optimization
6. Sustainability

* Not a balance, they are a synergy

## Operational Excellence
* Run and monitor systems to deliver business value
* Design principles
1. Perform Infrastructure as code, cloudformation
2. Annotate documentation, automate creation of annotated documentation after every build
3. Make frequent, small, reversible changes so that in case of failure, u can reverse it
4. Refine operations procedures frequently - ensure members are familiar with it 
5. Anticipate failure - learn from them
AWS:
1. Prepare - CloudFormation Infra as code, AWS Config evaluate compliance of CloudFormation
2. Operate - Automate as much as possible, release fast, remove manual process, AWS CloudFormation, AWS Config, AWS CloudTrail, AWS CloudWatch, AWS X-Ray (trace HTTP request)
3. Evolve, AWS CLoudFormation, CodeBuild, CodeCommit, CodeDeploy, CodePipeline

## Security
* Includes the ability to protect information, systems and assets while business value through risk assessments and mitigation strategies
* Design principles
* Implement a strong identity foundation - centralize privilege management and reduce or even eliminate reliance on long-term credentials - principles of least privilege - IAM
* Enable traceability - Integrate logs and metrics with systems to automatically respond and take action
* Apply security at all layers - like edge network, VPC, subnet, load balancer, every instance, operating system and application
* Automate security best practices
* Protect  data in transit and at rest - encryption, tokenization and access control
* Keep people away from data - reduce or eliminate the need for data or manual processing of data
* Prepare for security events - run incident response simulations and use tools with automation to increase your speed for detection, investigation and recovery
AWS:
1. Identity and access management: IAM, STS, MFA token, AWS Organization
2. Detective controls: Config, CloudTrail, CloudWatch 
3. Infra protection: CloudFront, AWS VPC, AWS Shield, WAF, Inspector
4. Data protection: KMS, S3 encryption, ELB, EBS, RDS encrypted, SSL capability
5. Incident response: IAM - remove privileges, CloudFormation - if someone deletes infra, get it back. AWS CloudWatch Events - alert events

## Reliability 
* Recover from infra or service disruption, acquire compute resources as needed, mitigate disruptions such as mis-config or transient network issues
* Design principles
1. Test recovery procedures, use automation to simulator failures
2. Automatically failover, anticipate and remediate failures before they occur
3. Scale horizontally to increase aggregate system availability - distribute requests across multiple, smaller resources to ensure that they don't share a common point of failure
4. Don't guess capacity, use auto scaling to satisfy demand
5. Manage change in automation - use automation to make changes to infra for rollbacks
AWS:
1. Foundations: IAM, VPC, Service Limits (now Service Quotas, monitor over time), AWS Trusted Advisor - look at service limits
2. Change management - AWS Auto scaling, CloudWatch, AWS CloudTrail, AWS Config
3. Failure management - Backups, AWS CloudFormation, AWS S3 backup data, S3 Glacier for archives, Route 53 for DNS]
4. Performance efficiency
* The ability to use computing resources efficiently to meet system requirements, and to maintain that efficiency as demand changes and technologies evolve
* Principles
1. Democratize advanced tech - advance tech become services and hence you can focus on more product development
2. Go global in minutes in multiple region
3. Use serverless for avoiding burden of managing servers
4. Experiment more often - easy to carry out comparative testing
5. Mechanical sympathy - Be aware of all AWS services
AWS:
1. Selection, Auto scaling ec2, Lambda serverless, EBS gp2 or io1, S3, RDS - provision db
2. Review, CloudFormation, AWS News blog 
3. Monitoring, CloudWatch, Lambda - doesn't throttle, runs in time 
4. Tradeoffs, RDS vs aurora, Elasticache for read performance, Snowball for data moving really fast or truck in longer time, CloudFront - global in minutes with cache at edge locations but cached data could be stale

## Cost optimization
* Run at lowest cost 
* Adopt a consumption mode - pay for what you use. E.g. lambda
* CloudWatch for checking overall efficiency
* Stop spending money on data center operations - AWS does the infra part and enables customers to focus on business logic
* Analyze and attribute expenditure - accurate identification of system usage and costs, help measure ROI - make sure to use tags
* Use managed and application level services to reduce the cost of ownership - lower cost per transaction
AWS:
1. Expenditure awareness, AWS Budgets, Cost and Usage Report, Cost Explorer, Reserved instances
2. Cost-effective resources, spot instance, reserved instance, S3 glacier lowest price point
3. Matching supply and demand, AWS Auto scaling, AWS Lambda 
4. Optimizing over time, AWS Trusted Advisor, AWS Cost and Usage Report, News Blog

## Sustainability 
* Minimizing environmental impacts of running cloud workloads
* Design principles
1. Understand impact - Establish performance indicator, evaluate improvements
2. Establish sustainable goals - set long-term goals for each workload, model return on investment
3. Maximize utilization - Right size each workload to maximize energy efficiency of the underlying hardware and minimize idle resources
4. Anticipate and adopt new, more efficient hardware and software and adopt new technologies over time
5. Use managed services - Shared service reduce amount of infra. They help automate sustainability best practices as moving infrequent access to cold storage adjusting compute capacity
6. Reduce the downstream impact of cloud workloads - Reduce the amount of energy or resources required to use your services and reduce the need for customers to upgrade their devices
AWS:
1. EC2 autoscaling, serverless offering (Lambda, Fargate) right amount of compute
2. Cost Explorer, AWS Graviton 2, EC2 T instances, Spot instances allow energy efficient when using capacity as well as using otherwise wasted energy via spot instance
3. EFS-IA, Amazon S3 Glacier, EBS Cold HDD volumes optimize archiving data
4. S3 Lifecycle Configuration, S3 intelligent Tiering data is in the right tier, Amazon Data Lifecycle manager
5. Read local, Write Global: RDS Read replicas, Aurora Global DB, DynamoGB Global table, CloudFront

## AWS Well-Architected Tool
* Free tool to review architectures against 6 pillar framework and adopt best practices
* How does it work?
1. Select your workload and answer questions
2. Review your answers against the 6 pillars
3. Obtain advice: get video and and docs, generate a report and see results in a dashboard

## AWS Right Sizing
* EC2 has many instance types, but choosing the most powerful instance type isn't the best choice, as the cloud is elastic
* Right sizing is the process of matching instance type and sizes to your workload performance and capacity requirements at the lowest possible cost
* Scaling up is easy so always start small
* It's also the process of looking at deployed instances and identifying opportunities to eliminate or downsize without compromising capacity or other requirements, which results in lower costs
* Important to Right Size 
1. Before a Cloud Migration to figure out cheapest possible migration to AWS
2. continuously after the cloud onboarding process. e.g. once a month
3. CloudWatch, Cost Explorer, Trusted Advisor, 3rd party tools help to figure out needs

## AWS Ecosystem - Free resources
* Blogs 
* Forums
* Whitepapers & Guides e.g. Well-Architected framework
* Automated, gold-standard deployments in the AWS cloud
1. Build your production environment quickly with templates
2. Leverages CloudFormation
* AWS Solutions
1. Deploy Vetted solutions on AWS 
2. AWS Landing zone: secure, multi-account environment
3. Replaced by AWS Control Tower
* AWS Support
1. Developer: Business hour email access to Cloud Support associates, general guidance < 24 hrs, system impaired < 12 hours
2. Business: 24x7 phone, email and chat access to Cloud Support Engineers, Production system impaired < 4 hours, production system down < 1 hour
3. Enterprise: Access to Technical Account Manager (TAM), concierge support team for billing and account best practices, business critical system down: < 15 minutes

## AWS Marketplace
* Digital catalog with 1000s of software listings from 3rd party vendors
* e.g. Custom AMI with OS, firewalls and solutions
* CloudFormation templates
* Software as a Service
* Buy containers
* Marketplace payments are gone through AWS bill

## AWS Training
* AWS Digital (online) and classroom training 
* AWS Private training for organizations
* Training and certification for U.S Government
* T & C for Enterprise 
* AWS Academy: help unis teach AWS
* Online courses

## AWS Professional Services & Partner Network
* Global network
* Work alongside your team and chosen APN (AWS Partner Network)
* APN Technology Partners: providing hardware, connectivity and software
* APN Consulting Partners: professional services form to help build on AWS
* APN Training Partners: find who can help you learn AWS
* AWS Competency Program: AWS Competencies are granted to APN Partners who have demonstrated technical proficiency and proven customer success in specialized solution areas
* AWS Navigate Program: help Partners become better Partners

## AWS Knowledge Center
* Contains the most frequent & common questions and requests

## AWS IQ 
* Quickly find professionals help you for your AWS projects
* Engage and pay AWS Certified 3rd party experts for on-demand project work
* Video-conferencing, contract management, secure collaboration, integrated billing
* For customers:
1. Submit request with project description
2. Review responses and connect to experts with requirements and timeline
3. Select expert based on rate, experience, etc
4. Work securely, give expert access to your AWS account
5. Pay per milestone, charges added into your AWS Bill
* For experts:
1. Create profile with photo, bio, certs
2. Connect with customers
3. Start a proposal with work description, price, milestones
4. Work securely, get appropriate access to customer's AWS account
5. Get paid, request payment after milestones are met

## AWS re:Post 
* AWS managed Q&A forum service offering crowd sourced, expert reviewed answers to technical questions about AWS that replaces the original AWS forums
* AWS Free Tier
* Members can get reputation points from participating
* Questions from AWS Premium Support customers without response from community are passed on to AWS Support engineers
* AWS re:Post is not intended for questions that are time-sensitive or involve any proprietary info

## AWS Managed Services (AMS)
* Team of people who provide infra and app support on AWS
* AMS offers experts who manage and operate your infra for security, reliability and availability
* Helps organizations offload routine management tasks and focus on their business objectives
* Fully managed service, so AWS handles common activities such as change requests, monitoring, patch management, security and backups services
* Implements best practices and maintains your infra to reduce operational overhead and risk
* AMS business hours are 24/365

1. Enable. Create a baseline governance and control model using inputs from people, process and tool sets
2. Sustain, build or migrate. Determine the fastest and most efficient way to integrate, develop and migrate your workloads
3. Operate. Active operational outcomes, scale globally and have observability, compliance and financial management
* You have to get in touch with AWS sales for this
* Benefits: Improved security, focus on automation, stronger compliance, reduced operating costs, simplified management, frictionless innovation