## AWS Shared Responsibility Model
* AWS's responsibility includes protecting the cloud infra such as physical hardware, facilities, networking, as well as managed services like S3, DynamoDB, RDS, etc.
* Customer responsibility includes security in the cloud. E.g. Management of Guest OS in EC2 instances, firewall & network configuration, IAM permissions

...

## Summary

Config: Track config changes and compliance against rules
Macie: Find sensitive data e.g. PII data from S3 buckets
CloudTrail: Track API calls made by users within account
AWS Security Hub: gather security findings from multiple accounts
Amazon Detective: find the root cause of security issues or suspicious activities
AWS Abuse: Report AWS resources used for abusive or illegal purposes
Root user privileges: 
1. Change account settings
2. Close AWS account
3. Change or cancel AWS support plan
4. Register as a seller in the Reserved Instance Marketplace