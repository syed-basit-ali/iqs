# Comprehensive DevOps Interview Questions

<small>All questions organized by domain with recommended focus areas</small>

---

## Table of Contents
1. [DevOps / SRE](#devops--sre) (1-12)
2. [Terraform](#terraform) (13-60)
3. [Ansible](#ansible) (61-79)
4. [AWS](#aws) (80-178)
5. [CI/CD](#cicd) (179-217)
6. [Observability & Monitoring](#observability--monitoring) (218-234)
7. [Linux / Scripting](#linux--scripting) (235-272)
8. [Docker / Kubernetes](#docker--kubernetes) (273-313)
9. [SCMs (GIT)](#scms-git) (314-314)
10. [Security](#security) (315-320)
11. [Experience / Scenario Based](#experience--scenario-based) (321-334)

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

13. How to set up the Terraform Project
14. What happens when you perform `terraform init`
15. What is the concept of backend in Terraform?
16. Where we define the backend and how we set up the remote backend
17. How can we setup multiple environments (dev, qa, uat, prod) — what are different approaches that can be used?
18. What is the difference between `for_each` and `count` in Terraform?
19. What's the difference between object and map in Terraform?
20. What is module in Terraform? How we call module in the main code?
21. How to create Terraform structure for project if you are starting new project

### State Management

22. State Locking — Define state locking, how it works.
23. Remote Backends — How do we achieve State locking with remote backend?
24. What is State File, how to manage it securely in a distributed team?
25. In Terraform, how do you make sure multiple parties do not modify the state file at the same time and corrupt it?
    - <small>You need to lock the state file. One way is with DynamoDB.</small>
26. In Terraform, if someone modifies the infrastructure directly from the AWS console, what are the implications and what actions should you take?
    - <small>The state file will be out of sync. Use `terraform refresh` to update the state file.</small>

### Modules & Resources

27. How to create a module? What are the minimum requirements?
28. Outputs — what is output.tf file?
29. How to use a module, how to specify the version of a module?
30. Create multiple EC2 instances using an EC2 module based on a list of Subnet IDs (one instance per subnet)
31. Difference between `for_each` & `count` with above example & how to refer EC2 instance resource in both cases
32. Access output of one module when creating a resource from another module
33. Give example of output from modules
34. What are Terraform Modules, ways to publish and source them?

### Advanced Features

35. How to provision resources (EC2, RDS) dynamically, using meta-arguments like count, foreach
36. How to manage existing manually created resources via IaC (Terraform) — Terraform import
37. How to deploy lambda functions
38. Terraform conditions
39. Dynamic (in context of terraform)
40. Lambda using Terraform
41. Linting and Formatting
42. Pre-commit checks

### Environment & Multi-Environment Setup

43. Steps to setup new terraform environment (directory structure, providers, backend)
44. How to setup common modules for multi-environment
45. Define/Suggest to structure a Terraform script to create resources across various different environments
46. Explain a list variable (containing subnets) and a resource using count to create EC2 instances using an AMI, instance type and subnet from the list
47. Explain a resource using `for` keyword with a `toset(list)`
48. What is the `toset()` function used for?
49. Explain a policy being defined using a Heredoc string, what does the policy do?
50. Explain an assume role policy
51. What will the output of a resource using count look like? (using [] brackets and 0 based index)

### Common Blocks & Best Practices

52. Give examples of common blocks (Ans: e.g. provider, module, data, variable, output etc)
53. What is a data block used for?
54. Is it possible to share resources between two different AWS accounts?
55. How do you maintain your state file to keep it safe from corruption? And what happens when your state file gets locked? How you will resolve it?
56. What is a tainted resource?
57. How to safely refactor a large Terraform codebase into modules without forcing resource recreation (handling `moved` blocks/state moves)?

### Terraform Workflows

58. In Terraform, what are the workflow commands?
    - <small>`init` → [fmt] → [validate] → `plan` → `apply` → [refresh] → `destroy`</small>
    - <small>If you have existing infrastructure, use `terraform import`</small>
    - <small>`terraform destroy` removes infrastructure known in state file (common in dev, rare in prod)</small>
    - <small>Commands in brackets are optional but recommended</small>

### Credentials & Secrets

59. How should you manage access credentials or other secrets in Terraform?
    - <small>HashiCorp/Terraform Vault</small>
    - <small>AWS Secrets Manager</small>

### Terraform vs CloudFormation

60. What are the differences between Terraform and CloudFormation?
    - <small>Both are IaC; Terraform works on multiple cloud providers and on-premise, CloudFormation only on AWS</small>
    - <small>Terraform uses HCL; CloudFormation uses JSON</small>

---

## Ansible

<small>Configuration management and automation</small>

### Basics

61. Do you know Ansible? What is it and what makes it different from others?
62. What is Ansible, and how does it differ from other configuration management tools?
63. What is an Ansible inventory? How do you define inventory?
64. Playbook without hosts — does it run? If yes, how and where would it run?
65. Explain the difference between Ansible Playbook and Ansible Role.
66. How do you define hosts in Ansible inventory?
67. What is an Ansible Task and how is it different from a Play?

### Advanced Concepts

68. How do you handle sensitive data like passwords in Ansible?
69. Describe the purpose of Ansible Vault.
70. What is idempotence in Ansible, and why is it important?
71. How do you use Ansible Galaxy to manage roles?
72. Explain the concept of Ansible Facts.
73. What is the difference between Ansible ad-hoc commands and Playbooks?
74. How do you loop over items in Ansible Playbooks?
75. What are Ansible Handlers and when are they triggered?
76. How can you limit tasks to specific hosts in Ansible Playbooks?
77. How do you debug Ansible Playbooks or roles?
78. What is the purpose of the ansible.cfg configuration file?

### Ansible vs Other Tools

79. What are the differences between Ansible and Puppet?
    - <small>Ansible is declarative and written in Python</small>
    - <small>Puppet is more task oriented and written in Ruby</small>
    - <small>Puppet considered superior for large deployments, but Ansible has more market traction</small>

---

## AWS

<small>Amazon Web Services core and advanced topics</small>

### IAM & Access Control

80. What is the difference between IAM role and an IAM user?
81. Ways of giving access to people to AWS services
82. AD users outside AWS — how to give them access to AWS services
83. Identity Based policies
84. Resource Based policies
85. What are the resources used to control access?
86. How can we control access between two EC2 instances?
87. Two EC2 instances are in the same subnet — how can we control access?
88. How can we control access to EC2 as a web server with traffic coming from the internet?
89. How do we configure access to EC2 instances running the same service?
90. Best practices to allow traffic to an EC2 Instance.

### Network & VPC

91. How to share resources between different VPCs.
92. How to share if we have overlapping IP ADDRESSES
93. How to monitor traffic IN VPC
94. Difference between security Group and NACL
95. Ways to access data from an S3 bucket from a private Instance without going through the public route (VPC Endpoints).
96. Type of VPC Endpoints, what is Endpoint Policy, how to restrict access using endpoint policy.
97. Restrict access to S3 Bucket using resource-based policy.
98. VPC Gateway endpoint — What does AWS do/create when you create it?
99. VPC endpoint — What does AWS do/create when you create it?
100. With the VPC Gateway endpoint for S3 enabled, we want to allow an EC2 instance to access an S3 bucket & restrict that bucket to be accessed by that EC2 instance. What Resource based policy will be added on S3?
101. Difference between Interface and Gateway VPC Endpoints
102. Is it possible to allow access to a specific S3 bucket from an instance in a private subnet? How?
103. How can two EC2 instances in two separate private subnets in two separate VPC connect to each other?
104. What are private endpoints?
105. What is the difference between VPC Peering and Transit Gateway?
    - <small>VPC peering connects one VPC directly to another (meshed architecture)</small>
    - <small>Transit Gateway is a hub-and-spoke architecture that simplifies multiple VPC connections</small>

### S3 & Storage

106. How to get S3 data if your EC2 instance doesn't have internet access
107. What is the maximum size of a single upload to S3?
    - <small>5 gigabytes</small>
108. What is the maximum size of an object in S3?
    - <small>5 terabytes</small>
109. If there is a 5GB single upload limit in S3, how do you get to a 5TB object?
    - <small>Multi-part uploads</small>
110. In S3, how would you design a bucket policy and IAM permissions to enforce encryption at rest and block all public access, including accidental ACLs?
111. How would you enforce "deny if not encrypted" and "deny if not TLS" at the bucket level using Terraform-managed policies?
112. How would you enforce encryption at rest for *all* PUTs using an S3 bucket policy, including blocking uploads that omit the required encryption headers?
113. Restrict access to S3 Bucket using resource-based policy.

### Load Balancers & Traffic

114. What can be the different destinations of traffic in ALB, ELB and NLB?
115. Enabling SSL on ALB using ACM
116. What AWS Security Services can be configured on top of ALB — Brief overview of how we configure them
117. Types of LoadBalancer in AWS — difference between Application & Network LoadBalancer, when & why to use one.
118. What is a load balancer?
119. What algorithms can be used in load balancers?
120. Can a load balancer be layer 4 and layer 7 at the same time?
121. What is the difference between a Network Load Balancer and an Application Load Balancer?
    - <small>NLB operates at Layer 3 (Network) and is stateless</small>
    - <small>ALB operates at Layer 5 (Session) and/or Layer 7 (Application) and is stateful</small>
122. HA for EC2s
123. HA for RDS
124. ALB / ELB
125. HTTPS with ALB
126. End-end HTTPS from Client to ALB to EC2

### Security & Certificates

127. Restricting access at the level of AWS regions
128. What is the difference between api gateway and CDN?
129. Which endpoints support the AWS WAF (ALB, CloudFront, API Gateway)?
130. Regional/Global CloudFront — why and when to use.
131. How are SSL certificates generated?
132. End-End TLS (ACM, {letsencrypt})
133. How are SSL certificates being used with NLB?
134. What is TLS with typical use cases?
135. How are certificates verified by the client?
136. What does the term "HSM" mean?

### API & Access

137. What is the difference between api gateway and CDN?
138. How to deploy code in Lambda
139. What is Lambda and what services use it?
    - <small>Lambda is an AWS managed, Serverless computing platform</small>
    - <small>Used by API Gateway, CloudWatch, S3, and CloudFront</small>
140. What languages does Lambda support?
    - <small>NodeJS, Python, Java, Go, PowerShell, C#, Ruby</small>
    - <small>Also supports any language via Lambda Runtime (complex, rare)</small>
141. How to deploy Lambda Functions in a secure production way (Alias, Versions, canary deployment)
142. How to manage Lambda Functions in a SCM (SAM Framework, CloudFormation, CodePipeline)
143. What is a Serverless Application Model?
144. Lambda Configurations / Lambda Handler
145. Do we need outbound rules for NACLs?
146. What port will be used to allow outbound traffic of a web server?
147. How to access EC2 from a Lambda?
148. Do you write lambda functions as well? What was the purpose of the last lambda you wrote?
149. Can we write a bash script in lambda?
150. How will you handle millions of requests in AWS lambda?
151. What is lambda concurrency?

### EC2 & Compute

152. How do you EC2 securely access S3 bucket?
153. Can you lose the public IP address associated with your EC2 instance?
154. How to apply patch on EC2
155. How to rollout the change in Prod
156. Diff ways to run commands on EC2
157. How to recover EC2 instance by "apm" repair?
158. How many subnets will be required for HA EC2 infrastructure?

### Databases

159. For a highly available RDS PostgreSQL setup in two AZs, what does Multi-AZ actually change behind the scenes, and what happens during a failover?
160. What relational databases does Amazon support?
    - <small>PostgreSQL, MySQL, MariaDB, SQL Server, Oracle</small>
    - <small>Aurora (serverless/managed for MySQL and PostgreSQL)</small>
161. What NoSQL databases does AWS support?
    - <small>DynamoDB, Cassandra, DocumentDB, MongoDB (custom support)</small>
162. Which database is a NoSQL database type that can quickly store and retrieve key-value pairs?
    - <small>DynamoDB</small>

### Monitoring & Management

163. How would you monitor and alert on an EC2 instance running out of disk space using CloudWatch, and what would you trigger when the alarm fires?
164. How can I take actions from CloudWatch alerts?
    - <small>Trigger Lambda functions and send SNS notifications</small>
165. How can I see details of API Calls?
    - <small>CloudTrail</small>

### Multi-Account & Cross-Account

166. In a multi-account AWS setup, how would you design IAM roles and trust policies so a central security account can read CloudTrail logs and Security Hub findings from all member accounts?
167. What exact permissions and policy types would you use to let member accounts write to that centralized S3 bucket while preventing them from reading or deleting any objects?
168. What specific S3 bucket policy conditions would you add on `s3:PutObject` to enforce encryption and ensure only the owning account controls object ownership, while still allowing cross-account writes?
169. Is it possible to share resources between two different AWS accounts?
170. Cross Account/Region Deployments

### Advanced Features

171. Provision K8s clusters using Terraform and deploy services/applications using Terraform, Helm, helm release (Terraform resource) and GitOps approach.
172. Service Discovery - CloudMap
173. What other high-level services have you used on AWS like Athena, Glue, QuickSight, complex networking using VPC and direct connect, and VPC peering?
174. How to avoid DDoS attacks AWS?
175. In AWS, how can you mitigate DDoS attacks?
    - <small>AWS Shield and CloudFront</small>
    - <small>CloudFront works due to its massive scale</small>
176. AWS CLI commands
177. What is the name of the Python library to interact with AWS?
    - <small>boto3</small>

### Policy & JSON

178. What are the elements inside a JSON policy document, explain each

---

## CI/CD

<small>Continuous Integration & Continuous Deployment</small>

### Jenkins

179. Explain the CI/CD process you have followed and what method you have used in your company to deploy the applications
180. Jenkins Share Library
181. Seed Jobs
182. Jenkins artifact
183. How to create in Jenkins if you have three repositories if you have IAC code
184. Top level overview how to create a CI/CD for Kubernetes APP
185. Jenkins share library
186. How to Pass Information from one Job to another
187. What to do if you have 100 different apps — how you will implement CI/CD for that? How many jobs you need?
188. How we can share pipeline code with different pipelines
189. How to store Jenkins pipeline
190. Docker build and docker push to custom DTR in Jenkins
191. Error detection in shared modules in Jenkins
192. Jenkins DSL plugin
193. Multi branch pipeline
194. Pass parameter from shared modules like "Get the first S3 bucket of an AWS account from one module to another"
195. Automation framework configuration with Jenkins for CI/CD
196. Jenkins Agent
197. Jenkins build & pipeline
198. Creation of new agent
199. How do you use Jenkins to perform CI/CD and what are the steps?
200. What are the advantages of using Jenkins?
201. Issues you can encounter while deploying the code by using Jenkins?
202. Couple of code snippets for Jenkins using screen share

### GitHub Workflows / Actions

203. What is GitHub Action, and how does it help automate workflows in your projects?
    - <small>These are "triggers" that GitHub makes in response to events (e.g., commit to master)</small>
    - <small>Typical use-case: triggering Jenkins to run CI/CD pipeline</small>
204. Explain the difference between GitHub Actions and GitHub Workflows.
205. How do you define a workflow in a GitHub Actions YAML file?
206. What are the key components of a GitHub Actions YAML file?
207. How can you trigger a GitHub workflow to run automatically?
208. Describe the purpose of the `on` keyword in a GitHub Actions YAML file.
209. How do you specify which events trigger a workflow to run?
210. What are environment variables in GitHub Actions, and how are they used?
211. Explain how you can use GitHub Actions to automate continuous integration (CI) processes.
212. How do you set up a GitHub Actions workflow to deploy your application to a cloud provider?
213. What is a GitHub Actions runner, and how does it contribute to the workflow process?
214. How can you define dependencies and steps within a GitHub Actions workflow?
215. Describe how you can use conditional expressions in GitHub Actions workflows.
216. What are artifacts in GitHub Actions, and how can they be used to share data between jobs?
217. Explain the concept of GitHub Actions' self-hosted runners and when you might use them.

---

## Observability & Monitoring

<small>ELK, Prometheus, Grafana</small>

218. What is ELK stack and what components does it consist of?
219. What does ELK stand for and what does it do?
    - <small>Elasticsearch, Logstash, and Kibana — framework for ingesting, storing, processing, and presenting logs</small>
220. How does Logstash process logs in the ELK stack?
221. What is the purpose of Elasticsearch in ELK stack?
222. How does Prometheus collect and store metrics?
223. Describe the difference between counters and gauges in Prometheus.
224. What are exporters in Prometheus and how do they work?
225. How does PromQL help query metrics in Prometheus?
226. Explain the role of service discovery in monitoring with Prometheus.
227. Explain the role of Grafana in observability.
228. How can Grafana help visualize complex data in real-time?
229. How does Grafana support alerting based on metric thresholds?
230. What is a metric in the context of monitoring?
231. Explain the concept of logs, metrics, and traces in observability.
232. Describe the use case of tracing in observability.
233. How can you ensure high availability for ELK stack components?

### Monitoring Experience

234. Which monitoring tools have you used to monitor your deployed products on production?

---

## Linux / Scripting

<small>Bash, Python, and Linux System Administration</small>

### Linux Commands

235. What is the purpose of the `chmod` command in Linux?
236. What is the purpose of the `grep` command in Linux?
237. What is the function of the `df` command in Linux?
238. What does the `ps` command do in Linux?
239. How to change user group in ubuntu?
240. What is the purpose of the `tar` command in Linux?
241. How do you restart a network service using the `systemctl` command?
242. Which command will tell you how long a system has been running?
243. Which network protocol is used to synchronize clocks?
244. How to check for Linux syscalls of a running process?
245. Where is the upstream DNS server address stored on Linux?
246. What Linux process states do you know?
247. On Linux what's the ID number of the init process?
248. Where are the system logs located?
249. Which protocol does ping use?
250. How to see network packets in Linux?
251. The `ssh-copy-id` command copies what to the remote host?
    - <small>It copies the public SSH key to the remote</small>
252. What command is used to determine the amount of disk usage for a directory?
    - <small>du</small>

### Bash Scripting

253. What command is used to display the first 10 lines of a file?
254. How do you redirect the output of a command to a file in Bash?
255. What command is used to find files based on their name in Bash?
256. How can you pass command-line arguments to a Bash script?
257. What command is used to replace text in a file using Bash?
258. What does the 'exit' command do in a Bash script?
259. What is the purpose of the 'source' command in Bash?
260. In order to extract text from the first column of a file called textfile, which command would you use?
261. In order for a Bash script to be executed like an OS command, it should start with a shebang line. What does this look like?

### Python

262. Do you know Python? What are %s and %d and how do you use them in a string?
263. What is "yield"? What is it and where do you use it?
264. Explain the difference between a list and a tuple in Python.
265. What is a dictionary in Python?
266. Explain the difference between "==" and "is" for comparing objects in Python.
267. What is a lambda function in Python?
268. How do you handle exceptions using try and except blocks?
269. Describe the difference between a shallow copy and a deep copy of a list.
270. How do you remove duplicates from a list while preserving the order?
271. What is the purpose of the "self" keyword in Python classes?
272. Are you an expert in any programming language?

---

## Docker / Kubernetes

<small>Containerization and orchestration</small>

### Docker

273. What is the difference between containers and Virtual machines?
274. What is Docker Compose used for?
275. What is a Docker volume?
276. Explain the concept of Docker networking.
277. What is Docker Swarm?
278. How can you pass environment variables to a Docker container?
279. How do you scale containers using Docker?
280. What is a container?
281. In Docker, what is the command to download an image?
    - <small>`docker pull`</small>
282. In Docker, what command would I use to enter the container in interactive mode?
    - <small>`docker exec -it <CONTAINER NAME> bash`</small>
283. In Docker, if I modified a container and now want to use it as a new image, what command would I use?
    - <small>`docker commit CONTAINER_NAME NEW_IMAGE_NAME`</small>
284. What is "DinD"?
    - <small>Docker in Docker — running one container inside another (mainly for dev/non-prod)</small>

### Kubernetes

285. Describe your experience with Kubernetes?
286. How do you rank yourself on Kubernetes?
287. What do you know about the CLI in Kubernetes?
288. What is the general architecture of Kubernetes?
    - <small>Control Plane (master) → Clusters → Nodes → Pods → Services</small>
289. How would I see the running architecture elements actually active in my K8s cluster?
    - <small>`kubectl get nodes/pods/services`</small>
290. What are the 5 service types in Kubernetes?
    - <small>ClusterIP, NodePort, LoadBalancer, Headless, ExternalName</small>
291. Can you ssh/connect to bash on the container inside the pod?
292. How do you get a description of a pod or a specific namespace, non-standard namespace?
293. How to check its logs of a pod?
294. Have you provisioned EKS clusters using terraform? And how much?
295. Any idea about the internal networking of Kubernetes?
296. Have you heard about the two network adapters Flannel and calico?
297. What happens if your persistence volume becomes full?
298. kubelet uses liveness probes to know when to restart a container
299. kubelet uses readiness probes know when a container is ready to start accepting traffic
300. multiple cache in K8s
301. how to track K8s container configuration
302. serverless vs K8s containers
303. Kubernetes Secret Store CSI Driver
304. Kubernetes manifest
305. Kubernetes limit and max resources
306. Kubernetes hook admissionregistration.k8s.io
307. Kubernetes volume types?
308. How do you manage Kubernetes in your company to deploy applications locally for testing?
309. Stateful and stateless in Kubernetes
310. Have you used Helm charts with Kubernetes to deploy them?
311. Argocd
312. Can you describe what the Stateful and Stateless aspects mean?
313. What version of Kubernetes do you have your most recent experience on?
    - <small>Most recent is 1.27, but in production typically 1.24 or 1.25</small>

---

## SCMs (GIT)

<small>Source Control Management</small>

314. What is git and what does "git rebase" do?

---

## Security

<small>AWS Security, HSM, Compliance</small>

315. How to avoid DDoS attacks AWS?
316. What are CVEs, and how can I search for those in AWS?
    - <small>CVEs are Common Vulnerabilities and Exposures (known security weaknesses)</small>
    - <small>AWS Inspector looks for these</small>
317. As a compliance and security staff, which AWS services you have used?
318. What other tools can be used to maintain and patch DevOps resources?
319. What are other options for security then IAM?
320. If you have to give access to a lab to all students throughout the world which secure channel will you use?
    - <small>VPN, Bastion host, Private subnets</small>

---

## Experience / Scenario Based

<small>Behavioral and practical experience questions</small>

### Experience Questions

321. Describe your experience with Docker?
322. How much experience do you have with Terraform in production? Explain it.
323. Describe your experience with Kubernetes?
324. Describe your experience with DynamoDB
325. What experience do you have with Linux system administration? What is the largest group of servers you have been part of operating?
326. Apart from the basic AWS services (ec2, s3, security groups, ALB, ASG) — what other high-level services have you used on AWS like Athena, Glue, Quicksight, complex networking using VPC and direct connect, and VPC peering?
327. What do you think is your strongest strength in DevOps? Through you can do any kind of stuff quickly?

### Behavioral Questions

328. Tell me about a time when you faced a setback in your work. How did you deal with it? What happened as a result?
329. Tell me about a time when you streamlined an element of your work based on customer feedback. What did you do and how did that enhance the customer experience?
330. Tell me about a time that you had a conflicting view of someone you worked with. What did you do and what was the outcome?
331. Explain an event where you followed a proactive approach in the past.
332. Describe a situation where you heard feedback from your colleagues.
333. Describe a situation when you felt compelled to speak up but when it took a lot of courage to do so.
334. Three strengths and weaknesses?

---

<small>Last Updated: May 1, 2026</small>
<small>Total Questions: 600+</small>
