
# Security, Identity & Compliance

## AWS Identity and Access Management (IAM)
### 1. Definition
IAM enables secure access control across AWS by managing users, roles, policies, and permissions at fine granularity.

### 2. Use-Cases
- Controlling access to AWS resources  
- Federating identities via SAML/OIDC  
- Least-privilege enforcement  

### 3. Additional Info
- Policies: identity-based, resource-based  
- Features: roles, STS, permission boundaries  

### 4. Limitations
- No built-in SSO (use Identity Center)  

### 5. Details
- **Characteristics:** Centralized authZ/authN; global  
- **Capabilities:** Roles; MFA; policy evaluation  
- **Pricing Model:** Free  
- **Security/IAM:** IAM itself  

### 6. Confusable Services
- Identity Center, Cognito  

### 7. Exam Notes
- IAM is free; roles used for AWS service access  

## IAM Policy Simulator
### 1. Definition
Tool for testing and debugging IAM policies.

### 2. Use-Cases
- Validating permissions  
- Troubleshooting denied access  

### 3. Additional Info
- Web console + API  

### 4. Limitations
- Simulation ≠ execution context  

### 5. Details
- **Characteristics:** Testing utility  
- **Capabilities:** Policy evaluation  
- **Pricing Model:** Free  
- **Security/IAM:** IAM  

### 6. Confusable Services
- Access Analyzer  

### 7. Exam Notes
- Used to test IAM permissions offline  

## IAM Identity Center
### 1. Definition
Centralized SSO for workforce authentication across AWS accounts and applications.

### 2. Use-Cases
- Multi-account SSO  
- Workforce identity management  

### 3. Additional Info
- Integrates with AD, Okta, others  

### 4. Limitations
- Not for customer identities  

### 5. Details
- **Characteristics:** Org-wide identity; regional  
- **Capabilities:** SSO; IdP integration  
- **Pricing Model:** Free  
- **Security/IAM:** IAM; MFA  

### 6. Confusable Services
- Cognito (app users), IAM  

### 7. Exam Notes
- "Workforce SSO" = Identity Center  

## AWS Key Management Service (KMS)
### 1. Definition
Managed encryption key service supporting symmetric and asymmetric keys.

### 2. Use-Cases
- Encrypting data at rest  
- Envelope encryption  
- HSM-backed security  

### 3. Additional Info
- Supports CMKs; automatic rotation  

### 4. Limitations
- Throughput limits  

### 5. Details
- **Characteristics:** FIPS-compliant; regional  
- **Capabilities:** Key creation; grants; rotation  
- **Pricing Model:** Key-hour + request charges  
- **Security/IAM:** IAM + key policies  

### 6. Confusable Services
- CloudHSM  

### 7. Exam Notes
- Key policies govern access  

## AWS Secrets Manager
### 1. Definition
Stores, rotates, and retrieves application secrets such as passwords and API keys.

### 2. Use-Cases
- Secret rotation  
- Secure retrieval in apps  

### 3. Additional Info
- Automatic rotation via Lambda  

### 4. Limitations
- Costlier than SSM Parameter Store  

### 5. Details
- **Characteristics:** Secret storage; encrypted  
- **Capabilities:** Rotation; versioning  
- **Pricing Model:** Per-secret + API calls  
- **Security/IAM:** KMS encryption  

### 6. Confusable Services
- SSM Parameter Store  

### 7. Exam Notes
- Automatic rotation = Secrets Manager  

## AWS Shield
### 1. Definition
AWS Shield protects applications from DDoS attacks using always-on detection and automatic inline mitigations.

### 2. Use-Cases
- Protecting public-facing apps  
- Reducing downtime from network floods  

### 3. Additional Info
- Standard included for free  

### 4. Limitations
- No advanced support without Shield Advanced  

### 5. Details
- **Characteristics:** Managed DDoS protection  
- **Capabilities:** Layer 3/4 detection  
- **Pricing Model:** Free  
- **Security/IAM:** Integrated with CloudFront/Route53  

### 6. Confusable
- WAF (filters traffic, not DDoS)  

### 7. Exam Notes
- “DDoS basic protection” → Shield Standard  


## AWS Shield Advanced
### 1. Definition
Enhanced DDoS protection with cost protection and advanced detection.

### 2. Use-Cases
- High-availability critical apps  
- Large enterprises needing rapid response  

### 3. Additional Info
- Includes 24/7 DDoS Response Team  

### 4. Limitations
- Subscription required  

### 5. Details
- **Characteristics:** Premium DDoS; global  
- **Capabilities:** Advanced L3–L7 metrics  
- **Pricing Model:** Monthly subscription  
- **Security/IAM:** IAM; integration with WAF  

### 6. Confusable
- Standard Shield  

### 7. Exam Notes
- SLA + cost protection → Advanced  


## AWS WAF
### 1. Definition
Web application firewall filtering malicious HTTP/S traffic at layer 7.

### 2. Use-Cases
- Blocking SQLi/XSS  
- Rate limiting  
- Protecting APIs and web apps  

### 3. Additional Info
- Works with ALB, API Gateway, CloudFront  

### 4. Limitations
- Requires designed rule sets  

### 5. Details
- **Characteristics:** Layer 7 filtering  
- **Capabilities:** Rules; managed rule groups  
- **Pricing Model:** Per-rule + request fees  
- **Security/IAM:** IAM; logging  

### 6. Confusable
- Shield (DDoS), SG/NACL (L3/4)  

### 7. Exam Notes
- SQLi/XSS mitigation → WAF  


## Amazon Inspector
### 1. Definition
Automated vulnerability management service for EC2, Lambda, and container images.

### 2. Use-Cases
- CVE detection  
- Runtime security posture  
- Container image scanning  

### 3. Additional Info
- Integrates with ECR  

### 4. Limitations
- Requires IAM setup for scanning  

### 5. Details
- **Characteristics:** Continuous scanning  
- **Capabilities:** CVE checks; risk scoring  
- **Pricing Model:** Per-resource scan  
- **Security/IAM:** IAM; KMS  

### 6. Confusable
- GuardDuty (threat detection), Security Hub  

### 7. Exam Notes
- “Vulnerability scanning” → Inspector  


## Amazon GuardDuty
### 1. Definition
Intelligent threat detection using ML and threat intel sources.

### 2. Use-Cases
- Detect account compromise  
- Detect anomalous traffic  

### 3. Additional Info
- Monitors CloudTrail, VPC Flow Logs, DNS logs  

### 4. Limitations
- Read-only detection; no automatic remediation  

### 5. Details
- **Characteristics:** Threat detection; regional  
- **Capabilities:** Anomaly detection; intel feeds  
- **Pricing Model:** Usage-based  
- **Security/IAM:** IAM; encrypted logs  

### 6. Confusable
- Inspector (vulnerabilities), Macie (data classification)  

### 7. Exam Notes
- “Anomalous API calls,” “threat intel” → GuardDuty  

## Amazon Macie
### 1. Definition
Amazon Macie uses ML to discover, classify, and protect sensitive data in Amazon S3.

### 2. Use-Cases
- Detecting PII in S3  
- Data security compliance  
- Monitoring S3 for sensitive content  

### 3. Additional Info
- Integrates with EventBridge for alerts  

### 4. Limitations
- Only scans S3 (not databases or other stores)  

### 5. Details
- **Characteristics:** ML-based data classification  
- **Capabilities:** PII detection; automated discovery  
- **Pricing Model:** Per-GB inspected + object inventory  
- **Security/IAM:** IAM; KMS for encrypted buckets  

### 6. Confusable
- GuardDuty (threats), Inspector (vulnerabilities)  

### 7. Exam Notes
- “PII in S3,” “sensitive data discovery” → Macie  


## AWS Security Hub
### 1. Definition
Security Hub aggregates and standardizes findings from AWS security services into a unified dashboard.

### 2. Use-Cases
- Central security posture management  
- Compliance frameworks (CIS, PCI)  
- Consolidated threat and vulnerability view  

### 3. Additional Info
- Integrates with GuardDuty, Inspector, Macie, Firewall Manager  

### 4. Limitations
- Does not perform detection on its own  

### 5. Details
- **Characteristics:** Aggregator; multi-account  
- **Capabilities:** Findings normalization; insights; compliance scoring  
- **Pricing Model:** Per-finding and check  
- **Security/IAM:** IAM; cross-account roles  

### 6. Confusable
- GuardDuty (detection), Config (compliance)  

### 7. Exam Notes
- “Centralize findings,” “compliance score” → Security Hub  


## Amazon Cognito
### 1. Definition
User identity and authentication service for apps, supporting sign-up, sign-in, and access control.

### 2. Use-Cases
- Customer identity management  
- OAuth/OIDC/SAML app authentication  
- Token-based API access  

### 3. Additional Info
- Features: User Pools + Identity Pools  

### 4. Limitations
- Not enterprise SSO (Identity Center)  

### 5. Details
- **Characteristics:** CIAM; scalable auth  
- **Capabilities:** Hosted UI; MFA; custom auth flows  
- **Pricing Model:** MAU-based  
- **Security/IAM:** IAM roles for Identity Pools  

### 6. Confusable
- Identity Center (workforce), IAM (infrastructure auth)  

### 7. Exam Notes
- “User Pools = authentication,” “Identity Pools = AWS access”  


## AWS Certificate Manager (ACM)
### 1. Definition
ACM issues, manages, and renews TLS/SSL certificates for use with AWS services.

### 2. Use-Cases
- Enabling HTTPS on ALB, CloudFront, API Gateway  
- Automatic certificate renewal  

### 3. Additional Info
- Supports public and private certificates  

### 4. Limitations
- Cannot export public certs (only private CA certs)  

### 5. Details
- **Characteristics:** Managed PKI; global for CloudFront  
- **Capabilities:** Auto-renewal; DNS validation  
- **Pricing Model:** Public certs free; ACM PCA billed  
- **Security/IAM:** IAM; ACM PCA permissions  

### 6. Confusable
- IAM Server Certificates (legacy), Route 53 (DNS only)  

### 7. Exam Notes
- “Free certs,” “automatic renewal” → ACM  


## AWS Artifact
### 1. Definition
Portal providing on-demand access to AWS compliance reports and agreements.

### 2. Use-Cases
- Downloading SOC/PCI/ISO reports  
- Managing compliance agreements  

### 3. Additional Info
- Free access; no request needed from AWS  

### 4. Limitations
- Read-only; no automation APIs  

### 5. Details
- **Characteristics:** Compliance documentation hub  
- **Capabilities:** Reports; certifications; agreements  
- **Pricing Model:** Free  
- **Security/IAM:** IAM policies for access  

### 6. Confusable
- Audit Manager (automated evidence collection)  

### 7. Exam Notes
- “Compliance reports,” “AWS certifications” → Artifact  

## AWS Config
### 1. Definition
AWS Config records configuration changes of AWS resources and evaluates compliance against defined rules.

### 2. Use-Cases
- Continuous compliance auditing  
- Tracking configuration drift  
- Recording resource changes for governance  

### 3. Additional Info
- Supports AWS-managed and custom Config Rules  

### 4. Limitations
- Does not prevent changes (detective, not preventive)  

### 5. Details
- **Characteristics:** Compliance + configuration history  
- **Capabilities:** Rules; remediation; timeline views  
- **Pricing Model:** Per-rule evaluation + configuration items  
- **Security/IAM:** IAM; KMS for logs  

### 6. Confusable
- CloudTrail (API logging), Security Hub (findings)  

### 7. Exam Notes
- “Configuration history,” “compliance rules” → Config  


## AWS Audit Manager
### 1. Definition
Audit Manager automates collection of compliance evidence to simplify audits.

### 2. Use-Cases
- Preparing SOC/PCI/ISO audits  
- Automating manual evidence gathering  

### 3. Additional Info
- Frameworks include CIS, NIST, PCI  

### 4. Limitations
- Evidence volume may increase storage costs  

### 5. Details
- **Characteristics:** Compliance automation  
- **Capabilities:** Evidence collection; assessment workflows  
- **Pricing Model:** Per-assessment + evidence storage  
- **Security/IAM:** IAM; encryption  

### 6. Confusable
- Artifact (documents only), Config (resource compliance)  

### 7. Exam Notes
- “Automated compliance evidence” → Audit Manager  


## IAM Access Analyzer
### 1. Definition
IAM Access Analyzer identifies unintended public or cross-account access in policies.

### 2. Use-Cases
- Detecting overly permissive resource policies  
- Governance for multi-account setups  

### 3. Additional Info
- Uses automated reasoning engine  

### 4. Limitations
- Findings require manual remediation  

### 5. Details
- **Characteristics:** Access analyzer; policy review  
- **Capabilities:** Public access detection; cross-account alerts  
- **Pricing Model:** Free  
- **Security/IAM:** IAM-managed  

### 6. Confusable
- Policy Simulator (tests policies manually)  

### 7. Exam Notes
- “Detect unintended public or cross-account access” → Access Analyzer  
