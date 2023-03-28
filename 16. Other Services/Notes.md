## Other services

## Amazon WorkSpaces
* Managed Desktop as a Service (DaaS) to easily provision Windows or Linux desktops
* Great to eliminate management of on-premise VDI (Virtual Desktop infra)
* Fast and scales to thousands
* Secured data - integrates with KMS
* Pay as you go pricing with hourly or monthly rates
* Multiple regions, deploy as many WorkSpaces as close to core business

## AppStream 2.0
* Desktop Application Streaming Service
* Deliver to any computer without acquiring, provisioning infra
* The application is delivered from within a web browser

### WorkSpaces vs AppSteam 2.0
* Workspaces is a fully managed VDI and desktop available, users can connect to VDI and open native or WAM applications. WorkSpaces are on-demand and always on
* AppSteam 2.0 streams a desktop application to web browsers without a virtual desktop on the cloud. Works with any device that has a web browser. Allow to configure an instance type per application type (E.g. more CPU, RAM, GPU)

## IoT Core
* Stands for Internet of Things. Network of internet-connected devices that are able to collect and transfer data
* AWS IoT Core allows you to easily connect IoT devices to the AWS cloud
* E.g. Connected car, connected lights, connected fridge
* Serverless, secure and scalable to billions of devices and trillions of messages
* IoT Core can act as hub for publishing/ subscribing to messages 
* Your applications cna communicate with your devices even when they aren't connected
* Integrates with AWS services like Lambda, S3, SageMaker, etc
* Build IoT applications that gather, process, analyze and act on data

## Elastic Transcoder
* Elastic Transcoder is used to convert media files stored in S3 into media files in the formats
* Media file in S3 bucket -> Transcoding Pipeline -> (Multiple files) -> S3 output bucket -> Compatible with Smartphones, Tablets, PCs
* Benefits
1. Easy to use
2. Highly scalable - large volume of files and sizes
3. Cost effective - duration-based pricing model
4. Fully managed & secure, pay for what you use

## AWS AppSync
* Backend for web and mobile applications, store and sync data across mobile and web apps in real-time
* Combines data from databases, APIOs, and other backend systems into a single GraphQL endpoint
* Makes use of GraphQL 
* Client code can be generated automatically using GraphQL
* Integrations with DynamoDB/ Lambda
* Real-time subscriptions
* Offline data synchronization (replaces Cognito Sync)
* Fine grained security
* AWS Amplify can leverage AWS AppSync in the background

## AWS Amplify
* Set of tools and services that help develop and deploy scalable full stack web and mobile applications
* Comprehensive suite of Authentication, Storage, API (Rest, GraphQL), CI/CD, PubSub, Analytics, AI/ML predictions, monitoring, Source Code from AWS, GitHub, etc
* Amplify has UI (Amplify Studio) where u can set up data schema, authentication, storage, lambda functions, graphql endpoints, rest api endpoints as well as analytics
* Amplify behind the scenes configures Amplify backend which leverages many AWS services like S3, Cognito, AppSync (GraphQL backend), API Gateway (Rest backend), SageMaker (ML), Lex, Lambda, DynamoDB, etc.

## Device Farm
* Fully-managed service that tests your web and mobile apps against desktop browsers, real mobile devices and tablets
* Runs tests concurrently on multiple devices (speed up execution)
* Ability to configure device settings (GPS, language, Wi-Fi, Bluetooth)
* Test web, native or hybrid devices
* Interact with devices
* Device farm can send reports, logs and screenshots

## AWS Backup
* Fully managed service to centrally manage and automate backups across AWS services
* On demand and scheduled backups
* Supports Point in Time Recovery
* Retention periods, lifecycle management, backup policies
* Cross-region backup
* Cross-account backup using AWS Organizations
* AWS Backup can create backup files with a (frequency, retention policy) for EC2, DynamoDB, EFS, FSx, EBS, RDS, Aurora, AWS Storage gateway (on premise storage access to unlimited storage) backed up to AWS S3

## Disaster Recovery Strategies
* Which one is cheapest? Back up and restore 
1. Backup and Restore
* Data is stored on the cloud, if a disaster occurs it is restored. Because the data is just backed up and the application is not running, when it is restored the cost is very minimal. Just backing up data over time.
2. Pilot light
* We have the cloud and we will run the core functions of the app, e.g. just the database and it's ready to scale but is not fully scaled, minimal setup is there on the cloud
* Core functions of the app, ready to scale, but minimal setup
3. Warm standby 
* Full version of the app is available to be recovered but at minimum size, if we need to do a disaster recovery, we just have to increase the size of the app
4. Multi-site/ Hot-site
* Full version of the app at the full size is ready to be used. Maximum cost, deployment is ready to be used in case of disaster

### Typical DR setup for cloud deployment
* If there is disaster for all AZ in us-easy-1, we can have a failover in eu-west-2 using Route 53

## AWS Elastic Diaster Recovery (DRS) - formerly CloudEndure Disaster Recovery
* Quickly and easily recover your physical, virtual and cloud-based servers into AWS
* E.g. protected most critical database, apps, protect data from attacks, etc
* Do continuous block-level replication for your servers using EDS
* OS, Apps, DB writes to disk and AWS Replication agent continuously replicates disks into staging environment in AWS with lost cost EC2 instances and EBS volumes, during failover, a better EC2 instance with bigger volumes is loaded in production, when the main system is back up, the backup system fall backs into main system

## DataSync
* Move large amount of data from on-premises to AWS
* Can synchronize to Amazon S3 (any storage classes - including Glacier), Amazon EFS, Amazon FSx for Windows
* Replication tasks can be scheduled hourly, daily or weekly
* Replication tasks are **incremental** after the first full load

## AWS Application Discovery Service
* Can use AWS Application discovery service to plan on-premise migration to the cloud
* Scan severs, get utilization information as well as dependency mapping
1. Agent-less discovery (AWS Agent-less Discovery Connector)
* VM inventory, configuration and performance history such as CPU, memory and disk usage
2. Agent-based discovery (AWS Application Discovery Agent)
* System configuration, system performance, running processes, and details of network
* Resulting data can be viewed within AWS Migration Hub 

## AWS Application Migration Service (MGN)
* MGN - we can lift and shift (re host) which simplifies migrating applications to AWS
* Converts your physical, virtual and cloud-based servers to run natively on AWS
* AWS Replication agent performs continuous replication of disks into a staging environment with low-cast EC2 instances & EBS volumes, when u need to do a cut over, you then increase the target EC2 instance and EBS volumes size for performance need
* Simply, you replicate data and some point do a cut over (automatically)

## AWS Fault injection Simulator 
* A fully managed service for running fault injection experiments on AWS workloads
* Based on chaos engineering -- stressing an application by creating disruptive events. E.g. high CPU or memory, observing how CPU responds and implementing improvements
* Helps uncover hidden bugs and performance bottlenecks
* Supports EC2, ECS, EKS, EKS, RDS. 
* Events can be monitored by CloudWatch or EventBridge and view results

## Step functions
* Build serverless visual workflow to orchestra your Lambda functions
* Features such as sequencing, parallel, conditions, timeout, error handling
* Can integrate with EC2, ECS, on-premises servers, API gateway, SQS queues, etc
* Possibility of implementing human approval feature (Workflow goes up to some point and then human says yes or no)
* Use case: order fulfillment, data processing, web applications, any workflow

## Ground station
* Fully managed service that lets you control satellite communications, process data, and scale satellite operations
* Provides a global network of satellite ground stations near AWS region
* Allows yo uto download satellite data to your AWS VPC within seconds
* Send satellite data to S3 or EC2 instance
* Use case: weather forecasting, surface imaging, communications, video broadcasts

## AWS Pinpoint
* Scalable 2-way (outbound/ inbound) marketing communications service
* Supports email, SMS, push, voice, and in-app messaging
* Ability to segment and personalize messages with the right content to customers
* Possibility to receive replies
* Scales to billions of messages per day
* Use cases: run campaigns by sending marketing, bulk, transactional SMS messages
* Stream events such as TEXT_SUCCESS, TEXT_DELIVERED are sent to SNS, Kinesis Data firehose or CloudWatch Logs

### AWS Pinpoint VS AWS SNS or AWS SES
* In SNS & SES, you manage each message's audience, content and delivery schedule
* In AWS Pinpoint, you create message templates, delivery schedules, highly-targeted segments and full campaigns