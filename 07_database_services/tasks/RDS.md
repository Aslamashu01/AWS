# Task: Setup highly available RDS cluster

## Problem to Be Solved
You’re a system engineer. Company you work for badly needs a relational database in AWS cloud that can run their critical production workloads without worrying about a database becoming unavailable due to the failure of a database component. For critical application workloads, a couple of minutes of application downtime can result in significant revenue losses. To reduce the load on the source instance and improve performance for read-heavy workloads, Cloud Databases users can redirect writes and reads to source and replica instances within the HA setup, respectively.

## Explanation of the Solution
- [Storage autoscaling](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PIOPS.StorageTypes.html#USER_PIOPS.Autoscaling)
- [Read replicas](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ReadRepl.html)
- [Multi-AZ deployment](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.MultiAZ.html)
- [Difference between read replicas and multi-AZ deployment](https://medium.com/awesome-cloud/aws-difference-between-multi-az-and-read-replicas-in-amazon-rds-60fe848ef53a)

Implementation Details:
- Open RDS dashboard
- Click “create database”
- Choose mysql as an engine
- Choose “dev/test” template
- Input a strong admin password
- Choose “burstable class” as your db instance class and choose “db.t3.small” as instance type
- Choose “Create a standby instance” at “Availability & durability”
- Create new security group at “Connectivity” and type some valid name for it
- Click “create database”
- Wait until database status be “Ready”
- Run virtual machine in chosen VPC
- Install mysql client on it
- Connect to the RDS instance
- Reboot RDS with failover enabled

### Benefits / Outcomes / Pros and Cons / Summary
Highly available solutions are mostly used at production environments in order to make them more resilient and stable in a case of emergency. But every single 9 in your SLA makes your infrastructure cost more. In case of RDS to provide high availability to your instance your bill grows significantly with each extra instance.

## Pricing
[Link to cost estimation of HA RDS deployment with 3 instances with 100 GB (about ~370$ per month)](https://calculator.aws/#/estimate?id=0452daa80baacaac5a6365e8ab437f69bd16cc92)


## Tearing down
- Select instance you created
- Click “Actions” -> “Delete”
- Do not create final snapshot and retain automated backups
