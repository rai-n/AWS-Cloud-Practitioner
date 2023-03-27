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