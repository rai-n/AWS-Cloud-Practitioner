## Communication patterns
1. Synchronous communication 
* Application to application
2. Asynchronous 
* Application will put an order in a queue and the queue is read to make a shipping order
* With synchronous applications, it can be problematic if there are sudden spikes of traffic. E.g. suddenly encode 1000 videos when its usually 10
* In this case it is better to decouple your application
1. Using SQS: queue model
2. Using SNS: pub/sub model
3. Using Kinesis: real time data streaming model

## SQS
* Simple queue service
* Multiple producers send messages into queue 
* Consumers will be polling (requesting) messages from the queue
* Fully managed, use to decouple applications
* Scales from 1 message per second to 10,000 per second 
* Default retention of messages: 4 days, maximum of 14 days
* No limit to how many messages can be in the queue 
* Messages are deleted after they're read by consumers
* Low latency (< 10 ms on publish and receive)
* Consumers share the work to read messages and scale horizontally
* Example, when there is a request to process a video, instead of sending it to the video application, we can insert the message in the SQS queue. A video processing layer can then have an auto scaling group of EC2 instances from the queue and process it. Based on the queue, the EC2 instances can scale accordingly. 2 layers of auto scaling groups for web server and video processing layer

## Kinesis 
* Real-time big data streaming
* Managed service to collect, process and analyze real-time streaming data at any scale
* Kinesis data streams: low latency streaming to ingest data at scale from hundreds to thousands of sources
* Kinesis data firehose: load streams into S3, Redshift, ElasticSearch, etc
* Kinesis data analytics: perform real-time analytics on streams using SDL
* Kinesis Video streams: monitor real-time video streams for analytics or ML

## SNS
* Simple notification service
* One message to many users
* Instead of a buying service talking to email notification, fraud service, shipping service & SQS queue (direct integration), it could use a publisher/ subscriber infra where buying service sends message to SNS topic and this automatically sends message to rest of the subscribers.
* Event publishers only sends message to one SNS topic and the as many event subscribers can listen to the SNS topic notification
* Each subscriber to the topic will get all the messages
* Teach topic can have up to 12,500,000 subs per topic, 100,000 topics limit for each account
* Subscribers an be SQS, Lambda, Kinesis Data Firehose, Emails, SMS & Mobile notifications, HTTP endpoints, etc.