# AWS-Cloud-Practitioner

## Cloud Computing Basics 
      
### Deployment models of cloud
   1. Private : Cloud service used by a single organization but not exposed to the public, Complete control, Security for sensitive applications (E.g Rackspace)
   2. Public : Cloud resources owned and operated by a third party cloud service provider delivered over the internet, six adv of cloud computing (E.g GCP, Azure, AWS)
   3. Hybrid : Combination of Public and Private cloud models, will have control over sensitive application in our private infrastructure (E.g On premises and AWS)
    
### 5 Characterstics of Cloud Computing
   1. On-demand and selfservice
   2. Broad network access
   3. Multi-tentency and resource pooling
   4. Rapid elasticity and scalability
   5. Measured Services
    
### 6 Advantages of cloud computing
    1. Trade capital expense (CAPEX) for operational expense (OPEX)
         • Pay On-Demand: don’t own hardware
         • Reduced Total Cost of Ownership (TCO) & Operational Expense (OPEX)
    2. Benefit from massive economies of scale
         • Prices are reduced as AWS is more efficient due to large scale
    3. Stop guessing capacity
         • Scale based on actual measured usage
    4. Increase speed and agility
    5. Stop spending money running and maintaining data centers
    6. Go global in minutes: leverage the AWS global infrastructure
    
### Types of Cloud Computing
    1. Infrastructure as a Service (IaaS)
         • Provide building blocks for cloud IT 
         • Provides networking, computers, data storage space
         • Highest level of flexibility
         • Easy parallel with traditional on-premises IT
    2. Platform as a Service (PaaS)
         • Removes the need for your organization to manage the underlying infrastructure
         • Focus on the deployment and management of your applications
    3. Software as a Service (SaaS)
         • Completed product that is run and managed by the service provider
         
 ### Example of Cloud Computing Types
   • Infrastructure as a Service: • Amazon EC2 (on AWS) • GCP, Azure, Rackspace, Digital Ocean, Linode
   • Platform as a Service: • Elastic Beanstalk (on AWS) • Heroku, Google App Engine (GCP), Windows Azure (Microsoft) 
   • Software as a Service: • Many AWS services (ex: Rekognition for Machine Learning) • Google Apps (Gmail), Dropbox, zoom
    
### • AWS has 3 pricing fundamentals, following the pay-as-you-go pricing model
    • Compute:
      • Pay for compute time
    • Storage:
      • Pay for data stored in the Cloud
    • Data transfer OUT of the Cloud:
      • Data transfer IN is free
    • Solves the expensive issue of traditional IT
    
### AWS Cloud Overview
    1. AWS Regions 
       • AWS has Regions all around the world 
       • Names can be us-east-1, eu-west-3… 
       • A region is a cluster of data centers 
       • Most AWS services are region-scoped
    2. AWS Availability Zones
       • Each region has many availability zones (usually 3, min is 2, max is 6). Example:
          • ap-southeast-2a
          • ap-southeast-2b
          • ap-southeast-2c
       • Each availability zone (AZ) is one or more discrete data centers with redundant power, networking, and connectivity
       • They’re separate from each other, so that they’re isolated from disasters
       • They’re connected with high bandwidth, ultra-low latency networking
    3. AWS Points of Presence (Edge Locations)
       • Amazon has 216 Points of Presence (205 Edge Locations & 11 Regional Caches) in 84 cities across 42 countries
       • Content is delivered to end users with lower latency
       
## IAM: Users & Groups 

### Key Notes:

   * IAM = Identity and Access Management, Global service
   * Users are people within your organization, and can be grouped
   * Groups only contain users, not other groups

### IAM-Permissions :

   * Users or Groups can be assigned JSON documents called policies
   * These policies define the permissions of the users

### Multi Factor Authentication - MFA

    • Users have access to your account and can possibly change configurations or delete resources in your AWS account
    • You want to protect your Root Accounts and IAM users
    • MFA = password you know + security device you own
    
### How can users access AWS ?
    • To access AWS, you have three options:
        • AWS Management Console (protected by password + MFA)
        • AWS Command Line Interface (CLI): protected by access keys
        • AWS Software Developer Kit (SDK) - for code: protected by access keys
    • Access Keys are generated through the AWS Console
    • Users manage their own access keys
    • Access Keys are secret, just like a password. Don’t share them
    • Access Key ID ~= username
    • Secret Access Key ~= password

### IAM Roles for Services 
    • Some AWS service will need to perform actions on your behalf
    • To do so, we will assign permissions to AWS services with IAM Roles
    • Common roles: 
          • EC2 Instance Roles 
          • Lambda Function Roles
          • Roles for CloudFormation
    
### IAM Security Tools :
    1. IAM Credentials Report (account-level) :
          • a report that lists all your account's users and the status of their various credentials
    2. IAM Access Advisor (user-level) :
          • Access advisor shows the service permissions granted to a user and when those services were last accessed.
          • You can use this information to revise your policies

### IAM Guidelines & Best Practices

    • Don’t use the root account except for AWS account setup
    • One physical user = One AWS user
    • Assign users to groups and assign permissions to groups
    • Create a strong password policy
    • Use and enforce the use of Multi Factor Authentication (MFA)
    • Create and use Roles for giving permissions to AWS services
    • Use Access Keys for Programmatic Access (CLI / SDK)
    • Audit permissions of your account with the IAM Credentials Report
    • Never share IAM users & Access Keys

### IAM Section – Summary 

    • Users: mapped to a physical user, has a password for AWS Console
    • Groups: contains users only 
    • Policies: JSON document that outlines permissions for users or groups
    • Roles: for EC2 instances or AWS services
    • Security: MFA + Password Policy
    • Access Keys: access AWS using the CLI or SDK
    • Audit: IAM Credential Reports & IAM Access Advisor
       
## EC2 Instances

### Introduction :
    • EC2 is one of the most popular of AWS’ offering 
    • EC2 = Elastic Compute Cloud = Infrastructure as a Service
    • It mainly consists in the capability of :
                • Renting virtual machines (EC2)
                • Storing data on virtual drives (EBS)
                • Distributing load across machines (ELB)
                • Scaling the services using an auto-scaling group (ASG)
### EC2 sizing & configuration options

    1. Operating System (OS): Linux or Windows 
    2. How much compute power & cores (CPU) 
    3. How much random-access memory (RAM) 
    4. How much storage space: 
        * Network-attached (EBS & EFS) 
        * Hardware (EC2 Instance Store) 
    5. Network card: speed of the card, Public IP address 
    6. Firewall rules: security group 
    7. Bootstrap script (configure at first launch): EC2 User Data 
    
### EC2 Instance types :

    Reference Link for types and use cases : https://aws.amazon.com/ec2/instance-types/
    
### Introduction to Security Groups

    • Security Groups are the fundamental of network security in AWS
    • They control how traffic is allowed into or out of our EC2 Instances.
    * Security groups only contain rules
    • Security groups rules can reference by IP or by security group
    * security groups are acting as a “firewall” on EC2 instances 
    • They regulate: 
        • Access to Ports 
        • Authorised IP ranges – IPv4 and IPv6 
        • Control of inbound network (from other to the instance) 
        • Control of outbound network (from the instance to other)
    
### Classic ports

    • 22 = SSH (Secure Shell) - log into a Linux instance
    • 21 = FTP (File Transport Protocol) – upload files into a file share
    • 22 = SFTP (Secure File Transport Protocol) – upload files using SSH
    • 80 = HTTP – access unsecured websites
    • 443 = HTTPS – access secured websites
    • 3389 = RDP (Remote Desktop Protocol) – log into a Windows instance
    
### Connecting to EC2 using SSH, Putty Tool and Instance Connect

    1. Using SSH : Watch the lecture (Mac/Linux, windows>=10)
    2. Using Putty Tool : Watch the lecture(All version of windows)
    3. EC2 Instance Connect : (All types of OS)
        • Connect to your EC2 instance within your browser
        • No need to use your key file that was downloaded
        • The “magic” is that a temporary key is uploaded onto EC2 by AWS
        • Works only out-of-the-box with Amazon Linux 2
        • Need to make sure the port 22 is still opened!
    
### EC2 Instances Purchasing Options

    • On-Demand Instances: short workload, predictable pricing
    • Reserved: (MINIMUM 1 year)
    • Reserved Instances: long workloads 
    • Convertible Reserved Instances: long workloads with flexible instances
    • Scheduled Reserved Instances: example – every Thursday between 3 and 6 pm
    • Spot Instances: short workloads, cheap, can lose instances (less reliable)
    • Dedicated Hosts: book an entire physical server, control instance placement
    • Dedicated Instances: no other customers will share your hardware
    
    Hotel Example :
    
    • On demand: coming and staying in resort whenever we like, we pay the full price
    • Reserved: like planning ahead and if we plan to stay for a long time, we may get a good discount.
    • Spot instances: the hotel allows people to bid for the empty rooms and the highest bidder keeps the rooms. You can get kicked out at any time
    • Dedicated Hosts: We book an entire building of the resort

### Responsibility Model for Customers :

    • Security Groups rules
    • Operating-system patches and updates
    * Software and utilities installed on the EC2 instance
    • IAM Roles assigned to EC2 & IAM user access management
    * Data security on your instance
    
### EC2 Section – Summary 

    • EC2 Instance: AMI (OS) + Instance Size (CPU + RAM) + Storage + security groups + EC2 User Data
    • Security Groups: Firewall attached to the EC2 instance
    • EC2 User Data: Script launched at the first start of an instance
    * SSH: start a terminal into our EC2 Instances (port 22)
    • EC2 Instance Role: link to IAM roles
    • Purchasing Options: On-Demand, Spot, Reserved (Standard + Convertible + Scheduled), Dedicated Host, Dedicated Instance

## EC2 Instance Storage Section
### EC2 Instance Storage - Summary 

    • EBS volumes: 
       • network drives attached to one EC2 instance at a time
       • Mapped to an Availability Zones
       • Can use EBS Snapshots for backups / transferring EBS volumes across AZ
    • AMI: create ready-to-use EC2 instances with our customizations
    • EC2 Image Builder: automatically build, test and distribute AMIs
    • EC2 Instance Store:
       • High performance hardware disk attached to our EC2 instance
       • Lost if our instance is stopped / terminated
    • EFS: network file system, can be attached to 100s of instances in a region

![EBS vs EFS](https://user-images.githubusercontent.com/62194896/201830238-6d9dfddf-41b8-4cf1-9212-740612899576.png)

### Shared Responsibility Model for EC2 Storage
    AWS :
        • Infrastructure
        • Replication for data for EBS volumes & EFS drives
        • Replacing faulty hardware
        • Ensuring their employees cannot access your data
        
    Customer :
        • Setting up backup / snapshot procedures
        • Setting up data encryption
        • Responsibility of any data on the drives
        • Understanding the risk of using EC2 Instance Store
        
## Elastic Load Balancing & Auto Scaling Groups Section
### Scalability & High Availability
    • Scalability means that an application / system can handle greater loads by adapting. 
    • There are two kinds of scalability:
        • Vertical Scalability ( Vertical Scalability means increasing the size of the instance )
        • Horizontal Scalability (= elasticity) ( Horizontal Scalability means increasing the number of instances / systems for your application )
    • Scalability is linked but different to High Availability

### High Availability 
    • High Availability usually goes hand in hand with horizontal scaling
    • High availability means running your application / system in at least 2 Availability Zones
    • The goal of high availability is to survive a data center loss (disaster)
    • High Availability: Run instances for the same application across multi AZ
      • Auto Scaling Group multi AZ
      • Load Balancer multi AZ

### Scalability vs Elasticity (vs Agility)
    • Scalability: ability to accommodate a larger load by making the hardware stronger (scale up), or by adding nodes (scale out)
    • Elasticity: once a system is scalable, elasticity means that there will be some “auto-scaling” so that the system can scale based on the load. This is “cloud-        friendly”: pay-per-use, match demand, optimize costs
    • Agility: (not related to scalability - distractor) new IT resources are only a click away, which means that you reduce the time to make those resources available      to your developers from weeks to just minutes.
### Elastic Load Balancers (ELB)
    • Distribute traffic across backend EC2 instances, can be Multi-AZ
    • Supports health checks
    • 3 types: Application LB (HTTP – L7), Network LB (TCP – L4), Classic LB (old)
### Auto Scaling Groups (ASG)
    • Implement Elasticity for your application, across multiple AZ
    • Scale EC2 instances based on the demand on your system, replace unhealthy
    • Integrated with the ELB

## Amazon S3 – Summary 
    • It’s(S3) advertised as ”infinitely scaling” storage 
### S3 Use cases :
         • Backup and storage 
         • Disaster Recovery 
         • Archive 
         • Hybrid Cloud storage 
         • Application hosting 
         • Media hosting 
         • Data lakes & big data analytics 
         • Software delivery 
         • Static website
### Buckets vs Objects: 
    • global unique name, tied to a region 
    • Naming convention
        • No uppercase
        • No underscore
        • 3-63 characters long
        • Not an IP
        • Must start with lowercase letter or number
    • Objects (files) have a Key
    • The key is composed of prefix + object name 
    • s3://my-bucket/my_folder1/another_folder/my_file.txt
### S3 security: 
    • IAM policy, S3 Bucket Policy (public access), S3 Encryption
### S3 Websites: 
    • host a static website on Amazon S3
    • If you get a 403 (Forbidden) error, make sure the bucket policy allows public reads!
### S3 Versioning: 
    • multiple versions for files, prevent accidental deletes
    • It is enabled at the bucket level
### S3 Access Logs: 
    • log requests made within your S3 bucket
### S3 Replication: 
    • Must enable versioning in source and destination
    • Cross Region Replication (CRR)
    • Same Region Replication (SRR)
    • Buckets can be in different accounts
    • Copying is asynchronous
    • Must give proper IAM permissions to S3
    • CRR - Use cases: compliance, lower latency access, replication across accounts
    • SRR – Use cases: log aggregation, live replication
### S3 Storage Classes: 
    • Standard, IA, 1Z-IA, Intelligent, Glacier, Glacier Deep Archive (Refer pdf for more info)
    
  ![S3 storage classes](https://user-images.githubusercontent.com/62194896/202256528-2dbd48c3-e924-4fe8-9c97-46b22d86506b.png)

    
### S3 Lifecycle Rules: 
    • transition objects between classes, it is automateable
### S3 Glacier Vault Lock / S3 Object Lock: 
    • WORM (Write Once Read Many)
### S3 Shared Responsibility model 
    • AWS :
         • Infrastructure (global security, durability, availability, sustain concurrent loss of data in two facilities)
         • Configuration and vulnerability analysis 
         • Compliance validation
    • Customer :
         • S3 Versioning
         • S3 Bucket Policies
         • S3 Replication Setup
         • Logging and Monitoring
         • S3 Storage Classes
         • Data encryption at rest and in transit

### Snow Family: 
    • import data onto S3 through a physical device, edge computing
    
  ![AWS Snow Family](https://user-images.githubusercontent.com/62194896/202257394-0517cfa4-5c3b-4855-889f-1711d8452116.png)

    
    • OpsHub: desktop application to manage Snow Family devices
### Storage Gateway: 
    • hybrid solution to extend on-premises storage to S3
    • Types of Storage Gateway:
         • File Gateway 
         • Volume Gateway
         • Tape Gateway

## Databases and Analytics Section

### Databases & Shared Responsibility on AWS
    • AWS offers use to manage different databases
    • Benefits include:
        • Quick Provisioning, High Availability, Vertical and Horizontal Scaling
        • Automated Backup & Restore, Operations, Upgrades
        • Operating System Patching is handled by AWS
        • Monitoring, alerting
    • Note: many databases technologies could be run on EC2, but you must handle yourself the resiliency, backup, patching, high availability, fault tolerance, scaling…
    
### Databases & Analytics Summary in AWS
    • Relational Databases - OLTP: RDS & Aurora (SQL)
           • RDS allows you to create databases in the cloud that are managed by AWS
                 • Postgres
                 • MySQL
                 • MariaDB
                 • Oracle
                 • Microsoft SQL Server
                 • Aurora (AWS Proprietary database)
           • Amazon Aurora
                 • Aurora is a proprietary technology from AWS (not open sourced)
                 • PostgreSQL and MySQL are both supported as Aurora DB 
                 • Aurora is “AWS cloud optimized” and claims 5x performance improvement over MySQL on RDS, over 3x the performance of Postgres on RDS
                 • Aurora storage automatically grows in increments of 10GB, up to 64 TB. 
                 • Aurora costs more than RDS (20% more) – but is more efficient
                 • Not in the free tier
    • RDS Deployments : Differences between Multi-AZ, Read Replicas, Multi-Region
    • In-memory Database: ElastiCache
                 • Caches are in-memory databases with high performance, low latency
                 • Helps reduce load off databases for read intensive workloads
    • Key/Value Database: DynamoDB (serverless) & DAX (cache for DynamoDB)
                 • NoSQL database - not a relational database 
                 • Scales to massive workloads, distributed “serverless” database
                 • Single-digit millisecond latency – low latency retrieval
                 • Integrated with IAM for security, authorization and administration
                 * DAX:
                     • Fully Managed in-memory cache for DynamoDB
                     • 10x performance improvement – single- digit millisecond latency to microseconds latency – when accessing your DynamoDB tables
    • Warehouse - OLAP: Redshift (SQL) 
                 • Redshift is based on PostgreSQL, but it’s not used for OLTP
                 • It’s OLAP – online analytical processing (analytics and data warehousing)
                 • Load data once every hour, not every second
                 • 10x better performance than other data warehouses, scale to PBs of data
                 • Columnar storage of data (instead of row based)
    • Hadoop Cluster: EMR
                 • EMR stands for “Elastic MapReduce”
                 • EMR helps creating Hadoop clusters (Big Data) to analyze and process vast amount of data
                 • The clusters can be made of hundreds of EC2 instances
                 • Use cases: data processing, machine learning, web indexing, big data…
    • Athena: query data on Amazon S3 (serverless & SQL) 
                 • Fully Serverless database with SQL capabilities
                 • Used to query data in S3
                 • Use Case: one-time SQL queries, serverless queries on S3, log analytics
    • QuickSight: dashboards on your data (serverless)
                 • Serverless machine learning-powered business intelligence service to create interactive dashboards
                 • Use cases:
                         • Business analytics
                         • Building visualizations
                         • Perform ad-hoc analysis
                         • Get business insights using data
    • DocumentDB: “Aurora for MongoDB” (JSON – NoSQL database)
    • Amazon QLDB: Financial Transactions Ledger (immutable journal, cryptographically verifiable)
                • QLDB stands for ”Quantum Ledger Database”
                • A ledger is a book recording financial transactions
                • Fully Managed, Serverless, High available, Replication across 3 AZ
                • Used to review history of all the changes made to your application data over time 
                • Immutable system: no entry can be removed or modified, cryptographically verifiable
                • It has only centralization component and no decentralization component
    • Amazon Managed Blockchain: managed Hyperledger Fabric & Ethereum blockchains
    • Glue: Managed ETL (Extract Transform Load) and Data Catalog service
    • Database Migration: DMS
               • Supports:
                    • Homogeneous migrations: ex Oracle to oracle
                    • Heterogeneous migrations: ex Microsoft SQL Server to Aurora
    • Neptune: graph database
          • Fully managed graph database 
          • A popular graph dataset would be a social network 
                  • Users have friends 
                  • Posts have comments 
                  • Comments have likes from users 
                  • Users share and like posts
          • Great for knowledge graphs (Wikipedia), fraud detection, recommendation engines, social networking
## Other Compute Section
### Other Compute - Summary
          • Docker: container technology to run applications
                 • Docker is a software development platform to deploy apps 
                 • Apps are packaged in containers that can be run on any OS 
                 • Apps run the same, regardless of where they’re run 
                      • Any machine 
                      • No compatibility issues 
                      • Predictable behavior 
                      • Less work 
                      • Easier to maintain and deploy 
                      • Works with any language, any OS, any tech
          • ECS: run Docker containers on EC2 instances
                      • ECS = Elastic Container Service
                      • Launch Docker containers on AWS
                      • You must provision & maintain the infrastructure (the EC2 instances)
          • Fargate: 
                      • Launch Docker containers on AWS
                      • You do not provision the infrastructure (no EC2 instances to manage)– simpler!
                      • Serverless offering
          • ECR(Amazon Elestice Container Registry): Private Docker Images Repository, Docker images are stored in Docker Repositories
            Note : • Serverless does not mean there are no servers…
          • Batch: run batch jobs on AWS across managed EC2 instances
                     • Fully managed batch processing at any scale
                     • Batch will dynamically launch EC2 instances or Spot Instances
                     • Batch jobs are defined as Docker images and run on ECS
   ![Batch vs Lambda](https://user-images.githubusercontent.com/62194896/202719577-e377a280-ecb1-48c6-92e0-3093076cd5a0.png)

          • Lightsail: predictable & low pricing for simple application & DB stacks
                     • Virtual servers, storage, databases, and networking 
                     • Use cases:
                         • Simple web applications (has templates for LAMP, Nginx, MEAN, Node.js…)
                         • Websites (templates for WordPress, Magento, Plesk, Joomla)
                         • Dev / Test environment 
  ### Lambda Summary
  ![Why Lambda](https://user-images.githubusercontent.com/62194896/202720410-e8e0a9f9-86b7-46b7-bceb-0e7e5ac2d827.png)

          • Lambda is Serverless, Function as a Service, seamless scaling, reactive
          • Lambda Billing:
             • By the time run x by the RAM provisioned
             • By the number of invocations
             • Based on calls and duration
          • Language Support: many programming languages except (arbitrary) Docker
          • Invocation time: up to 15 minutes
          • Event-Driven: functions get invoked by AWS when needed
          • Use cases:
             • Create Thumbnails for images uploaded onto S3
             • Run a Serverless cron job
          • API Gateway: expose Lambda functions as HTTP API
             
### Deploying and Managing Infrastructure at Scale Section
### CloudFormation
         • CloudFormation: (AWS only)
         • Infrastructure as Code, works with almost all of AWS resources
         • Repeat across Regions & Accounts
         • CloudFormation creates those for you, in the right order, with the exact configuration that you specify
![Cloud formation](https://user-images.githubusercontent.com/62194896/202962879-26a6b003-cfa8-4eec-b9b2-43dd08cff3b0.png)

### Beanstalk: (AWS only)
     • Platform as a Service (PaaS), limited to certain programming languages or Docker
     • Deploy code consistently with a known architecture: ex, ALB + EC2 + RDS 
     • Elastic Beanstalk is a developer centric view of deploying an application on AWS
     • It uses all the component’s we’ve seen before:           EC2, ASG, ELB, RDS, etc… 
     • But it’s all in one view that’s easy to make sense of! 
     • We still have full control over the configuration • Beanstalk = Platform as a Service (PaaS) 
     • Beanstalk is free but you pay for the underlying instances
     • Just the application code is the responsibility of the developer
     • Elastic Beanstalk – Health Monitoring
        • Health agent pushes metrics to CloudWatch
        • Checks for app health, publishes health events
### CodeDeploy (hybrid): deploy & upgrade any application onto servers
    • We want to deploy our application automatically
    • Works with EC2 Instances
    • Works with On-Premises Servers
    • Hybrid service
### CodeCommit :
    • Before pushing the application code to servers, it needs to be stored somewhere
    • Developers usually store code in a repository, using the Git technology
    • A famous public offering is GitHub, AWS’ competing product is CodeCommit
    • CodeCommit:
         • Source-control service that hosts Git-based repositories
         • Makes it easy to collaborate with others on code
         • The code changes are automatically versioned 
    • Benefits: 
         • Fully managed
         • Scalable & highly available
         • Private, Secured, Integrated with AWS
### AWS CodeBuild
    • Code building service in the cloud (name is obvious)
    • Compiles source code, run tests, and produces packages that are ready to be deployed (by CodeDeploy for example)
### AWS CodePipeline
    • Orchestrate the different steps to have the code automatically pushed to production 
    • Code => Build => Test => Provision => Deploy
    • Basis for CICD (Continuous Integration & Continuous Delivery)
    • Benefits:
         • Fully managed, compatible with CodeCommit, CodeBuild, CodeDeploy, Elastic Beanstalk, CloudFormation, GitHub, 3rd-party services (GitHub…) & custom plugins…
         • Fast delivery & rapid updates
### AWS CodeArtifact
    • Software packages depend on each other to be built (also called code dependencies), and new ones are created
    • Storing and retrieving these dependencies is called artifact management
    • Traditionally you need to setup your own artifact management system
    • Works with common dependency management tools such as Maven, Gradle, npm, yarn, twine, pip, and NuGet
    • Developers and CodeBuild can then retrieve dependencies straight from CodeArtifact
### AWS CodeStar
    • Unified UI to easily manage software development activities in one place
    • “Quick way” to get started to correctly set-up CodeCommit, CodePipeline, CodeBuild, CodeDeploy, Elastic Beanstalk, EC2, etc… 
    • Can edit the code ”in-the-cloud” using AWS Cloud9
### AWS Cloud9 
    • AWS Cloud9 is a cloud IDE (Integrated Development Environment) for writing, running and debugging code
    • AWS Cloud9 also allows for code collaboration in real-time (pair programming)
### Systems Manager (hybrid): 
    • patch, configure and run commands at scale
    • Helps you manage your EC2 and On-Premises systems at scale
    • Most important features are:
         • Patching automation for enhanced compliance
         • Run commands across an entire fleet of servers 
         • Store parameter configuration with the SSM Parameter Store
### OpsWorks (hybrid): 
    • Managed Chef and Puppet in AWS
    • Chef & Puppet help you perform server configuration automatically, or repetitive actions
    • They work great with EC2 & On-Premises VM
    • AWS OpsWorks = Managed Chef & Puppet
    • It’s an alternative to AWS SSM
    
## Global Infrastructure Section
    • A global application is an application deployed in multiple geographies
    • On AWS: this could be Regions and / or Edge Locations
    • Advantages :
        • Decreased Latency
        • Disaster Recovery (DR)
        • Attack protection
###  Global DNS: Route 53
    • Great to route users to the closest deployment with least latency
    • Great for disaster recovery strategies
    • Route53 is a Managed DNS (Domain Name System)
    • DNS is a collection of rules and records which helps clients understand how to reach a server through URLs
    • Types of Routing 53 policies:
              • Simple Routing Policy (No health checks)
              • Weighted Routing policy
              • Latency Routing policy
              • Failover Routing policy
### Global Content Delivery Network (CDN): CloudFront
    • Replicate part of your application to AWS Edge Locations – decrease latency
    • Cache common requests – improved user experience and decreased latency
    • Content Delivery Network (CDN)
    • Improves read performance, content is cached at the edge
    • Improves users experience
    • 216 Point of Presence globally (edge locations)
    • DDoS protection (because worldwide), integration with Shield, AWS Web Application Firewall
    • Cloudfront origins:
         • S3 Bucket
         • HTTP 
### S3 Transfer Acceleration
    • Accelerate global uploads & downloads into Amazon S3
### AWS Global Accelerator:
    • Improve global application availability and performance using the AWS global network
    • 2 Anycast IP are created for your application and traffic is sent through Edge Locations
    • The Edge locations send the traffic to your application
### AWS Outposts:
    • Deploy Outposts Racks in your own Data Centers to extend AWS services
    • AWS Outposts are “server racks” that offers the same AWS infrastructure, services, APIs & tools to build your own applications on-premises just as in the cloud
    • AWS will setup and manage “Outposts Racks” within your on-premises infrastructure and you can start leveraging AWS services on-premises
    • You are responsible for the Outposts Rack physical security
## Cloud Integration Section
### SQS:
    • Queue service in AWS
    • Multiple Producers, messages are kept up to 14 days
    • Multiple Consumers share the read and delete messages when done
    • Used to decouple applications in AWS
### SNS: 
    • Notification service in AWS
    • Subscribers: Email, Lambda, SQS, HTTP, Mobile…
    • Multiple Subscribers, send all messages to all of them
    • No message retention
    • Both SNS and SQS are used for decoupling the applications
### Kinesis: 
    • Real-time data streaming, persistence and analysis
### Amazon MQ:
    • Managed Apache MQ in the cloud (MQTT, AMQP.. protocols)
    • Useful when migrating to the cloud
## Monitoring Summary
### CloudWatch:
    • Metrics: monitor the performance of AWS services and billing metrics
    • Important Metrics 
         • EC2 instances: CPU Utilization, Status Checks, Network (not RAM)
         • Default metrics every 5 minutes
         • Option for Detailed Monitoring ($$$): metrics every 1 minute
         • EBS volumes: Disk Read/Writes
         • S3 buckets: BucketSizeBytes, NumberOfObjects, AllRequests
         • Billing:Total Estimated Charge (only in us-east-1)
         • Service Limits: how much you’ve been using a service API
         • Custom metrics: push your own metrics
    • Alarms: automate notification, perform EC2 action, notify to SNS based on metric
    • Logs: collect log files from EC2 instances, servers, Lambda functions…
        • The CloudWatch log agent can be setup on-premises too
    • Events (or EventBridge): react to events in AWS, or trigger a rule on a schedule
### CloudTrail: 
    • Provides governance, compliance and audit API calls made within your AWS account
    • A trail can be applied to All Regions (default) or a single Region.
    • If a resource is deleted in AWS, investigate CloudTrail first!
    • CloudTrail is enabled by default!
### CloudTrail Insights: 
    • automated analysis of your CloudTrail Events
### X-Ray: 
    • Trace requests made through your distributed applications
    • AWS X-Ray advantages
    • Troubleshooting performance (bottlenecks) 
    • Understand dependencies in a microservice architecture 
    • Pinpoint service issues • Review request behavior 
    • Find errors and exceptions 
    • Are we meeting time SLA? 
    • Where I am throttled? 
    • Identify users that are impacted
### Service Health Dashboard: 
    • status of all AWS services across all regions
    • Shows all regions, all services health
    • Shows historical information for each day
### Personal Health Dashboard: 
    • AWS Personal Health Dashboard provides alerts and remediation guidance when AWS is experiencing events that may impact you.
    • AWS events that impact your infrastructure
    • Shows how AWS outages directly impact you & your AWS resources
    • Alert, remediation, proactive, scheduled activities
## VPC Section
### VPC -Virtual Private Cloud: 
    • private network to deploy your resources (regional resource)
    • Subnets:allow you to partition your network inside your VPC (Availability Zone resource)
    • A public subnet is a subnet that is accessible from the internet
    • A private subnet is a subnet that is not accessible from the internet
    • To define access to the internet and between subnets, we use Route Tables
### Internet Gateway: 
    • Internet Gateways helps our VPC instances connect with the internet
    • Public Subnets have a route to the internet gateway
### NAT Gateway / Instances: 
    • NAT Gateways (AWS-managed) & NAT Instances (self-managed) allow your instances in your Private Subnets to access the internet while remaining private
### NACL: 
    • Stateless, subnet rules for inbound and outbound
    • A firewall which controls traffic from and to subnet
    • Can have ALLOW and DENY rules
    • Are attached at the Subnet level
    • Rules only include IP addresses
### Security Groups: 
    • Stateful, operate at the EC2 instance level or ENI
    • A firewall that controls traffic to and from an ENI / an EC2 Instance
    • Can have only ALLOW rules
    • Rules include IP addresses and other security groups
### VPC Peering: 
    • Connect two VPC with non overlapping IP ranges, non-transitive
    • Must not have overlapping CIDR (IP address range)
### VPC Endpoints: 
    • Endpoints allow you to connect to AWS Services using a private network instead of the public www network
    • VPC Endpoint Gateway: S3 & DynamoDB
    • VPC Endpoint Interface: the rest
### VPC Flow Logs: 
    • network traffic logs
### Site to Site VPN: 
    • VPN over public internet between on-premises DC and AWS
    • The connection is automatically encrypted
    • Goes over the public internet
### Direct Connect: 
    • Direct private connection to AWS
    • Establish a physical connection between on-premises and AWS
    • The connection is private, secure and fast
    • Goes over a private network    
### Site-to-Site VPN
    • On-premises: must use a Customer Gateway (CGW)
    • AWS: must use a Virtual Private Gateway (VGW)
### Transit Gateway: 
    • For having transitive peering between thousands of VPC and on-premises, hub-and-spoke (star) connection
    
## Security & Compliance Section
### Shared Responsibility on AWS
    • AWS responsibility - Security of the Cloud
       • Protecting infrastructure (hardware, software, facilities, and networking) that runs all the AWS services
       • Managed services like S3, DynamoDB, RDS, etc.
    • Customer responsibility - Security in the Cloud
       • For EC2 instance, customer is responsible for management of the guest OS (including security patches and updates), firewall & network configuration, IAM 
       • Encrypting application data 
    • Shared controls:
       • Patch Management, Configuration Management, Awareness & Training
![Shared Responsibility model](https://user-images.githubusercontent.com/62194896/203288445-9e458622-d800-427f-9b7e-d359a9b4d846.png)

### DDOS Protection on AWS
    • Shield: Automatic DDoS Protection + 24/7 support for advanced
    • AWS Shield Standard: 
       • protects against DDOS attack for your website and applications, for all customers at no additional costs
       • Provides protection from attacks such as SYN/UDP Floods, Reflection attacks and other layer 3/layer 4 attacks
    • AWS Shield Advanced: 24/7 premium DDoS protection
    • AWS WAF: Filter specific requests based on rules
       • Protects your web applications from common web exploits (Layer 7)
       • Layer 7 is HTTP (vs Layer 4 is TCP)
       • Deploy on Application Load Balancer, API Gateway, CloudFront
    • CloudFront and Route 53: 
         • Availability protection using global edge network
         • Combined with AWS Shield, provides attack mitigation at the edge
    • Define Web ACL (Web Access Control List):
         • Rules can include IP addresses, HTTP headers, HTTP body, or URI strings
         • Protects from common attack - SQL injection and Cross-Site Scripting (XSS)
         • Size constraints, geo-match (block countries)
         • Rate-based rules (to count occurrences of events) – for DDoS protection
### Penetration Testing :
     • AWS customers are welcome to carry out security assessments or penetration tests against their AWS infrastructure without prior approval for 8 services:
        • Amazon EC2 instances, NAT Gateways, and Elastic Load Balancers
        • Amazon RDS
        • Amazon CloudFront
        • Amazon Aurora
        • Amazon API Gateways
        • AWS Lambda and Lambda Edge functions
        • Amazon Lightsail resources
        • Amazon Elastic Beanstalk environments
### KMS: 
     • Encryption keys managed by AWS
     • KMS = AWS manages the encryption keys for us(Software)
     • Encryption Opt-in:
        • EBS volumes: encrypt volumes
        • S3 buckets: Server-side encryption of objects
        • Redshift database: encryption of data
        • RDS database: encryption of data
        • EFS drives: encryption of data
     • Encryption Automatically enabled: 
        • CloudTrail Logs
        • S3 Glacier
        • Storage Gateway
### CloudHSM: 
    • Hardware encryption, we manage encryption keys
### Types of Customer Master Keys: CMK
    • Customer Managed CMK:
         • Create, manage and used by the customer, can enable or disable
         • Possibility of rotation policy (new key generated every year, old key preserved)
         • Possibility to bring-your-own-key 
    • AWS managed CMK:
         • Created, managed and used on the customer’s behalf by AWS
         • Used by AWS services (aws/s3, aws/ebs, aws/redshift)
    • AWS owned CMK:
         • Collection of CMKs that an AWS service owns and manages to use in multiple accounts
         • AWS can use those to protect resources in your account (but you can’t view the keys)
    • CloudHSM Keys (custom keystore): 
         • Keys generated from your own CloudHSM hardware device
         • Cryptographic operations are performed within the CloudHSM cluster
### AWS Secrets Manager
    • Newer service, meant for storing secrets
    • Capability to force rotation of secrets every X days
    • Secrets are encrypted using KMS
### Artifact(not a service): 
    • Get access to compliance reports such as PCI, ISO, etc…
    • Portal that provides customers with on-demand access to AWS compliance documentation and AWS agreement
    • Can be used to support internal audit or compliance
### GuardDuty: 
    • Intelligent Threat discovery to Protect AWS Account 
    • Uses Machine Learning algorithms, anomaly detection, 3rd party data
    • One click to enable (30 days trial), no need to install software
    • Can setup CloudWatch Event rules to be notified in case of findings
![GuardDuty](https://user-images.githubusercontent.com/62194896/203292053-10b9c554-b8d0-4a1e-b411-f927f72eff89.png)

### Inspector: 
    • For EC2 only, install agent and find vulnerabilities
    • Automated Security Assessments for EC2 instances 
    • Analyze the running OS against known vulnerabilities
    • Analyze against unintended network accessibility
    • AWS Inspector Agent must be installed on OS in EC2 instances
### AWS Config:
    • Helps with auditing and recording compliance of your AWS resources
    • Helps record configurations and changes over time
### Macie :
    • Amazon Macie is a fully managed data security and data privacy service that uses machine learning and pattern matching to discover and protect your sensitive data in AWS.
    • Macie helps identify and alert you to sensitive data, such as personally identifiable information (PII)
### Security Hub :
    • Central security tool to manage security across several AWS accounts and automate security checks
    • Integrated dashboards showing current security and compliance status to quickly take actions
### Amazon Detective :
    • Sometimes security findings require deeper analysis to isolate the root cause and take action – it’s a complex process
    • Amazon Detective analyzes, investigates, and quickly identifies the root cause of security issues or suspicious activities (using ML and graphs)
    • Automatically collects and processes events from VPC Flow Logs, CloudTrail, GuardDuty and create a unified view
### AWS Abuse :
    • Report suspected AWS resources used for abusive or illegal purposes
    • Abusive & prohibited behaviors are:
        • Spam
        • Port scanning
        • DoS or DDoS attacks
        • Intrusion attempts
        • Hosting objectionable or copyrighted content
        • Distributing malware
### Root user privileges
    • Root user = Account Owner (created when the account is created)
    • Has complete access to all AWS services and resources
    • Lock away your AWS account root user access keys!
    • Do not use the root account for everyday tasks, even administrative tasks
    • Actions that can be performed only by the root user:
          • Change account settings (account name, email address, root user password, root user access keys)
          • View certain tax invoices
          • Close your AWS account
          • Restore IAM user permissions
          • Change or cancel your AWS Support plan
          • Register as a seller in the Reserved Instance Marketplace
          • Configure an Amazon S3 bucket to enable MFA
          • Edit or delete an Amazon S3 bucket policy that includes an invalid VPC ID or VPC endpoint ID
          • Sign up for GovCloud

### Machine Learning Section
     • Rekognition: face detection, labeling, celebrity recognition
     • Transcribe: audio to text (ex: subtitles)
     • Polly: text to audio
     • Translate: translations
     • Lex: build conversational bots – chatbots 
     • Connect: cloud contact center
     • Comprehend: natural language processing
     • SageMaker: machine learning for every developer and data scientist

## Account Best Practices – Summary 
    • Operate multiple accounts using Organizations
    • Use SCP (service control policies) to restrict account power
    • Easily setup multiple accounts with best-practices with AWS Control Tower
    • Use Tags & Cost Allocation Tags for easy management & billing
    • IAM guidelines: MFA, least-privilege, password policy, password rotation
    • Config to record all resources configurations & compliance over time
    • CloudFormation to deploy stacks across accounts and regions
    • Trusted Advisor to get insights, Support Plan adapted to your needs
    • Send Service Logs and Access Logs to S3 or CloudWatch Logs 
    • CloudTrail to record API calls made within your account
    • If your Account is compromised: change the root password, delete and rotate all passwords / keys, contact the AWS support

## Billing and Costing Tools – Summary 
    • TCO Calculator: from on-premises to AWS
    • Simple Monthly Calculator / Pricing Calculator: cost of services on AWS
    • Billing Dashboard: high level overview + free tier dashboard
    • Cost Allocation Tags: tag resources to create details on reports
    • Cost and Usage Reports: most comprehensive billing dataset
    • Cost Explorer:View current usage (detailed) and forecast usage
    • Billing Alarms: in us-east-1 – track overall and per-service billing
    • Budgets: more advanced – track usage, costs, RI, and get alerts
    • Savings Plans: easy way to save based on long-term usage of AWS
    
    Note : Refer the pdf for more details

## Advanced Identity - Summary 
    • IAM
       • Identity and Access Management inside your AWS account
       • For users that you trust and belong to your company
    • Organizations: manage multiple AWS accounts
    • Cognito: create a database of users for your mobile & web applications
    • Directory Services: integrate Microsoft Active Directory in AWS
    • Single Sign-On (SSO): one login for multiple AWS accounts & applications
    Note : Refer pdf for more details
    
### AWS Architecting & Ecosystem 
## Well Architected Framework General Guiding Principles 
    • Stop guessing your capacity needs 
    • Test systems at production scale 
    • Automate to make architectural experimentation easier 
    • Allow for evolutionary architectures 
    • Design based on changing requirements 
    • Drive architectures using data 
    • Improve through game days 
    • Simulate applications for flash sale days

## AWS Cloud Best Practices – Design Principles
    • Scalability: vertical & horizontal 
    • Disposable Resources: servers should be disposable & easily configured
    • Automation: Serverless, Infrastructure as a Service, Auto Scaling…
    • Loose Coupling: 
       • Monolith are applications that do more and more over time, become bigger
       • Break it down into smaller, loosely coupled components
       • A change or a failure in one component should not cascade to other components
    • Services, not Servers:
       • Don’t use just EC2
       • Use managed services, databases, serverless, etc !

## Well Architected Framework 
      5 Pillars
     • 1) Operational Excellence
     • 2) Security
     • 3) Reliability
     • 4) Performance Efficiency
     • 5) Cost Optimization
