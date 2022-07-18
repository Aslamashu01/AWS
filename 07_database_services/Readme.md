# AWS  Database Services

## Table of Content

- [Your goals](#your-goals)
- [Relational Database Service (RDS)](#amazon-relational-database-service-rds-amazon-rds)
- [DynamoDB](#amazon-dynamodb) 
- [ElastiCache](#amazon-elasticache)
- [Move to managed databases](#move-to-managed-databases)

## Recommended Trainings:

- [AWS Certified Solutions Architect - Associate (SAA-C02): 8 Databases](https://learn.epam.com/detailsPage?id=9ba80105-60eb-47b6-96dc-15f4bd6ac5e0&source=EXTERNAL_COURSE)
- [AWS Administration: Tips and Tricks](https://learn.epam.com/detailsPage?id=59938d3d-c5dc-4206-a43f-c90b03babd94&source=EXTERNAL_COURSE)
- [AWS: Storage and Data Management](https://learn.epam.com/detailsPage?id=b08af5ea-1be0-4d45-98d5-90491bbaa32f&source=EXTERNAL_COURSE)


## Your goals


- Be able to explain what AWS RDS is, what features it provides

- Explain what DynamoDB is for and what elements it has 

- Replication Options / Sharding. Active-passive and Active-Active replication. 

- Backing up Database Services 

- Understand DynamoDB Accelerator(DAX) in DynamoDB 

- Know how to monitor Database Services (key metrics, base and extended monitoring capabilities)

- Know about eventually consistent/strongly consistent reads and Read/Write capacity mode in DynamoDB 

- ElastiCache: Redis vs MemCached 


## Database Services on AWS

![](images/aws-dbs.png)


Modernize your data infrastructure with fully managed, purpose-built databases.

 AWS offers 15+ purpose-built engines to support diverse data models, including relational, key-value, document, in-memory, graph, time series, wide column, and ledger databases. Start small and scale as your applications grow with relational databases that are 3-5X faster than popular alternatives, or non-relational databases that give you microsecond to sub-millisecond latency. 
 
 Free your teams from time-consuming database tasks like server provisioning, patching, and backups. AWS fully managed database services provide continuous monitoring, self-healing storage, and automated scaling to help you focus on application development.

 Support multi-region, multi-primary replication, and provide full data oversight with multiple levels of security, including network isolation and end-to-end encryption. AWS databases deliver the high availability, reliability, and security you need for business-critical, enterprise workloads.

## Pricing considerations and free tier details:

|Database type|Use cases|AWS service|Free Tier Offer Details|Product Pricing|
|:----|:----|:----|:----:|:----|
|Relational|Traditional applications, enterprise resource planning (ERP), customer relationship management (CRM), ecommerce|Amazon Aurora|No|[Amazon Aurora Pricing](https://aws.amazon.com/rds/aurora/pricing/)|
|Relational|Traditional applications, enterprise resource planning (ERP), customer relationship management (CRM), ecommerce|Amazon RDS|12 MONTHS FREE 750 hours per month of db.t2.micro database usage (applicable database engines);   20 GB of general purpose (SSD) database storage   20 GB of storage for database backups and database snapshots  |[Amazon RDS Pricing](https://aws.amazon.com/rds/pricing/?p=ft&c=db)|
|Relational|Traditional applications, enterprise resource planning (ERP), customer relationship management (CRM), ecommerce|Amazon Redshift|2-MONTH FREE TRIAL 750 DC2.Large node hours per month|[Amazon Redshift Pricing](https://aws.amazon.com/redshift/pricing/?p=ft&c=db)|
|Key-value|High-traffic web applications, ecommerce systems, gaming applications|Amazon DynamoDB|ALWAYS FREE 25 GB of storage;   25 units of write capacity;   25 units of read capacity (enough to handle up to 200 million requests per month)|[Amazon DynamoDB Pricing](https://aws.amazon.com/dynamodb/pricing/?p=ft&c=db)|
|In-memory|Caching, session management, gaming leaderboards, geospatial applications|Amazon ElastiCache|12 MONTHS FREE 750 hours of cache.t2micro node usage|[Amazon ElastiCache Pricing](https://aws.amazon.com/elasticache/pricing/?p=ft&c=db)|
|In-memory|Caching, session management, gaming leaderboards, geospatial applications|Amazon MemoryDB for Redis|2-MONTH FREE TRIAL 750 t4g.small instance hours per month;   20 GB of data per month|[Amazon MemoryDB Pricing](https://aws.amazon.com/memorydb/pricing/?p=ft&c=db)|
|Document|Content management, catalogs, user profiles|Amazon DocumentDB (with MongoDB compatibility)|No|[Amazon DocumentDB Pricing](https://aws.amazon.com/documentdb/pricing/)|
|Wide column|High-scale industrial apps for equipment maintenance, fleet management, and route optimization|Amazon Keyspaces|3 MONTHS FREE 30 million on-demand write request units;   30 million on-demand read request units;   1 GB of storage (limit of one free tier per payer account)|[Amazon Keyspaces Pricing](https://aws.amazon.com/keyspaces/pricing/)|
|Graph|Fraud detection, social networking, recommendation engines|Amazon Neptune|No|[Amazon Neptune Pricing](https://aws.amazon.com/neptune/pricing/)|
|Time series|Internet of Things (IoT) applications, DevOps, industrial telemetry|Amazon Timestream|No|[Amazon Timestream Pricing](https://aws.amazon.com/timestream/pricing/)|
|Ledger|Systems of record, supply chain, registrations, banking transactions|Amazon Ledger Database Services (QLDB)|No|[Amazon Ledger Database Services (QLDB)Pricing](https://aws.amazon.com/qldb/pricing/)|



## Amazon Relational Database Service (Amazon RDS)

![](images/aws-rds.jpg)

Amazon Relational Database Service (Amazon RDS) is a service that makes it easier to set up, operate, and scale a relational databases (SQL) in the AWS Cloud. It provides cost-efficient, resizable capacity for an industry-standard relational database and manages common database administration tasks. 

Amazon RDS takes over many of the difficult and tedious management tasks of a relational database: 

- When you buy a server, you get CPU, memory, storage, and IOPS, all bundled together. With Amazon RDS, these are split apart so that you can scale them independently. If you need more CPU, less IOPS, or more storage, you can easily allocate them. 

- Amazon RDS manages backups, software patching, automatic failure detection, and recovery. 

- To deliver a managed service experience, Amazon RDS doesn't provide shell access to DB instances. It also restricts access to certain system procedures and tables that require advanced privileges. 

- You can have automated backups performed when you need them, or manually create your own backup snapshot. You can use these backups to restore a database. The Amazon RDS restore process works reliably and efficiently. 

- You can use the database products you are already familiar with: MySQL, MariaDB, PostgreSQL, Oracle, Microsoft SQL Server. 

- You can get high availability with a primary instance and a synchronous secondary instance that you can fail over to when problems occur. You can also use MariaDB, Microsoft SQL Server, MySQL, Oracle, and PostgreSQL read replicas to increase read scaling. 

- In addition to the security in your database package, you can help control who can access your RDS databases by using AWS Identity and Access Management (IAM) to define users and permissions. You can also help protect your databases by putting them in a virtual private cloud. 

![](images/rds-create.jpg)
![](images/rds-aws-arch-diagram-4.png)

### Monitoring:

Here a list of events that RDS records. Additionally, here you can get information about what information about an event recorded and the rotation period of records: 
- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ListEvents.html 
- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/monitoring-cloudwatch.html 
- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Monitoring.OS.html 

Amazon RDS provides automated recommendations for database resources, such as DB instances, read replicas, and DB parameter groups. These recommendations provide best practice guidance by analyzing DB instance configuration, usage, and performance data:

- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Recommendations.html 

### More details 

Example of CloudWatch alarm for RDS DB instance’s memory consumption:
- https://www.youtube.com/watch?v=TehQPNcudbM 


## Amazon DynamoDB 

![](images/aws-dynamodb-console.jpg)

**Amazon DynamoDB** is a fully managed **NoSQL** database service that provides fast and predictable performance with seamless scalability.

In DynamoDB, tables, items, and attributes are the core components that you work with. A table is a collection of items, and each item is a collection of attributes.  

DynamoDB supports eventually consistent and strongly consistent reads. 

DynamoDB comes in two Read/Write capacity modes, which should be chosen depending on application load and your budget. 

For working with data, you can access Amazon DynamoDB using the AWS Management Console, the AWS Command Line Interface (AWS CLI), or the DynamoDB API. 

### Use cases / Considerations 

![](images/no-sql-simple-app.png)

Whenever SQL database (like RDS) is not suitable for your needs (e.g., data structure is not the same across all items), DynamoDB is a great choice for such cases. 

If your application requires really fast reads (real-time bidding, social gaming, and trading applications) DynamoDB Accelerator (DAX) is a good choice, as it will cache query data from DynamoDB and your application will get the needed data much faster. 

As DynamoDB has two Read/Write capacity modes, it’s important to understand, whether to use On-Demand or Provisioned mode. 

### Governance 

DynamoDB provides on-demand backup capability. It allows you to create full backups of your tables for long-term retention and archival for regulatory compliance needs. For more information, see On-Demand Backup and Restore for DynamoDB. 

You can create on-demand backups and enable point-in-time recovery for your Amazon DynamoDB tables. Point-in-time recovery helps protect your tables from accidental write or delete operations. With point-in-time recovery, you can restore a table to any point in time during the last 35 days. For more information, see Point-in-Time Recovery: How It Works. 

DynamoDB allows you to delete expired items from tables automatically to help you reduce storage usage and the cost of storing data that is no longer relevant. For more information, see Expiring Items By Using DynamoDB Time to Live (TTL). 

Dynamo is also integrated with CloudWatch, allowing you to enable logging and monitoring. 

### Cautions 

Dynamo has a number of quotas you need to pay attention to. One of the most important limits is Read/Write throughput. If you exceed this limit, all queries and requests will be throttled. Setting up CloudWatch alerts to track such cases would be really nice. 

### Pricing considerations 

All info regarding DynamoDB pricing can be found in AWS docs 

### More details 

- https://www.youtube.com/watch?v=MF9a1UNOAQo  


## Amazon ElastiCache

![](images/aws-elasticache-console.jpg)

**Amazon ElastiCache** makes it easy to set up, manage, and scale distributed **in-memory cache** environments in the AWS Cloud. It provides a high performance, resizable, and cost-effective in-memory cache, while removing complexity associated with deploying and managing a distributed cache environment. ElastiCache works with both the Redis and Memcached engines. 

Supports Memcached and Redis engines:

![](images/elasticache-create.jpg)

An ElastiCache cluster is a logical grouping of one or more ElastiCache nodes. Data is partitioned across EC2 machines.

### Governance 

As most of AWS services, ElastiCache is fully integrated with [AWS CloudWatch](https://docs.aws.amazon.com/AmazonElastiCache/latest/mem-ug/CacheMetrics.html) for metrics, [AWS CloudTrail](https://docs.aws.amazon.com/AmazonElastiCache/latest/mem-ug/logging-using-cloudtrail.html) for logging and it also supports [AWS SNS](https://docs.aws.amazon.com/AmazonElastiCache/latest/mem-ug/ECEvents.html), sending all important events to a specific topic. 

For security, ElastiCache provides [several types of encryption](https://docs.aws.amazon.com/AmazonElastiCache/latest/mem-ug/encryption.html) and [Role Based Access Control](https://docs.aws.amazon.com/AmazonElastiCache/latest/mem-ug/Clusters.RBAC.html). 

### Cautions 

Memcached doesn’t have replication like Redis does, so you must make sure it`s handled from application side. 

### Pricing considerations 

All info regarding ElastiCache pricing can be found in [AWS docs](https://aws.amazon.com/elasticache/pricing/)

### More details 

- https://d0.awsstatic.com/whitepapers/performance-at-scale-with-amazon-elasticache.pdf  


## Move to managed databases

- https://aws.amazon.com/getting-started/hands-on/move-to-managed/?trk=gs_card


## Self-check

1. What's the difference between Relational, NoSQL and In-Memory databases?
2. If you need to store simple data(string/integer) in cache, will you use Redis or Memcached?
3. When you want to make sure you get the latest data from DynamoDB, which type of read will you use?
4. You need to make a snapshot in RDS at a specific time, is that possible? If yes, how?
5. Can you make your RDS instance highly available? If yes, how?
5. Can you make your DynamoDB highly available? If yes, how?
6. How can you backup Database services?
 
