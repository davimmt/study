## Sumário
* [What Are Clouds Made Of?](#what-are-clouds-made-of)
* [Overview of Identity and Access Management (IAM)](#overview-of-identity-and-access-management-iam)
* [Virtual Private Cloud (VPC)](#virtual-private-cloud-vpc)
* [Elastic Compute Cloud (EC2)](#elastic-compute-cloud-ec2)
* [AWS Storage Services](#aws-storage-services)
* [ELB and Auto Scaling](#elb-and-auto-scaling)
* [CloudFront and DNS](#cloudfront-and-dns)
* [SQL and NoSQL](#sql-and-nosql)
* [Serverless (Lambda)](#serverless-lambda)
* [Security and Compliance Services](#security-and-compliance-services)
* [Noteworthy AWS Services](#noteworthy-aws-services)
* [AWS Pricing, Billing, and Support Services](#aws-pricing-billing-and-support-services)

---

## What Are Clouds Made Of?
* Within the **traditional client-server architecture**, data is centralized in a local server storage, so that all client computers that use those informations are always updated equally.

* Now, with the **evolution of traditional client-server architecture (cloud type architecture)**, instead of using a local server, applications are now running remotely on a third party server - the cloud.
                
### Components needed to support applications (what clouds are made of)
* **Compute**: brain (CPU) + memory (RAM), gives as the ability of processing;
* **Storage**: data's save location;
* **Database**: app that stores data in a structured way, that can be easily retrieved; (not necessarily this one) 
* **Network**: Your devices -> Switch -> Modem -> Internet -> DNS Server (contact list/book) -> Facebook (e.g.)

### Data Center Challenges
* **Sprawl/Space**: datacenter running out of space;
* **Power & Cooling**: difficulty to handle;
* **Managing**: hard to manage a lot of servers that are not well structured and not using all of their power.

### Cloud Computing Services
* **Infrastructure as a Service (IaaS)**: Part or all of an infrastructure platform (compute + storage) provided by a third party. Underlying infrastructure required for running or providing cloud applications.

* **Plataform as Service (PaaS)**: Entire infrastructure and operating system provided by a third party.
Hypervisor: software layer between the hardware and the operating system, responsible for providing the operating system the abstraction of a virtual machines and control it’s access to the hardware device.
  * Advantage of using Virtual Machines (VM): the ability to migrate it, so if that is a problem with the underlying hardware, it can be easily moved to another piece of hardware.

* **Software as Service (SaaS)**: Entire infrastructure, operating system and software provided by a third party.

* Hardware / Servers > Hypervisor > VMs > OS > Apps

### Types of Cloud
* **Private** (local/on-premises): 
  * Advantages: fully customizable, higher security;
  * Disadvantages: higher cost overall (maintaining, life-cycle, employees to support it), lack of elasticity (not having great flexibility).

* **Hybrid** (part private/part public): 
  * Often used as a transition to public cloud (migration);
  * Sometimes used for backup and disaster recovery (DR).

* **Public** (Cloud/AWS):
  * Advantages: 
    * No capital costs;
    * Pay as you go;
    * Infinite scalability and elasticity (dynamically);
    * Faster and simplified deployment.
  * Disadvantages:
    * Governance challenges;
    * Restrictions, no flexibility;

* **Type of AWS cloud**[1]: mainly IaaS (but, basically, all of them).

* Some of their services as SaaS:
  * Simple Storage Service (S3): is a bulk storage service where you can upload any kind of file (external hard drive/Dropbox).
  * Additional services that provide applications as a frontend to those infrastructure services to simplify your ability to utilize AWS (or anything to support all they can offer).

### Cloud Terminology
* **Scalability**: ability to easily grow and size and capacity and/or scope based on demand.
  * But what happens if we over provision? What happens if we didn't really need these last two sets of servers? Well, in this example, we've already paid for this additional capacity. So it's wasted money. So when something is scalable you can grow it based on demand but if you overestimate, you essentially have wasted capacity and then there's a term called elasticity.
  
* **Elasticity**: it can grow, but it can also shrink.
  * When you're using cloud servers that are elastic, that means that you don't have to pay for that unused capacity, and then we have the terms fault tolerance and high availability. 

* **Fault tolerant**: it has the ability to withstand a certain amount of failure and still remain functional. 
  * Basically, it can self heal or it has a way to return itself to full capacity. An example of this might be a home network. We have this home network with multiple computers, and we have this router. Now let's assume that we have two ports on this router. If one of those ports were to fail, then we could continue to use the internet because the second port is able to pass the traffic. That means the router is fault tolerant. 

* **Highly availability**: are that which we’re still able to continue to use that service.
  * When we attempt to access it, it's there. We basically are able to bypass a failure because we have multiple routers as an example. So if we were in a situation where we had two routers and we had connectivity between both of those routers, if one router were to fail, the second router could continue to pass the traffic. That would be an example of high availability. We're still able to access the platform, and we don't have a single point of failure. If there's a single point of failure anywhere within the environment, then it's not completely highly available. You can have high availability at different levels but ultimately, if there's a single point of failure, it impacts your high availability.

### Primary Benefits of Cloud/AWS
* **Flexibility**: gives us the ability to choose and use as many AWS services as we need.

* **Cost effectiveness**: using cloud is much more cost effective than having to provision millions of dollars of gear within your data center. It converts your cost from a capital cost to an operational cost. By using cloud services, you no longer have those capital costs, so the ability to pay as you go and not have to worry about long term contracts or upfront money for a long term commitment and even getting discounts if you do reserve certain services for a certain period of time is very attractive to many organizations.

* **Capital costs**: mean that you have to pay a large amount of money upfront to cover the cost of that equipment, and you can't recover that cost for a long period of time because that cost has to be depreciated over a certain number of years (think about having to every 3 to 5 years spend millions and millions of dollars again to repeat that process. It's a never ending cycle). 

* **Operational costs**: are for things that you're paying for based on them being required at that time. So like a utility bill or a employee salary, those are things that are ongoing operational costs. 

* **Scalability and elasticity**: scalability gives us the ability to add resources on demand to accommodate growth. So in my virtual network, if I need to add additional server resources I provision additional EC2 instances and when my environment is elastic, if I no longer need those EC2 instances, I can shrink my environment and remove those instances, and my cost is only associated with what I'm actually using.

* **High availability and fault tolerance**: when an environment is fault tolerant, it is able to withstand the loss of a component within the infrastructure while remaining functional. Highly available systems stay operational for/during maintenance and system failures.

### AWS Global Infrastructure
* **Availability Zones**: they work together to make up a collection of AWS resources. Properly designed applications utilize multiple availability zones for high availability and fault tolerance. Those were our definitions or terms that we learned previously. Availability zones have direct low latency connections between each other, and each availability zone is isolated from others to ensure fault tolerance.

* **CloudFront**: basically think about how you go to access a web page and no matter where you are in the world, you want that web page to load quickly. You want the images to pop up fast on your desktop and the desktop of all of your users. So AWS uses their global network and these points of presence to replicate that data in those applications all around the world. And then that way everyone is able to get fast access to that data.

* **Networks**: they connect the AWS availability zones and regions together. They're fast networks, and they even have transoceanic cables that run across the ground under the ocean to link the regions that are located in different parts of the world.

### VPC (Virtual Private Cloud):
* **Networking**:
  * Direct Connect;
  * Route 53: has to do with DNS or domain name services. 
    * Domain names are important for how you go to access things on the internet. So think about you want to go to linuxacademy.com. In order for you to access linuxacademy.com a DNS server has to tell your computer where linuxacademy.com is. That service, on AWS, is called Route 53.

* **Compute**:
* **EC2**: virtual server, that you're allowed to set up they're called instances;
* **Lambda**: is something called serverless. So serverless compute is where you don't have to worry about doing the configuration yourself. 
    * So on EC2 you have to install an operating system and then you install your applications. When software updates come out, you have to install those, you manually have to manage that. Lambda is serverless because you don't have to manage those resources. You basically write code that completes a task and you are only responsible for managing that code. AWS manages the underlying compute resources where those functions run.
    
* **Storage**:
  * S3;
  * Glacier: is for long term storage, but you don’t have to access every day (keep for regulatory reasons).

## Overview of Identity and Access Management (IAM)
* It’s a service within AWS that you use to manage user accounts and groups. In addition to managing uses and groups, some additional things you can do with IAM include managing access policies that you apply to your users and groups, roles, user credentials, password policies, multi factor authentication, and API keys for programmatic access.
* **MFA (Multi-Factor Authentication)**: 6 random digits that changes from every login to grant secure access to one’s account.
* **IAM groups** refers to users and permissions to resources, whereas **IAM roles** refers to resources permisions to another resources.

## Virtual Private Cloud (VPC)
* A private subsection of AWS that you control and you can place AWS resources such as an EC2 instance or a database inside of the VPC. You have full control over who has access to the resources that you place inside of your VPC and then we have the AWS definition Amazon virtual private cloud lets you provision a logically isolated section of the AWS cloud, where you can launch AWS resources in a virtual network that you define. You have complete control over your virtual networking environment, including selection of your own IP address ranges, creation of subnets, and configuration of route tables as well as network gateways.
  * An EC2 instance can only be attached to 1 VPC at a time.

* **Subnet**: is shorthand for a subnetwork, which is a subsection of a network, generally a subnet includes all of the computers in a specific location. This will be the same as all of the computers being on the same subnetwork. So they would share some common characteristics in their addresses.
  * A subnet cannot span Availability Zones, it must reside within a single Availability Zone.

* **Internet Gateway**: it's a combination of hardware and software that provides your private network with a route to the outside world, the internet. AWS's definition is that an internet gateway is a horizontally scaled, redundant, and highly available VPC component that allows communication between instances in your VPC and the internet. It therefore imposes no availability risks or bandwidth constraints on your network traffic.
  * It's redundant and highly available, meaning that if it were to experience some type of a hardware or software failure that the internet gateway would continue to function. 
  * The internet gateway's purpose is to allow our instances or our resources within our VPC to be able to communicate with resources on the internet. The internet gateway's purpose is to allow our instances or our resources within our VPC to be able to communicate with resources on the internet. So if we were setting up a web server on our EC2 instance, the traffic from our users would cross the internet gateway into our VPC in order to access the web server.
  * It does not have any type of bandwidth constraints on it, meaning that it won't be a bottleneck for traffic going into and out of your VPC to and from the internet. So it means that your internet gateway is not going to slow down your traffic as it tries to cross back and forth to and from the internet.
  
 * A subnet is public when it has a route to the IGW, and it's private whent it doesn't.

* **Route Table**: contains a set of rules called routes that are used to determine where network traffic is directed. 
  * GPS of the VPC.
  * VPC’s a main route table associated with.
    * 0.0.0.0.0/0 -> Default route.
    * First Rule: default local route that says that all the resources that are inside one VPC can talk to each other.
    * Second Rule: if that traffic is not local for the VPC, then go ahead and automatically send it across the internet gateway out to the internet.

* **Network Access Control List (NACL)**: security layer (like a firewall) that sits in front of a subnet.
  * “Who’s allowed and who’s rejected?”
  
* **Security Group**: second security layer that at the instance layer or at the network adapter for the instance.

* AWS Cloud(VPC(Subnet(EC2 > Security Group >)> NACL > Route Table >)> IGW >)> Internet

* Nível de instância -> Security Group
* Nível de subnet -> EC2
* Nível de VPC -> NACL, Route Table, (IGW)
* Nível de Região -> VPC, Route Table, IGW

## Elastic Compute Cloud (EC2)
* **EC2**: it's a basic computer. It's a virtual computer, meaning that it's a logical computer or software based computer as opposed to a hardware based computer.
  * AWS's definition is that EC2 provides scalable computing capacity in the AWS Cloud.
* Using EC2 eliminates your need to invest in hardware upfront so you can deploy and develop applications faster.
* **EBS** stands for elastic block storage, the storage drive of your EC2, highly available and reliable storage volume..
* When purchasing a EC2 instance, there are 3 basic types:
  * **On demand**: allows you to purchase an instance type and provision it at any time and terminate it at any time. You're only charged for that instance, while it's running and is billed by the hour, you can provision and terminate an on demand instance, at any time.
  * **Reserved instances**: allow you to purchase an instance for a period of one or three years at a significant discount. But you're required or responsible for the cost of that instance for that entire period. It doesn't matter if you're instance is on or off.
  * **Spot instances**: You bid a price, and you're saying I don't want to pay any more than this price, and as long as the price is equal to or below that price, you have access to that instance. So it gives you a substantial discount for the use of unused instances that AWS has available. For spot instances you're charged by the minute. So when your bid is accepted, meaning the price is equal to or below your bid price an instance is provisioned for you, and that instance will stay online until the price is higher than your bid price. When that happens, the instance will automatically terminate. (*outdated: you no longer have to bid. You pay the spot price that is in effect for the hour the instances are launched*).

* **Charged based on**: purchasing options, instance type, EBS Optimized, AMI Type (OS), Data Transfer, Region.
* **Benefits**: 
  * Elastic web-scaling computing
  * Full root control
  * Flexible options
  * Integrates with most AWS services
  * Reliable
  * High level built-in security
  * Inexpensive
  * Easy to create
  
* **Primary Use Cases**:
  * Web applications
  * Web servers
  * Bach processing
  * Video processing
  * GPU intensive workload
  
* **Instance Types**: basically the CPU of your instance. 
  * The AWS definition is when you launch an instance the instance type that you specify determines the hardware of the host computer. That's the computer that's running your virtual server. Each instance type offers different compute, memory, and storage capabilities and our grouped in instance families based on these capabilities select an instance type based on the requirements of the application or software that you planned to run on that instance.

* **Difference between your security groups and NACLs**: 
  * The **NACLS** are at the subnet layer. They determine if the traffic can enter into the subnet at all.
  * **Security groups** are at the instance layer and they determine whether or not that traffic, once it's in the subnet, is allowed to talk to those individual instances.

## AWS Storage Services
* **S3 Storage Class**
  * **Standard**: most expensive because it has the most overall flexibility.
  * **Standard-IA**: data that is infrequently accessed but we still want that millisecond type latency (minimun of 3 AV).
  * **One-Zone-IA**: data that is infrequently accessed but we still want that millisecond type latency (minimun of 1 AV).
  * **Inteligent Tiering**: for data where you're not quite sure what the access pattern is going to look like. So intelligent tiering will then look at the patterns for how the file is being accessed and then it's able to move that data between the various storage classes you can see again.
  * **Glacier**: is for long term archival of data. So this is data that you are not going to need very frequently, maybe for the foreseeable future you don't see a reason why you would need access unless maybe you had an audit or for compliance reasons you had to keep that data.
  * **Glacier Deep Archive**: more cost effective than regular Glacier. But your retrieval times are much, much bigger.
 
 * **Object Lifecycles**: set of rules used to automatically transfer objects between storage classes at time (like conjobs).

* **AWS Storage Gateway**: a way for you to integrate your existing application services with AWS storage services without fully migrating to the AWS cloud your applications that are running within your corporate data center environment, connect to the AWS cloud using a virtual server or hardware device.
  * The AWS definition: hybrid storage service that enables your on-premises applications to seamlessly use AWS cloud. You can use the services for backup in archive, disaster recovery, cloud data processing, storage tiering, and migration.
  
* **SGW Deployment Types**
  * **File GW**: where data is uploaded to S3 for use with object based workloads.
  * **Volume GW**
    * **Stored volumes**: give you the ability to keep the customer data on the customer premises location. That data can then periodically be backed up to AWS based on snapshots.
    * **Cached volumes**: store data in AWS Cloud and then the data that's most frequently accessed by the customer is actually cached in the customer's data center for fastest access (so this gives the customer the best of both worlds).
  * **Tape GW**: designed for long term, off site data archiving. A virtual tape library talks to the customer's backup software. (?)

## ELB and Auto Scaling
* **Elastic Load Balancing**: evenly distributes traffic bettwen EC2 instances that are associeted with it.
  * AWS definition: a load balancer distibutes incoming application traffic across multiple EC2 instances in multiple AZ. This increases the fault tolerance. Detects unhealthy instances and routes traffic only to healthy instances.
  
 * **Auto Scaling**: automates the process of adding and removing instances based on traffic demand for your application.
   * We set a policy or rules that actually say what determines when to add more instances and what determines when to remove those instances.
   
* **AWS Load Balancers**
  * **Classic Load Balancer**:  previous generation load balancer that managed HTTP, HTTPS, and TCP traffic. It is now used primarily for anyone utilizing the EC2-Classic network.
  * **Application Load Balancer**: used for balancing traffic over HTTP and HTTPS.

## CloudFront and DNS
* **Route 53** where you configure and manage web domains for websites or applications that you host on AWS. 
* Route 53 has three main functions
  * Domain registration: let's you register domain names.
  * Domain name system service (DNS): translated friendly domain names into IP addresses. Responds to DNS queries using global network, wich reduces latency.
  * Health checking: R53 sends automated requests over the internet to your application to verufy that it's reacheble, available and functional.
  
* **CloudFront** is known as a content delivery network or a CDN. CDNs are locations that cache your content at what's known as edge locations that are located around the world.   * The benefit of using a CDN like CloudFront is that you allow your customers to get access to the content more quickly, and it also provides additional security.
  * CloudFront it's a content delivery network. What that does is as a user goes to access that data is, it pulls that data from the origin, which is your source server, and loads it onto a CloudFront edge location that's closest to the user.
  
* **Points of presence** are basically CloudFront edge locations. CloudFront edge locations provide fast access to content such as data, videos, applications, and APIs. The advantage is that it replicates that data to the various points that are in different places around the world to ensure that your customers don't experience a lot of latency when they try to access the data.

## SQL and NoSQL
* **Relational databases** => SQL => RDS (Relational Database Service): used for structured data in rows and columns.
  * Amazon Aurora
  * MySQL
  * MariaDB
  * PostgreSQL
  * Oracle
  
* **Non-relational databases** => NoSQL => DynamoDB: used for non structured data in key and values.
  * DDB only
  * Replaces MongoDB or Oracle NoSQL, e.g.
  
* **ElastiCache**: data caching (in memory data store) service used to help improve speed/performance of web applications running on AWS.
  * Memcached: memory object caching system
  * Redis: fast, open source, in-memory data store an cache
  
* **Redshift**: data warehouse database service designed to handle petabytes of data for analysis.
  * Allows you to run complex queries of standart SQL and BI tools.


## Serverless (Lambda)
* **Lambda**: serverless compute.
* Lambda will replace EC2 instances, for the most part.
  * With EC2 instance you have to provide all of its settings.
  * With Lambda, you simply upload your code, everything else runs on the background.
* Lambda can support from a few requests per day to thousands per second, and you only pay for what compute time that your code consumes. There's no charge when your code is not running.
* With EC2 instances we have to keep those servers up and running all the time.
* With Lambda, your code starts, it executes, it stops, and you only pay for the time that your code is running and it scales automatically based on load to execute as many of the Lambda functions as it needs to.
* Suported languages
  * Node
  * Java
  * C#
  * Ruby
  *  Go
  * .NET Core
  * Python

## Security and Compliance Services
* **Shared responsibility model** defines what the customer is responsible for and what AWS is responsible for when it comes to security and compliance.
* AWS is responsible for operating, managing, and controlling the components from the physical layer, meaning from the actual hardware that resides in the AWS data center up through the virtualization layer.
  * AWS is also responsible for things like physical security of that data center.
* The virtualization layer is where you as the customer then take over.
  *  So if you set up an EC2 instance, you install an operating system on that you're responsible for updating and patching that guest operating system. You're also responsible for any applications that you might install on to that instance as well.
  * Any data that you have or your ability to encrypt that data, that's all your responsibility as the client as well. Any type of network traffic protection that you would like to implement related to the VPC that's assigned to you. You as the customer are responsible for that. Your NACLS, your security groups, how your user accounts are managed. All of these things are your responsibility as the customer.
  
* Security Assessments or Penetration tests
  * Cans
    * EC2, NAT GW, ELB
    * RDS
    * CloudFront
    * Aurora
    * API GW
    * Lambda funcitons
    * Lightsail resources
    * Amazon Elastic Beanstal environments
  * Can'ts
    * DNS zones with R53
    * Denial of service (DoS), Distributed Denial of service (DDoS) simulated
    * Port, protocol, request flooding
    
* **AWS security related services** 
  * **AWS Oganizations**: allows you to *centrally manage your accounts and billing* but it also defines policies that can restrict access at the account level. So at the account level we can say what services and what actions different member accounts within that organization can take. So AWS Organizations is where you have a parent organization and then beneath that parent organization there are additional AWS accounts. 
  * **GuardDuty**: *a threat detection service that constantly monitors the AWS account and the workloads*, it uses threat intelligence feeds to detect threats to the environment. It's a proactive service that monitors for things that potentially could impact your environment.
  * **AWS Inspector**: *analyzes VPC environments for potential security issues*, so it uses a predefined template, and then it matches the environment to that template. And if it finds any differences between the two, then it's able to provide you with recommendations to help you resolve those potential security issues. 
  * **AWS Shield**: provides managed DDOS protection. 
  * **AWS Web Application Firewall (WAF)**: *monitors web requests that are forwarded to your ELB to CloudFront or API Gateway.* WAF half allows or denies access to the content based on the conditions that you specify and then you have AWS Artifact. 
  * **AWS Artifact**: is a portal that *provides access to compliance documentation.*
  
* **AWS Key Management Service (KMS)**: enables encryption of the data and provides centralized encryption, key storage, management, and auditing.
  * May be generated in the key management service or by a **cloud hardware security module or cloud HSM** (a hardware appliance that can be used to generate and manage your encryption keys).
  * Services that support KMS
    * S3 and Glacier
    * Storage Gateway
    * EBS
    * RDS, DynamoDB
    * SMS
    * CloudTrail
---

## Noteworthy AWS Services
*  **Quick start**: gives you the ability to use templates provided by AWS to help you get quickly set up and running within the AWS environment for a specific configuration.
  * **Linux Bastion Host**: quick start guide is designed to help you get a Bastion host set up and running so that you can get that connectivity into your instances that are in a private subnet.
* **Amazon Athena**: serveless interactive query service used to analyze data in S3 using standad SQL (billed only for the queries you run).
* **Amazon EMR**: provides a managed Hadoop framework, designed for processing broad sets of big data (web indexing, machine learning, log and financial analysis).
* **Amazon Lightsail**: VPServer instance aimed at developers to provide everything needed to launch a service quickly.
* **Amazon Rekognition**: provides video/image analysis.
* **Amazon Device Farm**: provides physical devices that can be used to test and troubleshoot application on mobile devices.
* **Amazon Mechanical Turk**: crowdsourcing marketplace that simplifies outsourcing of process and jobs to a distributed workforce, great for manual and time-consuming tasks.

---

## AWS Pricing, Billing, and Support Services
* **AWS organizations** allows you or your company to manage billing across multiple AWS accounts in one user interface.
  * AWS definition: Organizations offer policy based management for multiple accounts. You can create groups of accounts and apply policies to those accounts. You can also essentially manage policies across multiple accounts *without requiring custom scripts or manual processes.* You can create service control policies that centrally control services using multiple AWS accounts. So you can use SCP and based on things like what services you want your accounts to have access to or not have access to. You can create these policies that will then be pushed to all of the accounts within your organization. You can also use organizations to help automate the creation of new accounts using an API. And you can simplify billing for your multiple accounts by enabling you to set up a single payment method for all accounts in your organization through consolidated building, AWS organizations is available to all customers at no charge.
* Benefits
  * Centrally manage access policies across multiple AWS accounts
  * Controll access to AWS services
  * Automate AWS account creation and management
  * Consolidate billing across multiple AWS accounts
    * Allows you to view, manage, and pay bills for multiple AWS accounts in a single interface. 
    * With consolidated billing, you can see a combined view of charges incurred by all your accounts, as well as taking advantage of pricing benefits from aggregated use.

* **AWS Pricing Model**
  * Pay-as-you-go (few exceptions)
  * No long-term contract or complex licensing (few exceptions)
  * Volume discounts, the more you use a service, the cheaper it can get
  * No termination fees
  * Free Tier for new accounts for 1 year.
  
* S3
  * How much data you store
    * Data at rest
    * Charged per GB
    * Varies based on region and storage class
  * Requests
    * Moving data in/out S3
    * PUT, POST, LIST, GET requests
    * Lifecycle transitions
    * Data retrival, archive, restore
    
* EC2
  * Per second running
  * Dependens on pursaching option
  * Dependens on Instance Type
  * Dependens on AMI Type
  * Dependens on Region
  
* RDS can be purchased at a discounted rate for a term, and this purchasing option is RDS reserved instances.
* EC2 can be purchased at a discounted rate for a term, and this purchasing option is EC2 reserved instances.

* **Total Cost of Ownership (TCO)**: allows you to do a comparison of what costs are like when you have an on-premises location versus supporting those same resources on AWS cloud. 
  * Provide directional guidance on cost savings.
  * Also does a comparison with colocation. A colocation means that you are renting space like Rackspace from somebody else who owned the data center, so you're able to put your compute in network and storage resources into their data center, and you pay them a rental fee.
* **Simple Calculator**: estimates your monthly bill and it can provide you a per service breakdown of actual costs.
  * Replaced by AWS pricing calculator. 
* **Pricing Calculator**: estimates costs for services based on use cases.
  * Helps you identify the most cost effective use case for your instance, and service costs may also be compared on a per region basis.
* **Cost Explorer**: a free tool that allows you to view charts of your costs. 
  * You're able to view costs for a period of up to 13 months.
  * Forecasts how much you're likely to spin over the next three months.  

* **Trust Advisor**: service that advices and helps optimize aspects of one's AWS account.
  * Categories
    * Cost Optimization
    * Performance
    * Security
    * Fault tolerance
  * 7 core benefits
    * Security groups (port check) 
    * IAM use,
    * Multi factor authentication on root account
    * EBS snapshots 
    * RDS snapshots
    * Service limits 
    * S3 bucket permissions

* **Account compromised?**
  * Change AWS root account password
  * Change all IAM users' passwords
  * Delete or rotate all API access keys
  * Delete any resource in your account you did not create
  * Respond to AWS notifications and/or contact AWS Support
  
* **AWS Whitepapers**: a collection of technical documents that outlines many AWS relevant topics, including architectural best practices, security best practices, cloud computing economics, and serverless architecture.
* **AWS Services Documentation**: case use documentation for helping and guidance.

---

[1] “So what type of cloud is AWS? It is infrastructure has a service, meaning that all of this underlying hardware is provided by AWS and AWS provides you with access so that you can set up your platform. You can set up your virtual machines to install your operating system and your applications. AWS also provides some of their services in what looks more like software as a service. So as an example, AWS provides storage using something called Simple Storage Service, or S3, S3 is a bulk storage service where you can upload virtually any type of file. Think about how you have an external hard drive, may be on your computer or you might have a Dropbox as a service, S3 gives you that ability to save your data up into the cloud. AWS provides infrastructure as a service, but they also provide additional services that provide applications as a frontend to those infrastructure services to simplify your ability to utilize AWS. They basically want their interface to be presented to you in a way that makes it easy for you to use but they provide all of those infrastructure services necessary to support the overall environment. The compute, the storage, networking. They also provide the ability for you to use their virtualization services, databases. They have hundreds of tools that you can utilize to build and support your environment, everything from setting up your own platform with virtual machines to support your applications, to providing developer tools that help application developers make applications that can run on the AWS infrastructure.”

AWS Cloud (Network connections Regions and Availability Zones altogether) > Regions > Availability Zones > VPC > Subnet > EC2 instance
