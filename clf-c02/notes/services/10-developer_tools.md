
# Developer Tools

## AWS Cloud9
### 1. Definition
Cloud9 is a cloud-based IDE with collaborative editing, terminal access, and direct AWS integration.

### 2. Use-Cases
- Cloud-native development  
- Collaborative coding  
- Developing without local setup  

### 3. Additional Info
- Preconfigured environment with AWS CLI/SDKs  

### 4. Limitations
- Requires internet; not ideal for large local workloads  

### 5. Details
- **Characteristics:** Browser IDE  
- **Capabilities:** Terminal; debugger; EC2/SSH environments  
- **Pricing Model:** EC2/storage costs  
- **Security/IAM:** IAM; VPC access controls  

### 6. Confusable
- CloudShell (CLI-only)  

### 7. Exam Notes
- “Cloud IDE,” “collaboration” → Cloud9  


## AWS CloudShell
### 1. Definition
CloudShell provides a browser-based Linux shell with AWS CLI preinstalled.

### 2. Use-Cases
- Running CLI commands without local setup  
- Scripts and quick automation tasks  

### 3. Additional Info
- Persistent storage included  

### 4. Limitations
- Not a full IDE  

### 5. Details
- **Characteristics:** Browser shell  
- **Capabilities:** CLI; SDKs; persistent home directory  
- **Pricing Model:** Free  
- **Security/IAM:** IAM  

### 6. Confusable
- Cloud9 (IDE), AWS CLI locally  

### 7. Exam Notes
- “Ready-to-use CLI in browser” → CloudShell  


## AWS CodeCommit
### 1. Definition
CodeCommit is a fully managed Git repository service.

### 2. Use-Cases
- Source control for teams  
- Storing code securely in AWS  

### 3. Additional Info
- Integrates with CodePipeline  

### 4. Limitations
- Lacks some advanced Git hosting features  

### 5. Details
- **Characteristics:** Managed Git  
- **Capabilities:** Branching; pull requests; triggers  
- **Pricing Model:** Per-active-user  
- **Security/IAM:** IAM; KMS  

### 6. Confusable
- GitHub, GitLab  

### 7. Exam Notes
- “Private Git repos on AWS” → CodeCommit  


## AWS CodeBuild
### 1. Definition
CodeBuild is a fully managed CI service that compiles, tests, and builds artifacts.

### 2. Use-Cases
- Continuous integration  
- Building and testing code  
- Containerized build workflows  

### 3. Additional Info
- Supports buildspec.yml  

### 4. Limitations
- Pricing per build-minute  

### 5. Details
- **Characteristics:** Managed CI  
- **Capabilities:** Parallel builds; cache; reports  
- **Pricing Model:** Build-time minutes  
- **Security/IAM:** IAM; VPC builds  

### 6. Confusable
- CodePipeline (orchestration), CodeDeploy  

### 7. Exam Notes
- “CI builds,” “buildspec” → CodeBuild  


## AWS CodePipeline
### 1. Definition
CodePipeline automates CI/CD workflows using stages and actions.

### 2. Use-Cases
- Orchestrating builds, tests, deploys  
- Multi-environment pipelines  

### 3. Additional Info
- Integrates with CodeBuild, CodeDeploy, third-party tools  

### 4. Limitations
- Limited branching support  

### 5. Details
- **Characteristics:** CI/CD orchestration  
- **Capabilities:** Stages; approvals; automation  
- **Pricing Model:** Per-pipeline  
- **Security/IAM:** IAM  

### 6. Confusable
- Step Functions (general orchestration)  

### 7. Exam Notes
- “Pipeline orchestration,” “automate deployments” → CodePipeline  


## AWS CodeDeploy
### 1. Definition
CodeDeploy automates deployments to EC2, on-prem servers, and Lambda.

### 2. Use-Cases
- Rolling deployments  
- Blue/green deployments  
- Hybrid environment deployments  

### 3. Additional Info
- Supports AppSpec files  

### 4. Limitations
- Requires agents for EC2/on-prem  

### 5. Details
- **Characteristics:** Deployment automation  
- **Capabilities:** Blue/green; canary; hooks  
- **Pricing Model:** Free (EC2/Lambda usage billed)  
- **Security/IAM:** IAM; instance profiles  

### 6. Confusable
- CodePipeline (pipeline), Elastic Beanstalk  

### 7. Exam Notes
- “Blue/green deployments,” “AppSpec” → CodeDeploy  


## AWS CodeStar
### 1. Definition
CodeStar provides unified project dashboards and setup for CI/CD and Code* services.

### 2. Use-Cases
- Rapid project onboarding  
- Unified developer dashboards  

### 3. Additional Info
- Integrates IAM roles for teams  

### 4. Limitations
- Not widely adopted; limited customization  

### 5. Details
- **Characteristics:** Project management wrapper  
- **Capabilities:** Templates; dashboards  
- **Pricing Model:** Free  
- **Security/IAM:** IAM project roles  

### 6. Confusable
- CodePipeline (CI/CD), Cloud9  

### 7. Exam Notes
- “Unified developer dashboard” → CodeStar  


## AWS CodeArtifact
### 1. Definition
CodeArtifact is a managed artifact repository for package management (npm, Maven, PyPI, NuGet).

### 2. Use-Cases
- Storing software dependencies  
- Securing internal package distribution  

### 3. Additional Info
- Integrates with CI/CD tools  

### 4. Limitations
- Not a container registry (use ECR)  

### 5. Details
- **Characteristics:** Managed artifact repo  
- **Capabilities:** Package domains/repos; upstream caching  
- **Pricing Model:** Storage + data transfer  
- **Security/IAM:** IAM; KMS  

### 6. Confusable
- CodeCommit (source), ECR (container images)  

### 7. Exam Notes
- “Package repository,” “npm/Maven/PyPI” → CodeArtifact  


## AWS X-Ray
### 1. Definition
X-Ray traces distributed applications to diagnose performance issues and errors.

### 2. Use-Cases
- Distributed tracing  
- Root-cause analysis  
- Viewing service maps  

### 3. Additional Info
- Integrates with Lambda, ECS, API Gateway  

### 4. Limitations
- Requires instrumentation  

### 5. Details
- **Characteristics:** Tracing + observability  
- **Capabilities:** Segments; subsegments; sampling  
- **Pricing Model:** Trace storage and retrieval  
- **Security/IAM:** IAM; KMS  

### 6. Confusable
- CloudWatch (metrics/logs), OpenSearch  

### 7. Exam Notes
- “Distributed tracing,” “service map” → X-Ray  


## AWS AppConfig
### 1. Definition
AppConfig manages, validates, and deploys application configuration safely.

### 2. Use-Cases
- Feature flags  
- Dynamic configuration updates  
- Safely deploying config without redeploying apps  

### 3. Additional Info
- Part of Systems Manager  

### 4. Limitations
- Not a secrets service  

### 5. Details
- **Characteristics:** Config release management  
- **Capabilities:** Validation; controlled rollout  
- **Pricing Model:** Per-configuration deployment  
- **Security/IAM:** IAM; KMS  

### 6. Confusable
- Parameter Store, Secrets Manager  

### 7. Exam Notes
- “Feature flags,” “safe config rollouts” → AppConfig  
