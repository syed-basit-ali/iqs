# Merged DevOps Interview Questions

<small>Focused set of 24 critical questions on core DevOps competencies</small>

---

## Table of Contents
1. [IAM & Access Control](#iam--access-control)
2. [AWS Infrastructure](#aws-infrastructure)
3. [S3 & Storage Security](#s3--storage-security)
4. [Terraform & IaC](#terraform--iac)
5. [Monitoring & Observability](#monitoring--observability)
6. [Linux & System Administration](#linux--system-administration)
7. [Secrets Management](#secrets-management)
8. [Case Study](#case-study)

---

## IAM & Access Control

<small>Identity and Access Management in AWS</small>

1. What is the difference between IAM role and an IAM user?

2. In AWS, what are the practical differences between security groups and network ACLs, and when would you choose to use each?

3. If you allow inbound TCP 443 to an EC2 via its security group, what happens to the return traffic — do you need an explicit outbound rule, and why?

4. In a multi-account AWS setup, how would you design IAM roles and trust policies so a central security account can read CloudTrail logs and Security Hub findings from all member accounts?

5. What exact permissions and policy types would you use to let member accounts write to that centralized S3 bucket while preventing them from reading or deleting any objects?

---

## AWS Infrastructure

<small>VPC, RDS, and core AWS services</small>

1. In a VPC, what's the practical difference between a security group and a network ACL, and when would you use both?

2. For a highly available RDS PostgreSQL setup in two AZs, what does Multi-AZ actually change behind the scenes, and what happens during a failover?

3. How do you EC2 securely access S3 bucket?

---

## S3 & Storage Security

<small>S3 bucket policies, encryption, and access control</small>

1. In S3, how would you design a bucket policy and IAM permissions to enforce encryption at rest and block all public access, including accidental ACLs?

2. In Terraform, how would you create an S3 bucket with versioning enabled and default SSE-KMS encryption, and ensure it's blocked from public access?

3. How would you enforce "deny if not encrypted" and "deny if not TLS" at the bucket level using Terraform-managed policies?

4. What specific S3 bucket policy conditions would you add on `s3:PutObject` to enforce encryption and ensure only the owning account controls object ownership, while still allowing cross-account writes?

5. How would you enforce encryption at rest for *all* PUTs using an S3 bucket policy, including blocking uploads that omit the required encryption headers?

---

## Terraform & IaC

<small>Infrastructure as Code best practices and patterns</small>

1. How would you structure that Terraform so the policy document is readable and reusable across environments (dev/stage/prod) without copy-pasting?

2. When you manage multiple environments in Terraform, how do you handle remote state and state locking, and what backend approach do you prefer on AWS?

3. How do you safely refactor a large Terraform codebase into modules without forcing resource recreation (handling `moved` blocks/state moves)?

4. When you split modules across environments, how do you structure your configuration so dev/stage/prod differ without duplicating code — especially for secrets and environment-specific variables?

---

## Monitoring & Observability

<small>CloudWatch, alerting, and troubleshooting</small>

1. How would you monitor and alert on an EC2 instance running out of disk space using CloudWatch, and what would you trigger when the alarm fires?

2. How would you troubleshoot a sudden spike in 5XX errors on an Application Load Balancer using CloudWatch — what specific metrics and logs would you check first, in order?

3. If health checks are passing but 5XX persist, how would you differentiate whether the errors originate from the ALB or the targets using CloudWatch metrics?

---

## Linux & System Administration

<small>Linux filesystem management and process troubleshooting</small>

1. In Linux, how would you identify which process is holding a file open and preventing unmounting a busy filesystem?

2. How would you distinguish whether the "device is busy" is due to open files versus a mount namespace issue (container/process in another namespace)?

---

## Secrets Management

<small>Vault and secure credential handling</small>

1. How do you authenticate to Vault from automation (CI/CD or scripts) while keeping token exposure and rotation under control?

---

## Case Study

<small>Real-world scenario and architectural design</small>

1. FitTrack Case Study — Design and Deploy FitTrack's MVP Backend on AWS.

---

<small>Total Questions: 24</small>
<small>Last Updated: May 1, 2026</small>
