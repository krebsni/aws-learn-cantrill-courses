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
2. Data Link: addressing (MAC - 48 bits), frames, flow control (CSMA/CD or CSMA/CA), error detection and correction, VLANs, switches, bridges, frames, e.g Ethernet (IEEE 802.3) or Wi-Fi (IEEE 802.11)
3. Network: addressing (IPv4 - 32 bits, IPv6 - 128 bits), routing, packets, logical addressing, e.g. IP (Internet Protocol)
4. Transport: ports, segments, end-to-end connections, reliability, e.g. TCP, UDP

5. Session: connections, sessions, dialog control
6. Presentation: data representation, encryption, compression
7. Application: high-level APIs, resource sharing, remote file access, e.g. HTTP, FTP, SMTP

### Other Networking

#### Network Address Translation (NAT)

#### IP Adress Space and Subnetting

#### Distributed Denial of Service (DDoS)

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