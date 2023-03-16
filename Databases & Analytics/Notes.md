# Databases 

## Intro

* Storing data on a drive. E.g. EC2 instance store, S3, EFS, EBS can have limits. 
* Data can be efficiently stored and accessed by using different types of databases. 
* The data can be structured and indexes can be used to efficiently query the data.

## Relational Databases 
* Uses relations to link tables. 
* SQL used to query 

## NoSQL Databases
* Built for specific data model
* Flexible schema for building modern applications
* Benefits:
1. Flexible: easy to evolve data model
2. Scalable: designed to scale out by using distributed clusters
3. Performant: optimized for specific data model
 
## Shared Responsibility on AWS 
* AWS offers to manage different databases
* Benefits include:
1. Quick provision, high availability, vertical and horizontal scaling
2. Automated backup and restore, operations, upgrades
3. Operating System Patching is handled by AWS 
4. Monitoring and alerting
The database services could run on EC2 but you must handle yourself the resiliency, backup, patching, high availability, fault tolerance, scaling, etc. 

### AWS RDS 
* AWS Relational Database Service
* Managed DB service in the cloud for DB which use SQL as a query language. 
* Postgres, MySQL, MariaDB, Oracle, Microsoft SQL, Aurora (AWS)
* Has backup & restore 
* Monitoring dashboards
* Read replicas for read performance (Read only copy of database instance with the same or different AWS region)
* Multiple AZ setup for disaster recovery
* Scaling capability 
* Storage backed by EBS
* Can't SSH into instance 
* Typical solution: Elastic load balancer, EC2 instances (possibly in ASG), RDS DB

#### RDS Deployments
* Read replica: Scale read workload for up to 5 read replicas, data is written only to source DB.
* Multi-AZ: Failover in case of AZ outage, replication cross AZ to failover DB
* Multi-Region (Read replicas), source database in Eu can replicate data on RDS on US or AP and writes go to EU as well. Good for region issues. Less latency as application can read form local databases.

### AWS Aurora 
* EC2 instance connects directly to Aurora 
* Aurora supports PostgreSQL and MySQL 
* It is AWS cloud optimized and claims 5x performance improvement over MySQL on RDS, over 3x performance of Postgres on RDS.
* It costs 20% more than RDS but is more efficient
* Storage automatically grows in increments of 10GB up to 128TB

### AWS ElastiCache
* ElastiCache is used to get managed Redis or Memcached DB
* In memory databases with high performance and low latency 
* Helps reduce load off databases for read intensive workloads
* AWS will take care of availability and system configuration 
* Typical solution: Elastic Load balancer, EC2 Instances (possibly in ASG), read/write from slower SQL (relational) database or read/write from fast cache using ElastiCache in memory database. 

### DynamoDB 
* Fully managed highly available with replication across 3 AZ
* Key value NoSQL database 
* Scales to massive workloads, distributed serverless database 
1. Serverless does not mean absence of server. There are servers involved, but you can build and run applications without worrying about the underlying infrastructure. There is resource on demand and do not need to worry about auto scaling during peaks or troughs. 
2. Just need to create a table
* Millions of requests per seconds, trillions of rows, 100s of TB of storage
* Fast and consistent in performance
* Single-digit millisecond latency and low latency retrieval 
* Integrated with IAM for security 
* Low cost and auto scaling available
* Standard & Infrequent access table class

#### DynamoDB Accelerator - DAX 
* Fully managed in-memory cache for DynamoDB
* 10x performance improvement - single digit millisecond latency to microseconds latency when accessing DynamoDB tables. 
* Secure, highly scalable, highly available 

#### DynamoDB - Global table
* Makes table accessible with low latency in multiple regions
* There is 2 way replication between two global tables in different zones. 
* Active active replication (Keeping two or more live databases in sync with each other and for high availability)

### Redshift 
* Redshift is a PostgreSQL, but is not used for OLTP. 
* It's OLAP - only analytics processing (analytics and data warehousing)
* Load data once every hour, not every second 
* 10x better performance than other data warehouses, scale to PB of data
* Columnar storage of data (instead of row based)