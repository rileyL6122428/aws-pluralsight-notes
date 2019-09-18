## AWS Developer: The Big Picture (Ryan Lewis)

 

Course Overview:

 

  1. Core Services of AWS

  2. Extended Services

  3. Different ways to access AWS

 

### What is AWS

 

  Core AWS services:

 

    - Elastic Cloud Compute (EC2)

      like a VM, where you can run an application

    - Simple Storage Service (S3)

      AWS's famous static file hosting service

    - Relational Database Service (RDS)

      Umbrella term for several diff managed relation db service

    - Route53

      DNS Service that empowers your EC2 and S3 Buckes to be accessible via urls

 

  Enhancing your app with AWS DBs and App Services

 

    - Elastic Beanstalk (EB)

    - DynamoDB & RedShift (2 managed, NoSQL solutions)

    - Virtual Private Cloud (VPC)

    - CloudFront (CDN)

    - CloudWatch (store logs, alert you when ur app fails)

 

  Harnessing the power of AWS from the Command Line to Code

 

    - Web Console

    - Command line Utility

    - Software Development Kits (SDKs)

 

  **AWS is**

    Collection of cloud computing services

    Can work together or independently

    Runs or supports a computer program

 

  Called cloud computing because services are running in some magical data center

  somewhere

 

  Data Center -> a large group of networked computer servers used by orgs for

  the remote storage, processing, or distribution of large amounts of data

 

  Large enterprises (such as Netflix) have their entire app running on AWS, huge

  vote of confidence for the service

 

  Why use AWS?

 

    Cost & Scalability

 

  With AWS, you only pay for what you use

 

  Why deploy your app globally?

 

    Reduced Latency

    Increased Redundancy

 

  AWS Geographic Zone

 

    Region superset -> Availability Zone superset -> Data Center

 

  AWS Status Board:

 

    https://status.aws.amazon.com/

 

  Big, Elephant competitors in the room:

 

    Azure Web Services

 

    IBM Bluemix

 

    Heroku

 

 

### Elastic Cloud Compute

 

  An Instance is basically a computer

 

  Does, *basically* computing

 

  Cloud Compute -> service used for computing purposes located in the cloud

 

  Elastic -> computing service can expand and retract as needed

    you can set rules for scaling up and down automatically

 

  Basic building block is an instance

    Is a virtual server that is operator service agnostic

 

  Create an instance in the AWS Console:

 

    1. Choose an Amazon Machine Image (AMI)

      an image is a combination of an operating system + preinstalled software (Java, Python, etc.)

 

      Amazon provides / updates a selection of images

 

      Amazon security team does a lot of the security for u++!

 

      Caveat, once you create an instance form an image, the instance will not be updated unless you recreate with a new image.

 

      AWS event provides some ready to run apps in the AWS Marketplace tab

 

      When using an open source image, you only pay for the hardware usage your code is running on

 

    2. Choose an instance type

 

      Specs for your instance

        number of CPUs, RAM, network performance

 

      AWS provides families of instance specs, optimized for specific tasks

 

      family:t2.large -> General Purpose Large

      family:r3.large -> Memory Optimized

      family:c4.large -> Compute Optimized

 

      Compute optimized families are cheapest of them all

 

    3. Fine Grain Instance Details

 

      Includes Number of Instances / auto scaling group

      Use EC2 for Scaling AMIs

 

 

    4. Add Storage

 

      Storage = Elastic Block Storage (EBS)

 

      (note EBS not the same as S3)

 

    5. Tag Instance

 

    6. Security Group Configuration Section

 

      IP-based communication rules for a single or group of service instances

 

      *Security Group* controls which IP addresses can talk to your instance, and vice versa

 

 

    EC2 Instance are charged by the hour, pricing changes based on instance type and AMI type

 

    Pricing models:

 

      On-Demand Instances

      Reserved Instances

      Spot Instances

 

### Simple Storage Service (S3)

 

  Service that holds files

 

  Maximum Files Size is 5 Terabytes!

 

  Buckets are the foundational structure in S3

 

    Root resource for which you can add, delete, modify resources

 

    can be configured to

 

      trigger events when stuff happens

 

      preserve older versions of objects

 

      replicate objects across regions

 

    Once created buckets are assigned URLs with which you can access the objects contained within

 

    S3 Pricing Contributors:

 

      amount of data stored

      number of requests

      Amount of Data Transferred

 

### Relational Database Service (RDS)

 

  DBs are *managed* -> AWS handles the following for DBs:

 

    Scheduled Automated Backups

 

    Simple Software Updates

 

    Managed Infrastructure

 

    RDS DBs run on EC2

 

    RDS makes it easy to

 

      Take DB Snapshots

 

      Change the Hardware

 

    AWS Takes Security Seriously

 

    Separate services for NonRelational DBs, RedShift

 

### Route53

 

  DNS service for inside and outside AWS

 

### AWS Extended Service

 

  EB -> app service that will take your solution running in some language and get it running on an EC2 Instance

 

  DynamoDB, RedShift ->  NoSQL - Doc DB, RedShift manage Data Wharehouse solution

 

  VPC -> Virtual Private Cloud (used by almost every service in AWS)

 

  CloudFront -> CDN Service (can be used in conjuction with S3)

 

  CloudWatch -> Logging and alarm service used in conjuction with any other service

 

### Elastic Beanstalk

 

  Under the covers it's setting up your app on EC2, but provided a lot of

    conveniences that you would otherwise have to configure yourself

 

  Main structure/root level organization is an application

 

    inside are app versions

 

    can then deploy to an environment

 

    each env runs with Java or node (or something else), and can be configured

    with certain EC2 instance types

 

    App version are stored in an S3 Bucket, You can have 500 versions

 

    EB gives you monitoring for things like

      CPU usage

      Requests

      Network Traffic

 

    EB is free, you only pay for EC2 Instances, Load Balancers, and S3 Separately

 

 

## Dynamo DB

 

  a managed, NoSQL DB service that support document and key value storage models

 

  You pay for how much you store, and how often you query, and everything else

  is taken care of by AWS

 

  Core structure is a table

 

  Each table has primary keys, and can optionally have secondary keys as well

 

  Provisioned Throughput capacity = number of read/writes per second

 

  Each read write can use up to 4 kB / unit

 

  For data, first 25 GB Free

  provisioned throughput is where most of the cost is

 

### Red Shift

 

  Data wharehouse service

 

  Data Wharehouse is a technology that aggregates structured data from one or

  more sources so that it can be compared and analyzed for greater business

  intelligence

 

  Provides ETL capabilities (Extract Transform Load)

 

  Base unit of organization is a cluster

    Composed of nodes (VM instances)

 

  Lots of RedShift Security Options:

 

    Data Wharehouse Encryption

    VPC Protection

    No Pubic IP

 

### VPC (Virtual Private Cloud)

 

  allows you to secure your resource into groups

 

  Commonly used when launching EC2 instances

 

  Security Groups as a key piece to control, VPC next evolution of that

 

  Let's you

    1. have full control over routing tables

    2. Use NAT Gateways for Outbound Traffic

    3. Internal IP Address Allocation

 

  Under each VPC is a subnet

    usually have private and public subnet

 

  VPC Security:

 

  Internet

    -> Routing Table (controls what goes where)

    -> Network ACL (control who can come an go)

    -> VPC

 

  Pricing is *free*

 

### CloudWatch

 

  Key Functionality

    1. Monitoring Resources

    2. Acting On Alerts

 

  Ability to setup alarms for key metrics

 

  Notify

 

### CloudFront

 

  CDN Network

    works with S3, EC2, Load Balancer, Route53

    Easiest of the structure to setup

 

  Start by setting up a distribution

    set an original content that feeds into it

 

  Once feeder assigned, a unique URL is assigned

 

  You can then configure

    which HTTP methods are allowed,

    Which Edge Locations are used,

    Set SSL Certificates

 

  Pricing is convoluted *SAD*

 

## Harnessing the power of AWS from the Command Line

 

  Web Console

  SDK Software Development Kit

  CLI Commnd Line Interface

 

### Web Console

 

  Different console service Categories:

 

    1. Compute

    2. Storage & Content Delivery

    3. Database

    4. Networking

    5. Developer Tools

    6. Management Tools

    7. Security & Identity

    8. More...

 

  Console Menu Bar

 

    Resource Groups -> Group Resources according to their function

 

 

    Can drag services you frequently use into the menu bar

 

    Regions in top right, determines pricing

 

    Click on name in top right will show options, including billing

 

    Security Credentials (setup credentials on the account)

 

      Can set users to give teammates user accounts

 

    Click on a service to see it's dashboard

 

### Software Development Kit

 

  Lot's of supported languages

 

  Checkout GitHub/aws

 

  SDK's are libariries to help you interact with services in AWS (nothing special that SDKs do, just providing convenience)

 

  Anything you do through the console, you can do with an AWS SDK

 

  INstallation of node AWS SDK:

 

    npm i aws-sdk

 

 

### AWS CLI

 

  Useful for Shell scripts or  Batch Files

  Integrate into build pipeline

 

  Basic command syntax:

 

    `aws <service> <command> <flags>`

 

  AWS CLI Docs:

    docs.aws.amazon.com/cli/latest/reference

 

 

# AWS Developer: Getting Started

 

## Welcome to AWS

 

  Developing in the Clouds

  Even you can develop on AWS

  Tools of the Trade

  Who loves Pizza?

  Install the Magic

 

 

  * How developing in cloud is similar to AWS dev

    App runs on OS/Platform

    Requires platform to be installed

    HTTP Servers listens on ports

    Connects to outside DBs

 

  * How developing in cloud is different to AWS dev

 

    Local - Everything runs locally on same machine

    AWS - One Service = One Responsibility

 

    Local - Files stored on server

    AWS - Files served from S3

 

    Local - DB on same server as application

    AWS - DB as a Service

 

    Local - Connections done manually

    AWS - connections done with AWS SDK

 

### The Web of Amazon Web Services

 

### AWS Tooling: Web Console

 

  console

    -> configure & create resources

    -> Each service has its own dashboard

 

### AWS Tooling: CLI

 

  Great for Shell Scripting

  Feature Complete with Console & SDKs

  Interact with Any Service

 

  CLI Usage in This Course

    Configure local dev env

    Alternative to Console Actions

 

### AWS Tooling: Software Development Kits

 

  AWS Access Key gives access for SDK & CLI

 

### Who Luvs Pizza

 

  is the name of the demo application

 

CLI Command to see your EC2 Instances: `aws ec2 describe-instances`

 

 

## Sounding the Alarm with IAM and Cloudwatch

 

* CloudWatch

  Set Alarms & Notifications in response to Events

 

* IAM

  Simple User and Access Management

 

  Overview

    Watching the Clouds

    The Simplest Notification Service

    The First CloudWatch Alarm

    Users? Policies? Groups?

    Security is the Best Policy

 

* CloudWatch

  Service to set alarms based on Serviice Metric Thresholds

 

  EX:

    DynamoDB Read/Write Throughput

    EC2 CPU Usage

    Estimated Billing Charges

 

* Alarm Actions

    Send Notification via SNS

    Trigger AutoScaling Action

    Trigger EC2 Action

 

### SNS

 

* Simple Notification Service (integral with CloudWatch)

 

* Basic Unit = Topic

 

### Creating a Cloud Watch Alarm

 

### Identity & Access Management (IAM)

 

* Service to configure authentication and access for user accounts

 

* IAM User Management Aspects:

 

  1. Passwords

  2. Multi-Factor Authentication

  3. Access Keys

  4. SSH Keys

 

* Main structure is a policy, a collection of

  1. Permission

  2. Resource Permission

  3. Service Permission

 

* IAM Policy Examples

 

  Developer Group Policy

    - EC2 Full Access

 

  Tester Group Policy

    - DynamoDB Read-Only

    - S3 Full Access Test Bucket

 

### Securing Your AWS Account

 

  * Root Account Permissions:

    - Administer all Services

    - Modify billing information

    - Manage users

 

### Understanding Policies

 

  * By Default, no permissions

  * Policies can apply to users or groups

  * Policy Statement Properties

    1. Effect:

      "Allow" or "Deny", deny is default

    2. Action

      Operation user can perform on services

    3. Resource

      Specific Resources user can perform action on

 

  * AWS Managed Policies

    General Purpose, service-wide permissions

  * Custom Managed Policy

    Custom, Specific Resource Permissions

 

  * Use Policies to give Permissions

 

### Configuring Users and Groups

 

  * from IAM console, u can manage a user's access and persmissions

 

  * AWS recommends not creating things as a root user cuz u have unlimited access

 

## Getting Inside the Virtual Machine with EC2 and VPC

 

  * Services that Utilize EC2

    1. RDS

    2. ElastiCache

    3. Elastic Beanstalk

    4. Redshift

    5. Elastic MapReduce

    6. Elastic Block Storage

 

  * EC2 -> Virtual machine service that runs software of your choice

 

  * EC2 Additional Features

 

    1. Elastic IP

    2. Load Balancers

    3. Auto-Scaling Groups

 

  * VPC

    control routing to ur services

 

## VPC (Virtual Private Cloud)

 

  * is free!

 

  * Security Group defines allowed incoming/outgoing IP addresses and ports. Kind of like a mini-firewall.

 

  * VPCs use routing tables to configure routing destinations for traffic coming out of the VPC

 

  * Network Access Control List -> acts as IP filtering table (kind of like super power control lists)

 

  * Subnet -> sits inside a VPC and holds service Instances

 

  * Each subnet has its own routing table and Network Access Control List

  -> Allows you to create different routing rules withing the same VPC

 

  * CIDR -> Classless Inter Domain Routing

 

## EC2

 

  * EC2 is a virtual machine

    1. CPU

    2. Memory

    3. Storage

    4. Network

 

  * EC2 supports multiple types of operating systems. Any licensed OS costs more to run

 

  * Combination of OS + Software on EC2 is referred to as an AMI (Amazon Machine Image)

 

  * Each EC2 has a technical specification

 

    1. General Purpose

    2. Compute Optimized

    3. Memory Optimized

    4. Storage Optimized

 

  * Elastic Block Storage

 

    Independent Storage volumes used with EC2 instances

 

    Allows storage of the EBS lives separately from the instance

 

Use custom AMI (Amazon Machine Images) to scale EC2 Instances

 

Auto Scaling Group

  Expands or shrinks a pool of instances based on pre-defined rules

 

Use a load balancer to handle changing IPs for auto scalilng instances

 

Load Balancer: Routing applicance that maintains a consistent DNS entry and balances requests to multiple instances

 

## Hosting All Things with S3

 

  * Putting the S in S3

  * Buckets of Objects

  * Pizza Luv-ing Storage

  * Cross Origin Pizza Sharing

 

### S3 Overiew

 

  * Stored in region you select

  * Object is the fundamental storage unit

    consists of a file & metadata

      - Metadata -> File Type, Modified Date

      - File -> .jpg, .png, .json, .js, ...don't care

  * Max File Size -> 5 Terabytes

  * Max PUT operation -> 5 Gigabytes

 

  * Objects are collected in BUCKETS

  * Bucket serve a couple purposes

    - aggregates objects

    - Expose objects via URL

  * Objects identified by key

    key includes file path and file name

 

  * By Default, AWS only allows bucket creator to modify the bucket

    can define permissions or IAM Policies

 

  * Cross Region Replication, only copies to one region to reduce latency

 

  * CloudFront is the best way to solve geographic latency

 

 

## DB Services

 

### RDS Overview

 

  * DB instances are managed,

 

  * Managed means AWS handles a lot of maintenance tasks, such as:

    Software Upgrades

    Backups

    System health monitoring

 

  * Creating RDS instance makes an EC2 Instance behind the scene

 

  * RDS backups configured

 

    - by default, occur daily

    - configurable backup window

    - Backups stored 1 - 35 days

    - Restore DB from backup

 

  * Multi AZ Deployment

 

    - AZ stands for Availability Zone

    - automatic failover in case of catastrophe

 

  * Can create DB Read Replica

 

    - Non-production copy of db

    - eventual consistence with source

    - useful for running queries on data

    - Will not be used as failover

    - perfect for devs to read without risking actual prod copy of DB

 

### Choosing a DB Engine in RDS

 

  * current offereings:

 

    1. MySQL

    2. PostgreSQL

    3. SQL Server

    4. MariaDB

    5. Oracle DB

    6. Amazon Aurora

 

* Sequelize - Node.js ORM library

  Supports PostgreSQL, MySQL, and more

 

 

### Dynamo DB Overview

 

  * RDS is your non-relational DB solution

  * Main structure in Dynamo DB is a table

  * Table contains many rows of data called items

  * Items do need to include a primary (only limitation (string, number, or binary))

  * Other configurable property of a table is the Provisioned Throughput Capacity

    Defines how many Read/Write ops can occur per second, how much hardware u need

 

  * 1 write unit equals 4kiloBytes in size

 

### Deciding between RDS or Dynamo DB

 

  RDS ->

    1. Efficient Data Transfer

    2. Efficient Data Storage

    3. Easy Querying with SQL

 

    1. Strict Record Schema

 

 

  Dynamo DB

    0. has strong storage flexibility

    1. No Schema, only primary key restriction

 

    1. Limited Query Properties

 

  * Deciding Factor:

 

    Storage Flexibility vs Query Flexibility

 

    *IMPORTANT*

      You've coded talking to ur Dynamo DB

        and RDS, now you just need to create both and start/run ur app locally (revisit videos you have seen to do this)

 

* You need to give EC2 security policy certain policies in order to access DBs in RDS and DynamoDB

 

 

## Automating Your App with Elastic Beanstalk and CloudFormation

 

 

### Cloud Formation Overview

 

  * Service to provision resources using templates

 

  * The key tool in Cloudformation is a *template*

 

  * JSON Document

  * Contains configuration for resources that you want to deploy in multiple envs

  * You can check these templates into version control

  * No limit to amount of resources

 

  * Another unit of organization in Cloud Formation is the Stack

 

  * A stack is a group of AWS resources created by a single Cloud Formation Template

 

  * A template can be used to create more than one stack, but each stack has its own name (identity)

 

  * Other Cloud Formation Options:

    - Update Stack

    - Delete Stack

 

  * CloudFormation only creates the resources you explicitly configure in the template

 

  * CloudFormation has a couple of tools for creating stacks

    1. Cloud Formation Designer (Visual UI)

    2. Cloud Former Tool (look at existing resources and creates template)

 

### Elastic Beanstalk Overview

 

  * With cloud formation you can automate the creation of infrastructure, but with elastic bean stalk, you can automate the deployment of your application

 

  * Elastic Beanstalk lets you handle:

 

    1. Scaling

    2. Monitoring

    3. Resource Provisioning

 

  * Cloud Formation only provisions resources while Elastic Beanstalk purely dedicated to running your application

 

  * few key structures:

    1. Application

      Represents a logical application

      Runs a single platform

      Has 1 or more Application Versions

    2. Environments

      sits inside an Application

      Has independant config values for

        API, Scaling, App Version, etc

 

  * Elastic Beanstalk will take care of AMI creation, Uploading new code to EC2, Updating load config, Updating Auto-Scaling Groups, Terminating out-of-date instances, and more

 

* Cloud Formation: Stack files, specify the resources your app uses

* Elastic beanstalk, is Spring web to cloud formation, makes it easy to create a stack quickly, and deploy several different configs (or envs) concurrently. AWS assumes a lot of the environment config that you want (you can still go in and change the assumed config)

 

 

## Speeding up with CloudFront and ElastiCache

 

  1. use CloudFront to fight the war on latency

  2. Distribute Pizza-Luvrs with CloudFront

  3. Use Elasticache to cache app session data

  4. Store session data in Redis so we can deploy our app as a cluster

 

### Cloudfront Overview

 

  * One of the biggest challenges for a website is latency (amount of time it takes a web application request/response to reach the target)

 

  * One solution for latency: move your users and apps closer together

 

  * *CloudFront* -> Global Content Delivery Network designed to reduce latency and reduce application load

 

  * *CloudFront*

    1. Integrates with S3, EC2, Load Balancers

    2. Edges Content/"Objects" and serves them directly (items requested from CloudFront)

    3. Proxies dynamic content to origin source (request goes to CloudFront, then to EC2 with optimized in between connection)

 

  * *Distribution* -> A CloudFront "edge"

    Given it's own url

    Provides content from one or more origins

 

### Edging Your App with CloudFront

 

  * Typically no app changes required

 

  * Create CloudFront Distribution Steps:

 

    1. Select Delivery Method

      Web vs RTMP (we're looking at web)

    2. Create Distribution

      - Origin Settings (for forwarding  requests to ur AWS Services?)

      - Default Cache Behavior Settings (how CloudFront reacts to external requests)

      - Distribution Settings (select CloudFront Edge Locations, Domain Names, Certificates, ...)

 

 

### Configuring a CloudFront Distribution

 

After Distribution created, click on distributions to see and configure your CloudFront Distributions.

 

Things you can configure:

  * General Settings

    "Many of the settings we configured at creation time"

  * Origins

    AWS? Origins. Can Add, Delete, Edit new Origins

  * Behaviors

    Caching behaviors

  * Error Pages

  * Restrictions

  * Invalidations

 

*Reports and Analytics (in CloudFront Dashboard)*

 

Cache Statistics

  * Hits vs Misses

    *Hits* are when items are pulled from the cache

    *Misses* had to bypass cache and grab items from the AWS Origin

 

Popular Objects

  * Shows which objects/ requests paths are most often cached/requested

 

### ElastiCache Overview

 

  * ElastiCache -> Managed service for In-Memory cache datastore

 

  * ElastiCache Feature ->

    - Managed Maintenance, Upgrades, etc.

    - Automatic read replicas

    - Simple node management

 

  * Main structure in ElastiCache is a *Cluster*

    - collection of *nodes*

    - a *node* is a EC2 instance running the caching software

    - if you use Redis, a cluster comprises of one single node, with a couple of Read Replica Nodes

    - Redis is the industry leader for in-memory caching

 

### Configuring a Redis Cluster in ElastiCache

 

Need a security group for ElastiCache Group

 

When creating an ElastiCache Cluster, need to setup a Cache Subnet Group in VPC. Will setup our VPC group to host ElastiCache Clusters.

 

A Subnet group takes multiple subnets

 

ElastiCache creation steps:

 

  1. Select Engine (Redis or Memcached)

  2. Specify Cluster Details

  3. Configure Advanced settings

  4. Review

 

### Interacting with ElastiCache in Code