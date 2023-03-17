## ECS
* ECS stands for Elastic Container Service 
* Launch Docker containers on AWS 
* You have to provision and maintain the infrastructure (EC2 Instance)
* AWS takes care of starting and stopping containers
* It also has integration with application load balancer

## Fargate 
* Launch Docker containers on AWS
* Do not need to provision infrastructure (No EC2 instance to manage) - simpler! 
* Serverless offering
* AWS just runs the containers based on the CPU/ RAM needed for each container 

## ECR 
* Elastic Container Registry used for storing docker images
* Private Docker Registry on AWS
* Docker images are stored and is loaded as a container to be run on ECS or Fargate

## Serverless
* Serverless is a paradigm where developers don't manage the servers 
* Code is just deployed or functions 
* Initially serverless was function as a service, but was pioneered by AWS Lambda but now includes anything that's managed: 'databases, messaging, storage, etc'
* Serverless does not mean there are no servers, but it means you don't manage/ provision/ see them
* For example:
1. S3
2. DynamoDB
3. Fargate 
4. Lambda

## Lambda
* No server, virtual functions
* Limited by time, short execution 
* Run on demand
* Scaling is automated
+ Easy pricing 
1. Pay per request and compute time
2. Free tier of 1,000,000 AWS Lambda requests and 400,000 GBs of compute time
+ Integrated with the whole AWS suite of servers
+ Event driven: functions get invoked by AWS when needed
+ Integrated with many programming languages
+ Easy monitoring through AWS CloudWatch
+ Easy to get more resources per function (up to 10GB of RAM)
+ Increasing RAM will also improve CPU and network
+ Supports Nodejs, Python, Java 8, C#, Golang, Ruby, Custom Runtime API (any language)
+ Lambda Container Image 
1. The container image must implement the Lambda Runtime API
2. ECS/ Fargate is the preferred for running arbitrary Docker images

* Good use case for Lambda. E.g. thumbnail creation
* New image on S£ -> triggers Lambda create thumbnail function which pushes new thumbnail to S3 and pushes metadata in DynamoDB (image name, size, creation date, etc)
* Serverless CRON job, schedule based events. E.g. CloudWatch Events EventBridge can trigger Lambda function to perform a task every x minutes or at x.
* Pay per call, 1st 1,000,000 free and $0.20 per 1,000,000 requests after
* Pay per duration. Free tier is 400,000 GB-seconds of compute per month
1. This is 400,000 seconds if function is 1GB RAM
2. This is 3,200,000 seconds if function is 128MB RAM
3. After that $1.0 for 600,000 GB-seconds
4. It is usually very cheap to run AWS Lambda so it's very popular

## API Gateway 
* When building a serverless API
* CLient <-> (REST API) <-> API Gateway -> PROXY REQUESTS <-> LAMBDA <-> CRUD <-> DYNAMODB
* Fully managed service for developers to easily create, publish, maintain, monitor and secure APIs
* Serverless and scalable
* Supports RESTful API and WebSocket API
* Support for security, user authentication, API throttling, API keys, monitoring