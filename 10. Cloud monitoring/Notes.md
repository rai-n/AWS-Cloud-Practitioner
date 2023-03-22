## CloudWatch Metrics
* CloudWatch provides metrics for every service in AWS
* Metric is a variable to monitor. E.g. CPU Utilization, Network In, etc
* Metrics have timestamps
* Can create CloudWatch dashboard of metrics

## Important metrics
* EC2 instances: CPU Utilization (For scaling), Status Checks, Networks (not RAM)
* EBS volumes: Disk read/write
* S3 buckets: BucketSizeBytes, NumberOfObjects, AllRequests
* Billing metric, Available only in us-east-1, shows how much was spent in certain months
* Service limits: How much you've been using a service API
* Custom metrics: push your own metrics

## CloudWatch Alarms
* Alarms are used to trigger notifications for any metric
* Alarm actions:
1. Auto scaling: +/- EC2 instances desired count
2. EC2 actions: stop, terminate, reboot or recover an EC2 instance
3. SNS notification: send a notification into an SNS topic. E.g. if CPU Util > x send email
4. Various options (sampling, ^, min, max, etc)
5. Can choose the period to evaluate an alarm (1 min, 10 mins, 50 mins, etc)
6. Create a billing alarm on the CloudWatch billing metric. E.g. over £50 spent
* Alarm states include: OK, INSUFFICIENT_DATA, ALARM

## CloudWatch Logs
* CloudWatch Logs can collect logs from:
1. Elastic Beanstalk: collection of logs from application
2. ECS: collection from containers
3. Lambda: collection from function logs
4. CloudTrail: based on filter
5. CLoudWatch log agents: on EC2 machines or on-premises servers
6. Route53: Log DNS queries
* Enables real-time monitoring of logs, can react
* Adjustable CloudWatch logs retention time, week, month, etc
* By default tno logs from EC2 instance will go to CloudWatch as you need to run a CloudWatch agent on EC2 to push the log files you want. Make sure that EC2 instance has IAM permission to sent log data to CloudWatch logs. Log agent can be set up on-premise server as well directly to CloudWatch service

## EventBridge (formerly CloudWatch Events)
* React to events happening within AWS accounts
* Schedule (Cron kobs, scheduled scripts) -> every hour, trigger script on Lambda function
* Event pattern: event rules to react to a service doing something -> SNS topic with email notification to team when someone logs into IAM root account
* Trigger Lambda functions, SNS/SQS messages
* EventBridge has "Partner Event Bus" instead of "Default event bus like EC2, Lambda, S3" etc, AWS SaaS partners like zendesk or datadog can send events into your account.
* You can plug in your own custom application that would send your own events to your own custom event bus
* EventBridge has Schema Registry which models event schema
* You can archive events (all/ filter) sent to an event bus (indefinitely or set period)
* Ability to replay archived events

## CloudTrail
* Provides governance, compliance and audit for your AWS account
* CloudTrail is enabled by default 
* Gets a history of events / API calls made within your AWS Account by: 
1. Console actions
2. SDK actions
3. CLI actions
4. AWS Services actions
* Cat put logs from CloudTrail into CloudWatch Logs or S3
* A trail can be applied to All Regions (default) or a single region
* If an API call needs to be looked up, use CloudTrail

## X-Ray
* Debug in monoliths are easy, harder in distributed services using log. E.g. if there are SNS, EC2, etc
* X-Ray once enabled, a full picture of services are provided through X-Ray console
* X-Ray advantages: 
1. Troubleshoot performance (bottlenecks)
2. Understand dependencies in a microservice architecture
* Pinpoint service issues with tracing
* Review request behavior
* Find errors and exceptions
* Meeting time SLA? (Service level agreements)
* Where am I being throttled
* Identify users impacted

## CodeGuru
* ML-powered service for automated code review and application performance recommendations
* Provides two functionality
1. CodeGuru Reviewer: automated code reviews for static code analysis with actionable recommendations
* Identify critical issues, security vulnerabilities, hard to find bugs. E.g. best practices, security detection, input validation, resource leaks
* Uses ML & automated reasoning learnt from millions of code reviews on 1000s of open-source and Amazon repos
* Supports Java and Python, integrates with Github, Bitbucket and AWS CodeCommit
2. CodeGuru Profiler: visibility/ recommendations about application performance during runtime (production). Measures in real time and gives recommendations.
* Helps understand the runtime behavior of application. E.g. if its consume excessive CPU capacity on logging routine. 
* Features:
1. Identify and remove code inefficiencies
2. Improve application performance (e.g. reduce CPU Utilization)
3. Decrease compute costs
4. Provides heap summary (identify which objects using up memory)
5. Anomaly Detection
* Supports applications running on AWS or oon-premise
* Minimal overhead on application

## Health Dashboard
1. Service Health Dashboard
* Shows all regions, all services health
* Shows historical information for each day
* Has an RSS feed you can subscribe to
2. Account Health Dashboard
* Provides alerts and remediation guidance when AWS is experiencing events that may impact you
* While the Service Health Dashboard displays the general status of AWS services, Account Health Dashboard gives the personalized view into the performance and availability of the AWS services underlying your AWS resources
* The dashboard displays relevant and timely information to help you manage events in progress and provides proactive notification to help you plan for scheduled activities
* Can aggregate data from an entire AWS Organization
* Global service which can be accessed using the bell from the top right menu
* Shows how AWS outages directly impact you and what resource
* Provides alert, remediation, proactive notifications and planned activities