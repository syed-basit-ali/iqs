# DevOps Interview Questions

<small>Curated questions organized by domain with recommended focus areas</small>

## Table of Contents
1. [General DevOps Concepts](#general-devops-concepts)
2. [CI/CD](#cicd)
3. [Infrastructure & Cloud](#infrastructure--cloud)
4. [Containers & Orchestration](#containers--orchestration)
5. [Monitoring & Logging](#monitoring--logging)
6. [Security](#security)
7. [Scripting & Automation](#scripting--automation)

---

## General DevOps Concepts

<small>Core DevOps principles and IAM</small>

### Question 1
What is the difference between IAM role and an IAM user?

### Question 2
FitTrack Case Study — Design and Deploy FitTrack's MVP Backend on AWS.

---

## CI/CD

<small>Continuous Integration & Continuous Deployment with Jenkins, GitHub Actions</small>

### Question 1
How would you troubleshoot a sudden spike in 5XX errors on an Application Load Balancer using CloudWatch — what specific metrics and logs would you check first, in order?

### Question 2
If health checks are passing but 5XX persist, how would you differentiate whether the errors originate from the ALB or the targets using CloudWatch metrics?

---

## Infrastructure & Cloud

<small>VPC, Terraform, RDS, and AWS infrastructure concepts</small>

### Question 1
In a VPC, what's the practical difference between a security group and a network ACL, and when would you use both?

### Question 2
For a highly available RDS PostgreSQL setup in two AZs, what does Multi-AZ actually change behind the scenes, and what happens during a failover?

### Question 3
In Terraform, how would you create an S3 bucket with versioning enabled and default SSE-KMS encryption, and ensure it's blocked from public access?

### Question 4
When you manage multiple environments in Terraform, how do you handle remote state and state locking, and what backend approach do you prefer on AWS?

### Question 5
When you split modules across environments, how do you structure your configuration so dev/stage/prod differ without duplicating code — especially for secrets and environment-specific variables?

### Question 6
What are the practical differences between security groups and network ACLs, and when would you choose to use each?

### Question 7
If you allow inbound TCP 443 to an EC2 via its security group, what happens to the return traffic — do you need an explicit outbound rule, and why?

---

## Containers & Orchestration

<small>Docker and Kubernetes fundamentals</small>

### Question 1
(Question to be added)

---

## Monitoring & Logging

<small>CloudWatch, observability, and alerting</small>

### Question 1
How would you monitor and alert on an EC2 instance running out of disk space using CloudWatch, and what would you trigger when the alarm fires?

---

## Security

<small>IAM, S3 encryption, bucket policies, and multi-account access control</small>

### Question 1
How do you EC2 securely access S3 bucket?

### Question 2
In S3, how would you design a bucket policy and IAM permissions to enforce encryption at rest and block all public access, including accidental ACLs?

### Question 3
How would you enforce "deny if not encrypted" and "deny if not TLS" at the bucket level using Terraform-managed policies?

### Question 4
How do you authenticate to Vault from automation (CI/CD or scripts) while keeping token exposure and rotation under control?

### Question 5
In a multi-account AWS setup, how would you design IAM roles and trust policies so a central security account can read CloudTrail logs and Security Hub findings from all member accounts?

### Question 6
What exact permissions and policy types would you use to let member accounts write to that centralized S3 bucket while preventing them from reading or deleting any objects?

### Question 7
What specific S3 bucket policy conditions would you add on `s3:PutObject` to enforce encryption and ensure only the owning account controls object ownership, while still allowing cross-account writes?

### Question 8
How would you enforce encryption at rest for *all* PUTs using an S3 bucket policy, including blocking uploads that omit the required encryption headers?

---

## Scripting & Automation

<small>Terraform refactoring, module structure, and Linux filesystem management</small>

### Question 1
How would you structure Terraform so the policy document is readable and reusable across environments (dev/stage/prod) without copy-pasting?

### Question 2
How do you safely refactor a large Terraform codebase into modules without forcing resource recreation (handling `moved` blocks/state moves)?

### Question 3
In Linux, how would you identify which process is holding a file open and preventing unmounting a busy filesystem?

### Question 4
How would you distinguish whether the "device is busy" is due to open files versus a mount namespace issue (container/process in another namespace)?

---
