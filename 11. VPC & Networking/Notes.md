## IP Addresses in AWS
* IPv4 - Internet Protocol version 4 (4.3 Billion Addresses)
* Public IPv4 - can be used on the Internet 
* EC2 instance gets a new public IP address every time you stop and then start it 
* Private IPv4 - can be used on private networks (LAN) such as internal AWS networking
* Private IPv4 is fixed for EC2 instances even if you start/stop them
* Elastic IP - allows you to attach a fixed public IPv4 address to EC2 instance
* It has an ongoing cost if not attached to EC2 instance of it the instance is stopped, don't have to pay if its attached to an EC2 instance network
* IPv6 - Internet Protocol version 6 (3.4 * 10^38 addresses)
* every IP address is public (no private range)
* Example: 2001:db8:....

## VPC & SubNets Primer
* VPC - Virtual Private Cloud: private network to deploy your resources (regional resource)
* Subnets allow you to partition your network inside your VPC (Availability Zone resource)
* A public subnet is a subnet that is accessible from the internet
* A private subnet is not accessible from the internet
* To define access to the internet and between subnets so resources can communicate we use Route Table
* In a public subnet you can put load balancers and things like databases in the private subnet for better security
* Internet Gateway: helps VPC instances connect to internet. Public subnet will have a route to the internet gateway
* NAT Gateway/ NAT Instance: Use if you want instances in the private subnet to access the internet while while remaining private
1. Create NAT Gateway / NAT Instance within the public subnet
2. Create route from private subnet instance to the NAT gateway in the public subnet 
3. Create a route from NAT gateway to the internet gateway

## Network ACL & Security Groups
### NACL (Network ACL)
* firewall which controls traffic from and to a subnet
* Can ALLOW or DENY rules
* Are attached at subnet level
* Rules only include IP addresses
* Stateless: return traffic must be explicitly allowed by rules
* Process rules in number order when deciding whether to allow traffic
* Automatically applies to all instances in subnet it's associated with

### Security groups
* A firewall that controls traffic to and from an ENI/ EC2 instance
* Can only have ALLOW rules
* Rules include IP addresses and other security groups
* Stateful: return traffic is automatically allowed
* All rules are evaluated before deciding to allow traffic 
* Applies to instance only

## VPC Flow Logs 
* Capture information about IP traffic going into your interfaces
* VPC flow logs
* Subnet flow logs
* Elastic Network Interface flow logs
* Helps monitor and troubleshoot connectivity issues: E.g. 
1. If a subnet cannot connect to the internet
2. If a subnet cannot connect to a subnet
3. If internet cannot access a subnet
* Captures network information from AWS managed interfaces such as Elastic Load balancers, ElastiCache, RDS, Aurora
* VPS Flow logs data can go to S3/ CloudWatch logs

## VPC Peering
* Connect to two VPC privately using AWS network
* Make them behave if they were in the same network
* Ensure IP ranges do not overlap CIDR
* VPC Peering connection is not transitive (A -> B | C -> A | C ! -> B)

## VPC Endpoints
* Endpoints allow you to connect to AWS services using a private network instead of public www network
* This gives you enhanced security and lower latency to access AWS services
* VPC Endpoint Gateway lets S3, DynamoDB connect to instances in private subnet
* VPC Endpoint Interface: connect any other service on AWS

## PrivateLink (VPC Endpoint Services)
* Most secure & scalable way to expose a service to 1000s of VPCs
* Does not require VPC peering, internet gateway, NAT, route tables...
1. If are talking to a vendor on the AWS marketplace and they run an application service in their own VPC and you want to use their application service in your application within your VPC
2. Requires a network load balancer on third party service vpc. An AWS private link is then established connecting with an elastic network interface to the consumer application

## Site to Site VPN & Direct Connect 
* On-premise data center 
* Want to connect it to AWS VPC
1. Can use Site to Site VPN -> connect on-premise VPN to AWS, the connection is auto encrypted through the public internet. Limited bandwidth and some security concerns
2. Can use Direct Connect (DX) -> Establish a physical connection between on-premises and AWS. The connection is private, secure and fast. Goes over a private network. Have to get a direct connect between the on-premise and AWS partner and takes at least a month to establish
* For site to site VPN, you must use a Customer Gateway (CGW). AWS must use a virtual private gateway provisioned.

## Client VPN
* Connect from computer using OpenVPN to your private network in AWS and on-premises
* Allow you to connect to EC2 instances over a private IP
* Establish VPN connection over the public internet. Can use Site to Site VPN to connect to on-premise data center

## Transit gateway
* For having a transitive peering between thousands of VPC and on-premises, hub-and-spoke (star) connection
* One single gateway to provide this functionality 
* Works with direct connect gateway, vpn connections

# Summary 
VPC Endpoints: Provides private access to AWS services within a VPC 
PrivateLink: Privately connect to a service in a 3rd party VPC 
VPC Flow Logs: network traffic logs 
Site to Site VPN: VPN over public internet between on-premises DC and AWS 
Client VPN: OpenVPN connection from your computer into the VPC 
Direct Connect: direct private connection to AWS 
Transit Gateway: Connect thousands of VPC and on-premises networks together