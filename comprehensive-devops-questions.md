# Comprehensive DevOps Interview Questions

<small>All questions organized by domain with recommended focus areas</small>

---

## Table of Contents
1. [DevOps / SRE](#devops--sre)
2. [Terraform](#terraform)
3. [Ansible](#ansible)
4. [AWS](#aws)
5. [CI/CD](#cicd)
6. [Observability & Monitoring](#observability--monitoring)
7. [Linux / Scripting](#linux--scripting)
8. [Docker / Kubernetes](#docker--kubernetes)
9. [SCMs (GIT)](#scms-git)
10. [Security](#security)
11. [Experience / Scenario Based](#experience--scenario-based)

---

## DevOps / SRE

<small>Site Reliability Engineering fundamentals</small>

1. Describe the difference between SLIs, SLOs, and SLAs in site reliability engineering.
2. How do you handle incident response and post-incident reviews?
3. How do you mitigate the risks associated with software releases and updates?
4. How do you ensure security and compliance in a production environment?
5. Explain how you would scale a service horizontally to handle increased traffic.
6. What is Infrastructure as Code (IaC)?
7. Define Chaos Engineering.
8. What is the purpose of Monitoring and Observability?
9. Define "Lift & Shift" in DevOps practices.
10. What languages are you comfortable working in?
    - <small>Focus on Bash, Python, and Java (most common with internal expertise)</small>
    - <small>**Note**: Need to build expertise in Go (increasingly frequent)</small>
11. What is DevOps? Why do we need it?
12. Explain/describe "IaaS, PaaS, SaaS"?

---

## Terraform

<small>Infrastructure as Code with HashiCorp Terraform</small>

### Project Setup & Basics

1. How to set up the Terraform Project
2. What happens when you perform `terraform init`
3. What is the concept of backend in Terraform?
4. Where we define the backend and how we set up the remote backend
5. How can we setup multiple environments (dev, qa, uat, prod) — what are different approaches that can be used?
6. What is the difference between `for_each` and `count` in Terraform?
7. What's the difference between object and map in Terraform?
8. What is module in Terraform? How we call module in the main code?
9. How to create Terraform structure for project if you are starting new project

### State Management

10. State Locking — Define state locking, how it works.
11. Remote Backends — How do we achieve State locking with remote backend?
12. What is State File, how to manage it securely in a distributed team?
13. In Terraform, how do you make sure multiple parties do not modify the state file at the same time and corrupt it?
    - <small>You need to lock the state file. One way is with DynamoDB.</small>
14. In Terraform, if someone modifies the infrastructure directly from the AWS console, what are the implications and what actions should you take?
    - <small>The state file will be out of sync. Use `terraform refresh` to update the state file.</small>

### Modules & Resources

15. How to create a module? What are the minimum requirements?
16. Outputs — what is output.tf file?
17. How to use a module, how to specify the version of a module?
18. Create multiple EC2 instances using an EC2 module based on a list of Subnet IDs (one instance per subnet)
19. Difference between `for_each` & `count` with above example & how to refer EC2 instance resource in both cases
20. Access output of one module when creating a resource from another module
21. Give example of output from modules
22. What are Terraform Modules, ways to publish and source them?

### Advanced Features

23. How to provision resources (EC2, RDS) dynamically, using meta-arguments like count, foreach
24. How to manage existing manually created resources via IaC (Terraform) — Terraform import
25. How to deploy lambda functions
26. Terraform conditions
27. Dynamic (in context of terraform)
28. Lambda using Terraform
29. Linting and Formatting
30. Pre-commit checks

### Environment & Multi-Environment Setup

31. Steps to setup new terraform environment (directory structure, providers, backend)
32. How to setup common modules for multi-environment
33. Define/Suggest to structure a Terraform script to create resources across various different environments
34. Explain a list variable (containing subnets) and a resource using count to create EC2 instances using an AMI, instance type and subnet from the list
35. Explain a resource using `for` keyword with a `toset(list)`
36. What is the `toset()` function used for?
37. Explain a policy being defined using a Heredoc string, what does the policy do?
38. Explain an assume role policy
39. What will the output of a resource using count look like? (using [] brackets and 0 based index)

### Common Blocks & Best Practices

40. Give examples of common blocks (Ans: e.g. provider, module, data, variable, output etc)
41. What is a data block used for?
42. Is it possible to share resources between two different AWS accounts?
43. How do you maintain your state file to keep it safe from corruption? And what happens when your state file gets locked? How you will resolve it?
44. What is a tainted resource?
45. How to safely refactor a large Terraform codebase into modules without forcing resource recreation (handling `moved` blocks/state moves)?

### Terraform Workflows

46. In Terraform, what are the workflow commands?
    - <small>`init` → [fmt] → [validate] → `plan` → `apply` → [refresh] → `destroy`</small>
    - <small>If you have existing infrastructure, use `terraform import`</small>
    - <small>`terraform destroy` removes infrastructure known in state file (common in dev, rare in prod)</small>
    - <small>Commands in brackets are optional but recommended</small>

### Credentials & Secrets

47. How should you manage access credentials or other secrets in Terraform?
    - <small>HashiCorp/Terraform Vault</small>
    - <small>AWS Secrets Manager</small>

### Terraform vs CloudFormation

48. What are the differences between Terraform and CloudFormation?
    - <small>Both are IaC; Terraform works on multiple cloud providers and on-premise, CloudFormation only on AWS</small>
    - <small>Terraform uses HCL; CloudFormation uses JSON</small>

---

## Ansible

<small>Configuration management and automation</small>

### Basics

1. Do you know Ansible? What is it and what makes it different from others?
2. What is Ansible, and how does it differ from other configuration management tools?
3. What is an Ansible inventory? How do you define inventory?
4. Playbook without hosts — does it run? If yes, how and where would it run?
5. Explain the difference between Ansible Playbook and Ansible Role.
6. How do you define hosts in Ansible inventory?
7. What is an Ansible Task and how is it different from a Play?

### Advanced Concepts

8. How do you handle sensitive data like passwords in Ansible?
9. Describe the purpose of Ansible Vault.
10. What is idempotence in Ansible, and why is it important?
11. How do you use Ansible Galaxy to manage roles?
12. Explain the concept of Ansible Facts.
13. What is the difference between Ansible ad-hoc commands and Playbooks?
14. How do you loop over items in Ansible Playbooks?
15. What are Ansible Handlers and when are they triggered?
16. How can you limit tasks to specific hosts in Ansible Playbooks?
17. How do you debug Ansible Playbooks or roles?
18. What is the purpose of the ansible.cfg configuration file?

### Ansible vs Other Tools

19. What are the differences between Ansible and Puppet?
    - <small>Ansible is declarative and written in Python</small>
    - <small>Puppet is more task oriented and written in Ruby</small>
    - <small>Puppet considered superior for large deployments, but Ansible has more market traction</small>

---

## AWS

<small>Amazon Web Services core and advanced topics</small>

### IAM & Access Control

1. What is the difference between IAM role and an IAM user?
2. Ways of giving access to people to AWS services
3. AD users outside AWS — how to give them access to AWS services
4. Identity Based policies
5. Resource Based policies
6. What are the resources used to control access?
7. How can we control access between two EC2 instances?
8. Two EC2 instances are in the same subnet — how can we control access?
9. How can we control access to EC2 as a web server with traffic coming from the internet?
10. How do we configure access to EC2 instances running the same service?
11. Best practices to allow traffic to an EC2 Instance.

### Network & VPC

12. How to share resources between different VPCs.
13. How to share if we have overlapping IP ADDRESSES
14. How to monitor traffic IN VPC
15. Difference between security Group and NACL
16. Ways to access data from an S3 bucket from a private Instance without going through the public route (VPC Endpoints).
17. Type of VPC Endpoints, what is Endpoint Policy, how to restrict access using endpoint policy.
18. Restrict access to S3 Bucket using resource-based policy.
19. VPC Gateway endpoint — What does AWS do/create when you create it?
20. VPC endpoint — What does AWS do/create when you create it?
21. With the VPC Gateway endpoint for S3 enabled, we want to allow an EC2 instance to access an S3 bucket & restrict that bucket to be accessed by that EC2 instance. What Resource based policy will be added on S3?
22. Difference between Interface and Gateway VPC Endpoints
23. Is it possible to allow access to a specific S3 bucket from an instance in a private subnet? How?
24. How can two EC2 instances in two separate private subnets in two separate VPC connect to each other?
25. What are private endpoints?
26. What is the difference between VPC Peering and Transit Gateway?
    - <small>VPC peering connects one VPC directly to another (meshed architecture)</small>
    - <small>Transit Gateway is a hub-and-spoke architecture that simplifies multiple VPC connections</small>

### S3 & Storage

27. How to get S3 data if your EC2 instance doesn't have internet access
28. What is the maximum size of a single upload to S3?
    - <small>5 gigabytes</small>
29. What is the maximum size of an object in S3?
    - <small>5 terabytes</small>
30. If there is a 5GB single upload limit in S3, how do you get to a 5TB object?
    - <small>Multi-part uploads</small>
31. In S3, how would you design a bucket policy and IAM permissions to enforce encryption at rest and block all public access, including accidental ACLs?
32. How would you enforce "deny if not encrypted" and "deny if not TLS" at the bucket level using Terraform-managed policies?
33. How would you enforce encryption at rest for *all* PUTs using an S3 bucket policy, including blocking uploads that omit the required encryption headers?
34. Restrict access to S3 Bucket using resource-based policy.

### Load Balancers & Traffic

35. What can be the different destinations of traffic in ALB, ELB and NLB?
36. Enabling SSL on ALB using ACM
37. What AWS Security Services can be configured on top of ALB — Brief overview of how we configure them
38. Types of LoadBalancer in AWS — difference between Application & Network LoadBalancer, when & why to use one.
39. What is a load balancer?
40. What algorithms can be used in load balancers?
41. Can a load balancer be layer 4 and layer 7 at the same time?
42. What is the difference between a Network Load Balancer and an Application Load Balancer?
    - <small>NLB operates at Layer 3 (Network) and is stateless</small>
    - <small>ALB operates at Layer 5 (Session) and/or Layer 7 (Application) and is stateful</small>
43. HA for EC2s
44. HA for RDS
45. ALB / ELB
46. HTTPS with ALB
47. End-end HTTPS from Client to ALB to EC2

### Security & Certificates

48. Restricting access at the level of AWS regions
49. What is the difference between api gateway and CDN?
50. Which endpoints support the AWS WAF (ALB, CloudFront, API Gateway)?
51. Regional/Global CloudFront — why and when to use.
52. How are SSL certificates generated?
53. End-End TLS (ACM, {letsencrypt})
54. How are SSL certificates being used with NLB?
55. What is TLS with typical use cases?
56. How are certificates verified by the client?
57. What does the term "HSM" mean?

### API & Access

58. What is the difference between api gateway and CDN?
59. How to deploy code in Lambda
60. What is Lambda and what services use it?
    - <small>Lambda is an AWS managed, Serverless computing platform</small>
    - <small>Used by API Gateway, CloudWatch, S3, and CloudFront</small>
61. What languages does Lambda support?
    - <small>NodeJS, Python, Java, Go, PowerShell, C#, Ruby</small>
    - <small>Also supports any language via Lambda Runtime (complex, rare)</small>
62. How to deploy Lambda Functions in a secure production way (Alias, Versions, canary deployment)
63. How to manage Lambda Functions in a SCM (SAM Framework, CloudFormation, CodePipeline)
64. What is a Serverless Application Model?
65. Lambda Configurations / Lambda Handler
66. Do we need outbound rules for NACLs?
67. What port will be used to allow outbound traffic of a web server?
68. How to access EC2 from a Lambda?
69. Do you write lambda functions as well? What was the purpose of the last lambda you wrote?
70. Can we write a bash script in lambda?
71. How will you handle millions of requests in AWS lambda?
72. What is lambda concurrency?

### EC2 & Compute

73. How do you EC2 securely access S3 bucket?
74. Can you lose the public IP address associated with your EC2 instance?
75. How to apply patch on EC2
76. How to rollout the change in Prod
77. Diff ways to run commands on EC2
78. How to recover EC2 instance by "apm" repair?
79. How many subnets will be required for HA EC2 infrastructure?

### Databases

80. For a highly available RDS PostgreSQL setup in two AZs, what does Multi-AZ actually change behind the scenes, and what happens during a failover?
81. What relational databases does Amazon support?
    - <small>PostgreSQL, MySQL, MariaDB, SQL Server, Oracle</small>
    - <small>Aurora (serverless/managed for MySQL and PostgreSQL)</small>
82. What NoSQL databases does AWS support?
    - <small>DynamoDB, Cassandra, DocumentDB, MongoDB (custom support)</small>
83. Which database is a NoSQL database type that can quickly store and retrieve key-value pairs?
    - <small>DynamoDB</small>

### Monitoring & Management

84. How would you monitor and alert on an EC2 instance running out of disk space using CloudWatch, and what would you trigger when the alarm fires?
85. How can I take actions from CloudWatch alerts?
    - <small>Trigger Lambda functions and send SNS notifications</small>
86. How can I see details of API Calls?
    - <small>CloudTrail</small>

### Multi-Account & Cross-Account

87. In a multi-account AWS setup, how would you design IAM roles and trust policies so a central security account can read CloudTrail logs and Security Hub findings from all member accounts?
88. What exact permissions and policy types would you use to let member accounts write to that centralized S3 bucket while preventing them from reading or deleting any objects?
89. What specific S3 bucket policy conditions would you add on `s3:PutObject` to enforce encryption and ensure only the owning account controls object ownership, while still allowing cross-account writes?
90. Is it possible to share resources between two different AWS accounts?
91. Cross Account/Region Deployments

### Advanced Features

92. Provision K8s clusters using Terraform and deploy services/applications using Terraform, Helm, helm release (Terraform resource) and GitOps approach.
93. Service Discovery - CloudMap
94. What other high-level services have you used on AWS like Athena, Glue, QuickSight, complex networking using VPC and direct connect, and VPC peering?
95. How to avoid DDoS attacks AWS?
96. In AWS, how can you mitigate DDoS attacks?
    - <small>AWS Shield and CloudFront</small>
    - <small>CloudFront works due to its massive scale</small>
97. AWS CLI commands
98. What is the name of the Python library to interact with AWS?
    - <small>boto3</small>

### Policy & JSON

99. What are the elements inside a JSON policy document, explain each

---

## CI/CD

<small>Continuous Integration & Continuous Deployment</small>

### Jenkins

1. Explain the CI/CD process you have followed and what method you have used in your company to deploy the applications
2. Jenkins Share Library
3. Seed Jobs
4. Jenkins artifact
5. How to create in Jenkins if you have three repositories if you have IAC code
6. Top level overview how to create a CI/CD for Kubernetes APP
7. Jenkins share library
8. How to Pass Information from one Job to another
9. What to do if you have 100 different apps — how you will implement CI/CD for that? How many jobs you need?
10. How we can share pipeline code with different pipelines
11. How to store Jenkins pipeline
12. Docker build and docker push to custom DTR in Jenkins
13. Error detection in shared modules in Jenkins
14. Jenkins DSL plugin
15. Multi branch pipeline
16. Pass parameter from shared modules like "Get the first S3 bucket of an AWS account from one module to another"
17. Automation framework configuration with Jenkins for CI/CD
18. Jenkins Agent
19. Jenkins build & pipeline
20. Creation of new agent
21. How do you use Jenkins to perform CI/CD and what are the steps?
22. What are the advantages of using Jenkins?
23. Issues you can encounter while deploying the code by using Jenkins?
24. Couple of code snippets for Jenkins using screen share

### GitHub Workflows / Actions

25. What is GitHub Action, and how does it help automate workflows in your projects?
    - <small>These are "triggers" that GitHub makes in response to events (e.g., commit to master)</small>
    - <small>Typical use-case: triggering Jenkins to run CI/CD pipeline</small>
26. Explain the difference between GitHub Actions and GitHub Workflows.
27. How do you define a workflow in a GitHub Actions YAML file?
28. What are the key components of a GitHub Actions YAML file?
29. How can you trigger a GitHub workflow to run automatically?
30. Describe the purpose of the `on` keyword in a GitHub Actions YAML file.
31. How do you specify which events trigger a workflow to run?
32. What are environment variables in GitHub Actions, and how are they used?
33. Explain how you can use GitHub Actions to automate continuous integration (CI) processes.
34. How do you set up a GitHub Actions workflow to deploy your application to a cloud provider?
35. What is a GitHub Actions runner, and how does it contribute to the workflow process?
36. How can you define dependencies and steps within a GitHub Actions workflow?
37. Describe how you can use conditional expressions in GitHub Actions workflows.
38. What are artifacts in GitHub Actions, and how can they be used to share data between jobs?
39. Explain the concept of GitHub Actions' self-hosted runners and when you might use them.

---

## Observability & Monitoring

<small>ELK, Prometheus, Grafana</small>

1. What is ELK stack and what components does it consist of?
2. What does ELK stand for and what does it do?
    - <small>Elasticsearch, Logstash, and Kibana — framework for ingesting, storing, processing, and presenting logs</small>
3. How does Logstash process logs in the ELK stack?
4. What is the purpose of Elasticsearch in ELK stack?
5. How does Prometheus collect and store metrics?
6. Describe the difference between counters and gauges in Prometheus.
7. What are exporters in Prometheus and how do they work?
8. How does PromQL help query metrics in Prometheus?
9. Explain the role of service discovery in monitoring with Prometheus.
10. Explain the role of Grafana in observability.
11. How can Grafana help visualize complex data in real-time?
12. How does Grafana support alerting based on metric thresholds?
13. What is a metric in the context of monitoring?
14. Explain the concept of logs, metrics, and traces in observability.
15. Describe the use case of tracing in observability.
16. How can you ensure high availability for ELK stack components?

### Monitoring Experience

17. Which monitoring tools have you used to monitor your deployed products on production?

---

## Linux / Scripting

<small>Bash, Python, and Linux System Administration</small>

### Linux Commands

1. What is the purpose of the `chmod` command in Linux?
2. What is the purpose of the `grep` command in Linux?
3. What is the function of the `df` command in Linux?
4. What does the `ps` command do in Linux?
5. How to change user group in ubuntu?
6. What is the purpose of the `tar` command in Linux?
7. How do you restart a network service using the `systemctl` command?
8. Which command will tell you how long a system has been running?
9. Which network protocol is used to synchronize clocks?
10. How to check for Linux syscalls of a running process?
11. Where is the upstream DNS server address stored on Linux?
12. What Linux process states do you know?
13. On Linux what's the ID number of the init process?
14. Where are the system logs located?
15. Which protocol does ping use?
16. How to see network packets in Linux?
17. The `ssh-copy-id` command copies what to the remote host?
    - <small>It copies the public SSH key to the remote</small>
18. What command is used to determine the amount of disk usage for a directory?
    - <small>du</small>

### Bash Scripting

19. What command is used to display the first 10 lines of a file?
20. How do you redirect the output of a command to a file in Bash?
21. What command is used to find files based on their name in Bash?
22. How can you pass command-line arguments to a Bash script?
23. What command is used to replace text in a file using Bash?
24. What does the 'exit' command do in a Bash script?
25. What is the purpose of the 'source' command in Bash?
26. In order to extract text from the first column of a file called textfile, which command would you use?
27. In order for a Bash script to be executed like an OS command, it should start with a shebang line. What does this look like?

### Python

28. Do you know Python? What are %s and %d and how do you use them in a string?
29. What is "yield"? What is it and where do you use it?
30. Explain the difference between a list and a tuple in Python.
31. What is a dictionary in Python?
32. Explain the difference between "==" and "is" for comparing objects in Python.
33. What is a lambda function in Python?
34. How do you handle exceptions using try and except blocks?
35. Describe the difference between a shallow copy and a deep copy of a list.
36. How do you remove duplicates from a list while preserving the order?
37. What is the purpose of the "self" keyword in Python classes?
38. Are you an expert in any programming language?

---

## Docker / Kubernetes

<small>Containerization and orchestration</small>

### Docker

1. What is the difference between containers and Virtual machines?
2. What is Docker Compose used for?
3. What is a Docker volume?
4. Explain the concept of Docker networking.
5. What is Docker Swarm?
6. How can you pass environment variables to a Docker container?
7. How do you scale containers using Docker?
8. What is a container?
9. In Docker, what is the command to download an image?
    - <small>`docker pull`</small>
10. In Docker, what command would I use to enter the container in interactive mode?
    - <small>`docker exec -it <CONTAINER NAME> bash`</small>
11. In Docker, if I modified a container and now want to use it as a new image, what command would I use?
    - <small>`docker commit CONTAINER_NAME NEW_IMAGE_NAME`</small>
12. What is "DinD"?
    - <small>Docker in Docker — running one container inside another (mainly for dev/non-prod)</small>

### Kubernetes

13. Describe your experience with Kubernetes?
14. How do you rank yourself on Kubernetes?
15. What do you know about the CLI in Kubernetes?
16. What is the general architecture of Kubernetes?
    - <small>Control Plane (master) → Clusters → Nodes → Pods → Services</small>
17. How would I see the running architecture elements actually active in my K8s cluster?
    - <small>`kubectl get nodes/pods/services`</small>
18. What are the 5 service types in Kubernetes?
    - <small>ClusterIP, NodePort, LoadBalancer, Headless, ExternalName</small>
19. Can you ssh/connect to bash on the container inside the pod?
20. How do you get a description of a pod or a specific namespace, non-standard namespace?
21. How to check its logs of a pod?
22. Have you provisioned EKS clusters using terraform? And how much?
23. Any idea about the internal networking of Kubernetes?
24. Have you heard about the two network adapters Flannel and calico?
25. What happens if your persistence volume becomes full?
26. kubelet uses liveness probes to know when to restart a container
27. kubelet uses readiness probes know when a container is ready to start accepting traffic
28. multiple cache in K8s
29. how to track K8s container configuration
30. serverless vs K8s containers
31. Kubernetes Secret Store CSI Driver
32. Kubernetes manifest
33. Kubernetes limit and max resources
34. Kubernetes hook admissionregistration.k8s.io
35. Kubernetes volume types?
36. How do you manage Kubernetes in your company to deploy applications locally for testing?
37. Stateful and stateless in Kubernetes
38. Have you used Helm charts with Kubernetes to deploy them?
39. Argocd
40. Can you describe what the Stateful and Stateless aspects mean?
41. What version of Kubernetes do you have your most recent experience on?
    - <small>Most recent is 1.27, but in production typically 1.24 or 1.25</small>

---

## SCMs (GIT)

<small>Source Control Management</small>

1. What is git and what does "git rebase" do?

---

## Security

<small>AWS Security, HSM, Compliance</small>

1. How to avoid DDoS attacks AWS?
2. What are CVEs, and how can I search for those in AWS?
    - <small>CVEs are Common Vulnerabilities and Exposures (known security weaknesses)</small>
    - <small>AWS Inspector looks for these</small>
3. As a compliance and security staff, which AWS services you have used?
4. What other tools can be used to maintain and patch DevOps resources?
5. What are other options for security then IAM?
6. If you have to give access to a lab to all students throughout the world which secure channel will you use?
    - <small>VPN, Bastion host, Private subnets</small>

---

## Experience / Scenario Based

<small>Behavioral and practical experience questions</small>

### Experience Questions

1. Describe your experience with Docker?
2. How much experience do you have with Terraform in production? Explain it.
3. Describe your experience with Kubernetes?
4. Describe your experience with DynamoDB
5. What experience do you have with Linux system administration? What is the largest group of servers you have been part of operating?
6. Apart from the basic AWS services (ec2, s3, security groups, ALB, ASG) — what other high-level services have you used on AWS like Athena, Glue, Quicksight, complex networking using VPC and direct connect, and VPC peering?
7. What do you think is your strongest strength in DevOps? Through you can do any kind of stuff quickly?

### Behavioral Questions

8. Tell me about a time when you faced a setback in your work. How did you deal with it? What happened as a result?
9. Tell me about a time when you streamlined an element of your work based on customer feedback. What did you do and how did that enhance the customer experience?
10. Tell me about a time that you had a conflicting view of someone you worked with. What did you do and what was the outcome?
11. Explain an event where you followed a proactive approach in the past.
12. Describe a situation where you heard feedback from your colleagues.
13. Describe a situation when you felt compelled to speak up but when it took a lot of courage to do so.
14. Three strengths and weaknesses?

---

<small>Last Updated: May 1, 2026</small>
<small>Total Questions: 600+</small>
