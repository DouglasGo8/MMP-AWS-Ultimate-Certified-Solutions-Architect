# AWS Ultimate Certified Solutions Architect Associated 2021

---

## AWS Regions

* AWS Global cloud provider with many data centers around the world, e.g us-east-1, eu-west-3, (usually 3, min 2 max 6) / ap-southeast-2a/2b/2c
 
* ***AZs*** represents data centers with redundant power networking and connectivity - [Full AWS Regions](https://aws.amazon.com/about-aws/global-infrastructure)

  ![AWS Regions](/assets/images/aws_regions.png)

## IAM Introduction

* Acronym for Identity and Access Management
* All related security services are here:
  > Users
  > Groups contains Users
  > Roles used with resources
* IAM Federation
  > Big Enterprises can login in AWS using their company credentials using identity federation with SAML standard (Active Directory)
* One IAM User per PHYSICAL PERSON, never share credentials info aws passwords etc
* One IAM Role per Application
* ***Never*** keep IAM credentials hard-coded
* ROOT Account must be used just for initial Setup
* Initial User with ***Attached existing Policies directly*** and Admin permissions, after create a Group (admin) with recent user created and ***AdministratorAccess Policy***

## EC2

* Most popular service offered by AWS
* Consist in the capability of
  > Virtual Machines (EC2)
  > Store data on virtual drives (EBS)
  > Spread load across machines (ELB)
  > Scaling the services using an auto-scaling group (ASG)
* AMIS stands AWS Machine Image, basic represents OS and Software over the machine ***whoami***

## Security Groups

* Are the fundamental of network security in AWS
* They Control how traffic is allowed into or out of our EC2 Machine, basic control inbound/outbound traffic
* Outbound all traffic is allowed
* To use SSH must be enale 22 port on Inbound Rules over *0.0.0.0/0,::0*
* Security Groups are acting as a "firewall" over EC2 instances
* Can be attached to multiples instances
* Locked down to a region
* It's good to mantain one separate sg fo SSH access
* Private/Public IPs (IPv4) is the most common in AWS, when a company have a private network it can talk to AWS using Internet Gateway ![Private vs Public](/assets/images/ip_private_public.png)
* Public IP the machine can be identified on the internet (WWW)
* Private IP means the machine can only be indentified on a private network only, two diferent private networks (two different companies) can have the same IPs
* Is a fixed public IP for your instance, you can attach it to one instance at a time, try avoid using EIP, or use Load Balancer
* By default EC2 comes with
  * A private IP for internal AWS Network
  * A public IP, for the WWW
* SSH don't use private IP, can be only public IP
* With EIP even after stop EC2 instance they keep attached on it

---

## EC2 Instances Type

* On demand instances - short, predictable pricing
  * Reserved
  * Spot Instances
  * Dedicated Instances
  * Dedicated Hosts
* On Demand has the highest cost but no upfront payment, prefered for elastic workloads
* Reserved Instances up to 75% over on-demand
  * Scheduled Reserved Instances - launch within time window
  * Spot instances up to 90% over on-demand - not great for critial jobs or databases
* Combo - Reserved Instances for Web App + On Demand to Back End App Workloads
* EC2 Classification
  * R application that needs a lot of RAM - in-memory caches
  * C application that needs good CPU - compute / databases
  * M application that are balanced - general / web app
  * I application that need good I/O - databases
  * G application that need GPU -  machine learning
  * T2/T3 burstable instances
  * Real world tips [EC2 Types](https://www.ec2instances.info)
* EC2 AMIs the images bellow can be customised at runtime using EC2 User Data
  * Ubuntu
  * Fedora
  * RedHat
  * Windows
  * Custom AMIs ![Customs AMIS with optmizations](/assets/images/custom_amis.png)
  * Public AMIs, dont recommended
* Placement Groups
* Elastic Network Interfaces (ENI) represents virtual card net to gives EC2 instances access to network each have the attrs:
  * Primary private IPv4 one or more secondary IPv4
  * One Elastic IP (IPv4) per private IPv4
  * One Public IPv4
  * A Mac Address
  * Can be attached in EC2 instance
* EC2 Hibernate
  * The in-memory (RAM) state is preserved
  * The instance boot is much faster
  * Supported by C, M and R AMI's family