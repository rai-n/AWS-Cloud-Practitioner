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
* 