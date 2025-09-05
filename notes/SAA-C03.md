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

### IAM Basics

- user, user group, roles, policies
- ID Provider (IDP, manage ids), authenticate, authorize