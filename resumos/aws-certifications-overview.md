# AWS Certifications Overview

## Sumary
- [Cloud Practitioner Concepts](#cloud-practitioner-concepts)
- [Solution Architect Associate Concepts](#solution-architect-associate-concepts)
- [Main Technologies](#main-technologies)

---

## Cloud Practitioner Concepts

### Define the AWS Cloud and its value proposition:
 - A secure cloud service that provides computing, networking, storaging and various services. 
 - It proposes Agility, Elasticity, Flexibility and Security.

### Define the Advantages of Cloud Computing:
 - Trade capital expense for variable expense
 - Massive economies of scale
 - Stop guessing capacity
 - Speed and agility
 - Stop spending money running and maintaining data centers
 - Go global in minutes

### List the different well-architected framework design principles:
  - **Operational excellence:**
    - Perform operations as code
    - Make frequent, small, reversible changes
    - Refine operations procedures frequently
    - Anticipate faillure
    - Learn from all operational failures

  - **Security:**
    - Implement a strong identity foundation
    - Enable traceability
    - Apply security at all layers
    - Automate security best practices
    - Protect data in transit and at rest
    - Keep people away from data
    - Prepare for security events

  - **Reliability:**
    - Automatically recover from failure
    - Test recovery procedures
    - Scale horizontally to increase aggregate workload availability
    - Stop guessing capacity
    - Manage change in automation

  - **Performance Efficiency:**
    - Selecting the right resource types and sizes based on workload requirements
    - Monitoring performance
    - Making informed decisions to maintain efficiency as business needs evolve

  - **Cost Optimization:**
    - Eliminate unneeded cost or suboptimal resources
    - Understanding and controlling where money is being spent
    - Selecting the most appropriate and right number of resource types, analyzing spend over time
    - Scaling to meet business needs without overspending

## Solution Architect Associate Concepts
### Gateway Storage Volumes
 - **Cached volumes** – You store your data in S3 and retain a copy of frequently accessed data subsets locally. Cached volumes offer substantial cost savings on primary storage and minimize the need to scale your storage on-premises. You also retain low-latency access to your frequently accessed data.
 - **Stored volumes** – If you need low-latency access to your entire data set, first configure your on-premises gateway to store all your data locally. Then asynchronously back up point-in-time snapshots of this data to S3. This configuration provides durable and inexpensive off-site backups that you can recover to your local data center or EC2.

### AWS DMS 
 - **Engine Conversion Tool** – Homogeneous database migration.
 - **Schema Converton Tool** – Heterogeneous database migration

### Placement groups
 - **Cluster** – packs instances close together inside an Availability Zone. Used for HPC, low-latency network performance necessary for tightly-coupled node-to-node communication.

 - **Partition** – spreads your instances across logical partitions such that groups of instances in one partition do not share the underlying hardware with groups of instances in different partitions. Used by large distributed and replicated workloads, such as Hadoop, Cassandra, and Kafka.

 - **Spread** – strictly places a small group of instances across distinct underlying hardware to reduce correlated failures.

### AWS Glue
 - **Catalog** – Holds the metadata and the structure of the data.
 - **Database** – Used to create or access the database for the sources and targets.
 - **Table** – Create tables in the database that can be used by the source and target.
 - **Crawler** – A crawler is used to retrieve data from the source using classifiers.
 - **Classifier** – Checks whether a given file is in a format it can handle.

### Disaster recovery options
 - **Backup & Restore**:
   - Lower priority and cost;
   - Restore and deploy resources after event;
   - Recovery Point Objetive/Recovery Time Objective: Hours.
 - **Pilot Light**:
   - Less priority and cost;
   - Core services ready;
   - Start and scale resources after event;
   - RPO/RTO: 10s minutes.
 - **Warm Standby**:
   - More priority and cost;
   - Bussiness critical services ready;
   - Scale resources after event;
   - RPO/RTO: minutes.
 - **Multi-Site Active-Active**:
   - Zero downtime;
   - Zero-near loss;
   - Bigger cost;
   - RPO/RTO: real time.
   ---
   > Recovery Point Objetive – amount of information tolerable to lose.

   > Recovery Time Objective – amount of time operations take to return to normal.

### RAIDS
 - **General types:**
   - **Mirroring** – one disk exact copy of another disk;
   - **Stripping** – data is spread across more than on disk;
   - **Parity** – parity bits is store in the end of data to check integridy.

 - **RAID levels:**
   - **RAID 0** – block-level stripping
   - **RAID 1** – data mirroring
   - **RAID 4** – block-level stripping with dedicated parity disk
   - **RAID 5** – block-level stripping with distributed parity disk
   - **RAID 6** – block-level stripping with double parity disk
   - **RAID 10** – RAID 1 + RAID 0
   - **RAID 2 & 3** – not used

---

## Main Technologies

### Analytics
 - **Athena**: Query Data in S3 using SQL
 - **EMR**: Simplifies running big data frameworks (Apache Hadoop)
 - **Compute Optimizer**: Analyzes (machine learning) metrics of utilization and makes recommendations
 - **Elasticsearch**: Full-text search and analytics engine.
 - **Data Pipeline**: Web service used to automate data movement and transformation
 - **AWS Glue**: Serverless service that makes Extraction, Transformation, and Loading of data to warehouses or lakes.

### Cost Management
 - **Cost Explorer**: Analyze Your AWS Cost and Usage, provides usage-based forecasts of estimated billing for the next month
 - **Budgets**: Set Custom Cost and Usage Budgets (alerts)
 - **Cost and Usage Report**: Access Granular Comprehensive Cost and Usage Information, tracks your usage and provides estimated charges (without usage-based forecasts)
 - **Bills**: List the Historical Cost that would have been ocurried over the past month
 - **Savings Plans**: Save up to 72% on compute usage with flexible pricing
 - **Pricing Calculator**: create an estimate for the cost of your use cases

### Compute
 - **Elastic Container Registry**: Store and Retrieve Docker Images
 - **Elastic Container Service**: Run and Manage Docker Containers, simple API
 - **Lightsail**: Non-tech Launch and Manage Virtual Private Servers, saving doest not apply
 - **Elastic Beanstalk**: Quickly deploy and manage applications in the AWS Cloud without worrying about the infrastructure (.NET, Node, Python)
 - **Fargate**: Run Containers without Managing Servers or Clusters, serverless
 - **Outposts**: Run AWS services on-premises

### Database
 - **Aurora**: High Performance fully-managed Relational Database
 - **DynamoDB**: fully-managed serverless NoSQL Database
  - **Redshift**: Fast, Simple, Cost-effective Data Warehousing, BI Tools, optimized for analysis and reporting of large amounts of data
 - **DocumentDB**: fully-managed document database
 - **ElastiCache**: In-memory Caching System
 - **RDS**: Managed Relational Database Service for MySQL, PostgreSQL, Oracle, SQL Server, and MariaDB
 - **RDS on VMware**: Automate on-premises database management

### Migration
 - **Server Migration Service**: Used to migrate on-premises workloads to AWS EC2.
  - **DataSync**: Used to migrate NFS servers to S3, EFS, Fsx, etc. It does not support database migrations.
  - **Schema Conversion Tool**: Makes heterogeneous database migrations by automatically converting the source database schema.
  - **Database Migration Service**: Migrate databases with minimal downtime, remaining fully operational during migration.

### Developer Tools
 - **Cloud9**: IDE, Write, Run, and Debug Code
 - **CodeBuild**: Build and Test Code, fully managed continuous integration service that compiles source code
 - **CodeCommit**: Store Code in Private Git Repositories
 - **CodeDeploy**: Automate Code Deployment
 - **CodePipeline**: Release Software using Continuous Delivery, automate BTD
 - **CodeStar**: Develop and Deploy Applications, unified interface
 - **X-Ray**: Analyze and debug your applications
 - **CodeGuru**: Provides intelligent recommendations for improving code quality (machine learning)

### Management
 - **CloudWatch**: Monitor Resources and Applications metrics
 - **CloudFormation**: Create and Manage Resources with Templates
 - **CloudTrail**: Track User Activity and API Usage, enables governance, compliance and risk auditing
 - **Config**: Track Resource Inventory and Changes
 - **OpsWorks**: Automate Operations (replication and deployment) with Chef and Puppet, configure layers
 - **Organizations**: Central governance and management across accounts
 - **Personal Health Dashboard**: Personalized View of Services Health
 - **Service Health Dashboard**: Up-to-minute health info
 - **Service Catalog**: Create and Use Standardized Products (IAM, CloudFormation)
 - **Trusted Advisor**: Optimize Performance and Security, check service limits and provide guidance to provision resources (P,CO,S,FT,SL)
 - **Well-Architected Tool**: Review and improve your workloads
 - **Control Tower**: Automated deployments in multi-account environments.
 - **Migration Hub**: Used to track the progress of migrations in AWS.

### Networking and Content Delivery
 - **CloudFront**: Global Content Delivery Network
 - **Route 53**: Scalable Domain Name System
 - **Global Accelerator**: Improve application availability and performance
 - **Transit Gateway**: Easily scale VPC and account connections through a central hub
 - **Elastic Load Balancing**: Distribute incoming traffic across multiple targets
 - **PrivateLink**: Private connectivity between VPCs, AWS products and their on-premise networks without exposing traffic to the public Internet.

### Security and Compliance
 - **IAM**: Manage User Access and Encryption Keys
 - **Cognito**: Identity Management for your Apps (mobile, web)
 - **Detective**: Investigate potential security issues, machine learning
 - **GuardDuty**: Managed Threat Detection Service, continuously monitors for malicious activity (accounts, workloads, and data stored in S3)
 - **Inspector**: Analyze Application Security (create assessment template)
 - **Macie**: Discover, Classify, and Protect your Data (machine learning)
 - **CloudHSM**: Hardware-based Key Storage for Regulatory Compliance
 - **Key Management Service**: Managed Creation and Control of Encryption Keys
 - **RAM**: Simple, secure service to share AWS resources (accross regions)
 - **Security Hub**: Unified security and compliance center, automate continuos security checks of your high-priority 
 - **Shield**: DDoS Protection
 - **WAF**: Filter Malicious Web Traffic
 - **Secrets Manager**: Stores encrypted credentials and eliminates the need for hard-coding credentials
 - **Encryption SDK**: Encryption client-side library, do not require AWS

### Storage
 - **Elastic File System (EFS)**: Fully managed file system for Linux EC2
 - **FSx for Lustre**: High-performance storage. It can read data from S3 and connect to multiple instances at the same time. 
 - **Storage Gateway**: Hybrid Storage Integration
 - **CloudEndure Disaster Recovery**: Highly automated disaster recovery
 - **QuickSight**: Fast Business Analytics Service
 - **Simple Notification Service (SNS)**: Pub/Sub, Mobile Push and SMS
 - **Simple Queue Service (SQS)**: Managed Message Queues, helps decoupling app components, used to facilitate horizontal scaling

### Others
 - **Polly**: Converts texo into voice audios. Uses Lexicon to map dictionaries.


---

## AWS Shared Responsability Model
![](../img/share_responsability_model.png)
