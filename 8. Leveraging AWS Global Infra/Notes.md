## Why global application 
* Global applications can be deployed in multiple regions/ edge locations for decreases latency.
* Latency is time taken for a packet to reach a server, deploy applications closer to users to decrease latency and better experience
* Having a disaster recovery plan
1. if an entire AWS region goes down due to earthquake, storm, power, politics, etc, you can fail over to another region and the application would still be working 
2. This increases the availability of the application
* Distributed global infrastructure is harder to attack
* Key terms: 
1. Region: For deploying application and infrastructure
2. Availability zone: Made up of multiple data centers
3. Edge locations: for content delivery as close to users as possible

## Route 53 
* Managed DNS (Domain name system)
* Collection of rules and records which helps client understand how to reach a server through URLs
* Typical types of records:
1. 12.34.56.78 == A record (IPv4)
2. 2001:0db985...:0000:0000 ...  == AAAA (IPv6)
3. search.google.com => www.google.com == CNAME (hostname to hostname)
4. example.com => AWS resource == Alias (E.g. ELB, CloudFront, S3, RDS, etc)
* Routing policies: 
1. Simple routing policy (no health check - load balancing), url => ip
2. Weighted routing policy (can use health checks, weights associated with each compute resource. E.g. 70 weight, 20 weight 10 weight respectively)
3. Latency routing policy - users will be rerouted to their closest geographical server to minimize latency between users and servers
4. Failover routing policy - (disaster recovery) - DNS will do health check on primary instance and if it fails it routes to failover instance