# Cloud Practitioner - Concepts

## Table of Contents

- ⛅ [The 5 Criteria of Cloud Computing](#the-5-criteria-of-cloud-computing)
- 🟢 [Availability Concepts](#availability-concepts)
- 📈 [Scaling Concepts](#scaling-concepts)
- 🧭 [AWS Well-Architected Framework](#aws-well-architected-framework)
- 🧩 [AWS Cloud Adoption Framework (CAF)](#aws-cloud-adoption-framework-caf)
- 🚀 [Adoption Strategies](#adoption-strategies)
- 📦 [The 7 Rs Migration Strategies](#the-7-rs-migration-strategies)
- 💰 [Cloud Economics and Total Cost of Ownership](#cloud-economics-and-total-cost-of-ownership)
- 🛡️ [Shared Responsibility Model](#shared-responsibility-model)
- 🔐 [AWS Access Management Capabilities](#aws-access-management-capabilities)
- 💸 [AWS Pricing Models & Cost Optimization](#aws-pricing-models--cost-optimization)
- 🆘 [AWS Technical Resources & Support Options](#aws-technical-resources--support-options)

## ⛅ The 5 Criteria of Cloud Computing {#the-5-criteria-of-cloud-computing}

### Top-Level Intent

These five characteristics (defined by NIST) describe what fundamentally distinguishes cloud computing from traditional IT environments. AWS exams often test whether you recognize these attributes as intrinsic properties of the cloud model.

### 🔹1. On-Demand Self-Service

Users can provision compute, storage, and other resources whenever needed, without requiring human intervention from AWS staff. Key characteristics include immediacy, user autonomy, and the ability to provision through the console, CLI, or APIs. This enables rapid experimentation and deployment.

- Not the same as autoscaling — this is about **customer-initiated provisioning without human involvement**.
- Does not depend on APIs specifically; the console qualifies.
- Does not imply infinite capacity, only immediate access to provisioning mechanisms.
- Look for phrases like “no need to contact support,” “spin up environments instantly,” or “developers can launch resources independently.”

### 🔹2. Broad Network Access

Cloud resources can be accessed via standard networking mechanisms (typically HTTPS and APIs) from a variety of devices and locations. Key characteristics include device independence, location flexibility, and the use of widely adopted protocols.

- Does not require public Internet access — private networking, VPN, or Direct Connect still qualify.
- Not about geographic distribution, only about standardized network accessibility.
- Clues include “accessible from mobile devices,” “global team access,” and “standardized endpoints.”

### 🔹3. Resource Pooling

AWS aggregates physical resources and dynamically allocates them to customers as needed. Key characteristics include multi-tenancy, abstraction from the underlying hardware, and dynamic allocation. Customers don’t need to know the specific servers or physical locations backing their services.

- Not customers pooling their own resources — **AWS** does the pooling.
- Availability Zones and Regions are boundaries, not the pool.
- Multi-tenancy is implied but not explicitly required in every service.
- Watch for wording like “shared infrastructure,” “abstracted hardware,” or “location independence.”

### 🔹4. Elasticity / Rapid Elasticity

Cloud capacity can rapidly expand or contract to match workload demand. Key characteristics include rapid scaling, automatic or near-automatic adjustment, and aligning resource levels with utilization patterns. This supports cost efficiency and performance stability.

- Elasticity is often confused with scalability:
  - Scalability = ability to grow
  - Elasticity = **automatic adjustment up and down**
- Elasticity usually implies horizontal scaling on AWS, though vertical scaling can be part of broader elasticity strategies.
- Signals include “unpredictable workloads,” “automatic scaling,” or “resources adjust based on demand.”

### 🔹5. Measured Service (Monitoring & Billing)

AWS automatically tracks and measures resource consumption — compute hours, storage consumption, data transfer — and bills according to usage. Key characteristics include metering, transparency, automated reporting, and pay-as-you-go pricing.

- Not simply cost visibility — it’s about **automated metering tied directly to billing**.
- Not the same as cost optimization tools; this is the underlying mechanism those tools rely on.
- Look for clues like “usage-based billing,” “metered consumption,” “pay only for what you use,” or “automated usage tracking.”

### High-Level Summary for Exam Context

| Criterion            | Core Intent                              | Typical AWS Clue Words                   |
| -------------------- | ---------------------------------------- | ---------------------------------------- |
| On-demand            | User can provision without human support | immediate provisioning, autonomous setup |
| Broad network access | Access via standard network protocols    | remote access, device flexibility        |
| Resource pooling     | Shared, abstracted infrastructure        | multi-tenant, location independence      |
| Elasticity           | Rapid auto scale up/down based on load   | unpredictable workloads, autoscaling     |
| Measured service     | Usage-based metering & billing           | pay-as-you-go, automated tracking        |

### Common Confusions & Pitfalls

- Elasticity is not the same as scalability; exams often hide
  elasticity as **automatic** scaling.
- Resource pooling means multi-tenancy --- dedicated hardware
  contradicts this idea unless explicitly requested.
- On-demand self-service differs from "manual provisioning"; if humans
  must approve requests, it is not true cloud.
- Measured service refers to **automated metering**, not manual cost
  tracking.
- Network access does not only mean public internet --- private
  connectivity still qualifies.
- Broad network access does not imply "publicly accessible"; secure
  and private still count.

### Exam Hints

- "Scale automatically" → Elasticity
- "Pay only for what you use" → Measured Service
- "Provision resources without human interaction" → On-Demand
  Self-Service
- "Available over the internet or through APIs" → Broad Network Access
- "Shared infrastructure, multi-tenant environment" → Resource Pooling
- When the question asks, "Which of the following is a fundamental
  characteristic of cloud computing?" these 5 are the canonical
  answers.

## 🟢 Availability Concepts {#availability-concepts}

These terms describe different approaches to ensuring systems remain operational under varying levels of stress, failure, or catastrophe. The exam often tests your ability to distinguish between minimizing downtime, eliminating downtime, and surviving large-scale disruptive events.

### 🔹High Availability (HA)

Designing systems to minimize downtime by reducing single points of failure and allowing services to continue operating when components fail. This typically involves redundancy across Availability Zones, load balancing, and automatic failover. The intention is continuous service with brief or minimal interruptions.

- HA does **not** guarantee zero downtime.
- Usually scoped within a Region, not across Regions.
- Auto Scaling alone doesn’t provide HA without multi-AZ design.
- Clues: “improve uptime,” “survive AZ failure,” “minimize but not eliminate downtime,” “multi-AZ RDS.”

### 🔹Fault Tolerance

Systems continue operating **without interruption** even if components fail. This often requires full duplication of critical infrastructure, synchronous replication, and automated transparent failover. The intent is zero downtime during component-level failures.

- Fault tolerance is stricter than HA.
- More expensive due to redundant infrastructure.
- Single-AZ designs cannot be fault tolerant.
- Clues: “continuous operation,” “zero downtime,” “redundant components,” “system keeps running despite failure.”

### 🔹Disaster Recovery (DR)

Designing systems to continue operation—or be restorable—after major regional disruption or catastrophe. DR addresses Region-level resilience and uses strategies like backups, cross-Region replication, warm standby environments, and Route 53 failover.

- DR ≠ HA. HA handles smaller failures; DR handles large-scale disasters.
- Backups alone do not equal DR readiness.
- Requires balancing RTO/RPO with cost.
- Clues: “regional outage,” “RTO/RPO,” “cross-Region failover,” “restore service after disaster.”
- Know AWS’s four DR strategies: backup/restore, pilot light, warm standby, multi-site.
  - Backup and restore — Periodically back up data and infrastructure and restore them into a new environment after a disaster.
  - Pilot light — Keep only the critical core of the system running in another Region and scale it up when needed.
  - Warm standby — Run a smaller-capacity but fully functional version of the system in another Region, ready to scale during failover.
  - Multi-site (active-active) — Operate full workloads in multiple Regions simultaneously for instant failover.

### Summary Table

| Concept           | Goal                         | Typical Downtime      | Scope        | AWS Clue Words                          |
| ----------------- | ---------------------------- | --------------------- | ------------ | --------------------------------------- |
| High availability | Minimize downtime            | Very low, but nonzero | Multi-AZ     | improve uptime, survive AZ failure      |
| Fault tolerance   | Zero downtime                | None                  | Component/AZ | continuous operation, redundant systems |
| Disaster recovery | Survive large-scale disaster | Varies by strategy    | Region-level | RTO/RPO, regional outage, failover      |

## 📈 Scaling Concepts {#scaling-concepts}

- **Vertical scaling (scale up)** — Increasing the size or power of a single instance (e.g., moving from `t2.micro` to `t2.large`) to handle more load on one machine; simple but limited by maximum instance size.
- **Horizontal scaling (scale out)** — Adding more instances of the same type (e.g., from 1× `t2.micro` to N× `t2.micro`) to distribute load and improve availability.
- **Elasticity** — Automatically adjusting horizontal capacity based on demand, typically using Auto Scaling.

#### Notes / Pitfalls

- Vertical scaling does not improve availability.
- Horizontal scaling requires load balancing to be effective.
- Elasticity implies **automatic** scaling, not just scalability.

#### Exam Cues

- “Increase instance size” → vertical.
- “Add more instances” → horizontal.
- “Automatic scaling based on demand” → elasticity.

## 🧭 AWS Well-Architected Framework {#aws-well-architected-framework}

The Well-Architected Framework is AWS’s “blueprint for doing cloud right.” It provides principles and best practices across six pillars: Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, and Sustainability.

## 🔹Operational Excellence

This pillar focuses on running workloads effectively through automation, observability, and continuous improvement. It emphasizes making small, reversible changes and learning from failures to refine operations. The goal is to evolve systems safely while maintaining high operational quality.

- **Perform operations as code**

  - Automate provisioning with CloudFormation.
  - Use scripts or runbooks instead of manual steps.
  - Version-control all operational configuration.

- **Make frequent small reversible changes**

  - Deploy through CI/CD pipelines with small batches.
  - Use feature flags for instant rollback.
  - Avoid large risky deployments.

- **Refine operational procedures frequently**

  - Update runbooks after incidents.
  - Re-test workflows regularly.
  - Conduct scheduled operations reviews.

- **Anticipate failures**

  - Run game days.
  - Validate alarm paths.
  - Confirm failover triggers remain correct.

- **Learn from all operational failures**

  - Hold blameless postmortems.
  - Automate remediation of recurring issues.
  - Share lessons learned across teams.

## 🔹Security

The security pillar focuses on protecting systems and data through identity, detection, infrastructure protection, and incident response. It promotes a layered security model and heavy use of automation. The goal is to minimize exposure and ensure data confidentiality, integrity, and availability.

- **Implement a strong identity foundation**

  - Enforce least privilege with IAM roles.
  - Require MFA for admin/root access.
  - Use IAM Access Analyzer to detect broad permissions.

- **Maintain traceability**

  - Record all API calls with CloudTrail.
  - Use CloudWatch Logs for centralized logging.
  - Detect anomalies with GuardDuty.

- **Apply security at all layers**

  - Use SGs and NACLs for network segmentation.
  - Add WAF at the application layer.
  - Use private subnets for sensitive systems.

- **Automate security best practices**

  - Rotate secrets automatically.
  - Run Inspector scans regularly.
  - Enforce policies with AWS Config rules.

- **Protect data in transit and at rest**

  - Enforce TLS.
  - Encrypt with KMS keys.
  - Require bucket-level encryption.

- **Keep people away from your data**

  - Use SSM Session Manager instead of SSH.
  - Use automated deployments rather than shell access.
  - Restrict interaction with production systems.

- **Prepare for security events**

  - Maintain IR playbooks.
  - Predefine isolation procedures.
  - Trigger containment with EventBridge.

## 🔹Reliability

The reliability pillar focuses on ensuring workloads recover quickly from failures and continue to function correctly as demand changes. It emphasizes automatic recovery, distributed design, and testing recovery paths. The goal is to build systems that gracefully withstand component or infrastructure failures.

- **Automatically recover from failure**

  - Auto Scaling replaces unhealthy instances.
  - RDS Multi-AZ failover.
  - CloudWatch alarms trigger auto-recovery.

- **Test recovery procedures**

  - Simulate Region or AZ outages.
  - Test backup restoration.
  - Rehearse failover workflows regularly.

- **Scale horizontally to increase availability**

  - Load balance across multiple instances.
  - Spread microservices across AZs.
  - Use distributed queues to decouple components.

- **Stop guessing capacity**

  - Enable Auto Scaling groups.
  - Use DynamoDB autoscaling.
  - Choose serverless services when possible.

- **Manage change with automation**

  - IaC for predictable rollouts.
  - Blue/green or canary deployments.
  - Automation via Systems Manager.

## 🔹Performance Efficiency

This pillar focuses on using resources efficiently and selecting the right technologies for the workload. It emphasizes serverless approaches, global architectures, and continual experimentation. The goal is to maintain performance as load, data, and technologies evolve.

- **Democratize advanced technologies**

  - Use managed AI/ML services.
  - Offload workloads to DynamoDB or S3.
  - Use managed streaming instead of self-hosting Kafka.

- **Go global in minutes**

  - Use CloudFront for global caching.
  - Use Route 53 latency routing.
  - Deploy new Regions easily via IaC.

- **Use serverless architectures**

  - Build compute with Lambda.
  - Use SQS/SNS for messaging.
  - Use Aurora Serverless for autoscaling DB workloads.

- **Experiment more often**

  - Test new instance types quickly.
  - Prototype using managed services.
  - Spin up disposable test stacks.

- **Consider mechanical sympathy**

  - Select instance families aligned with workload.
  - Use EBS Provisioned IOPS when needed.
  - Use Graviton for CPU efficiency.

## 🔹Cost Optimization

The cost optimization pillar focuses on avoiding unnecessary cost and ensuring money is spent where it adds business value. It emphasizes governance, right-sizing, and selecting the optimal pricing model. The goal is to achieve maximum value per dollar spent.

- **Deliver business value at the lowest cost**

  - Use Spot, Savings Plans, Reserved Instances.
  - Use S3 lifecycle rules.
  - Choose cost-appropriate storage classes.

- **Define and enforce tags, account structure, metrics**

  - Tag resources for allocation.
  - Organize with AWS Organizations.
  - Use Budgets and Cost Explorer.

- **Share ownership and build a CCoE**

  - Teams monitor their own costs.
  - Conduct cost reviews.
  - Provide central best-practices guidance.

## 🔹Sustainability

This pillar focuses on minimizing the environmental impact of cloud workloads. It encourages choosing energy-efficient services, maximizing utilization, and optimizing resource consumption. The goal is to reduce both direct and indirect environmental footprint.

- **Understand your impact**

  - Use AWS sustainability dashboards.
  - Identify high-emission workloads.
  - Track compute/storage consumption trends.

- **Establish sustainability goals**

  - Define utilization KPIs.
  - Commit to greener services/instances.
  - Measure progress regularly.

- **Maximize utilization**

  - Consolidate workloads.
  - Use autoscaling.
  - Favor serverless where appropriate.

- **Adopt newer efficient hardware/software**

  - Migrate to Graviton.
  - Use modern runtimes/SDKs.
  - Prefer energy-efficient instance families.

- **Use managed services**

  - Reduce footprint with Lambda, DynamoDB.
  - Use Intelligent-Tiering.
  - Depend on managed autoscaling.

- **Reduce downstream impact**

  - Use CloudFront caching.
  - Optimize file formats (Parquet/ORC).
  - Use event-driven processing.

### Pitfalls

- Confusing **multi-AZ** with **multi-Region** — only multi-Region is DR.
- Thinking **“serverless = reliability”** — it's performance efficiency unless context is DR/HA.
- Believing cost optimization = picking “the cheapest service.” AWS stresses **business value**.
- Assuming operational excellence = monitoring — it’s about _procedures, change management, and continuous improvement_.
- Mixing up identity (IAM) with network security — identity is always **Security pillar**.
- Choosing performance efficiency answers when the scenario is clearly about _resilience under failure_.

### Scenario Cues

- “Automate operations,” “reversible deployments,” “runbooks” → **Operational Excellence**
- “Least privilege,” “encryption,” “audit logs,” “WAF” → **Security**
- “Failover,” “multi-AZ,” “RTO/RPO,” “auto recovery” → **Reliability**
- “Choosing instance family,” “serverless,” “global user latency” → **Performance Efficiency**
- “Lifecycle rules,” “Savings Plans,” “governance,” “tagging” → **Cost Optimization**
- “Energy efficiency,” “Graviton,” “reduce resource usage” → **Sustainability**

### Exam Hints

- DynamoDB autoscaling: **performance efficiency**, not cost optimization.
- CloudFront is performance unless combined with WAF.
- TLS = always **Security**, even if it improves performance.
- “Deploy globally in minutes” = performance efficiency.
- “Stop guessing capacity” = reliability, unless tied to cost.

## 🧩 AWS Cloud Adoption Framework (CAF) {#aws-cloud-adoption-framework-caf}

The AWS CAF provides a structured way to evaluate and prepare an organization for cloud adoption. It organizes capabilities into six perspectives, each addressing different readiness needs. The exam focuses on recognizing the intention behind each perspective and identifying which one fits a given scenario.

### 🔹Business Perspective

This perspective ensures cloud adoption aligns with business goals and delivers measurable outcomes. It focuses on value realization, financial modeling, and prioritizing cloud initiatives based on business impact.

- Examples

  - The **CIO** defines KPIs (e.g., cost savings, deployment speed) to measure cloud adoption success.
  - The **finance team** creates TCO and ROI models comparing on-prem vs AWS.
  - The **executive steering committee** ranks workloads for migration based on business value.

### 🔹People Perspective

This perspective ensures that staff have the skills, roles, and organizational structure required for cloud success. It deals with training, cultural change, and preparing teams for cloud-native work.

- Examples

  - The **HR/training department** builds AWS learning paths and certification programs.
  - **Engineering managers** rewrite job descriptions to include cloud responsibilities.
  - A **Cloud Center of Excellence (CCoE)** runs workshops to shift culture toward cloud adoption.

### 🔹Governance Perspective

This perspective defines policies, controls, and financial management processes that guide cloud usage. It ensures accountability, compliance, and strategic alignment.

- Examples

  - The **cloud governance board** establishes tagging standards and budget controls.
  - The **compliance team** configures guardrails using AWS Organizations SCPs.
  - The **PMO** implements reporting processes to track cloud adoption progress.

### 🔹Platform Perspective

This perspective focuses on designing, building, and optimizing the technical foundation on AWS. It ensures the cloud environment is secure, scalable, and well-architected.

- Examples

  - The **cloud architecture team** designs the landing zone, VPC setup, and IAM structure.
  - **DevOps teams** build CI/CD pipelines for automated deployments.
  - **Solution architects** define modernization patterns like serverless or microservices.

### 🔹Security Perspective

This perspective ensures security practices, teams, and controls align to protect data and workloads during and after migration.

- Examples

  - The **security operations team** defines data protection requirements and encryption strategies.
  - **SecOps engineers** enable CloudTrail, GuardDuty, and Security Hub.
  - The **IAM team** enforces least-privilege access and implements identity federation.

### 🔹Operations Perspective

This perspective defines how workloads are run, monitored, and supported after migration. It emphasizes reliability, automation, and continuous improvement.

- Examples

  - The **operations/SRE team** builds dashboards using CloudWatch and X-Ray.
  - The **SRE team** writes incident response runbooks and manages the on-call process.
  - **Automation engineers** implement scaling, patching, and remediation workflows with Systems Manager.

### Pitfalls

- Treating migration as entirely technical — CAF includes business, people, and governance aspects.
- Confusing **Governance** with **Operations** — governance = policy; operations = day-to-day running.
- Assuming Security perspective only means encryption — it covers identity, detection, compliance, and risk.
- Ignoring People perspective — exams expect recognition that skills and culture matter.
- Thinking Platform perspective is just VPC/EC2 — it includes architecture, automation, and modernization.

### Scenario Identifiers

- “Business value, KPIs, ROI, TCO” → **Business**
- “Training, roles, skills, cultural shift” → **People**
- “Policies, controls, guardrails, budget ownership” → **Governance**
- “Landing zone, architecture, CI/CD, modernization patterns” → **Platform**
- “Identity, encryption, monitoring, compliance” → **Security**
- “Monitoring, runbooks, automation, operations after migration” → **Operations**

### Exam Tricks

- If the question is about **who owns decisions or policies**, the answer is **Governance**, not People or Business.
- If the scenario mentions **skills gaps**, “training,” or “role changes,” it is always **People**.
- If the question mentions **landing zones**, **multi-account setup**, or **infrastructure foundations**, the answer is **Platform**.
- If the prompt references **detecting threats** (e.g., GuardDuty), it falls under **Security**, not Operations.
- “Ongoing monitoring and response” → **Operations**, not Security, unless explicitly tied to risk.
- Questions about ROI or value realization never belong to Platform or Operations — always **Business**.
- Governance vs Security trick: **SCPs = Governance**, **IAM policies = Security**.

# 🚀 Adoption Strategies {#adoption-strategies}

### 🔹 Project

A small, focused cloud effort delivering one workload or outcome ---
quick wins, fast learning.

- Migrate a single internal app to EC2 to test cloud readiness.
- Build a lightweight serverless prototype for a new feature.

### 🔹 Foundation

Sets up the core environment, governance, and security required for
large-scale cloud adoption.

- Deploy a multi-account landing zone with Organizations and baseline IAM.
- Establish centralized logging, monitoring, and network architecture.

### 🔹 Migration

Moves many workloads or entire portfolios to AWS using repeatable
patterns.

- Rehost dozens of servers through Migration Hub and Application Migration Service.
- Migrate enterprise databases to RDS or Aurora during a data center exit.

### 🔹 Reinvention

Transformation using cloud-native services to innovate and modernize how
the business operates.

- Replace legacy jobs with event-driven Lambda pipelines.
- Build new digital products using AI/ML and microservices.

## 📦 The 7 Rs Migration Strategies {#the-7-rs-migration-strategies}

### 🔹 Retire

Remove applications no longer providing value.

- A regional sales reporting tool is shut down after adoption of a
  unified global analytics platform.
- An FTP server used by one vendor is removed when the vendor migrates
  to API-based file exchange.
- A nightly batch job is eliminated when real-time event streaming
  replaces its function.

### 🔹 Retain

Keep systems on-premises due to constraints or dependencies.

- A manufacturing control system must remain on-site due to
  sub-millisecond latency requirements.
- A legacy mainframe stays on-prem during a multi‑year modernization
  effort.
- A hardware‑tied licensing server remains on‑prem because its
  physical dongle cannot be virtualized.

### 🔹 Rehost ("Lift and Shift")

Move workloads to AWS with no code changes.

- 150 VMs are lifted into EC2 due to a data center lease expiring in
  90 days.
- A Java monolith is migrated unchanged to EC2 due to limited
  modernization time.
- A retail website is moved as‑is to EC2 to leverage Auto Scaling
  before peak season.

### 🔹 Relocate

Move entire VMware estates to VMware Cloud on AWS.

- A bank moves its vSphere clusters to VMware Cloud on AWS to avoid
  rewriting dozens of applications.
- A company scales storage capacity by relocating all VMware workloads
  instead of redesigning apps.
- A merger consolidates infrastructure rapidly by relocating both
  companies' VMware environments.

### 🔹 Repurchase ("Drop and Shop")

Replace existing software with SaaS.

- A custom CRM is replaced by Salesforce.
- A self‑hosted Jira/Confluence setup becomes Atlassian Cloud.
- An on‑prem Exchange server is replaced with Microsoft 365.

### 🔹 Replatform ("Lift, Tinker, and Shift")

Make small optimizations during migration.

- A SQL Server instance moves to RDS to eliminate patching while
  keeping schema.
- An app is containerized and run on ECS Fargate without redesign.
- Static assets are moved to S3 + CloudFront during migration for
  performance gains.

### 🔹 Refactor / Re‑architect

Redesign applications to use cloud‑native features.

- A monolith becomes microservices on Lambda, SQS, and DynamoDB.
- A nightly ETL is replaced with Kinesis + Lambda for real‑time
  processing.
- A legacy CMS is rebuilt as a serverless API backend.

### Exam Hints

- Retire → "no longer needed," "duplicate," "deprecated."
- Retain → "cannot migrate yet," "latency/hardware constraint,"
  "compliance barrier."
- Rehost → "as‑is," "lift and shift," "minimal changes," "deadline
  pressure."
- Relocate → "VMware Cloud on AWS," "keep vCenter/vMotion," "move
  entire VMware environment."
- Repurchase → "replace with SaaS," "drop and shop," "move to
  Salesforce/Jira Cloud."
- Replatform → "minor improvements," "move DB to RDS," "containerize,"
  "small optimizations."
- Refactor → "rewrite," "modernize," "microservices," "serverless,"
  "architectural transformation."

## 💰 Cloud Economics and Total Cost of Ownership {#cloud-economics-and-total-cost-of-ownership}

TCO represents the full cost of running workloads across their
lifecycle. Cloud economics focuses on how AWS shifts organizations from
large upfront investments (CAPEX) to ongoing operational expenses
(OPEX), while lowering labor and licensing overhead.

### 🔸 Operational Expenses (OPEX)

Ongoing, usage-based costs for running workloads.

- Monthly EC2, S3, and CloudWatch charges based on consumption.
- Higher EC2 usage during peak seasons, lower in off-season.
- No power, cooling, or physical data center maintenance costs.

### 🔸 Capital Expenses (CAPEX)

Upfront infrastructure investments replaced or avoided through cloud
migration.

- Avoiding the purchase of 60 physical servers by moving to EC2.
- Skipping a SAN upgrade by adopting S3/EFS.
- Canceling construction of an additional on-prem server room.

### 🔸 Labor Costs

Human effort required to operate and maintain infrastructure.

- Sysadmins no longer patch OS instances after switching to RDS and
  Lambda.
- Ops teams stop swapping failed hardware because AWS handles it.
  Engineers transition from managing VMware clusters to cloud
  automation.

### 🔸 Software Licensing Costs

Licenses for operating systems, databases, and middleware.

- Eliminating SQL Server licensing by moving to Aurora PostgreSQL.
- Reducing Windows Server licensing by switching EC2 instances to
  Amazon Linux.
- Replacing a costly monitoring suite with CloudWatch and X-Ray.

### Pitfalls & Confusions

- Cloud reduces **CAPEX**, but **OPEX can increase** without
  optimization.
- Managed services reduce labor but may increase direct service cost.
- Lift-and-shift migrations often retain expensive licenses.
- Underutilized cloud resources still waste money.
- Reserved Instances and Savings Plans reduce **OPEX**, not CAPEX.

### Exam Hints

- **OPEX** → pay-as-you-go, variable usage, monthly billing.
- **CAPEX** → upfront server purchases, hardware refresh cycles, data
  center buildouts.
- **Labor** → patching, maintenance, operational overhead; automation
  reduces these costs.
- **Licensing** → OS/DB licensing impact; managed services reduce
  proprietary license requirements.
- **General economics** → CAPEX→OPEX shift, elasticity, right-sizing,
  avoid over-provisioning, reduce undifferentiated heavy lifting.

## 🛡️ Shared Responsibility Model {#shared-responsibility-model}

AWS secures the **cloud itself**, while customers secure **what they run
in the cloud**. The split depends on whether a service is unmanaged,
managed, or fully managed.

### 🔸 Customer-Only Responsibilities

You control configuration, data, access, and application security.

- The security team rotates IAM access keys and enforces MFA --- AWS
  never handles identity governance.
- The DevOps team configures S3 bucket policies and encryption; AWS
  does not block insecure policies automatically.
- A product team classifies and secures sensitive data in DynamoDB ---
  AWS never inspects customer data.

### 🔸 AWS-Only Responsibilities

AWS controls and operates the foundational infrastructure.

- AWS maintains physical data centers, including access controls,
  power, and cooling.
- AWS patches and upgrades the hypervisor and underlying compute
  hardware.
- AWS ensures regional networking, availability zone isolation, and S3
  durability replication.

### 🔹Unmanaged Services (Customer controls more)

Examples: EC2, EBS, VPC

- Ops teams patch the OS on EC2 because AWS only manages the hardware
  beneath it.
- Database administrators install, configure, and update databases
  running on EC2.
- Network engineers configure routing tables, security groups, and
  NACLs.

### 🔹Managed Services (Shared control)

Examples: RDS, ECS, EKS

- AWS patches the RDS database engine, while DB teams manage schema
  design and query timing.
- AWS maintains the ECS control plane, while developers configure IAM
  roles, task definitions, and autoscaling.
- AWS runs the EKS Kubernetes control plane, but platform engineers
  secure worker nodes and pod-level policies.

### 🔹Fully Managed Services (AWS controls most)

Examples: Lambda, DynamoDB, S3, CloudFront

- AWS manages all server infrastructure for Lambda; developers focus
  only on code and IAM permissions.
- AWS handles DynamoDB scaling, patching, and replication, while teams
  design tables and access controls.
- AWS ensures S3 durability and replication; customers configure
  bucket policies, encryption, and lifecycle rules.

### Common Confusions & Pitfalls

- Customers secure data, IAM, network rules, and app-layer security
  --- AWS never does this for you.
- AWS patches OS **only** for fully managed runtimes (Lambda,
  Fargate), _not_ for EC2.
- Misconfigured S3 buckets or IAM policies are always customer faults.
- Logging is not automatic --- customers must enable CloudTrail, VPC
  Flow Logs, and application logs.
- Encryption responsibilities are shared: customers must turn it on
  and configure keys; AWS manages the infrastructure.
- Physical security, hardware maintenance, regional isolation, and
  backbone networking are always AWS responsibilities.

### Exam Hints

- Customer → IAM, access control, data security, EC2 OS patching,
  network configuration, enable encryption.
- Customer → enable CloudTrail, configure bucket policies, manage
  app-layer vulnerabilities.
- AWS → physical facilities, hardware, hypervisor, global networking,
  AZ/Region design.
- Unmanaged → EC2/EBS/VPC → customer manages OS, runtime, patches,
  network rules.
- Managed → RDS/EKS/ECS → AWS manages platform; customer manages
  configuration and data.
- Fully managed → Lambda/S3/DynamoDB → AWS handles servers; customer
  handles data and permissions.
- "Public S3 bucket," "overly permissive IAM," "unencrypted data" →
  customer issue.
- "Hardware failure," "data center outage," "facility access" → AWS
  responsibility.
- "Who enables logging?" → customer.
- "Who secures customer data?" → customer.
- "AWS automatically manages..." → usually refers to fully managed
  services.

## 🔐 AWS Access Management Capabilities {#aws-access-management-capabilities}

AWS access management defines how identities authenticate and what
actions they can perform. Key concepts include the account root user,
IAM users, groups, roles, and policies.

### AWS Accounts & the Root User

The AWS account is the primary isolation and billing boundary. The root
user has unrestricted permissions and should be used only when a task
cannot be delegated.

- Only the root user can close the AWS account or change the support
  plan.
- A security engineer must use the root identity to enable S3 MFA
  Delete.
- Payment methods and tax documents can only be modified by the root
  user.

### Users, Groups, and Roles

IAM identities define how people and services authenticate and what they
can access.

#### Users

Long-term identities intended for humans or legacy systems that still
rely on long-lived credentials.

- Characteristics
  - Have passwords or access keys.
  - Should rarely have permissions attached directly.
  - Protected with MFA.
- Examples
  - A developer logs in to the console using their IAM user for daily
    tasks.
  - A support engineer uses an IAM user to troubleshoot CloudWatch logs.
  - A legacy build pipeline temporarily uses an IAM user's access keys
    until refactored to use roles.

### Groups

Used to organize users and assign permissions collectively.

- Characteristics
  - Groups cannot contain other groups.
  - Users can belong to multiple groups.
  - Policies should be attached at the group level.
- Examples
  - A "Developers" group grants access to dev resources like S3 buckets
    and Lambda test functions.
  - A "ReadOnlyAuditors" group provides global read-only access for
    internal audits.
  - A "NetworkAdmins" group manages VPC security groups and route
    tables.

### Roles

Intended for temporary access by AWS services, applications, or external
identities. Roles have no long-term credentials.

- Characteristics
  - Provide short-lived credentials through STS.
  - Assumed by services, applications, or users who need temporary
    privilege elevation.
  - Used for automation, cross-account access, and federation.
- Examples
  - A Lambda function assumes an execution role to read items from
    DynamoDB.
  - An EC2 instance uses its instance role to upload logs to S3 without
    storing access keys.
  - A developer from one AWS account assumes a role in another account
    to deploy resources there.

### Managed and Customer-Managed Policies

Policies define permissions using JSON statements. AWS-managed policies
provide convenience; customer-managed policies enable precise control.

#### Examples

- A team attaches the AWS-managed "AmazonEC2ReadOnlyAccess" policy for
  quick onboarding.
- A security engineer writes a customer-managed policy allowing access
  only to specific S3 prefixes.
- A compliance team sets a permissions boundary to ensure developers
  cannot escalate themselves.

### IAM Policy Simulator

A tool for testing how policies behave before applying them.

#### Examples

- A developer tests whether a Lambda execution role can write logs to
  CloudWatch.
- A security engineer verifies a deny condition blocks access to a
  restricted S3 bucket.
- A DevOps team checks that a cross-account deployment role has all
  required permissions.

### Common Confusions & Pitfalls

- Users are for humans; roles are for temporary access by services or
  external identities.
- Groups are for permission assignment, not authentication.
- The root user cannot be restricted and should not be used for daily
  operations.
- Explicit deny overrides allow.
- EC2 instance roles provide temporary credentials; keys should never
  be stored on the server.
- Cross-account access requires assuming a role, not sharing IAM user
  credentials.
- IAM permissions do not grant network access; SGs and NACLs are
  separate layers.

### Exam Hints

- Root user → close account, modify payment, enable MFA Delete.
- Users → long-term identities; secured with MFA; avoid inline user
  policies.
- Groups → simplify permission management; cannot nest.
- Roles → temporary credentials; used by AWS services and
  cross-account access.
- AWS-managed policies → broad and convenient.
- Customer-managed policies → tailored to least privilege.
- Policy Simulator → test effective permissions.
- Least privilege → almost always the correct exam answer.
- "Temporary access required" or "service needs permissions" → use a
  role.
- Federation or SSO → external users assume a role, no IAM users
  created.

## 💸 AWS Pricing Models & Cost Optimization {#aws-pricing-models--cost-optimization}

AWS offers several pricing models arranged by cost efficiency. Choosing
the right model is a major part of cost optimization and depends on
workload predictability, tolerance for interruptions, tenancy
requirements, and licensing constraints.

### 🔹Spot Instances

Deeply discounted spare EC2 capacity with interruption risk. Best for
fault-tolerant or flexible workloads.

- A video transcoding system uses Spot since jobs can retry
  automatically if an instance is reclaimed.
- A data science team runs large Monte Carlo simulations overnight
  using Spot Fleet for massive savings.
- A CI/CD system uses Spot for non-critical build agents, falling back
  to on-demand when Spot is unavailable.

### 🔹Savings Plans

Commit to a consistent hourly spend for 1--3 years. Most flexible
discount model, applies to EC2, Fargate, and Lambda.

- A platform engineering team moves to Savings Plans while gradually
  shifting workloads from EC2 to Lambda.
- A product team with diverse compute workloads (ECS + Lambda) uses a
  3-year Compute Savings Plan for predictable costs.
- A company migrating instance families frequently chooses Savings
  Plans to avoid managing multiple RI types.

### 🔹Reserved Instances (Standard RIs)

1--3 year commitment for high discounts. Ideal for steady, predictable
workloads.

- A billing service running 24/7 is covered with 3-year Standard RIs
  to cut predictable compute cost.
- A database team commits to RIs for stable RRDS instances that won't
  change size in the foreseeable future.
- A corporate intranet server that runs continuously is placed under
  RIs for long-term savings.

### 🔹Convertible Reserved Instances

Similar to RIs but allow changing instance families, OS, or tenancy.
Slightly smaller discount than Standard RIs.

- A modernization team switches EC2 instance families during
  refactoring without losing Reserved Instance benefits.
- A company changes from Windows to Linux AMIs and updates the RI type
  instead of buying new reservations.
- An analytics system scaling vertically over time upgrades instance
  sizes using Convertible RIs.

### 🔹Zonal Reserved Instances

RIs tied to a specific Availability Zone. Provide both cost savings and
a capacity reservation.

- A financial trading application with strict AZ affinity secures
  capacity during market peaks.
- A healthcare system guarantees AZ availability before planned
  seasonal patient load increases.
- A company with strict compliance runs a legacy app in a fixed AZ and
  uses Zonal RIs to lock in both price and capacity.

### 🔹On-Demand Instances

Pay by the hour or second with no commitment. Best for short-lived or
unpredictable workloads.

- A developer tests new architectures in EC2 without any commitments.
- A sudden traffic surge uses on-demand instances until Auto Scaling
  brings online additional capacity.
- A data migration team runs temporary EC2 instances for a multi-day
  transfer job.

### 🔹Capacity Reservations

Guarantee capacity in a specific AZ with no long-term commitment. Still
billed at on-demand rates unless paired with RIs or Savings Plans.

- A ticketing platform reserves capacity ahead of a major event to
  guarantee availability.
- A financial application reserves capacity during quarter-end batch
  processing windows.
- A research lab running GPU workloads reserves capacity for scheduled
  simulation days.

### 🔹Dedicated Instances

Run workloads on hardware isolated to a single customer. Provides
tenancy isolation but not licensing benefits.

- A regulated company isolates workloads for compliance, avoiding
  shared tenancy.
- A latency-sensitive system avoids noisy neighbors by using dedicated
  tenancy.
- A customer uses dedicated instances to meet internal security
  policies requiring isolated tenancy.

### 🔹Dedicated Hosts

Physical servers fully allocated to you. Required for certain BYOL
licensing and compliance scenarios. The most expensive option.

- A company brings SQL Server Enterprise licenses that require
  tracking cores/sockets.
- A security audit demands host-level visibility unavailable on
  standard EC2.
- A legacy enterprise application with strict hardware-binding
  licensing runs on a Dedicated Host.

### Common Confusions & Pitfalls

- RIs and Savings Plans lower cost, but do not guarantee capacity.
  Only Zonal RIs and Capacity Reservations do.
- Spot Instances can be interrupted --- exam questions often hide
  "fault-tolerant" or "can retry jobs" as clues.
- Savings Plans apply across compute types; RIs are tied to instance
  families or platforms unless convertible.
- Dedicated Instances are not the same as Dedicated Hosts --- only
  Dedicated Hosts provide license tracking and host visibility.
- Capacity Reservations without a discount still incur on-demand cost
  unless paired with RIs or Savings Plans.
- The cheapest option is not always the correct answer; exam scenarios
  care about predictability and compliance.
- Zonal RIs = discount + reservation; Standard RIs = discount only.

### Exam Hints

- "Workload can tolerate interruptions" → Spot
- "Commitment but want flexibility across compute services" → Savings
  Plans
- "Steady-state, predictable workload" → Standard RIs
- "Need to change instance family or OS later" → Convertible RIs
- "Need AZ capacity guarantee" → Zonal RI or Capacity Reservation
- "Unpredictable short-term workloads" → On-Demand
- "Hardware isolation required" → Dedicated Instances
- "Compliance or licensing visibility needed" → Dedicated Hosts
- "Transitioning architectures (EC2 → Lambda)" → Savings Plans
- "Company prefers cost predictability" → RIs or Savings Plans
- "GPU or burst workloads intermittently scheduled" → Capacity
  Reservations

## 🆘 AWS Technical Resources & Support Options {#aws-technical-resources--support-options}

AWS provides multiple support tiers tailored to different business and
technical needs. Exams often test response-time differences, 24/7
availability, and TAM access.

### 🔸Basic Support

Included for free with all AWS accounts; provides no technical
troubleshooting.

- Characteristics
  - No access to AWS support engineers
  - Billing & account support only
  - "Best effort" responses
  - Trusted Advisor core checks only
- Examples
  - A hobbyist hosts a personal website with Basic support.
  - A startup in prototyping relies solely on documentation and forums.
  - A student or training environment uses Basic support with no urgency
    requirements.

### 🔸Developer Support

Designed for early development work; **business-hours** support only.

- Characteristics
  - Email access to support engineers during business hours
  - Response within 24 business hours
  - No production-critical guidance
  - Trusted Advisor core checks
- Examples
  - A small team building an MVP sends occasional architecture
    questions.
  - A developer debugging Lambda issues files non-urgent tickets.
  - A testing environment where downtime is not critical uses Developer
    support.

### 🔸Business Support

Suitable for production workloads needing 24/7 coverage.

- Characteristics
  - **24/7** access to Cloud Support Engineers
  - 1-hour response for production system down
  - Full Trusted Advisor checks
  - Access to IEM (pay-per-use)
  - Architectural guidance for production systems
- Examples
  - An e-commerce store running production requires immediate help if
    checkout fails.
  - A SaaS platform preparing for a major release requests IEM
    assistance.
  - A company with global users relies on 24/7 support for outages.

### 🔸Enterprise On-Ramp Support

A transitional tier for organizations scaling toward mission-critical
operations.

- Characteristics
  - **24/7** access with faster responses than Business
  - Access to a pool of TAMs (not dedicated)
  - Proactive architectural and operational reviews
  - Discounted IEM
  - Ideal for organizations growing but not yet requiring full
    Enterprise support
- Examples
  - A healthcare startup expects rapid scaling and wants proactive
    guidance.
  - A fintech company running customer workloads wants stronger
    escalation paths.
  - A mid-sized SaaS moving toward regulatory compliance seeks early TAM
    engagement.

### 🔸Enterprise Support

Top-tier support for mission-critical, large-scale AWS environments.

- Characteristics
  - **Dedicated Technical Account Manager (TAM)**
  - 15-minute response for critical issues
  - IEM included
  - Concierge billing + governance support
  - Proactive architectural reviews (e.g., Well-Architected)
  - Best for highly regulated or global mission-critical workloads
- Examples
  - A global retailer prepares Black Friday with TAM-led scaling
    reviews.
  - A bank operating 24/7 transactional systems requires near-immediate
    escalation.
  - A healthcare organization undergoing compliance audits depends on
    Enterprise architectural guidance.

### Common Confusions & Pitfalls

- Developer = **business-hours only**.
- Only Business, Enterprise On-Ramp, Enterprise = **24/7 support**.
- Only Enterprise = **Dedicated TAM**.
- Trusted Advisor full checks start at Business tier.
- Developer and Basic support levels do NOT include architectural
  guidance.
- IEM included only with Enterprise; On-Ramp gets discounts; Business
  pays per event.
- "Production workload" strongly implies Business or higher.

### Exam Hints

- "Needs 24/7 support for production" → Business
- "Needs a dedicated TAM" → Enterprise
- "Proactive guidance but not full Enterprise cost" → Enterprise
  On-Ramp
- "Office hours support is fine" → Developer
- "No cost support" → Basic
- "Preparing for major event launch" → Business + IEM or Enterprise
- "Highly regulated, mission-critical" → Enterprise
