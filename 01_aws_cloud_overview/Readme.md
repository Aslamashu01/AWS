>## ! DISCLAIMER
>Despite the most of the labs in this course can be done using the AWS free tier, i.e. without any charging, there a couple of tasks that require creation of paid resources.
Resources like NAT Gateway, Route53 zone etc., will cost you some money (but not that much, fortunately). Anyway, before creating any type of resources, please be sure you carefully read and understood the appropriate pricing policy. Every type of resource is AWS has its own pricing page, for example [Route53 pricing](https://aws.amazon.com/route53/pricing/). If you cannot find the pricing policy in official AWS documentation, just google it, for example "NAT gateway pricing".
To avoid extra money expenditures, you can [set up a billing alert](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html) that will notify you immediately after you have reached some threshold in your billing.
And of course, do not forget cleaning up all the unnecessary resources after completing the lab.


# Your goals

- Know about AWS Fundamentals Course  

- Be familiar with "The Five Pillars of AWS"

- Understand "Shared Responsibility Model" 

- Know about AWS Support

- Learn about AWS Quotas

- Get brief familiarity with AWS provided services and domains 

- Budget alerts 


# AWS Cloud Overview

   **Amazon Web Services (AWS)** is the world’s most comprehensive and broadly adopted cloud platform, offering over 200 fully featured services from data centers globally.
   AWS has the most extensive global cloud infrastructure. No other cloud provider offers as many Regions with multiple Availability Zones connected by low latency, high throughput, and highly redundant networking. AWS has 80 Availability Zones within 25 geographic regions around the world, and has announced plans for 15 more Availability Zones and 5 more AWS Regions.

   The platform is developed with a combination of infrastructure as a service (IaaS), platform as a service (PaaS) and packaged software as a service (SaaS) offerings.

## AWS Fundamentals. 
### Core Concepts
Please learn carefully the following AWS Fundamentals course: 
>Click here >> [AWS FUNDAMENTALS](https://aws.amazon.com/getting-started/fundamentals-core-concepts/)

This AWS Fundamentals Course is designed to teach you the core concepts you need to work effectively within AWS.
When first starting, AWS can seem overwhelming. A cloud-native paradigm of building infrastructure can be a radical departure from the traditional on-premises way of doing things. And regardless if this is your first time working with infrastructure or you've been tuning Linux kernels for the last decade, it can be hard to know where to start with AWS's selection of over 175 services.

The AWS Fundamentals Course is designed to help you get started with AWS regardless of your experience. In this course, we will teach you about the [five pillars](https://aws.amazon.com/architecture/well-architected/?e=gs2020&p=fundcore&p=gsrc&c=fcc) of AWS, mental models to use when thinking about the cloud, and key concepts that will be applicable across any service you end up using.
Structure
The AWS Fundamentals Course will be divided into five modules. Each module will follow the following format:

- **Intro**: A short description of the pillar we will be focusing on
- **Mental Model**: A guiding mental model to help you understand the concepts introduced in each pillar
- **Concepts**: Key concepts covering broad foundational topics for each pillar
- **Conclusion**: Summary of what we discussed
- **Further Reading**: Additional links and resources

#### The Five Pillars
The Five Pillars covered in the AWS Fundamentals Course come from the [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/?e=gs2020&p=fundcore&p=gsrc&c=fcc). 
The Well-Architected Framework is the distillation of over a decade of experience building scalable applications on the cloud.
The Five Pillars consist of the following areas: ***Operational Excellence***, ***Security***, ***Reliability***, ***Performance Efficiency***, and ***Cost Optimization***.

![](images/aws_five_pillars.png)
<br><br>
---
<br><br>
### Shared Responsibility Model

Security and Compliance is a shared responsibility between AWS and the customer. 
This shared model can help relieve the customer’s operational burden as AWS operates, 
manages and controls the components from the host operating system and virtualization 
layer down to the physical security of the facilities in which the service operates. 
The customer assumes responsibility and management of the guest operating system 
(including updates and security patches), other associated application software as well 
as the configuration of the AWS provided security group firewall. 
Customers should carefully consider the services they choose as their responsibilities 
vary depending on the services used, the integration of those services into their 
IT environment, and applicable laws and regulations. The nature of this shared 
responsibility also provides the flexibility and customer control that permits 
the deployment. As shown in the chart below, this differentiation of responsibility 
is commonly referred to as Security “of” the Cloud versus Security “in” the Cloud.

![](images/aws_shared_responsibility_model.png)

**AWS responsibility “Security of the Cloud”** - AWS is responsible for protecting 
the infrastructure that runs all of the services offered in the AWS Cloud. 
This infrastructure is composed of the hardware, software, networking, and facilities 
that run AWS Cloud services.

**Customer responsibility “Security in the Cloud”** – Customer responsibility will be 
determined by the AWS Cloud services that a customer selects. This determines the amount 
of configuration work the customer must perform as part of their security responsibilities. 
For example, a service such as Amazon Elastic Compute Cloud (Amazon EC2) is categorized 
as Infrastructure as a Service (IaaS) and, as such, requires the customer to perform all 
of the necessary security configuration and management tasks. Customers that deploy an 
Amazon EC2 instance are responsible for management of the guest operating system 
(including updates and security patches), any application software or utilities installed 
by the customer on the instances, and the configuration of the AWS-provided firewall 
(called a security group) on each instance. For abstracted services, such as Amazon S3 
and Amazon DynamoDB, AWS operates the infrastructure layer, the operating system, 
and platforms, and customers access the endpoints to store and retrieve data. 
Customers are responsible for managing their data (including encryption options), 
classifying their assets, and using IAM tools to apply the appropriate permissions.

For more information please checkout the following materails: > [Shared Responsibility Model](https://aws.amazon.com/compliance/shared-responsibility-model/)

### [Video Course]: AWS Overview based on AWS Practitioner certification:
**Course Description**: This course is about basic AWS services and concepts. 
All topics in it will help to prepare and pass AWS Practitioner Certification.
<br><br>
[![AWS Practitioner_Certification](images/aws_overview_based_on_practitioner_certification_course.png)](https://youtu.be/3hLmDS179YE)

## [AWS Support](docs/Support_center.md)

### General description:

AWS Support offers a range of plans that provide access to tools and expertise that support your AWS solutions&#39; success and operational health. All support plans provide 24/7 access to customer service, AWS documentation, technical papers, and support forums. For technical support and more resources to plan, deploy, and improve your AWS environment, you can choose a support plan that best aligns with your AWS use case.

AWS for each account provides a basic plan. The basic plan is free for each AWS customer. You are able to change the basic plan to three different paid plans:

- Developer
- Business
- Enterprise

### Detailed overview

A detailed overview and compare existing plans are available here:

[https://aws.amazon.com/premiumsupport/plans/](https://aws.amazon.com/premiumsupport/plans/)

Keep in mind most major features available across all plans.

All AWS customers automatically have 24/7 access to these features of Basic Support:

- One-on-one responses to account and billing questions;
- Support forums;
- Service health checks;
- Documentation, technical papers, and best practice guides.


Customers with a Developer Support plan have access to these additional features:

- Everything covered from the basic plan;
- Best practice guidance;
- Building-block architecture support: guidance on how to use AWS products, features, and services together;
- Supports an unlimited number of support cases that can be opened by one primary contact, which is the AWS account root user.

Business Support or Enterprise Support plan have access to the next features:

- Use-case guidance – What AWS products, features, and services to use to best support your specific needs;
- AWS Trusted Advisor – A feature of AWS Support, which inspects customer environments and identifies opportunities to save money, close security gaps, and improve system reliability and performance. You can access all Trusted Advisor checks;
- The AWS Support API to interact with Support Center and Trusted Advisor. You can use the AWS Support API to automate support case management and Trusted Advisor operations;
- Third-party software support – Help with Amazon Elastic Compute Cloud (Amazon EC2) instance operating systems and configuration. Also, help with the performance of the most popular third-party software components on AWS. Third-party software support isn&#39;t available for customers on Basic or Developer Support plans;
- Supports an unlimited number of AWS Identity and Access Management (IAM) users who can open technical support cases.


Enterprise Support plan have access to next features:

- Application architecture guidance – Contextual guidance on how services fit together to meet your specific use case, workload, or application;
- Infrastructure event management – Short-term engagement with AWS Support to get a deep understanding of your use case. After analysis, provide architectural and scaling guidance for an event;
- Technical account manager – Work with a technical account manager (TAM) for your specific use cases and applications;
- White-glove case routing;
- Management business reviews.


##### _Note_:

_Good idea moving from basic to more high plan just when it needs only. For instance, if you need additional support from AWS or_ _temporarily_ _need to have some features which available only in more high plans, you can get it in the next 30 days. And after, to move back to the basic (develop) plan._

##### _Keep in mind_:

_For urgently contact with AWS support, use a chat or phone call as an answer method._

### Monitoring status

You can easy to monitor all statuses of your case in the Support Center. A flow looks like this:

1. Unassigned
2. Work in Progress (WIP)
3. Pending Customer Action (ask for more information) or Pending Amazon Action (let you know that the case is being investigated)
4. The last status is close Case. It means your problem is solved.  If you don&#39;t respond within ten days, the case is closed automatically. Nevertheless, you can always reopen a resolved or closed case.

For each update, you receive email with the correspondence and a link to the case in Support Center.

##### _Important note_:

- _You can&#39;t respond to case correspondence by email. Use the link in the email to navigate to the support case._
- _You must sign in to the AWS account that submitted the support case. If you sign in as an IAM user, you must have the required permissions to view support cases._

### Useful links:

- AWS Knowledge Center Videos: How do I change my AWS Support plan?

[https://www.youtube.com/watch?v=TM98uI7TYPs&amp;ab\_channel=AmazonWebServices](https://www.youtube.com/watch?v=TM98uI7TYPs&amp;ab_channel=AmazonWebServices)

- AWS Knowledge Center Videos: How do I sign up for an AWS Support plan?

[https://www.youtube.com/watch?v=E6fMAMCE\_dc&amp;ab\_channel=AmazonWebServices](https://www.youtube.com/watch?v=E6fMAMCE_dc&amp;ab_channel=AmazonWebServices)

- Getting started with AWS Support:

[https://docs.aws.amazon.com/awssupport/latest/user/getting-started.html](https://docs.aws.amazon.com/awssupport/latest/user/getting-started.html)

- Access AWS Support

[https://docs.aws.amazon.com/awssupport/latest/user/accessing-support.html](https://docs.aws.amazon.com/awssupport/latest/user/accessing-support.html)

- Changing your AWS Support plan

[https://docs.aws.amazon.com/awssupport/latest/user/changing-support-plans.html](https://docs.aws.amazon.com/awssupport/latest/user/changing-support-plans.html)

---
## [AWS service quotas](docs/Service_quotas.md)

### Service Overview

Each AWS account has default quotas. Default quotas calls like limits, and that limits linked with each AWS services. Unless otherwise noted, each quota is Region-specific. Along with looking up the quota values, you can also request a quota increase from the Service Quotas console.

### Use cases / Considerations

When your infrastructure grows you can meet with default AWS limits for your Account. For instance, Amazon EC2 Auto Scaling has a limit of 200 groups per region. If you should have more resources than is defined in the limits, you have few options to achieve it::

- Open the Service Quotas console _(__reference link: D__)._ In the navigation pane, choose AWS services. Select a service, select a quota, and follow the directions to request a quota increase. For more information, see Requesting a Quota Increase in the Service Quotas User Guide _(__reference link: E__)._ (This way is recommended);
- Use the request-service-quota-increase AWS CLI command _(__reference link: F__)_;
- Open the AWS Support Center page _(__reference link: G__),_ sign in if necessary, and choose to Create case. Choose Service limit increase. Complete and submit the form.


##### _Keep in mind_:

If a service is not yet available in Service Quotas, use AWS Support Center instead. Increases are not granted immediately. It might take a couple of days for your increase to become effective.

Also, an important note, all services are separated into two different groups, where the first is adjustable, and the second one is not adjustable. If a service is adjustable then you can make a request for increasing a quota for service. And if a service is not adjustable you can not be increasing a quota for it. For instance, you are able to make a request for Auto Scaling groups per region service, but you can not do anything with SNS topics per Auto Scaling group.

Also, you can easily view current service quotas applied to your AWS account. There are few options which you can follow:

- Open the Service endpoints _(__reference link: A__)_ and quotas page in the documentation, search for the service name, and click the link to go to the page for that service. To view the service quotas for all AWS services in the documentation without switching pages, view the information in the Service Endpoints and Quotas page _(__reference link: A__)_ in the PDF instead.
- Open the Service Quotas console _(__reference link: B__)._ In the navigation pane, choose AWS services and select a service.
- Use the list-service-quotas _(__reference link: C__)_ and list-aws-default-service-quotas AWS CLI commands _(__reference link: С__)._


### Reference links:

1. Service endpoints and quotas page:

    - [https://docs.aws.amazon.com/general/latest/gr/aws-service-information.html](https://docs.aws.amazon.com/general/latest/gr/aws-service-information.html)
    - Link for PDF file: [https://docs.aws.amazon.com/general/latest/gr/aws-general.pdf#aws-service-information](https://docs.aws.amazon.com/general/latest/gr/aws-general.pdf#aws-service-information)
    <br />

1. Link for a dashboard with service quotas in the current region:

    - [https://console.aws.amazon.com/servicequotas/home](https://console.aws.amazon.com/servicequotas/home)
    <br />

1. Link for AWS CLI command for a request service quotas for current aws account:

    - [https://docs.aws.amazon.com/cli/latest/reference/service-quotas/list-service-quotas.html](https://docs.aws.amazon.com/cli/latest/reference/service-quotas/list-service-quotas.html) (get current quotas)
    - [https://docs.aws.amazon.com/cli/latest/reference/service-quotas/list-aws-default-service-quotas.html](https://docs.aws.amazon.com/cli/latest/reference/service-quotas/list-aws-default-service-quotas.html) (get default qoutas)
    <br />

1. Link to service quotas console:

    - [https://console.aws.amazon.com/servicequotas/home](https://console.aws.amazon.com/servicequotas/home)
    <br />

1. Requesting a quota increase:

    - [https://docs.aws.amazon.com/servicequotas/latest/userguide/request-quota-increase.html](https://docs.aws.amazon.com/servicequotas/latest/userguide/request-quota-increase.html)
    <br />

1. Link for AWS CLI command for a quota increase

    - [https://docs.aws.amazon.com/cli/latest/reference/service-quotas/request-service-quota-increase.html](https://docs.aws.amazon.com/cli/latest/reference/service-quotas/request-service-quota-increase.html)
    <br />

1. Link for AWS Support Center page:

    - [https://console.aws.amazon.com/support/home#/](https://console.aws.amazon.com/support/home#/)

### General useful links:

- View and Manage Quotas for AWS Services Using Service Quotas:

[https://www.youtube.com/watch?v=ZTwfIIf35Wc&amp;ab\_channel=AmazonWebServices](https://www.youtube.com/watch?v=ZTwfIIf35Wc&amp;ab_channel=AmazonWebServices)

---

**What are the services provided by AWS?**

Each type of service is categorized under a domain:
- AWS Networking and Content Delivery services
- AWS Compute services
- AWS Storage services
- Database services
- Analytics 
- Developer Tools
- Management tools
- IoT
- Security
- Enterprise app

#### **AWS Networking and Content Delivery services**

|Category|Service description|AWS service|
| :- | :- | :- |
|Network foundations|Define and provision a logically isolated network for your AWS resources|Amazon VPC|
||<p>Connect VPCs and on-premises networks through a central hub </p><p></p>|AWS Transit Gateway|
||<p>Provide private connectivity between VPCs, services, and on-premises applications </p><p></p>|AWS PrivateLink|
|Application networking|Automatically distribute traffic across a pool of resources, such as instances, containers, IP addresses, and Lambda functions|Elastic Load Balancing|
||Provide application-level networking for containers and microservices|AWS App Mesh|
||Create, maintain, and secure APIs at any scale|Amazon API Gateway|
|<p>Edge networking</p><p></p>|<p>Securely deliver data, videos, applications, and APIs to customers globally with low latency, and high transfer speeds </p><p></p>|Amazon CloudFront|
||<p>Route users to Internet applications with a managed DNS service </p><p></p>|Amazon Route 53|
||<p>Direct traffic through the AWS Global network to improve global application performance </p><p></p>|AWS Global Accelerator|
|Network security|<p>Safeguard applications running on AWS against DDoS attacks </p><p></p>|AWS Shield|
||<p>Protect your web applications from common web exploits </p><p></p>|AWS WAF|
||<p>Centrally configure and manage firewall rules </p><p></p>|AWS Firewall Manager|

#### **AWS Compute services**

|Category|Service description|AWS service|
| :- | :- | :- |
|<p>Instances (Virtual machines) </p><p></p>|Secure and resizable compute capacity (virtual servers) in the cloud|Amazon Elastic Compute Cloud (EC2)|
||Run fault-tolerant workload for up to 90% off|Amazon EC2 Spot Instances|
||Automatically add or remove compute capacity to meet changes in demand|Amazon EC2 Autoscaling|
||Easy-to-use cloud platform that offers you everything you need to build an application or website|Amazon Lightsail|
|Containers|Highly secure, reliable, and scalable way to run containers|Amazon Elastic Container Service (ECS)|
||Easily store, manage, and deploy container images|Amazon Elastic Container Registry (ECR)|
||Fully managed Kubernetes service|Amazon Elastic Kubernetes Service (EKS)|
||Serverless compute for containers|AWS Fargate|
|Serverless|Run code without thinking about servers. Pay only for the compute time you consume|AWS Lambda|

#### **AWS Storage services**

|Category|Service description|AWS service|
| :- | :- | :- |
|<p>Object storage</p><p></p>|<p>Object storage built to store and retrieve any amount of data from anywhere</p><p></p>|<p>Amazon S3</p>|
|<p>File storage</p><p></p>|<p>Simple, serverless, set-and-forget, elastic file system</p><p></p>|<p>Amazon Elastic File System</p>|
||<p>Fully managed file storage built on Windows Server</p><p></p>|<p>Amazon FSx for Windows File Server</p><p></p>|
||Amazon FSx for Lustre is a fully managed service that provides cost-effective, high-performance, scalable storage for compute workload|<p>Amazon FSx for Lustre</p>|
|<p>Block storage</p>|Amazon Elastic Block Store (EBS) is an easy to use, high-performance, block-storage service|<p>Amazon Elastic Block Store</p>|

#### **Database services**

|Category|Service description|AWS service|
| :- | :- | :- |
|Relational|Traditional applications, ERP, CRM, e-commerce|Amazon Aurora, Amazon RDS, Amazon Redshift|
|Key-value|High-traffic web apps, e-commerce systems, gaming applications|Amazon DynamoDB|
|In-memory|Caching, session management, gaming leaderboards, geospatial applications|Amazon ElastiCache for Memcached, Amazon ElastiCache for Redis|

#### **AWS Security, Identity, & Compliance services**

|Category|Service description|AWS service|
| :- | :- | :- |
|<p>Identity & access management</p>|<p>Securely manage access to services and resources</p>|AWS Identity & Access Management (IAM)|
||Managed Microsoft Active Directory|AWS Directory Service|
||Identity management for your apps|Amazon Cognito|
|Detection|Managed threat detection service|Amazon GuardDuty|
||Analyze application security|Amazon Inspector|
||Record and evaluate configurations of your AWS resources|AWS Config|
||Track user activity and API usage|AWS CloudTrail|
|Data protection|Key storage and management|AWS Key Management Service (KMS)|
||Hardware based key storage for regulatory compliance|AWS CloudHSM|
||Provision, manage, and deploy public and private SSL/TLS certificates|AWS Certificate Manager|
||Rotate, manage and retrieve secrets|AWS Secrets Manager|


