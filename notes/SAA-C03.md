# AWS Certified Solutions Architect Associate (SAA-C03) Course Notes

## Introduction

Possible learning path:

- Solutions Architect Associate
- Developer Associate
- SysOps Administrator Associate
- Solutions Architect Professional

Case study — Animals4life

## Course Fundamentals and AWS Accounts

### Accounts

Create two AWS root accounts:

- AC-TRAINING-AWS-GENERAL
  - User: iamadmin with AdministratorAccess
- AC-TRAINING-AWS-PRODUCTION
  - User: iamadmin with AdministratorAccess

### Further steps

- Activate MFA on root accounts and iamadmin users
- Billing: PDF invoices, leaving free tier notification on
- Creating budgets (e.g. $5 per month)
- Create access keys, download and store securely
- Install AWS CLI, configure profiles with access keys
  - ```aws configure --profile ac-training-aws-general```
  - ```aws configure --profile ac-training-aws-general```
  - enter access keysfor both use ```us-east-1``` as default region
  - try commands like:
    - ```aws s3 ls --profile ac-training-aws-general```
  - after configuring profiles with access keys, optionally downloaded access key files should be deleted

### IAM Basics

- user, user group, roles, policies
- ID Provider (IDP, manage ids), authenticate, authorize

## Tech Fundamentals

### OSI 7-Layer Model

(06.09.2025)

1. Physical: HUBs, Repeaters, Cables, no media access control, no collision detection, no device identification, e.g. Ethernet (IEEE 802.3) or Wi-Fi (IEEE 802.11)
2. Data Link: frames, addressing (MAC - 48 bits), flow control (CSMA/CD or CSMA/CA), error detection and correction, VLANs, switches, bridges, frames, e.g Ethernet (IEEE 802.3) or Wi-Fi (IEEE 802.11)
3. Network: packets, addressing (IPv4 - 32 bits, IPv6 - 128 bits), routing, logical addressing, e.g. IP (Internet Protocol)
4. Transport: ports, segments, end-to-end connections, reliability, e.g. TCP, UDP
5. Session: connections, sessions, dialog control
6. Presentation: data representation, encryption, compression
7. Application: high-level APIs, resource sharing, remote file access, e.g. HTTP, FTP, SMTP

### Other Networking

#### Network Address Translation (NAT)

- NAT: 1:1 mapping of private to public IPs
- PAT (Port Address Translation, also known as NAT overload): many:1 mapping of private to public IPs using ports
- IPv6 not requiring NAT/PAT due to large address space

#### IP Adress Space and Subnetting

- IPv4 (32 bits) vs IPv6 (128 bits)
- Public vs Private IPs
  - Public IPs are routable on the internet, assigned by IANA and RIRs
  - Private IPs are not routable on the internet, can be used within private networks
- RFC 1918 private IP ranges:
  - 10.0.0.0 - 10.255.255.255 (1 x Class A, 16,777,216 addresses)
  - 172.16.0.0-172.31.255.255 (16 x Class B, 1,048,576 addresses)
  - 192.168.0-192.168.255.266 (256 x Class C, 65,536 addresses)
- Subnetting: dividing a network into smaller sub-networks (subnets) to improve performance and security
  - Subnet mask: defines the network and host portions of an IP address
  - CIDR notation: e.g. /24 means 255.255.255.0
  - Splitting, e.g. a /24 into two /25 subnets

#### Distributed Denial of Service (DDoS)

- Types of attacks:
  - Application layer attacks (e.g. HTTP floods)
  - Protocol attacks (e.g. SYN floods)
  - Volume-based attacks (e.g. DNS amplification)
- Mitigation strategies:
  - Rate limiting

#### VLANs, TRUNKs & QinQ

#### Decimal to Binary Conversion (IP Addressing)

#### SSL / TLS

#### Border Gateway Protocol (BGP)

#### Stateful vs Stateless Firewalls

#### JumboFrames

#### Layer 7 Firewalls

#### IP Sec VPN Fundamentals

#### Fibre Optic Cable 101


### DNS & DNSSEC

### Containers & Virtualization

### Backups / DR

### Data Formats & Configuration Formats

### Cloud Computing 101

## AWS Fundamentals

### Public vs Private Services

### AWS Global Infrastructure

- Regions
- Availability Zones (AZs)
- Edge Locations
- Resilience
  - Global resilient
  - Region resilient
  - AZ resilient

### Virtual Private Cloud (VPC)

- VPC within one account and one region
- CIDR = Classless Inter-Domain Routing
- one default VPC, many custom VPCs per region
  - default: 1 VPC per region (172.31.0.0/16), /16 CIDR, public subnets in each AZ, default security group (SG), default NACL (Network Access Control List), default route table, internet gateway (IGW) attached

### Elastic Compute Cloud (EC2)

- IAAS (Infrastructure as a Service) -> instances (VMs)
- Private by-default (VPC), public via Elastic IPs (EIPs)
- AZ resilient
- On-demand billing (per second)
- Storage: EBS (Elastic Block Store) - persistent block storage, or (local) instance store - ephemeral storage
- Lifecycle
  - Running <-> stopped -> terminated, running -> terminated
  - Stopped: not running, not billed for CPU/memory/networking, but still billed for storage (EBS)
- AMI (Amazon Machine Image):
  - Permissions: public, ownner (implicit allow) or external (specific AWS accounts allowed)
  - Root Volume/Block Device Mapping
- Connecting:
  - Linux: SSH (port 22), authentication via key pair (private key .pem file on client, public key placed on instance)
  - Windows: RDP (port 3389), password (generated using private key .pem file)

- DEMO:
  - on EC2, create key pair, download .pem file, set permissions to 400
  - create EC2 instance in default VPC, t2.micro (free tier), Amazon Linux 2 AMI, use created key pair, create new security group allowing SSH from own IP, try connecting via SSH

### Simple Storage Service (S3)

- General
  - Public service
  - Regional based/resilient
  - Object storage (not flie/block storage like EBS) -> can't mount
  - good for offload, used as standard input/output for many AWS services
  - ARN: arn:aws:s3:::bucket_name/key_name
- Objects and Buckets
  - Buckets (containers for objects)
    - in regions, but global namespace (bucket names must be **unique globally**)
    - 100 buckets per account by default (can be increased to 1000 via support ticket) -> architectural consideration (don't create buckets by users in account)
  - Objects (files)
    - up to 5TB, unlimited objects in buckets
    - identified by key, can have version ID, metadata, access control information (ACL) and subresources


### Cloud Formation (CF)

- General
  - IAAS (Infrastructure as a Service) -> infrastructure as code (IaC)
  - JSON or YAML templates
  - Create, update, delete (cleans up all logical and physical resources) stacks (groups of resources)
  - Declarative programming (not imperative)
  - Idempotent (apply multiple times, same result)
- Basics
  - Templates
    - AWSTemplateFormatVersion (optional), must be followed by Description
    - Metadata (controls UI)
    - Parameters: promt users for input
    - Mappings (optional)
    - Conditions: allow condition making
    - Outputs
    - Resources: instances with type and properties
  - Templates create stacks, cloud formation creates logical resources and physical resource, CloudFormation keeps template and stack in sync (create, update, delete)
  - => automate infrastructure provisioning, version control, etc.




## Helpful commands

- `df -k` list mounted disks
- `dmesg`