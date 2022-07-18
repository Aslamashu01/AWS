# Systems Manager

Systems Manager is comprised of individual capabilities, which are grouped into five categories: 

- Operations Management
    - Explorer
    - OpsCenter
- Application Management
    - Application Manager
    - AppConfig
    - Parameter Store
- Change Management
    - Change manger
    - Automation
    - Change calendar
    - Maintenance Windows
- Node Management
    - Fleet manager
    - Compliance
    - Inventory
    - Session manager
    - Run Command
    - State Manager
    - Patch Manager
    - Distributor
- Shared Resources

### Useful links:
- [What is AWS Systems Manager? (Video)](https://youtu.be/MK4ZoCs-muo)
- [AWS Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html)
- [SSM Capabilities](https://docs.aws.amazon.com/systems-manager/latest/userguide/features.html)
- [How SSM works](https://docs.aws.amazon.com/systems-manager/latest/userguide/how-it-works.html)
- [Accessing Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/access-methods.html)
- [Systems Manager prerequisites](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-prereqs.html)
- [AWS Systems Manager Pricing](https://aws.amazon.com/systems-manager/pricing/)


## Operations Management

### Explorer

Explorer is a customizable operations dashboard that reports information about your AWS resources. Explorer displays an aggregated view of operations data (OpsData) for your AWS accounts and across Regions. In Explorer, OpsData includes metadata about your EC2 instances, patch compliance details, and State Manager association compliance details. OpsData also includes information from supporting AWS services like AWS Trusted Advisor, AWS Compute Optimizer, and information about your AWS Support cases.
To raise operational awarness, Explorer also displays operational work items (OpsItems). Explorer provides context about how OpsItems are distributed across your business units or applications, how they trend over time, and how they vary by category. You can group and filter information in Explorer to focus on items that are relevant to you and that require action. When you identify high priority issues, you can use Systems Manager OpsCenter to run Automation runbooks and quickly resolve those issues.

#### Useful links:
- [Explorer](https://docs.aws.amazon.com/systems-manager/latest/userguide/Explorer.html)
- [Getting started with Systems Manager Explorer and OpsCenter](https://docs.aws.amazon.com/systems-manager/latest/userguide/Explorer-setup.html)
- [Using Systems Manager Explorer](https://docs.aws.amazon.com/systems-manager/latest/userguide/Explorer-using.html)
- [Exporting OpsData from Systems Manager Explorer](https://docs.aws.amazon.com/systems-manager/latest/userguide/Explorer-exporting-OpsData.html)
- [Troubleshooting Systems Manager Explorer](https://docs.aws.amazon.com/systems-manager/latest/userguide/Explorer-troubleshooting.html)
- [Get Started with AWS Systems Manager Explorer (video)](https://www.youtube.com/watch?v=XTwv1vSH4h4)
- [How does Explorer works? (video)](https://www.youtube.com/watch?v=2efz7EH4czQ&t=1297)
- [Explorer Pricing](https://aws.amazon.com/systems-manager/pricing/#Explorer)

### OpsCenter

OpsCenter provides a central location where operations engineers and IT professionals can view, investigate, and resolve operational work items (OpsItems) related to AWS resources. OpsCenter is designed to reduce mean time to resolution for issues impacting AWS resources. This Systems Manager capability aggregates and standardizes OpsItems across services while providing contextual investigation data about each OpsItem, related OpsItems, and related resources. OpsCenter also provides Systems Manager Automation documents (runbooks) that you can use to quickly resolve issues. You can specify searchable, custom data for each OpsItem. You can also view automatically-generated summary reports about OpsItems by status and source.
OpsCenter is integrated with Amazon EventBridge and Amazon CloudWatch. This means you can configure these services to automatically create an OpsItem in OpsCenter when a CloudWatch alarm enters the ALARM state or when EventBridge processes an event from any AWS service that publishes events. Configuring CloudWatch alarms and EventBridge events to automatically create OpsItems enables you to quickly diagnose and remediate issues with AWS resources from a single console.

#### Useful links: 
- OpsCenter
- Getting started with OpsCenter
- Creating OpsItems
- Working with OpsItems
- Remediating OpsItem issues using Systems Manager Automation
- Viewing OpsCenter summary reports
- Supported resources reference
- Auditing and logging OpsCenter activity
- Aggregate and Resolve Operational Issues Using AWS Systems Manager OpsCenter (video)
- Integrate AWS Systems Manager OpsCenter with Amazon CloudWatch Alarms (video)
- Integrate Your Data Sources into AWS Systems Manager OpsCenter Using Amazon EventBridge
- OpsCenter Pricing
- Resource limits for OpsCenter

## Application Management

### Application Manager

Application Manager, a capability of AWS Systems Manager, helps DevOps engineers investigate and remediate issues with their AWS resources in the context of their applications. Application Manager aggregates operations information from multiple AWS services and Systems Manager capabilities to a single AWS Management Console.
In Application Manager, an application is a logical group of AWS resources that you want to operate as a unit. This logical group can represent different versions of an application, ownership boundaries for operators, or developer environments, to name a few.

After you set up and configure AWS services and Systems Manager capabilities, Application Manager displays the following types of information about your resources:
- Alarms provided by Amazon CloudWatch
- Compliance information provided by AWS Config and Systems Manager State Manager
- Kubernetes cluster information provided by Amazon EKS
- Log data provided by AWS CloudTrail and Amazon CloudWatch Logs
- OpsItems provided by Systems Manager OpsCenter
- Resource details provided by the AWS services that host them.

#### Useful links:
- Application Manager
- Features of Application Manager
- Getting started with Systems Manager Application Manager
- Working with Application Manager
- Working with Amazon EKS in Application Manager
- Working with runbooks
- Resource quotas for Application Manager

### AppConfig

Use AWS AppConfig, a capability of AWS Systems Manager, to create, manage, and quickly deploy application configurations. You can use AWS AppConfig with applications hosted on Amazon Elastic Compute Cloud (Amazon EC2) instances, AWS Lambda, containers, mobile applications, or IoT devices.

AWS AppConfig use cases:
- Application tuning – Introduce changes carefully to your application that can be tested with production traffic.
- Feature toggle – Turn on new features that require a timely deployment, such as a product launch or announcement.
- Allow list – Allow premium subscribers to access paid content.
- Operational issues – Reduce stress on your application when a dependency or other external factor impacts the system.

#### Useful links:
- What Is AWS AppConfig?
- Getting started
- Working with AWS AppConfig
- AWS AppConfig overview (video)
- Manage and Deploy Application Configurations with AWS AppConfig (video)
- AppConfig pricing
- Service Quotas
- Configuration store quotas and limitations

### Parameter Store

AWS Parameter Store provides secure, hierarchical storage for configuration data management and secrets management. You can store data such as passwords, database strings, Amazon Machine Image (AMI) IDs, and license codes as parameter values. You can store values as plain text or encrypted data. You can reference Systems Manager parameters in your scripts, commands, SSM documents, and configuration and automation workflows by using the unique name that you specified when you created the parameter.

#### Useful links:
- Parameter Store
- Setting up Parameter Store
- Working with Parameter Store
- AWS Systems Manager Parameter Store Introduction (video)
- AWS Systems Manager Parameter Store Tutorial (video)
- AWS Systems Manager Parameter Store | Concept | Demo (video)
- Setting up notifications or trigger actions based on Parameter Store events
- Auditing and logging Parameter Store activity
- Managing parameter tiers
- Increasing Parameter Store throughput
- Parameter Store Pricing


## Change Management

### Change manger

Change Manager, a capability of AWS Systems Manager, is an enterprise change management framework for requesting, approving, implementing, and reporting on operational changes to your application configuration and infrastructure. From a single delegated administrator account, if you use AWS Organizations, you can manage changes across multiple AWS accounts and across AWS Regions. Alternatively, using a local account, you can manage changes for a single AWS account. Use Change Manager for managing changes to both AWS resources and on-premises resources. With Change Manager, you can use pre-approved change templates to help automate change processes for your resources and help avoid unintentional results when making operational changes.

#### Useful links:
- Change Manager
- Setting up Change Manager
- Working with Change Manager
- Auditing and logging Change Manager activity
- Troubleshooting Change Manager
- AWS on Air 2020: AWS Systems Manager Change Manager (video)
- Change Manager pricing
- Audit Change Manager activity using Amazon CloudWatch alarms
- Audit Change Manager activity using AWS CloudTrail

### Automation

Systems Manager Automation simplifies common maintenance and deployment tasks of Amazon EC2 instances and other AWS resources. Automation enables you to do the following:
- Build automations to configure and manage instances and AWS resources.
- Create custom runbooks or use pre-defined runbooks maintained by AWS.
- Receive notifications about Automation tasks and runbooks by using Amazon EventBridge.
- Monitor Automation progress and details by using the AWS Systems Manager console.

#### Use-cases:

- **Perform common IT tasks** - automation can simplify common IT tasks such as changing the state of one or more instances (using an approval automation) and managing instance states according to a schedule
- **Safely perform disruptive tasks in bulk** - Systems Manager includes features that help you target large groups of instances by using Amazon EC2 tags, and velocity controls that help you roll out changes according to the limits you define.
- **Simplify complex tasks** - Automation offers one-click automations for simplifying complex tasks such as creating golden Amazon Machines Images (AMIs), and recovering unreachable EC2 instances
- **Enhance operations security** - Using delegated administration, you can restrict or elevate user permissions for various types of tasks. Delegated administration enables you to provide permissions for certain tasks on certain resource without having to give a user direct permission to access the resources.
- **Share best practices** - Automation lets you share best practices with the rest of your organization. You can create best practices for resource management in runbooks and easily share the runbooks across AWS Regions and groups

#### Useful links:
- Create own SSM Document and Execute Automation (Video)
- Setting up Automation
- Working with automations
- Systems Manager Automation actions reference
- Working with runbooks
- Systems Manager Automation runbook reference
- Automation walkthroughs
- Understanding automation statuses
- Troubleshooting Systems Manager Automation
- Automation pricing
- Monitoring Systems Manager events with Amazon EventBridge


### Change calendar

AWS Systems Manager Change Calendar (Change Calendar) lets you set up date and time ranges when actions you specify (for example, in Systems Manager Automation runbooks) may or may not be performed in your AWS account. In Change Calendar, these ranges are called events. When you create a Change Calendar entry, you are creating a Systems Manager document of the type ChangeCalendar. In Change Calendar, the document stores iCalendar 2.0 data in plaintext format. Events that you add to the Change Calendar entry become part of the document.

#### Useful links:
- Setting up Change Calendar
- Working with Change Calendar
- Add Change Calendar dependencies to Automation documents

### Maintenance Windows

AWS Systems Manager Maintenance Windows let you define a schedule for when to perform potentially disruptive actions on your instances such as patching an operating system, updating drivers, or installing software or patches. Maintenance Windows also lets you schedule actions on numerous other AWS resource types, such as Amazon Simple Storage Service (Amazon S3) buckets, Amazon Simple Queue Service (Amazon SQS) queues, AWS Key Management Service (AWS KMS) keys, and many more. For a full list of supported resource types that you can include in a maintenance window target, see Supported Resources for AWS Resource Groups in the AWS Resource Groups User Guide.

#### Useful links:
- Setting up Maintenance Windows
- Working with maintenance windows (console)
- Systems Manager Maintenance Windows tutorials (AWS CLI)
- Maintenance window walkthroughs
- Maintenance window scheduling and active period options
- Registering maintenance window tasks without targets
- Troubleshooting maintenance windows

## Node Management

### Fleet manager

AWS Systems Manager Fleet Manager (Fleet Manager) is a unified user interface (UI) experience that helps you remotely manage your server fleet running on AWS, or on premises. With Fleet Manager, you can view the health and performance status of your entire server fleet from one console. You can also gather data from individual instances to perform common troubleshooting and management tasks from the console. This includes viewing folder and file contents, Windows registry management, operating system user management, and more.


#### Useful links:
- Getting started with Fleet Manager
- Working with Fleet Manager
- AWS on Air 2020: AWS What’s Next ft. AWS Systems Manager Fleet Manager

### Compliance

You can use AWS Systems Manager Compliance to scan your fleet of managed instances for patch compliance and configuration inconsistencies. You can collect and aggregate data from multiple AWS accounts and Regions, and then drill down into specific resources that aren’t compliant. By default, Compliance displays current compliance data about Systems Manager Patch Manager patching and Systems Manager State Manager associations.
Patch compliance data from Patch Manager can be sent to AWS Security Hub. Security Hub gives you a comprehensive view of your high-priority security alerts and compliance status. It also monitors the patching status of your fleet.

#### Useful links:
- Getting started with Compliance
- Creating a Resource Data Sync for Compliance
- Working with Compliance
- Remediating compliance issues using EventBridge
- Compliance walkthrough (AWS CLI)


### Inventory

AWS Systems Manager Inventory provides visibility into your Amazon EC2 and on-premises computing environment. You can use Inventory to collect metadata from your managed instances. You can store this metadata in a central Amazon Simple Storage Service (Amazon S3) bucket, and then use built-in tools to query the data and quickly determine which instances are running the software and configurations required by your software policy, and which instances need to be updated. You can configure Inventory on all of your managed instances by using a one-click procedure. You can also configure and view inventory data from multiple AWS Regions and accounts.
If the pre-configured metadata types collected by Systems Manager Inventory don't meet your needs, then you can create custom inventory.

#### Useful links:
- Learn more about Systems Manager Inventory
- Setting up Systems Manager Inventory
- Configuring inventory collection
- Working with Systems Manager inventory data
- Working with custom inventory
- Viewing inventory history and change tracking
- Systems Manager Inventory walkthroughs
- Troubleshooting problems with Systems Manager Inventory
- Collect Inventory Data with Systems Manager Inventory (video)

### Session manager

Session Manager is a fully managed AWS Systems Manager capability that lets you manage your Amazon Elastic Compute Cloud (Amazon EC2) instances, on-premises instances, and virtual machines (VMs) through an interactive one-click browser-based shell or through the AWS Command Line Interface (AWS CLI). Session Manager provides secure and auditable instance management without the need to open inbound ports, maintain bastion hosts, or manage SSH keys. Session Manager also makes it easy to comply with corporate policies that require controlled access to instances, strict security practices, and fully auditable logs with instance access details, while still providing end users with simple one-click cross-platform access to your managed instances.
Support for Windows Server, Linux and macOS instances.

#### Useful links:
- Session Manager
- Setting up Session Manager
- Working with Session Manager
- Auditing session activity
- Logging session activity
- Session document schema
- Troubleshooting Session Manager
- Session Manager pricing 

### Run Command

AWS Systems Manager Run Command lets you remotely and securely manage the configuration of your managed instances. A managed instance is any EC2 instance or on-premises machine in your hybrid environment that has been configured for Systems Manager. Run Command enables you to automate common administrative tasks and perform one-time configuration changes at scale. You can use Run Command from the AWS Management Console, the AWS Command Line Interface, AWS Tools for Windows PowerShell, or the AWS SDKs. Run Command is offered at no additional cost.

#### Useful links:
- Setting up Run Command
- Running commands using Systems Manager Run Command
- Handling exit codes with scripts
- Understanding command statuses
- Run Command walkthroughs
- Troubleshooting Systems Manager Run Command
- Remotely Run Commands on an EC2 Instance (hands-on)
- AWS Systems Manager Run Command (video)
- AWS Systems Manager RUN Command - Execute Command on EC2 Instance (video)
- Streamline Configuration Management Automation Using AWS Systems Manager Run Command (video)
- Systems Manager service quotas

### State Manager

AWS Systems Manager State Manager (State Manager) is a secure and scalable configuration management service that automates the process of keeping your Amazon Elastic Compute Cloud (Amazon EC2) and hybrid infrastructure in a state that you define.

#### Use-cases:
- Bootstrap instances with specific software at start-up.
- Download and update agents on a defined schedule, including AWS Systems Manager SSM Agent (SSM Agent).
- Configure network settings.
- Join instances to a Windows domain (only Windows Server instances).
- Patch instances with software updates throughout their lifecycle.
- Run scripts on Linux, macOS, and Windows managed instances throughout their lifecycle.

#### Useful links:
- State Manager
- About State Manager
- Working with associations in Systems Manager
- AWS Systems Manager State Manager walkthroughs
- Combating Configuration Drift Using Amazon EC2 Systems Manager and Windows PowerShell DSC
- Configure Amazon EC2 Instances in an Auto Scaling Group Using State Manager
- Ansible with AWS Systems Manager State Manager (video) 

### Patch Manager

AWS Systems Manager Patch Manager automates the process of patching managed instances with both security related and other types of updates. You can use Patch Manager to apply patches for both operating systems and applications. (On Windows Server, application support is limited to updates for Microsoft applications.) You can use Patch Manager to install Service Packs on Windows instances and perform minor version upgrades on Linux instances. You can patch fleets of Amazon Elastic Compute Cloud (Amazon EC2) instances or your on-premises servers and virtual machines (VMs) by operating system type. This includes supported versions of Amazon Linux, Amazon Linux 2, CentOS, Debian Server, macOS, Oracle Linux, Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES), Ubuntu Server, and Windows Server. You can scan instances to see only a report of missing patches, or you can scan and automatically install all missing patches.

#### Useful links:
- Patch Manager
- Patch Manager prerequisites
- How Patch Manager operations work
- About patching operations
- About patch baselines
- Remediating out-of-compliance instances (Patch Manager)
- Use Kernel Live Patching on Amazon Linux 2 instances
- Working with Patch Manager (console)
- Working with Patch Manager (AWS CLI)
- AWS Systems Manager Patch Manager walkthroughs
- Troubleshooting Patch Manager
- Patching for your Amazon EC2 Instances (video)
- AWS Systems Manager - Automate Patching for Amazon EC2 Instances (video)  
- Patch Manager pricing

### Distributor

AWS Systems Manager Distributor lets you package your own software—and find AWS-provided agent software packages, such as AmazonCloudWatchAgent, or third-party packages such as Trend Micro—to install on AWS Systems Manager managed instances. Distributor publishes resources, such as software packages, to AWS Systems Manager managed instances. Publishing a package advertises specific versions of the package's document—a Systems Manager document that you create when you add the package in Distributor—to managed instances that you identify by managed instance IDs, AWS account IDs, tags, or an AWS Region.Deploys packages to both Windows and Linux instances

#### Useful links:
- Distributor
- Setting up Distributor
- Working with Distributor
- Auditing and logging Distributor activity
- Troubleshooting AWS Systems Manager Distributor
- Manage Distribution of Software Packages with AWS Systems Manager Distributor (video) 
- Distributor pricing
- Supported package platforms and architectures
