* Security group is the firewall of EC2 instances, stateful
* Network ACL is the firewall of VPC subnets, stateless
* NACL is applicable at the subnet level so any instance in the subnet with an associated NACL will follow the rules of that NACL. Security groups have to be assigned explicitly to the instance. Any instance within the subnet group get the rule applied. With a security group, you have to manually assign a security group to the instance. 
* By default, all rules are denied for security groups and you have to set allow rules.
* Site to site vpn happens over the public internet but direct connect happens over private AWS global network
* Route 53 = dns service + health checks  for endpoints for high availability
* S3 transfer acceleration routes traffic from far away using AWS edge location instead of public internet for less congestion and faster transfer
* S3 retrieval charges per GB retrieved except standard and intelligent tiering which does not have retrieval charges
* Dedicated host, the physical server is always the same. With dedicated instance, the machine using could change but you are nto sharing the machine with others
* With AWS pricing calculator, you compare the costs of application on-premise to AWS such as server admin, storage, network, it labour
* IAM access advisor shows the service permissions granted to a user and when those services were last accessed. You can use this to revise your policies
* IAM credential, you can generate and download a credential report that lists all users in your account and status of their credentials, including passwords, access keys, and MFA devices
* AWS systems manager allows you to get central operational insights from multiple AWS services and automate tasks across AWS resources. Can group resources such as apps, layers of stack and prod. Select a resource and view api activity, config changes, operational alerts, patch compliance status, can also take action on each resource group.Visualize data from grouped operations
* WAF can inspect CLoudFront distributions running on any HTTP web-server
* New to AWS, use LightSail - it includes virtual machine, sdd based storage, data transfer, dns management with static ip for low, predictable price. Good for people with little cloud experience
* AWS IAM Identity center is successor to AWS SSO. Built on top of IAM to simplify access management to multiple AWS accounts. You can create users directly in IAM identity center or you can bring them from your existing workforce directory. 
* Convertible reserved instance, purchase convertible reserved instances if you need additional flex such as ability to use different instance families, os, or tenancies over the reserved instance term. Convertible rs instance provides discount up to 54% compared to on demand. This is useful when workloads are likely to change.