# AWS IAM Security Hardening Lab

## Overview

This project documents a hands-on AWS Identity and Access Management (IAM) security lab designed to simulate real-world cloud security engineering tasks. The lab covers four core areas of cloud security that are foundational to any cloud security engineer role: account hardening, least privilege access, role-based access control, and audit logging.

All configurations were performed in a live AWS environment using the AWS Management Console.

---

## Skills Demonstrated

- AWS IAM user and role creation and management
- MFA enforcement on root and IAM accounts
- Custom IAM policy authoring in JSON
- Least privilege access design and validation
- IAM role-based access control for EC2 workloads
- Temporary credential management via AWS STS
- Audit logging and threat investigation with AWS CloudTrail

---

## Lab Architecture

AWS Account
├── Root Account (MFA enforced, locked away)
├── IAM Users
│   ├── iam-admin (AdministratorAccess, MFA enforced)
│   └── dev-sarah (custom least privilege S3 read-only policy)
├── IAM Roles
│   └── ec2-s3-readonly-role (assumed by EC2, temporary credentials)
├── S3
│   └── iam-lab-dev-bucket (protected resource)
├── EC2
│   ├── iam-lab-server (role attached, S3 access via temporary credentials)
│   └── iam-lab-server-norole (no role, no credentials, access denied)
└── CloudTrail
└── iam-lab-audit-trail (full management event logging, log file validation enabled)

---

## Modules

| Module | Topic | Key Concepts |
|--------|-------|-------------|
| [Module 1](./module-1-mfa-hardening.md) | Account Hardening & MFA Enforcement | Root security, IAM user creation, MFA |
| [Module 2](./module-2-least-privilege.md) | Least Privilege Policy Writing | Custom JSON policies, scoped resource access, policy testing |
| [Module 3](./module-3-role-based-access.md) | Role-Based Access Control | IAM roles, trust policies, EC2 instance profiles, STS |
| [Module 4](./module-4-cloudtrail-auditing.md) | Auditing & Monitoring with CloudTrail | API logging, event investigation, log integrity |

---

## Real-World Relevance

Each module in this lab maps directly to tasks performed by cloud security engineers in production environments:

**Module 1** mirrors the Day 1 account hardening checklist that security teams run on any new AWS account. MFA on root and named IAM users are CIS Benchmark requirements and are checked by every cloud security audit.

**Module 2** reflects the core of IAM work — writing policies that give exactly the access needed and nothing more. Overly permissive IAM policies are consistently ranked among the top causes of cloud security incidents.

**Module 3** demonstrates the industry-standard pattern for giving AWS services access to other AWS services. Hardcoded credentials in application code are a leading cause of data breaches — roles with temporary credentials eliminate that risk entirely.

**Module 4** covers the detection and investigation side of cloud security. CloudTrail is the foundational audit tool in AWS and is required by SOC 2, PCI-DSS, HIPAA, and virtually every enterprise compliance framework.

---

## Screenshots

All lab screenshots are located in the [`/screenshots`](./screenshots/) directory, organized by module.

---

## Tools & Services Used

- AWS IAM
- AWS S3
- AWS EC2
- AWS CloudTrail
- AWS STS (Security Token Service)
- AWS EC2 Instance Connect

