## Interesting notes

* Active passive failover, when you want a primary resource to be available most of the time and secondary resource on standard in case all primary resources become unavailable
* Active active failover, when all resources are active until a resource becomes unhealthy it is not used
* AWS inspector is an automated, security assessment service that helps you check for unintended network accessibility of your EC2 instances and for vulnerabilities there. Inspector assessments are offered as pre-defined rules packages mapped to common security best practices and vulnerabilities
* AWS customers can carry out penetration test
* AWS Cost Explorer lets you visualize understand and manage AWS costs and usage over time. It gives you a detailed breakdown of cost going back 12 months and also allows you to forecast future costs
* AWS Cost and Usage Reports - contains the most comprehensive set of data available, provides raw data which can be sent to S3 and then processed with Athena
* AWS Budgets give the ability to set custom budgets that alert when the cost or usage (or are forecasted to exceed) budget amount. Can also be used when utilization drops below a target. Can be created at monthly, quarterly or yearly level
* AWS Pricing calculator lets you check out AWS services and find the cost of services on AWS. E.g. modelling the infra before building them to see how much it will cost
* AWS Personal Health Dashboard provides alerts and remediation guidance when AWS is experiencing events that might affect you. It is not used to get operational insights of AWS resources.
* EBS is high performant block storage service, cannot be accessed by multiple EC2 instances simultaneously
* You can create Snapshots to back up EBS since data is divided into blocks. You have to use AWS backup to create backups for storing backups of EFS 