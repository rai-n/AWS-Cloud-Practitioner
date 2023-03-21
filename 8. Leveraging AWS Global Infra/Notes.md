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

## CloudFront
* CDN 
* Improves read performance, content is cached at the edge 
* Improves UX
* 216 points of presence globally
* DDoS protection, integrated with Shield. AWS Web Application Firewall
* Several origins. E.g. 
1. S3 bucket -> Distribute fields and cache them at the edge, enchanted security with CloudFront Origin Access Control. CloudFront can be used as an ingress to upload files to S3.
2. Custom origin (HTTP) -> Application Load balancer, EC2 instance, S3 static website, any HTTP backend
* When a client makes a request to a CloudFront Edge location, local cache is checked if the data is there. If so, it is fetched from cache, otherwise it goes to the origin to get the request result which is then cached and sent.
* Difference between CloudFront and S3 Cross Region Replication 
1. CloudFound -> Global Edge Network, Files are going to be cached in each edge location for a day maybe. Great for static content. 
2. S3 Cross Region Replication -> Must be set up for each region you want replication to happen to. Files are updated in near real-time. Read only. Great for dynamic content that needs to be available at low-latency in few regions.

## S3 Transfer acceleration
* Increase transfer speed by transferring file ot an AWS edge location which will forward the data to the S3 bucket in the target location

## Global Accelerator 
* Improve global application availability and performance using the AWS global network
* Leverage AWS internal network to proxy/ optimize the route to your application (60% improvement)
* Difference between Global Accelerator and CloudFront 
1. They both use AWS global network and its edge locations are around the world 
2. Both services integrated AWS shield for DDos protection 
* CloudFront - CDN to improve performance by caching content such as images and videos, content is served at the edge
* Global Accelerator - No caching, proxying packets, at the edge to applications running in one or more AWS region. Improves performance for a wide range of applications over TCP or UDP
* Good for HTTP use case that require static IP addresses
* Good for HTTP use cases that requires deterministic, fast regional failover and good performance 

## Outposts
* Outposts are server racks that offer the same WAS infra, services, API & tools to build your own applications on premise just as in the cloud
* AWS will setup and manage outposts racks within your own on-premises infrastructure and you can start leveraging AWS services on-premises
* You are now responsible for the physical security of outpost rack

### Benefits 
* Low latency access to on-premise systems
* Local data processing
* Data residency 
* Easier migration from on-premises to the cloud
* Fully managed service
* Services that work: 
1. EC2, EBS, S3, EKS, ECS, RDS, EMR

## AWS WaveLength
* Infrastructure deployments embedded within the telecom providers data centers at the edge of 5G networks.
* Brings AWS services to edge of 5G network. E.g. EC2, EBS, VPC...
* Ultra low latency applications through 5G networks
* Traffic doesn't leave the telecom providers network as it is served through through carrier's own gateway
* High bandwidth and secure connection to the parent AWS region can be done
* No additional charges or agreements
* Use cases: Smart cities, ML-assisted diagnostics, connected vehicles, interactive live video streams, AR/VR, real time gaming

## Local Zones
* Places AWS compute, storage, database, and other selected AWS services closer to end users to run latency sensitive applications
* Extends VPC to more locations - "Extension of an AWS Region"
* Compatible with EC2, RDS, ECS, EBS, ElastiCache, Direct Connect
* AWS Region N.Virginia (us-east-1) can have Local Zone to Boston, Chicago, Dallas, Houston, Miami

## Global Application Architecture 
1. Single region, single AZ
* Low availability
* High global latency
* Easy to set up
2. Single region, multi AZ
* High availability
* High global latency
* Medium difficulty
3. Multi region, active-passive
* Low global read latency from passive instances in different regions
* High global writes latency since all writes go to active region
4. Multi region, active active 
* Low global reads and write latency and users can access instances in multiple regions closer to them
* More difficult to set up
* E.g. DynamoDB