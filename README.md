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
        
