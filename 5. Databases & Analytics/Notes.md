# Databases 

## Summary 

* Relational DB - Online Transaction Processing: RDS & Aurora (SQL)
* Differences Multi-AZ, Read replica, multi-region 
If one data center (i.e. AZ) loses power, we want our applications to automatically fail over to another data center in the same region. This is termed Multi-AZ. But, if we want our applications to fail over to another data center when the entire region is gone, we need multi-region support.
* In-memory DB: ElastiCache 
* Key/Value DB: DynamoDB (serverless) & DAX (Cache for DynamoDB)
* Warehouse - Online Analytics Processing: Redshift (SQL)
* Hadoop Cluster: EMR (Elastic MapReduce)
* Athena: Query data on S3 (serverless & SQL)
* QuickSight: dashboards for data (serverless)
* DocumentDB: Aurora for MongoDB (JSON NoSQL DB)
* Amazon QLDB: Financial Transaction Ledger (immutable journal, cryptographically verifiable)
* Amazon Managed Blockchain: Managed Hyperledger Fabric & Ethereum blockhains
* Glue Managed ETL (Extract Transform Load) and Data Catalog service for discovering datasets into various databases 
* Database Migration: DMS
* Neptune: Graph DB

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
* Load data, e.g. once every hour, not every second 
* 10x better performance than other data warehouses, scale to PB of data
* Columnar storage of data (instead of row based)
* Massively Parallel Query Executed (MPP), high available 

### EMR 
* Elastic MapReduce 
* Helps create Hadoop clusters for Big Data to analyze and process vast amount of data 
* Clusters can be made up of hundreds of EC2 instances. E.g. Apache Spark, HBase, Presto, Flink
* EMR takes care of provisioning and configuration 
* Has Auto-scaling and integrated with spot instances 
* Use cases: data processing, machine learning, web indexing and big data

### Athena 
* Serverless query service to perform analytics against S3 object
* Use SQL to query the files
* Supports CSV, JSON, ORC, Avro, and Parquet
* User loads data into S3 bucket, AWS Athena will query and analyze the data 
* Amazon QuickSight can be used to get reporting and dashboard from Athena
* $5.0 per TB of data scanned
* "Analyze data in S3 using serverless SQL, think Athena" 

### QuickSight 
* Serverless machine learning powered business intelligence service to create interactive dashboards
* Fast, automatically scaling, embed-able with per-session pricing#
* Can run on top of RDS DB, Aurora, Athena, RedShift, S3 
* Use cases:
1. Business analytics
2. Visualizations 
3. Ad-hoc analysis
4. Get business insights using data

### DocumentDB 
* Aurora is an "AWS implementation" of PostgreSQL/ MySQL
* DocumentDB is the same for MongoDB 
* MongoDB is used to store, query and index JSON data 
* Similar deployment concepts as Aurora (Fully managed, highly available, with replication across 3 AZ)
* DocumentDB storage automatically grows in increments of 10GB up to 64TB
* Automatically scales to workloads with millions of requests per seconds

### Neptune 
* Fully managed graph database
* Popular graph dataset would be a social network 
1. Users have friends 
2. Posts have comments 
3. Comments have likes from users
4. Users share and like posts
* Highly available across 3 AZ, with up to 15 read replicas 
* Build and run applications working with highly connected datasets - optimized for these complex and hard queries
* Can store up to billions of relations and query the graph with milliseconds latency
* Great for knowledge graphs (Wikipedia), fraud detection, recommendation engines and social networking

### QLDB 
* QLDB stands for Quantum Ledger Database 
* A ledger is a book recording financial transactions
* Fully managed, serverless, high available, replication across 3 AZ
* Used to review history of all the changes made to application data over time 
* Immutable system: no entry can be removed or modified, cryptographically verifiable
* 2-3x better performance than common ledger blockchain frameworks, manipulate data using SQL

### Amazon Managed Blockchain
* Blockchain makes it possible to build applications where multiple parties can execute transactions without the need for a trusted central authority
* Is a managed service to
1. Join public blockchain networks
2. Create own scalable private blockchain network
3. Compatible with Hyperledger Fabric and Ethereum
* No decentralized component, in accordance with financial regulation rules

### Glue 
* **Managed extract, transform and load ETL service**
* When you have datasets that are not in the right form for analytics. 
* ETL service is used to prepare and transform the service 
* With glue, it's a fully serverless service
* E.g. Glue ETL extracts data from S3 or RDS and glue script is written to transform the data and the data is loaded into redshift to do analytics. 
* Glue data catalog is a catalog of datasets in the AWS infra and the glue catalog will have a reference of everything, the column name, field names, field types, etc and services like Athena or Redshift can be used to discover the datasets and build the proper schema

### DMS 
* Database Migration Service 
An EC2 instance running DMS can extract data from a source DB and insert the data into a target DB
* Quick and secure migrate database to AWS, resilient and self healing
* The source database remains available during the migration
* Supports: 
1. Homogeneous migration: Oracle to oracle 
2. Heterogenous migration: MS SQL to Aurora 