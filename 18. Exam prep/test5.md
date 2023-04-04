* AWS Budget is useful for making alerts when you exceed or forecasted to exceed desired spending limit. AWS trusted advisor for finding under utilized resources
* AWS endpoints allow you to private access AWS services using AWS internal network instead of using public internet and therefore without imposing availability risks or bandwidth constraints on network traffic
* CloudWatch billing vs Budgets
1. CloudWatch billing alarms: sends an alarm when the actual cost exceeds a threshold
2. Budgets: sends an alarm when actual cost exceeds the budgeted amount or even when the forecast exceeds the budgeted amount
* Data transferred out to an EC2 instance or Amazon CloudFront when it is in the same region as the S3 bucket is free. Data transferred in from the internet is also free
* Global accelerator is a networking service that helps you improve the availability and performance of the applications that you offer to your global users. GLobal accelerator improves performance for a wide range of applications over TCP or UDP by proxying packets at the edge to applications running in one more more AWS regions
1. Global accelerator is a good fit for non-HTTP use cases - GA is a good fit for non-HTTP use cases such as gaming, iot, voice over ip, as well as http use cases that specifically require static ip addresses for failover
* GA provides static ip addresses that act as a fixed entry point into your applications - it provides static ip addresses that provide a fixed entry point to app and eliminate need for complexity of managing specific ip addresses for different aws regions and availability zones
* S3 standard and S3 intelligent-tiering do not charge any retrieval fee, as well there is no minimum storage duration charge
* In AWS organizations, cost-benefit from reserved instance sharing only works if the instance used is in the same availability region as the reserved instance. The actual physical location does not have to be the same, just the az. e.g. us-west-2a

* Warm standby strategy
* When selecting your disaster recovery strategy, you might weigh the benefits of lower recovery time objective and recovery time objective, vs the cost of implementing and operating a strategy. The pilot light and warm up standby both offer a good balance of benefits and cost. 

This strategy replicates data from primary region to data resources in the recovery region such as amazon RDS db instances of dynamodb table. These resources are ready to serve requests. In addition to replication, this strategy requires you to create a continuous backup in the recovery region. This is because when "human action" type diaster occur, data can be deleted or corrupted, and replication will replicate bad data. Backups are necessary to enable you to get the last known good state. 
The warmup strategy deploys a functional stack but at reduced capacity. The DR endpoint can handle requests, but cannot handle production level of traffic. It may be more, but is always less than the full production deployment for cost savings. If the passive stack is deployed to the recovery region at full capacity, however, then this strategy is known as hots standby because the warm standby deploys a functional stack to the recovery region, this makes it easier to rest region readiness using synthetic transaction
* Mission critical systems you can use multi-site active active. Expensive but near zero data loss and zero downtime
* Pilot light maintains more critical core elements of the system in aws. When the time for recovery comes, you can rapidly provision a full scale production environment around the critical core.
* In warm standby, a lesser number of instances is used to manage the system and it is not mission critical. It is also an active/passive failover configuration. Standby system is scaled up for production load and dns records will route all traffic to aws for dr
* AWS services that offer life cycle management: S3
* How ot make S3 data private: Use S3 block public access to ensure all S3 resources stay private
* Which S3 storage classes don't charge any data retrieval fee: Standard, S3 intelligent-tiering
* Which AWS storage service can be directly used with on-premises systems: EFS. EFS file systems can be accessed from on-premises, you must have an AWS direct connect or AWS VPN connection between your on-premises data center and your Amazon VPC. YOu mount an EFS file system on your on-premises linux server using the standard linux mount command for mounting a file system