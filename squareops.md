# DevOps Interview Questions

## General / Behavioral
- Introduce yourself and walk me through your experience?
- Can you describe a typical day in your current role?

## CI/CD & Build Optimization
- How did you reduce the build time in your project?
- (Build time for application is 1.5 hr so Follow-up: Build still takes ~1.5 hours—what further optimizations would you suggest?)
- What are the benefits of using ephemeral agents in CI/CD pipelines? How are you handling the creation, connection & destruction of the agent? 
- How do you handle build artifacts creation and management?
- How did you migrate your codebase from one repository/system to another (e.g., Bitbucket to GitHub)?
- What is a divergent branch? How to handle them?
- What is the branching strategy you follow (e.g., GitFlow, trunk-based)?

## Docker & Containerization
- What are the different stages in a multi-stage Docker build?
- How do you reduce Docker image size?

## Terraform
- Suppose one of your team members has manually changed the infrastructure from the AWS console, How will you handle the state drift? How will you ensure this does not happen again in future? 
- How to handle multiple cloud providers in a single terraform configuration?

## Logging, Monitoring & Observability
- How do you decide which logs should go to Prometheus vs. Splunk (or any logging system)?
- How do you handle log isolation and avoid high cardinality issues?
- How do you integrate Prometheus into your application?
- How are you using observability tools to improve application performance?
- Can you explain the complete EFK (Elasticsearch, Fluentd, Kibana) flow in your system?
- How do you manage logs in Kubernetes clusters?

## Security & Secrets Management
- Since you’ve worked with both CyberArk Conjur and AWS Secrets Manager, which would you choose for EKS and why?
- How do you securely manage application secrets in Kubernetes?