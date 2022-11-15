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
        
        
