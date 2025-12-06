
# Management & Governance

## AWS CloudFormation
### 1. Definition
CloudFormation automates provisioning of AWS resources using templates written in JSON/YAML.

### 2. Use-Cases
- Infrastructure as Code  
- Multi-account stack deployments  
- Reproducible environments  

### 3. Additional Info
- Supports StackSets for org-wide deployment  

### 4. Limitations
- Complex templates can be hard to maintain  

### 5. Details
- **Characteristics:** IaC; declarative  
- **Capabilities:** Drift detection; change sets  
- **Pricing Model:** Free (pay for resources)  
- **Security/IAM:** IAM roles; stack policies  

### 6. Confusable
- CDK (higher-level IaC), Terraform (3rd party)  

### 7. Exam Notes
- “Infrastructure as Code,” “StackSets” → CloudFormation  


## AWS Systems Manager
### 1. Definition
Systems Manager provides unified operational management for compute resources, including patching, automation, inventory, and secure remote access.

### 2. Use-Cases
- Patch orchestration  
- Remote command execution  
- Parameter & secret storage  
- Hybrid fleet management  

### 3. Additional Info
- Includes SSM Agent, Automation, Session Manager, Parameter Store  

### 4. Limitations
- Requires SSM agent for EC2/on-prem  

### 5. Details
- **Characteristics:** Ops management suite  
- **Capabilities:** Automation; Run Command; Patch Manager  
- **Pricing Model:** Free for many features  
- **Security/IAM:** IAM; KMS; secure tunnels  

### 6. Confusable
- OpsWorks, Config, CloudWatch  

### 7. Exam Notes
- “Run Command,” “Session Manager (no SSH)” → SSM  


## Amazon CloudWatch
### 1. Definition
CloudWatch provides monitoring, logging, metrics, alarms, dashboards, and event-driven automation.

### 2. Use-Cases
- Collecting application and infrastructure metrics  
- Log analytics  
- Triggering alarms or automated responses  

### 3. Additional Info
- Features: Logs, Metrics, Events, Alarms, Dashboards  

### 4. Limitations
- Log ingestion/storage costs  

### 5. Details
- **Characteristics:** Observability; regional  
- **Capabilities:** Metrics; Logs Insights; alarms  
- **Pricing Model:** Per-metric, log ingestion, dashboards  
- **Security/IAM:** IAM; KMS  

### 6. Confusable
- X-Ray (tracing), OpenSearch logs  

### 7. Exam Notes
- “Metrics + Logs + Alarms” → CloudWatch  


## AWS CloudTrail
### 1. Definition
CloudTrail records API calls and account activity for auditing and governance.

### 2. Use-Cases
- Compliance  
- Security investigations  
- Monitoring API-level activity  

### 3. Additional Info
- Event history stored for 90 days by default  

### 4. Limitations
- Not real-time monitoring (CloudWatch Events is)  

### 5. Details
- **Characteristics:** API logging; multi-region  
- **Capabilities:** Trails; insights; event history  
- **Pricing Model:** Per-event for org trails  
- **Security/IAM:** IAM; KMS  

### 6. Confusable
- CloudWatch Events (real-time), Config (resources only)  

### 7. Exam Notes
- “API calls,” “audit logs,” “governance” → CloudTrail  


## AWS Organizations
### 1. Definition
Organizations manages multi-account environments with centralized governance, billing, and SCP-based permission boundaries.

### 2. Use-Cases
- Multi-account management  
- Central billing  
- Guardrails via SCPs  

### 3. Additional Info
- Organizational units (OUs) group accounts  

### 4. Limitations
- SCPs do not grant permissions (only restrict)  

### 5. Details
- **Characteristics:** Multi-account governance  
- **Capabilities:** SCPs; consolidated billing  
- **Pricing Model:** Free  
- **Security/IAM:** IAM; SCPs  

### 6. Confusable
- Control Tower (turnkey setup), IAM for roles  

### 7. Exam Notes
- “SCPs restrict, do not grant permissions” → Organizations  

## AWS Control Tower
### 1. Definition
AWS Control Tower automates the setup of a secure, compliant multi-account AWS environment using best-practice blueprints.

### 2. Use-Cases
- Setting up a governed landing zone  
- Automating account creation with guardrails  
- Multi-account standardization  

### 3. Additional Info
- Uses Organizations, Config, CloudTrail, IAM  

### 4. Limitations
- Opinionated architecture; limited customization  

### 5. Details
- **Characteristics:** Turnkey landing zone  
- **Capabilities:** Guardrails; account factory  
- **Pricing Model:** Free (resources billed)  
- **Security/IAM:** SCPs; IAM; Config rules  

### 6. Confusable
- Organizations (manual setup), Service Catalog  

### 7. Exam Notes
- “Landing zone,” “guardrails” → Control Tower  


## AWS Service Catalog
### 1. Definition
Service Catalog allows organizations to curate and manage approved IT products for deployment.

### 2. Use-Cases
- Standardizing resource stacks  
- Self-service provisioning  
- Enforcing compliance  

### 3. Additional Info
- Supports product portfolios and constraints  

### 4. Limitations
- Requires CloudFormation templates  

### 5. Details
- **Characteristics:** Product governance  
- **Capabilities:** Portfolios; versioning  
- **Pricing Model:** Free  
- **Security/IAM:** IAM; constraints  

### 6. Confusable
- Marketplace (3rd-party apps), CloudFormation  

### 7. Exam Notes
- “Approved products,” “governed self-service” → Service Catalog  


## AWS License Manager
### 1. Definition
License Manager tracks and governs software licenses across AWS and on-prem systems.

### 2. Use-Cases
- Tracking commercial software use  
- Enforcing license rules  
- Managing BYOL  

### 3. Additional Info
- Integrates with EC2, RDS, and on-prem VMware  

### 4. Limitations
- Only tracks supported license types  

### 5. Details
- **Characteristics:** License governance  
- **Capabilities:** Rules; tracking; enforcement  
- **Pricing Model:** Free  
- **Security/IAM:** IAM  

### 6. Confusable
- Cost Explorer (billing), Organizations  

### 7. Exam Notes
- “Track licenses,” “BYOL governance” → License Manager  


## AWS Health Dashboard
### 1. Definition
AWS Health Dashboard provides account-specific and global insights into service status, outages, and maintenance events.

### 2. Use-Cases
- Monitoring AWS service impact  
- Tracking operational issues  
- Viewing maintenance notifications  

### 3. Additional Info
- Two views: Account Health & Service Health  

### 4. Limitations
- Not real-time alerting (use CloudWatch Events)  

### 5. Details
- **Characteristics:** AWS service health visibility  
- **Capabilities:** Outage alerts; maintenance notices  
- **Pricing Model:** Free  
- **Security/IAM:** IAM  

### 6. Confusable
- CloudWatch (monitoring), Personal Health Dashboard  

### 7. Exam Notes
- “Service disruptions,” “maintenance events” → Health Dashboard  


## AWS Trusted Advisor
### 1. Definition
Trusted Advisor provides automated best-practice checks covering cost optimization, performance, security, and resilience.

### 2. Use-Cases
- Cost-saving recommendations  
- Security best-practice scanning  
- Performance guidance  

### 3. Additional Info
- Full checks require Business/Enterprise support  

### 4. Limitations
- Limited checks for Basic/Developer support plans  

### 5. Details
- **Characteristics:** Best-practice advisor  
- **Capabilities:** Recommendations; dashboards  
- **Pricing Model:** Included with support tier  
- **Security/IAM:** IAM  

### 6. Confusable
- Compute Optimizer (performance only), Security Hub  

### 7. Exam Notes
- “Cost optimization,” “support plan required” → Trusted Advisor  

## AWS Pricing Calculator
### 1. Definition
The AWS Pricing Calculator estimates AWS costs by modeling services, configurations, and usage patterns.

### 2. Use-Cases
- Cost estimation for new workloads  
- Comparing architectural alternatives  

### 3. Additional Info
- Browser-based; exportable estimates  

### 4. Limitations
- Estimates only—actual billing varies  

### 5. Details
- **Characteristics:** Cost modeling tool  
- **Capabilities:** Multi-service estimates; templates  
- **Pricing Model:** Free  
- **Security/IAM:** Public tool; optional save via account  

### 6. Confusable
- Cost Explorer (actual spend)  

### 7. Exam Notes
- “Estimate costs before deployment” → Pricing Calculator  


## AWS Data Lifecycle Manager
### 1. Definition
Automates creation, retention, and deletion of EBS snapshots and EBS-backed AMIs.

### 2. Use-Cases
- Scheduled snapshots  
- Snapshot lifecycle governance  
- Automated AMI rotation  

### 3. Additional Info
- Works with EBS & EC2 AMIs only  

### 4. Limitations
- Not multi-service (use AWS Backup for broader scope)  

### 5. Details
- **Characteristics:** Snapshot automation  
- **Capabilities:** Policies; retention; tagging  
- **Pricing Model:** Free  
- **Security/IAM:** IAM; KMS for snapshots  

### 6. Confusable
- AWS Backup (multi-service), CloudWatch Events  

### 7. Exam Notes
- “Automate EBS snapshots” → DLM  


## AWS Billing and Cost Management Dashboard
### 1. Definition
Central location for viewing AWS costs, invoices, payment methods, and billing alerts.

### 2. Use-Cases
- Tracking monthly spend  
- Managing billing preferences  

### 3. Additional Info
- Includes cost allocation tags and payment settings  

### 4. Limitations
- Not an analytics tool (use Cost Explorer)  

### 5. Details
- **Characteristics:** Billing overview  
- **Capabilities:** Invoices; budgets; alerts  
- **Pricing Model:** Free  
- **Security/IAM:** IAM billing permissions  

### 6. Confusable
- Cost Explorer, Budgets  

### 7. Exam Notes
- “Billing details,” “invoices,” “payment methods” → Billing Dashboard  


## AWS Budgets
### 1. Definition
AWS Budgets sets custom cost and usage thresholds and sends alerts when exceeding or approaching limits.

### 2. Use-Cases
- Monthly cost control  
- Forecast-based alerts  
- Enforcing guardrails for teams  

### 3. Additional Info
- Supports cost, usage, RI/Savings Plan coverage  

### 4. Limitations
- Notifications only; no automatic remediation without Lambda  

### 5. Details
- **Characteristics:** Budgeting & alerting  
- **Capabilities:** Alerts; forecasting; reports  
- **Pricing Model:** Per-budget  
- **Security/IAM:** IAM  

### 6. Confusable
- Cost Explorer (analysis), Billing Dashboard  

### 7. Exam Notes
- “Alert when cost exceeds threshold” → Budgets  


## AWS Cost Explorer
### 1. Definition
Cost Explorer analyzes AWS spending, usage patterns, and cost trends.

### 2. Use-Cases
- Monthly cost analysis  
- RI and Savings Plan recommendations  

### 3. Additional Info
- Provides cost forecasting  

### 4. Limitations
- Limited long-term data granularity  

### 5. Details
- **Characteristics:** Visualization + analysis tool  
- **Capabilities:** Filtering; trends; recommendations  
- **Pricing Model:** Free (detailed data may incur cost)  
- **Security/IAM:** IAM  

### 6. Confusable
- Budgets (alerts), CUR (raw data)  

### 7. Exam Notes
- “Analyze past spend,” “RI recommendations” → Cost Explorer  


## AWS Cost & Usage Report (CUR)
### 1. Definition
CUR delivers the most detailed AWS cost and usage data, stored in S3 for analytics.

### 2. Use-Cases
- Deep cost auditing  
- Custom chargeback or showback  
- Feeding BI tools for Cost FinOps  

### 3. Additional Info
- Can integrate with Athena, Redshift, QuickSight  

### 4. Limitations
- Large files; requires external tooling  

### 5. Details
- **Characteristics:** Raw cost data; hourly granularity  
- **Capabilities:** Line-item details; multi-service analytics  
- **Pricing Model:** Free (S3 storage billed)  
- **Security/IAM:** IAM; encryption  

### 6. Confusable
- Cost Explorer (UI summaries), Budgets  

### 7. Exam Notes
- “Most detailed cost data,” “S3-exported” → CUR  


## AWS Billing Conductor
### 1. Definition
Billing Conductor enables custom chargeback and cost distribution across teams or organizational units.

### 2. Use-Cases
- Custom internal cost allocation  
- Pricing adjustments for business units  

### 3. Additional Info
- Integrates with CUR  

### 4. Limitations
- No impact on AWS invoice—internal only  

### 5. Details
- **Characteristics:** Internal billing governance  
- **Capabilities:** Pricing rules; billing groups  
- **Pricing Model:** Per-billing record  
- **Security/IAM:** IAM  

### 6. Confusable
- Cost Explorer (analysis), CUR (raw data)  

### 7. Exam Notes
- “Internal chargeback,” “billing groups” → Billing Conductor  
