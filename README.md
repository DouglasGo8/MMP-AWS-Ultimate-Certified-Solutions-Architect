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
