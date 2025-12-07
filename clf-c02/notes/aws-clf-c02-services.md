# AWS Services Mega Document

## Table of Contents

- [Compute](#01-compute)
- [Networking](#02-networking)
- [Storage](#03-storage)
- [Databases](#04-databases)
- [Ai Ml](#05-ai_ml)
- [Analytics](#06-analytics)
- [Security](#07-security)
- [Management](#08-management)
- [App Integration](#09-app_integration)
- [Developer Tools](#10-developer_tools)
- [Frontend Mobile](#11-frontend_mobile)
- [Business Apps](#12-business_apps)
- [End User Computing](#13-end_user_computing)
- [Iot](#14-iot)
- [Migration Transfer](#15-migration_transfer)
- [Marketplace Partners](#16-marketplace_partners)

---

## 01-compute


## Amazon EC2
Amazon Elastic Compute Cloud (EC2) provides resizable compute capacity in the cloud.

### 1. Definition
Amazon EC2 is a web service that provides secure, resizable compute capacity using virtual machines called instances. It offers a wide selection of instance types optimized for compute, memory, storage, and GPU needs. EC2 gives deep OS-level control, customizable networking, and flexible purchasing models such as On-Demand, Reserved, Spot, and Savings Plans. It integrates closely with EBS for block storage, VPC for networking, IAM for security, and Auto Scaling for elasticity.

### 2. Use-Cases
- Lift-and-shift of on-prem servers
- Long-running workloads requiring OS-level customization
- High-performance computing, GPU workloads, enterprise applications

### 3. Additional Info
- Purchasing models: On-Demand, Reserved Instances, Spot Instances, Savings Plans
- Instance types: General Purpose, Compute Optimized, Memory Optimized, Storage Optimized, Accelerated Computing

### 4. Limitations
- Requires OS and patch management
- Not serverless; scaling must be configured

### 5. Details
- **Characteristics**
  - Type: Virtual machine compute
  - Mode: Customer-managed OS, AWS-managed hardware
  - Performance: Depends on instance type; enhanced networking available
  - Durability/HA: AZ-specific; multi-AZ via Auto Scaling
  - Scope: Regional (instances run in specific AZs)
- **Capabilities**
  - Full OS access, custom AMIs
  - Flexible networking (ENIs, SGs, VPC)
  - Multiple purchasing models
  - Integration with EBS, SSM, Auto Scaling, ELB
- **Pricing Model**
  - Per-second or per-hour instance cost; varies by type, OS, region, model
- **Security / IAM**
  - IAM instance profiles, SGs, NACLs, encrypted EBS, SSM access

### 6. Confusable Services
- AWS Lambda: Event-based, serverless, short-lived compute
- AWS Fargate: Serverless containers, not VMs
- Amazon Lightsail: Simpler VPS alternative for small apps
- AWS Batch: Batch scheduler using EC2 or Fargate
- Elastic Beanstalk: PaaS wrapper around EC2

### 7. Exam Notes
- OS-level control → choose EC2
- Cost optimization questions often involve Spot/Reserved/Savings Plans
- EC2 does NOT automatically fail over between AZs
- SGs = stateful; NACLs = stateless

## Amazon EC2 Auto Scaling
Automatically adjusts the number of Amazon EC2 instances to maintain application performance and optimize cost.

### 1. Definition
Amazon EC2 Auto Scaling automatically launches or terminates EC2 instances based on demand. It uses Auto Scaling Groups (ASGs), launch templates, scaling policies, and health checks to maintain desired capacity and availability. It integrates with CloudWatch metrics, Elastic Load Balancing, and multiple AZs for resilience.

### 2. Use-Cases
- Applications with fluctuating traffic patterns  
- Ensuring minimum and maximum capacity levels  
- Maintaining high availability across multiple AZs  

### 3. Additional Info
- Scaling Types: Target tracking, step scaling, simple scaling, scheduled scaling  
- Core Concepts: ASGs, launch templates, desired/min/max capacity  

### 4. Limitations
- Only works with EC2 instances  
- Requires careful configuration to avoid scaling oscillations  

### 5. Details
- **Characteristics**
  - Type: Automated capacity management for EC2
  - Mode: Metric-driven or schedule-based scaling
  - Performance: Responds to CloudWatch metrics
  - Durability/HA: Multi-AZ placement; automatic replacement of unhealthy instances
  - Scope: Regional
- **Capabilities**
  - Maintain desired EC2 instance count
  - Replace unhealthy instances automatically
  - Scale based on CPU, ALB request count, custom metrics
- **Pricing Model**
  - No cost for the scaling service; pay for EC2, ELB, and CloudWatch usage
- **Security / IAM**
  - IAM roles for ASG operations, instance profiles; SGs/NACLs control access

### 6. Confusable Services
- AWS Auto Scaling: Larger umbrella that manages scaling for ECS, DynamoDB, etc.  
- Lambda scaling: Handles concurrency automatically, not EC2 instances.  
- Application Auto Scaling: Scales services other than EC2.

### 7. Exam Notes
- Keywords: “Maintain desired capacity,” “scale EC2 instances,” “replace unhealthy instances.”  
- Use target tracking for simple, metric-based scaling.  
- Multi-AZ HA requires ASG spanning multiple subnets.

## Elastic Load Balancing (ELB)
Distributes incoming traffic across multiple targets to improve application availability, scalability, and fault tolerance.

### 1. Definition
Elastic Load Balancing automatically distributes incoming application or network traffic across multiple targets—such as EC2 instances, IP addresses, or containers—within one or more Availability Zones. It provides health checks, automatic failover, and multiple load balancer types: Application (ALB), Network (NLB), and Gateway (GLB), as well as the legacy Classic Load Balancer.

### 2. Use-Cases
- Distributing HTTP/HTTPS traffic across web servers  
- Offloading TLS/SSL termination  
- Providing a single entry point for scalable applications  
- High-throughput, low-latency network traffic routing (NLB)

### 3. Additional Info
- Load Balancer Types:  
  - **ALB** → Layer 7, routing by path/host, WebSockets  
  - **NLB** → Layer 4, ultra‑low latency, static IPs  
  - **GWLB** → For firewalls and security appliances  
  - **Classic LB** → Legacy  
- Integrates with Auto Scaling, ECS, EKS, and Lambda (via ALB)

### 4. Limitations
- Not a global traffic manager (use Route 53 for global routing)  
- Classic Load Balancer is deprecated for new designs  

### 5. Details
- **Characteristics**
  - Type: Managed load balancing service
  - Mode: Fully managed, scales automatically
  - Performance: High throughput; NLB supports millions of requests per second
  - Durability/HA: Multi-AZ distributed nodes
  - Scope: Regional
- **Capabilities**
  - Health checks and failover  
  - HTTPS termination (ALB/NLB)  
  - Routing rules, listener rules, WebSockets (ALB)  
- **Pricing Model**
  - Charged per Load Balancer-hour + LCU (ALB/NLB) + data processing  
- **Security / IAM**
  - Security groups (ALB), IAM for certificate management, integration with ACM and WAF

### 6. Confusable Services
- **Amazon Route 53:** DNS routing, not load balancing within a Region.  
- **AWS Global Accelerator:** Improves global client performance using Anycast; not a load balancer.  
- **API Gateway:** For API management, authentication, transformations; not a general load balancer.

### 7. Exam Notes
- ALB = path/host routing, HTTP/HTTPS, WebSockets.  
- NLB = extreme performance, TCP/UDP, static IPs.  
- ELB + Auto Scaling = high availability and elasticity.

## AWS Lambda
Serverless compute service that runs code in response to events without provisioning or managing servers.

### 1. Definition
AWS Lambda lets you run code by uploading functions and setting triggers from AWS services or external events. It automatically provisions compute, scales based on concurrency, manages execution environments, and charges only for compute time consumed. Lambda integrates with S3, API Gateway, DynamoDB Streams, EventBridge, Kinesis, and many other services.

### 2. Use-Cases
- Event-driven processing for S3 uploads, DynamoDB Streams, Kinesis events  
- Backend APIs when paired with API Gateway  
- Scheduled tasks without servers  
- Lightweight ETL and data transformations  

### 3. Additional Info
- Supports multiple runtimes: Node.js, Python, Java, Go, .NET, Ruby + custom runtimes  
- Triggers: S3, SNS, SQS, API Gateway, EventBridge, DynamoDB Streams, Kinesis, CloudWatch  

### 4. Limitations
- Max execution time per function (timeout limit)  
- Stateless; persistent storage requires external services (S3, DynamoDB, etc.)  
- Cold starts may introduce latency  

### 5. Details
- **Characteristics**
  - Type: Serverless function compute  
  - Mode: Event-driven, fully managed  
  - Performance: Auto-scales concurrency; cold starts possible  
  - Durability/HA: Highly available across multiple AZs  
  - Scope: Regional  
- **Capabilities**
  - Run code in response to events or schedules  
  - Integrate widely across AWS  
  - Support layers, environment variables, versions/aliases  
- **Pricing Model**
  - Pay per request + per GB-second of compute time  
  - Optional charges for provisioned concurrency  
- **Security / IAM**
  - IAM execution roles, VPC access, resource-based policies for triggers  

### 6. Confusable Services
- **Fargate:** Runs containers; Lambda runs functions.  
- **EC2:** Full servers for long-running workloads; Lambda for short event-based tasks.  
- **Step Functions:** Orchestrates Lambda functions; not compute itself.  

### 7. Exam Notes
- Keywords: “run code without servers,” “event-driven,” “pay only for compute time.”  
- Common pairing: API Gateway + Lambda = serverless API.  
- S3 upload triggers, DynamoDB/Kinesis stream processing often indicate Lambda.

## AWS Fargate
Serverless compute engine for containers that runs tasks and pods without provisioning or managing EC2 instances.

### 1. Definition
AWS Fargate is a serverless compute engine for running containers using Amazon ECS or Amazon EKS. It eliminates the need to provision, scale, or manage EC2 instances. You specify CPU and memory requirements per task/pod, and Fargate launches and scales the workloads automatically while managing the underlying infrastructure.

### 2. Use-Cases
- Running microservices in containers without managing servers  
- Spiky or unpredictable workloads needing automatic scaling  
- Secure isolation of containers without shared EC2 infrastructure  

### 3. Additional Info
- Works with ECS (tasks) and EKS (pods)  
- Resource model: vCPU + memory per task/pod  
- Integrates with ALB/NLB, CloudWatch, IAM, VPC networking  

### 4. Limitations
- Less control over underlying infrastructure than EC2-backed clusters  
- May cost more at high scale compared to optimized EC2 clusters  

### 5. Details
- **Characteristics**
  - Type: Serverless container compute  
  - Mode: Managed execution of ECS tasks or EKS pods  
  - Performance: Automatic scaling without cluster capacity planning  
  - Durability/HA: Multi-AZ support through ECS/EKS configuration  
  - Scope: Regional  
- **Capabilities**
  - Run containers without EC2 provisioning  
  - Fine-grained task-level resource assignment  
  - Full VPC networking for each task/pod  
- **Pricing Model**
  - Pay per vCPU-second and GB-second for running tasks/pods  
- **Security / IAM**
  - IAM roles for tasks; SGs and VPC networking; strong isolation boundaries

### 6. Confusable Services
- **ECS/EKS on EC2:** More control but requires node management.  
- **Lambda:** Runs functions, not containers; Fargate is suitable for containerized applications.  
- **EC2:** Requires infrastructure management; Fargate removes that overhead.  

### 7. Exam Notes
- Keywords: “run containers without managing servers,” “serverless containers.”  
- Appears in questions involving ECS/EKS + no infrastructure management.  
- Great answer when containerization is required but ops overhead must be minimized.

## Amazon Elastic Container Service (Amazon ECS)
Highly scalable, AWS-native container orchestration service for deploying and managing Docker containers using EC2 or Fargate.

### 1. Definition
Amazon ECS is a fully managed container orchestration service that deploys, runs, and scales Docker containers on AWS. It supports two launch types: EC2-backed clusters for custom infrastructure control, and AWS Fargate for serverless container execution. ECS manages service scheduling, task placement, networking, logging, and integration with load balancers and IAM.

### 2. Use-Cases
- Running microservices architectures with Docker containers  
- Migrating existing containerized workloads to AWS  
- Batch or event-driven container workloads  
- Large-scale, distributed applications on EC2 or Fargate  

### 3. Additional Info
- Core Concepts: **Clusters**, **Tasks**, **Task Definitions**, **Services**  
- Launch Types: **EC2** (self-managed instances) or **Fargate** (fully managed)  
- Integrates with ALB/NLB, CloudWatch, IAM, ECR, Systems Manager  

### 4. Limitations
- ECS is AWS-specific; not built for multi-cloud portability like Kubernetes  
- Requires understanding task/service model and IAM permissions  

### 5. Details
- **Characteristics**
  - Type: Managed container orchestration  
  - Mode: ECS control plane + EC2 or Fargate compute  
  - Performance: Scales with number of containers and cluster resources  
  - Durability/HA: Multi-AZ capable with load balancers and Auto Scaling  
  - Scope: Regional  
- **Capabilities**
  - Run, scale, and manage containerized applications  
  - Integrated service discovery, auto scaling, deployment strategies  
  - Task-level IAM roles and CloudWatch monitoring  
- **Pricing Model**
  - ECS control plane is free; pay for EC2 or Fargate resources  
- **Security / IAM**
  - Task roles, execution roles, SGs, VPC networking, encryption options  

### 6. Confusable Services
- **Amazon EKS:** Kubernetes-based; ECS uses AWS-native APIs.  
- **AWS Fargate:** Compute engine; ECS is the orchestrator.  
- **EC2:** Hosts compute, but does not orchestrate containers.  

### 7. Exam Notes
- ECS is often the answer when AWS-native container orchestration is desired.  
- ECS + Fargate is common for fully managed container deployments.  
- ECS + EC2 provides more control but requires node management.  

## Amazon Elastic Kubernetes Service (Amazon EKS)
Fully managed Kubernetes control plane for running Kubernetes workloads at scale on AWS using EC2 or Fargate worker nodes.

### 1. Definition
Amazon EKS is a managed Kubernetes service that eliminates the need to install, operate, and maintain Kubernetes control planes. AWS manages the API servers, etcd database, and control plane availability across multiple AZs. You run Kubernetes worker nodes either on EC2 or AWS Fargate. EKS integrates deeply with AWS networking, IAM authentication, load balancers, CloudWatch, and ECR.

### 2. Use-Cases
- Running existing Kubernetes workloads on AWS  
- Organizations standardized on Kubernetes requiring managed control planes  
- Hybrid or multi-cloud strategies using portable Kubernetes APIs  
- Advanced microservices architectures requiring Kubernetes features  

### 3. Additional Info
- Worker Options: EC2 worker nodes or Fargate pods  
- EKS Anywhere + EKS Distro extend Kubernetes beyond AWS  
- Supports Kubernetes-native tooling (kubectl, Helm, operators)  

### 4. Limitations
- Kubernetes operational complexity still exists for workloads  
- More complex than ECS for simple deployments  
- Control plane billed per cluster  

### 5. Details
- **Characteristics**
  - Type: Managed Kubernetes control plane  
  - Mode: Customer-managed workers; AWS-managed control plane  
  - Performance: Highly available, auto-scaled control plane  
  - Durability/HA: Multi-AZ control plane with automatic failover  
  - Scope: Regional  
- **Capabilities**
  - Run standard Kubernetes workloads  
  - Integrate with VPC networking, IAM authentication, ALB/NLB ingress  
  - Support EKS add-ons, cluster autoscaling, service mesh tools  
- **Pricing Model**
  - Per-cluster fee + EC2 or Fargate costs for nodes/pods  
- **Security / IAM**
  - IAM authentication for Kubernetes API  
  - Security groups, network policies, service accounts (IRSA)  

### 6. Confusable Services
- **Amazon ECS:** Simpler AWS-native container orchestrator; not Kubernetes.  
- **AWS Fargate:** Runs containers; EKS is the orchestrator.  
- **EC2 Auto Scaling:** Scales servers, not Kubernetes workloads.  

### 7. Exam Notes
- If the question explicitly mentions “Kubernetes,” “kubectl,” “Helm,” or multi-cloud portability → EKS.  
- EKS control plane is fully managed by AWS; customers manage only nodes.  
- IRSA (IAM Roles for Service Accounts) often appears in security questions.  

## Amazon Elastic Container Registry (Amazon ECR)
Fully managed container image registry for securely storing, managing, and deploying Docker container images.

### 1. Definition
Amazon ECR is a managed container image registry that stores, manages, and retrieves Docker images. It integrates tightly with ECS, EKS, and AWS Fargate, making it easy to build CI/CD pipelines and container-based workloads. ECR supports private and public repositories, vulnerability scanning, lifecycle policies, and fine-grained access control via IAM.

### 2. Use-Cases
- Hosting container images for ECS/EKS/Fargate applications  
- Integrating image builds into CI/CD pipelines (CodeBuild, CodePipeline, GitHub Actions)  
- Enforcing security scanning and retention policies  
- Cross-account sharing of images  

### 3. Additional Info
- Supports OCI-compatible images  
- Lifecycle rules for pruning old or unused images  
- Image scanning for vulnerabilities (basic and enhanced)  

### 4. Limitations
- Stores only container images (not a general artifact store like CodeArtifact)  
- Regional service; images must be replicated manually for multi-region architectures  

### 5. Details
- **Characteristics**
  - Type: Managed container image registry  
  - Mode: Fully managed with high availability  
  - Performance: Optimized for low-latency pulls by ECS/EKS/Fargate  
  - Durability/HA: Multi-AZ storage  
  - Scope: Regional  
- **Capabilities**
  - Store, pull, and push Docker images  
  - Integrate with container orchestrators and build systems  
  - Enforce lifecycle management and vulnerability scanning  
- **Pricing Model**
  - Charged for storage + data transfer (pull/push)  
- **Security / IAM**
  - IAM permissions for pushing/pulling  
  - Encryption at rest (KMS optional)  
  - Private or public repositories  

### 6. Confusable Services
- **Docker Hub / GitHub Container Registry:** External registries; ECR is AWS-native with IAM integration.  
- **Amazon ECS/EKS:** Orchestrate containers; ECR stores images.  
- **AWS CodeArtifact:** General package repository, not container-focused.  

### 7. Exam Notes
- Phrases like “store and manage container images on AWS” → ECR.  
- CI/CD questions often include ECR + CodeBuild/CodePipeline.  
- IAM restrictions on image access are commonly tested.  

## AWS Batch
Fully managed batch computing service that dynamically provisions compute resources to run batch workloads at any scale.

### 1. Definition
AWS Batch is a managed service that runs batch computing workloads using EC2 instances or AWS Fargate without requiring you to manage compute scheduling or capacity. It evaluates job requirements, provisions compute automatically, manages queues and priorities, handles job retries, and integrates with container images via ECR.

### 2. Use-Cases
- Large-scale batch workloads such as simulations, analytics, rendering, or ETL  
- Processing large numbers of short-lived containerized jobs  
- Scientific workloads that require parallel processing  
- Spot instance–based cost optimization for compute-heavy tasks  

### 3. Additional Info
- Core Components: **Job queues**, **job definitions**, **compute environments**  
- Compute Options: On-Demand EC2, EC2 Spot, or Fargate  
- Logging via CloudWatch Logs  

### 4. Limitations
- Suited for batch, not real-time interactive workloads  
- Requires container-based jobs or packaged applications  

### 5. Details
- **Characteristics**
  - Type: Managed batch scheduler and compute orchestrator  
  - Mode: Uses EC2 or Fargate compute  
  - Performance: Scales automatically based on queue depth  
  - Durability/HA: Multi-AZ compute environments  
  - Scope: Regional  
- **Capabilities**
  - Automatic provisioning and scaling of compute resources  
  - Job queuing, priorities, dependencies, retries  
  - Integration with Spot Instances for cost savings  
- **Pricing Model**
  - No charge for Batch itself; pay for underlying EC2/Fargate resources  
- **Security / IAM**
  - IAM roles for jobs, compute environments, and container access  

### 6. Confusable Services
- **Lambda:** Event-driven, not designed for large, long-running batch workloads.  
- **ECS:** Container orchestration, but not a job scheduler with queues.  
- **EC2 Auto Scaling:** Scales servers, not batch jobs.  

### 7. Exam Notes
- Keywords: “batch,” “queue,” “large-scale processing,” “automatic provisioning.”  
- Spot Instances + AWS Batch = common cost optimization scenario.  
- Use Batch for scheduled or triggered batch jobs that need compute at scale.

## AWS Elastic Beanstalk
Fully managed Platform-as-a-Service (PaaS) for deploying and scaling web applications without managing underlying infrastructure.

### 1. Definition
AWS Elastic Beanstalk is a managed application deployment service that automates infrastructure provisioning, application deployment, load balancing, scaling, and monitoring. Developers upload application code (e.g., Java, .NET, Node.js, Python, Go, PHP, Ruby), and Beanstalk provisions the required resources such as EC2, Auto Scaling groups, security groups, and Elastic Load Balancers. Users can still access and customize the underlying infrastructure if desired.

### 2. Use-Cases
- Rapid deployment of web applications without deep AWS infrastructure knowledge  
- Teams wanting simplified deployment but optional access to EC2 instances  
- Traditional web applications using standard runtimes  
- Environments requiring automatic scaling and load balancing  

### 3. Additional Info
- Supports rolling, immutable, and blue/green deployment strategies  
- Environment types: Single-instance or load-balanced, Auto Scaling  
- Managed platform updates (patching managed by Beanstalk)  

### 4. Limitations
- Less flexible than building architecture directly with AWS services  
- Platform versioning may lag behind the latest runtime releases  
- Default configurations may need tuning for complex workloads  

### 5. Details
- **Characteristics**
  - Type: Managed PaaS for web applications  
  - Mode: Orchestrates EC2, ASG, ELB, RDS (optional), CloudWatch  
  - Performance: Based on underlying EC2 instance types  
  - Durability/HA: Multi-AZ support for load-balanced environments  
  - Scope: Regional  
- **Capabilities**
  - Automated application deployment and environment management  
  - Built-in scaling, load balancing, and health monitoring  
  - Full infrastructure visibility and optional customization  
- **Pricing Model**
  - No extra cost for Beanstalk; pay for underlying AWS resources  
- **Security / IAM**
  - IAM roles for Beanstalk service and EC2 instances  
  - Security groups, VPC integration, and optional HTTPS via ACM  

### 6. Confusable Services
- **AWS Amplify:** Geared toward full-stack mobile/web apps; Beanstalk is more backend/server-oriented.  
- **Lambda + API Gateway:** For fully serverless architectures; Beanstalk uses EC2.  
- **EC2 Auto Scaling + ELB:** Underpins Beanstalk but requires manual setup when used directly.  

### 7. Exam Notes
- Keywords: “deploy web application quickly,” “managed environment,” “no need to provision servers.”  
- Beanstalk is ideal when teams want simplicity but optional low-level control.  
- Load-balanced environments = multi-AZ HA automatically.

## Amazon Lightsail
Simplified virtual private server (VPS) service for small applications with predictable, bundled monthly pricing.

### 1. Definition
Amazon Lightsail provides easy-to-use virtual private servers, databases, storage, and networking designed for simple workloads. It offers preconfigured blueprints (WordPress, LAMP, Node.js, etc.), fixed monthly pricing bundles, and simplified management. Lightsail is ideal for developers, small businesses, and hobby projects that do not require the full flexibility of EC2 and VPC.

### 2. Use-Cases
- Hosting simple websites, blogs, and small business applications  
- Development and test environments  
- Migrating from traditional VPS hosting providers  
- Lightweight workloads needing predictable costs  

### 3. Additional Info
- Provides instances, containers, databases, load balancers, and DNS  
- Bundled pricing includes compute, SSD storage, and data transfer  
- Easy upgrades to full AWS VPC-based services  

### 4. Limitations
- Less flexible and scalable than EC2  
- Not intended for complex architectures or large-scale deployments  
- Limited networking customization compared to full VPC  

### 5. Details
- **Characteristics**
  - Type: Simplified VPS compute service  
  - Mode: Preconfigured bundles and blueprints  
  - Performance: Suitable for small to moderate workloads  
  - Durability/HA: Basic failover; not multi-AZ by default  
  - Scope: Regional  
- **Capabilities**
  - Quick provisioning of VPS instances with prebuilt stacks  
  - Managed databases, object storage, and DNS  
  - Static IPs and basic load balancing  
- **Pricing Model**
  - Flat monthly bundles based on instance size and data transfer  
- **Security / IAM**
  - Simplified security model; IAM used for account-level control  

### 6. Confusable Services
- **Amazon EC2:** More flexible and scalable, but more complex and not bundled.  
- **Elastic Beanstalk:** Managed application service built on EC2; Lightsail is simpler.  
- **AWS Amplify:** Focused on frontend/mobile apps and serverless backends.  

### 7. Exam Notes
- Keywords: “simple VPS,” “predictable pricing,” “quick deployment.”  
- Not for large-scale architectures; for simplicity and small projects.  
- Includes blueprints like WordPress and LAMP for rapid deployment.

## AWS Outposts
Brings native AWS infrastructure, services, APIs, and tools to on‑premises locations for a consistent hybrid cloud experience.

### 1. Definition
AWS Outposts is a fully managed service that delivers AWS-designed hardware racks or servers to customer data centers or edge locations. It allows you to run AWS compute, storage, and selected services locally while maintaining seamless integration with your AWS Region. Outposts enables low-latency workloads, data residency compliance, and hybrid architectures using the same APIs and tools as in AWS.

### 2. Use-Cases
- Low-latency applications requiring compute close to users or equipment  
- On-premises data processing due to regulatory, compliance, or residency needs  
- Hybrid migrations, modernizing on-prem apps using AWS services locally  
- Environments requiring consistent tooling across cloud and on-prem  

### 3. Additional Info
- Variants: **Outposts racks** (full-size) and **Outposts servers** (smaller form factor)  
- Requires reliable network connectivity to an AWS Region for full functionality  
- Supports AWS services like EC2, EBS, EKS, RDS (varies by configuration)  

### 4. Limitations
- Physical installation required; long procurement lead times  
- Not all AWS services are supported on Outposts  
- Connectivity to AWS Region is required for full management  

### 5. Details
- **Characteristics**
  - Type: Hybrid cloud infrastructure deployed on-premises  
  - Mode: AWS-managed hardware + Region-integrated control plane  
  - Performance: Low-latency on-prem execution  
  - Durability/HA: Depends on local rack redundancy and facility power  
  - Scope: Physical location tied to a specific AWS Region  
- **Capabilities**
  - Run AWS services locally with consistent APIs  
  - Integrate with VPC networking extended to on-prem  
  - Seamless hybrid operations with AWS tools and monitoring  
- **Pricing Model**
  - Typically based on hardware configuration and multi-year terms  
- **Security / IAM**
  - IAM, security groups, KMS encryption, and AWS networking apply  

### 6. Confusable Services
- **Local Zones:** AWS-operated infrastructure near populations; not customer premises.  
- **Wavelength Zones:** Edge compute in telecom networks for 5G latency use cases.  
- **Direct Connect:** Connectivity service, not compute infrastructure.  

### 7. Exam Notes
- Keywords: “AWS services on-premises,” “hybrid deployment,” “data residency.”  
- Outposts = AWS hardware shipped to your data center.  
- Ideal for hybrid workloads with consistent tooling across environments.

## Amazon API Gateway
Fully managed service for creating, securing, and scaling APIs, enabling applications to access backend services via REST, HTTP, or WebSocket endpoints.

### 1. Definition
Amazon API Gateway is a managed service for building and managing APIs at scale. It enables developers to create RESTful, HTTP, and WebSocket APIs that act as a “front door” to applications running on AWS Lambda, EC2, container services, or on-prem systems. API Gateway handles request routing, transformation, throttling, authentication, monitoring, caching, and versioning.

### 2. Use-Cases
- Building serverless APIs using Lambda  
- Exposing microservices or backend services securely  
- Creating real-time communication APIs using WebSockets  
- Enabling consistent access to legacy or on-prem services  

### 3. Additional Info
- API Types: **REST API**, **HTTP API**, **WebSocket API**  
- Supports throttling, request validation, stages, and caching  
- Integrates with IAM, Cognito, Lambda, VPC links, and CloudWatch  

### 4. Limitations
- REST APIs can be more expensive and complex than HTTP APIs  
- Cold starts in Lambda-backed APIs may affect latency  

### 5. Details
- **Characteristics**
  - Type: Managed API gateway and integration layer  
  - Mode: Works with serverless or server-based backends  
  - Performance: Highly scalable; caching improves latency  
  - Durability/HA: Multi-AZ highly available  
  - Scope: Regional or edge-optimized (via CloudFront)  
- **Capabilities**
  - Request/response transformation, validation, rate limiting  
  - Authentication via IAM, Cognito, Lambda authorizers  
  - API versioning, stages, and usage plans  
- **Pricing Model**
  - Pay per API call + optional cache capacity  
- **Security / IAM**
  - IAM permissions, Cognito authentication, API keys, Lambda authorizers  

### 6. Confusable Services
- **ALB:** Can route HTTP requests but lacks deep API features.  
- **Amazon AppSync:** GraphQL API service; API Gateway is REST/HTTP/WebSocket.  
- **CloudFront:** CDN, not an API manager.  

### 7. Exam Notes
- Key phrases: “serverless API,” “front door to backend services,” “authentication,” “throttling.”  
- HTTP APIs = cheaper, simpler alternative to REST APIs.  
- API Gateway + Lambda appears frequently in serverless application questions.


---

## 02-networking


# Networking & Content Delivery

## Amazon VPC
Amazon Virtual Private Cloud (VPC) provides logically isolated virtual networks in AWS with full control over IP addressing, routing, and security.

### 1. Definition
Amazon VPC enables you to create isolated virtual networks in AWS where you define IP ranges, subnets, route tables, gateways, and security boundaries. It forms the foundation for AWS networking, supporting segmentation, custom routing, and hybrid connectivity via VPN or Direct Connect.

### 2. Use-Cases
- Hosting applications in isolated network environments  
- Multi-tier architectures using public and private subnets  
- Hybrid connectivity with on-prem networks  

### 3. Additional Info
- Components: Subnets, route tables, Internet/NAT gateways, NACLs, security groups  
- IP Space: Customer-defined CIDR blocks  

### 4. Limitations
- CIDR ranges cannot shrink once defined  
- Requires careful routing/security configuration for connectivity  

### 5. Details
- **Characteristics**
  - Type: Virtual network environment  
  - Mode: Fully customer-defined networking  
  - Performance: High-speed internal network  
  - Durability/HA: Multi-AZ architecture via subnets  
  - Scope: Regional  
- **Capabilities**
  - Complete network configuration control  
  - Segmentation using subnets  
  - Hybrid connectivity with VPN/DX  
- **Pricing Model**
  - VPC itself is free; IGW, NAT, endpoints incur charges  
- **Security / IAM**
  - SGs (stateful), NACLs (stateless), IAM for resource access  

### 6. Confusable Services
- **AWS Transit Gateway:** Connects networks; VPC is the network.  
- **AWS PrivateLink:** Private service access, not general networking.  
- **Subnets:** Components within a VPC, not standalone networks.  

### 7. Exam Notes
- Public subnet = route to IGW  
- SGs = stateful; NACLs = stateless  
- VPC is Regional; subnets are AZ-scoped  

## Subnets (Public/Private)
Subnets divide a VPC into AZ-scoped network segments and determine internet accessibility based on routing.

### 1. Definition
Subnets are subdivisions of a VPC’s CIDR block. A subnet in a single AZ becomes **public** when its route table has a route to an Internet Gateway (IGW); it remains **private** when it does not. Subnets enforce application-tier separation and govern east–west and north–south traffic patterns.

### 2. Use-Cases
- Public web tier vs. private application/database tiers  
- AZ-based fault isolation  
- Controlling outbound and inbound connectivity  

### 3. Additional Info
- Public subnet → IGW route  
- Private subnet → no IGW route; outbound enabled via NAT  

### 4. Limitations
- Cannot span AZs  
- IP exhaustion if CIDR sized too small  

### 5. Details
- **Characteristics:** Network segment; AZ-scoped; high-throughput internal networking  
- **Capabilities:** Traffic segmentation; public/private tiering; NAT/IGW routing  
- **Pricing Model:** No charge for subnets; routing components may incur costs  
- **Security/IAM:** Works with SGs and NACLs  

### 6. Confusable Services
- NAT Gateway (outbound-only), Internet Gateway (public access), Route tables (control traffic)  

### 7. Exam Notes
- Public = IGW route; private = no IGW route  
- NAT enables outbound for private subnets  

## Internet Gateway
Enables VPC resources to access the public internet.

### 1. Definition
An Internet Gateway (IGW) is a scalable, redundant VPC component that supports public inbound/outbound traffic for resources in public subnets.

### 2. Use-Cases
- Public-facing applications  
- Outbound internet access for public subnets  

### 3. Additional Info
- Must attach to a VPC  
- Operates with route tables  

### 4. Limitations
- Private subnets require NAT for outbound access  

### 5. Details
- **Characteristics:** Internet connectivity; redundant; regional  
- **Capabilities:** Public routing; inbound/outbound flows  
- **Pricing Model:** No IGW cost; data transfer billed  
- **Security/IAM:** SGs/NACLs control traffic  

### 6. Confusable Services
- NAT Gateway, VPC Endpoints, Virtual Private Gateway  

### 7. Exam Notes
- Public subnet = route to IGW  
- IGW enables both inbound + outbound  

## Virtual Private Gateway
VPN termination endpoint on AWS for hybrid connectivity.

### 1. Definition
A Virtual Private Gateway (VGW) terminates IPSec VPN tunnels for Site-to-Site VPNs and connects an on-prem network to a single VPC.

### 2. Use-Cases
- Hybrid connectivity  
- Encrypted site-to-site VPN  

### 3. Additional Info
- Supports BGP and static routing  

### 4. Limitations
- One VPC attachment  
- Internet-based latency  

### 5. Details
- **Characteristics:** Managed IPSec endpoint; regional  
- **Capabilities:** Encrypted tunnels; failover with dual tunnels  
- **Pricing Model:** VPN-hour + data transfer  
- **Security/IAM:** VPN encryption; IAM for config  

### 6. Confusable Services
- Transit Gateway (multi-VPC), Direct Connect (private link), Client VPN  

### 7. Exam Notes
- Two tunnels per VPN  
- Good for fast hybrid setup  

## NAT Gateway
Enables private subnet instances to initiate outbound internet access without exposing inbound paths.

### 1. Definition
NAT Gateway is a managed, scalable service placed in a public subnet to provide outbound-only traffic for private subnet resources.

### 2. Use-Cases
- Private workloads needing updates or API calls  
- Secure private-tier architectures  

### 3. Additional Info
- Automatic scaling; highly available per AZ  

### 4. Limitations
- Not multi-AZ by itself; deploy one per AZ  

### 5. Details
- **Characteristics:** Outbound internet; managed; AZ-scoped  
- **Capabilities:** Outbound NAT translation; high throughput  
- **Pricing Model:** Hourly + data processing fees  
- **Security/IAM:** Routing + SG/NACL enforcement  

### 6. Confusable Services
- IGW (inbound/outbound), NAT instance (legacy), VPC Endpoints  

### 7. Exam Notes
- Must be in a public subnet  
- Private subnet → NAT → IGW  

## AWS Client VPN
Managed client VPN service for remote user access into AWS and on-prem networks.

### 1. Definition
AWS Client VPN provides OpenVPN-based secure remote access for users, integrating with Directory Service, IAM, or certificate authentication.

### 2. Use-Cases
- Remote developer access  
- Workforce VPN into AWS  
- Hybrid remote connectivity  

### 3. Additional Info
- Supports split tunneling  
- Scales elastically  

### 4. Limitations
- User-based, not site-based  
- Performance depends on client network  

### 5. Details
- **Characteristics:** Remote-access VPN; regional  
- **Capabilities:** Identity-based auth; VPC routing  
- **Pricing Model:** Endpoint-hour + connection-hour  
- **Security/IAM:** IAM/AD auth; TLS; SGs  

### 6. Confusable Services
- Site-to-Site VPN, Direct Connect, AWS VPN Client software  

### 7. Exam Notes
- For remote individuals, not networks  
- Requires authorization rules for subnets  

## AWS Site-to-Site VPN
Creates encrypted IPSec tunnels between on-prem networks and AWS VPCs.

### 1. Definition
AWS Site-to-Site VPN provides secure IPSec connectivity from customer gateways to AWS via Virtual Private Gateway or Transit Gateway, supporting dual tunnels for redundancy.

### 2. Use-Cases
- Hybrid cloud connectivity  
- Encrypted on-prem to AWS access  
- Backup link for Direct Connect  

### 3. Additional Info
- Two redundant tunnels per VPN  
- Supports BGP for dynamic routing  

### 4. Limitations
- Latency varies with internet  
- Lower throughput than DX  

### 5. Details
- **Characteristics:** IPSec VPN; regional endpoints  
- **Capabilities:** Encrypted tunnels; failover; BGP routing  
- **Pricing Model:** Connection-hour + data transfer  
- **Security/IAM:** IPSec encryption; IAM for config  

### 6. Confusable Services
- Direct Connect, Client VPN, Transit Gateway VPN  

### 7. Exam Notes
- Two tunnels always provided  
- Use as backup for Direct Connect  

## AWS Direct Connect
Provides private, dedicated network connectivity between on-premises and AWS.

### 1. Definition
AWS Direct Connect establishes a private physical network connection that bypasses the public internet, enabling predictable latency and higher throughput.

### 2. Use-Cases
- High-throughput hybrid workloads  
- Consistent low-latency connections  
- Data migration at scale  

### 3. Additional Info
- Speeds: 1/10/100 Gbps  
- DX Gateway supports multiple VPCs  

### 4. Limitations
- Requires physical installation  
- Long provisioning times  

### 5. Details
- **Characteristics:** Dedicated link; private routing  
- **Capabilities:** Stable bandwidth; hybrid networking  
- **Pricing Model:** Port-hour + discounted transfer  
- **Security/IAM:** Private link; encryption optional  

### 6. Confusable Services
- VPN (internet-based), Global Accelerator, Transit Gateway  

### 7. Exam Notes
- “Consistent,” “private,” “low-latency” → Direct Connect  
- Combine DX + VPN for HA  

## AWS PrivateLink
Provides private connectivity to AWS services and customer services over VPC endpoints without traversing the public internet.

### 1. Definition
AWS PrivateLink allows private communication between VPCs and AWS services or SaaS applications using interface VPC endpoints (ENIs) without using public IPs or internet paths.

### 2. Use-Cases
- Access AWS services privately  
- Connect VPCs without exposing traffic  
- Provide internal SaaS services privately  

### 3. Additional Info
- Uses ENIs in subnets  
- Supports cross-account access  

### 4. Limitations
- Not for full VPC-to-VPC routing (use TGW instead)  

### 5. Details
- **Characteristics:** Private service access; ENI-based  
- **Capabilities:** Private connectivity; cross-account publishing  
- **Pricing Model:** Endpoint-hour + data processing  
- **Security/IAM:** SGs; IAM policy controls  

### 6. Confusable Services
- VPC Peering, Transit Gateway, Gateway Endpoints  

### 7. Exam Notes
- “Access AWS services privately” → PrivateLink  
- Interface endpoints = PrivateLink  

## AWS Transit Gateway
Hub-and-spoke network transit service connecting VPCs, on-prem networks, and VPNs.

### 1. Definition
AWS Transit Gateway (TGW) acts as a central router for connecting multiple VPCs and networks, simplifying complex architectures by replacing many VPC peering links.

### 2. Use-Cases
- Large multi-VPC architectures  
- Centralized hybrid connectivity  
- Reducing VPC peering mesh complexity  

### 3. Additional Info
- Supports attachments: VPC, VPN, DX, peering  
- Route domains isolate segments  

### 4. Limitations
- Higher cost than peering for small setups  
- More complex routing policies  

### 5. Details
- **Characteristics:** Regional hub router; scalable  
- **Capabilities:** VPC/VPN/DX attachments; centralized routing  
- **Pricing Model:** Attachment-hour + data processing  
- **Security/IAM:** IAM for config; SG/NACL still apply  

### 6. Confusable Services
- VPC Peering, PrivateLink, Virtual Private Gateway  

### 7. Exam Notes
- “Many VPCs,” “centralized routing,” “hub-and-spoke” → TGW  
- TGW != PrivateLink (service access)  

## VPC Endpoints (Gateway & Interface)
Private connections to AWS services without internet routing.

### 1. Definition
VPC Endpoints enable private connectivity to AWS services. Gateway endpoints support S3 and DynamoDB; interface endpoints (via PrivateLink) support many AWS and SaaS services.

### 2. Use-Cases
- Private access to AWS APIs  
- Avoid NAT + IGW traffic costs  
- Restrict workloads to internal-only connectivity  

### 3. Additional Info
- Gateway endpoints = route table targets  
- Interface endpoints = ENIs  

### 4. Limitations
- Gateway endpoints limited to S3/DynamoDB  

### 5. Details
- **Characteristics:** Private connectivity; regional  
- **Capabilities:** Remove public internet path; secure service access  
- **Pricing Model:** Interface endpoint hourly + data; gateway free  
- **Security/IAM:** Endpoint policies; SGs  

### 6. Confusable Services
- PrivateLink, NAT Gateway, Internet Gateway  

### 7. Exam Notes
- Gateway = S3 & DynamoDB  
- Interface = PrivateLink-based  

## Amazon Route 53
Highly available and scalable DNS service providing domain registration, DNS routing, and health checking.

### 1. Definition
Amazon Route 53 is a managed DNS and domain registration service used to route end-user requests to applications running on AWS or elsewhere. It supports routing policies such as simple, weighted, latency-based, failover, geolocation, and multivalue. Route 53 also provides DNS health checks and traffic flow management for global architectures.

### 2. Use-Cases
- Domain registration and DNS hosting  
- Global routing and traffic steering  
- Failover routing for multi-region applications  

### 3. Additional Info
- Policies: Simple, weighted, failover, geolocation, latency, multivalue  
- Health checks support automated failover  

### 4. Limitations
- Not a CDN (use CloudFront)  
- Does not provide TLS termination (use ACM/ELB)  

### 5. Details
- **Characteristics:** Global DNS; highly available; low-latency  
- **Capabilities:** DNS resolution, routing policies, health checks  
- **Pricing Model:** Hosted zone fee + queries  
- **Security/IAM:** DNSSEC support; IAM permissions  

### 6. Confusable Services
- CloudFront (CDN), Global Accelerator (Anycast routing), ELB (traffic distribution)  

### 7. Exam Notes
- Weighted = A/B testing; latency = user proximity  
- Failover routing uses health checks  

## Amazon CloudFront
Global content delivery network (CDN) accelerating delivery of web content to users worldwide.

### 1. Definition
Amazon CloudFront is a CDN that caches and delivers content through a global network of edge locations. It improves performance and reduces latency for static, dynamic, video, and API content. CloudFront integrates with S3, ALB, API Gateway, and Lambda@Edge for global request processing.

### 2. Use-Cases
- Accelerating websites and APIs  
- Streaming media  
- Protecting applications via AWS Shield and WAF integration  

### 3. Additional Info
- Edge functions via Lambda@Edge  
- Supports signed URLs/cookies for access control  

### 4. Limitations
- Cache invalidation may incur cost  
- Latency still depends on edge coverage  

### 5. Details
- **Characteristics:** Global CDN; edge-based caching  
- **Capabilities:** Content caching, TLS termination, global distribution  
- **Pricing Model:** Data transfer + requests  
- **Security/IAM:** WAF, Shield, signed URLs  

### 6. Confusable Services
- Global Accelerator (TCP/UDP acceleration)  
- S3 Transfer Acceleration (S3 uploads only)  

### 7. Exam Notes
- “Global CDN,” “edge caching,” “Lambda@Edge” → CloudFront  
- Often paired with S3 static websites  

## AWS Global Accelerator
Improves global application performance and availability using AWS global network and Anycast IP addresses.

### 1. Definition
AWS Global Accelerator routes user traffic over the AWS global backbone instead of the public internet, using two static Anycast IPs for improved latency, performance, and failover. It directs traffic to optimal AWS endpoints based on health, geography, and routing policies.

### 2. Use-Cases
- Improving global application latency  
- Providing static IPs for multi-region failover  
- Hybrid or global deployments requiring consistent performance  

### 3. Additional Info
- Works with ALB, NLB, EC2, and IP endpoints  
- Automatic health checks and failover  

### 4. Limitations
- Not a CDN (no caching)  
- Pricing higher than CloudFront for global traffic patterns  

### 5. Details
- **Characteristics:** Anycast routing; global network acceleration  
- **Capabilities:** Latency optimization; static IPs; multi-region failover  
- **Pricing Model:** Data transfer + accelerator-hour  
- **Security/IAM:** SG/NACLs; IAM config  

### 6. Confusable Services
- CloudFront (CDN), Route 53 (DNS routing), Direct Connect (private link)  

### 7. Exam Notes
- If question mentions “static Anycast IPs” → Global Accelerator  
- Improves performance but does NOT cache content  


---

## 03-storage


# Storage

## Amazon S3
Object storage service offering high durability, scalability, and global accessibility.

### 1. Definition
Amazon S3 is a fully managed object storage service designed for storing and retrieving any amount of data. It provides 11-nines durability, multiple storage classes, lifecycle policies, versioning, replication, event notifications, and fine-grained access controls. S3 is foundational for data lakes, application storage, static hosting, backups, and big data workflows.

### 2. Use-Cases
- Data lakes and analytics  
- Backup and archival storage  
- Static website hosting  
- Application asset storage  
- Event-driven serverless pipelines  

### 3. Additional Info
- Storage classes: Standard, IA, One Zone-IA, Glacier Instant/Deep Archive, Intelligent-Tiering  
- Features: Versioning, lifecycle rules, replication, encryption, access points  

### 4. Limitations
- Object-level access only (not POSIX)  
- Eventual consistency for overwrite/delete  

### 5. Details
- **Characteristics:** Object storage; serverless; regional with global access  
- **Capabilities:** Events, replication, lifecycle, encryption, versioning  
- **Pricing Model:** Storage, requests, retrieval, data transfer  
- **Security/IAM:** IAM policies, bucket policies, ACLs, SSE-S3/KMS  

### 6. Confusable Services
- EFS/FSx (file storage), EBS (block storage), Glacier services (archival), Storage Gateway  

### 7. Exam Notes
- “Object storage,” “11 9’s durability,” “data lake,” “static website” → S3  
- Block public access prevents unintended exposure  

## Amazon EBS
Block storage volumes for EC2 instances with high performance and low latency.

### 1. Definition
Amazon Elastic Block Store (EBS) provides persistent block storage volumes for EC2 instances. It supports SSD and HDD volume types, snapshots, encryption, and high availability within an AZ.

### 2. Use-Cases
- Databases and transactional workloads  
- Boot volumes for EC2  
- Low-latency block storage needs  

### 3. Additional Info
- Snapshots stored in S3  
- Volume types: gp3, io2, st1, sc1  

### 4. Limitations
- AZ-scoped; requires snapshot+restore for cross-AZ/region copying  

### 5. Details
- **Characteristics:** Block storage; persistent; AZ-bound  
- **Capabilities:** Snapshots, resizing, encryption, high IOPS options  
- **Pricing Model:** Per GB-month + provisioned IOPS  
- **Security/IAM:** KMS encryption; IAM for volume/snapshot access  

### 6. Confusable Services
- EFS/FSx (file storage), S3 (object storage), Instance Store  

### 7. Exam Notes
- EBS = persistent block storage; Instance Store = ephemeral  
- gp3 default; io2 for highest IOPS  

## Amazon EFS
Fully managed, elastic NFS file system for Linux workloads shared across multiple instances.

### 1. Definition
Amazon Elastic File System (EFS) is a scalable, elastic file system providing shared POSIX storage for Linux workloads across multiple AZs. It automatically grows and shrinks as files are added or removed.

### 2. Use-Cases
- Shared application storage  
- Container/compute clusters (ECS/EKS)  
- Lift-and-shift NFS workloads  

### 3. Additional Info
- Performance modes: General Purpose, Max I/O  
- Storage classes: Standard, IA  

### 4. Limitations
- Higher cost than some storage types  
- Not compatible with Windows (use FSx)  

### 5. Details
- **Characteristics:** NFS; multi-AZ; elastic; regional  
- **Capabilities:** Shared file access; scaling; encryption; access points  
- **Pricing Model:** Per GB-month; IA class reduces cost  
- **Security/IAM:** SG-based access; POSIX permissions; IAM for API access  

### 6. Confusable Services
- FSx (Windows or Lustre), S3 (object), EBS (block)  

### 7. Exam Notes
- Multi-AZ, POSIX = EFS  
- Automatically scales with usage  

## Amazon FSx (Windows & Lustre)
Managed file systems optimized for Windows workloads or high-performance computing.

### 1. Definition
Amazon FSx provides fully managed file storage offerings: FSx for Windows File Server (SMB, Active Directory integration) and FSx for Lustre (high-performance parallel file system for HPC and ML).

### 2. Use-Cases
- Windows file shares  
- HPC workloads requiring Lustre  
- ML and big data needing high throughput  

### 3. Additional Info
- Supports SMB (Windows) and Lustre protocols  
- Integrates with Active Directory  

### 4. Limitations
- FSx for Lustre not POSIX-complete for all workloads  
- FSx Windows requires AD  

### 5. Details
- **Characteristics:** High-performance file systems; regional  
- **Capabilities:** AD integration; high throughput; parallel file access  
- **Pricing Model:** Throughput + storage + backups  
- **Security/IAM:** KMS encryption; AD permissions; IAM for API  

### 6. Confusable Services
- EFS (Linux NFS), EBS (block), S3 (object)  

### 7. Exam Notes
- Windows SMB needs FSx Windows  
- HPC parallel access → FSx Lustre  

## AWS Storage Gateway
Hybrid cloud storage service connecting on-prem workloads with AWS storage.

### 1. Definition
AWS Storage Gateway provides hybrid storage with file, volume, and tape gateway modes for integrating on-prem environments with AWS storage services.

### 2. Use-Cases
- Hybrid backup and archival  
- On-prem file shares backed by cloud storage  
- Tape replacement for backup systems  

### 3. Additional Info
- Modes: File Gateway, Volume Gateway, Tape Gateway  

### 4. Limitations
- Requires on-prem appliance or VM  
- Latency depends on network link  

### 5. Details
- **Characteristics:** Hybrid storage; connects on-prem to AWS  
- **Capabilities:** Cached/Stored volumes; virtual tapes; S3-backed file shares  
- **Pricing Model:** Appliance-hour + data transfer  
- **Security/IAM:** KMS; IAM roles; SSL  

### 6. Confusable Services
- DataSync (transfer automation), Backup, Snowball  

### 7. Exam Notes
- File Gateway → S3-backed NFS/SMB  
- Tape Gateway replaces physical tape libraries  

## AWS Backup
Centralized, automated backup service for AWS and on‑prem workloads.

### 1. Definition
AWS Backup provides fully managed, policy‑driven backup orchestration across AWS services and on-premises environments. It standardizes backup plans, retention, scheduling, vaulting, and compliance tracking.

### 2. Use-Cases
- Centralizing backups across AWS services  
- Meeting compliance and retention policies  
- Cross-region/cross-account backup strategies  

### 3. Additional Info
- Supports EC2, EBS, RDS, DynamoDB, EFS, FSx, Storage Gateway, and more  
- Backup Vaults support encryption and access policies  

### 4. Limitations
- Some service features vary by region  
- Backup windows may impact performance on certain workloads  

### 5. Details
- **Characteristics:** Centralized, policy-driven, multi-service coverage  
- **Capabilities:** Scheduled backups, lifecycle policies, vaulting  
- **Pricing Model:** Per-GB backup + restore charges  
- **Security/IAM:** Backup Vault Lock, KMS, IAM policies  

### 6. Confusable Services
- Data Lifecycle Manager (EBS snapshots only)  
- Storage Gateway (hybrid storage, not centralized backup)  

### 7. Exam Notes
- “Centralize backups,” “policy-based retention,” “cross-region backup” → AWS Backup  

## AWS DataSync
Automated data transfer service between on‑prem, AWS storage, and AWS services.

### 1. Definition
AWS DataSync automates and accelerates data movement to, from, and between AWS storage services using a purpose-built protocol.

### 2. Use-Cases
- Migrations from on‑prem NAS to AWS  
- Periodic sync workflows  
- Large dataset transfer with verification  

### 3. Additional Info
- Supports S3, EFS, FSx, SMB, NFS  
- Includes data validation and encryption  

### 4. Limitations
- Requires DataSync agent for on-prem workloads  

### 5. Details
- **Characteristics:** High-speed transfer; automated scheduling  
- **Capabilities:** Incremental syncs; bandwidth controls; filtering  
- **Pricing Model:** Per-GB transferred  
- **Security/IAM:** TLS; IAM roles; encryption in transit  

### 6. Confusable Services
- Transfer Family (protocol-based user transfer)  
- Snowball (offline transfer)  

### 7. Exam Notes
- “Accelerated transfer,” “automated sync,” “NFS/SMB to S3/EFS” → DataSync  

## AWS Transfer Family
Managed SFTP, FTPS, and FTP endpoints backed by Amazon S3 or EFS.

### 1. Definition
AWS Transfer Family provides fully managed file transfer endpoints using traditional protocols (SFTP, FTPS, FTP) with S3 or EFS as storage backends.

### 2. Use-Cases
- Legacy system integrations  
- Partner data exchange workflows  
- Secure file onboarding into S3/EFS  

### 3. Additional Info
- User authentication via IAM, AD, or custom identity providers  

### 4. Limitations
- Not designed for large-scale migration (use DataSync instead)  

### 5. Details
- **Characteristics:** Managed protocol servers; scalable  
- **Capabilities:** Protocol endpoints; identity integration  
- **Pricing Model:** Endpoint-hour + data transfer  
- **Security/IAM:** IAM-based controls; VPC support  

### 6. Confusable Services
- DataSync (automated migration)  
- S3 presigned URLs (object uploads without protocols)  

### 7. Exam Notes
- “SFTP/FTP to S3/EFS” → Transfer Family  

## AWS Elastic Disaster Recovery
Disaster recovery service enabling fast failover of on‑prem or cloud workloads into AWS.

### 1. Definition
AWS Elastic Disaster Recovery (DRS) continuously replicates on-prem or cloud servers into AWS and enables rapid recovery during disaster events.

### 2. Use-Cases
- Business continuity for critical systems  
- Replacing traditional DR infrastructure  
- Migration with minimal downtime  

### 3. Additional Info
- Replication to lightweight EC2 instances until failover  

### 4. Limitations
- Requires agent installation for on-prem servers  

### 5. Details
- **Characteristics:** Continuous replication; low RPO/RTO  
- **Capabilities:** Failover, failback, non-disruptive tests  
- **Pricing Model:** Replication & storage costs + EC2 on failover  
- **Security/IAM:** Encryption, IAM roles  

### 6. Confusable Services
- AWS Backup (backup, not DR)  
- CloudEndure (precursor technology)  

### 7. Exam Notes
- “Fast failover,” “continuous replication,” “DR strategy” → DRS  

## AWS Snow Family
Physical devices for offline or edge data transfer and edge compute.

### AWS Snowcone
### 1. Definition
Small, rugged edge device for data transfer and lightweight compute at the edge.

### Use-Cases
- Harsh environments  
- IoT/edge compute  
- Limited connectivity  

### Confusable
- Snowball (larger capacity), DataSync (online only)

### AWS Snowball
### 1. Definition
Rugged appliance for large-scale data transfer or edge compute workloads.

### Use-Cases
- Mass data migration  
- Edge ML/compute workloads  

### Confusable
- Snowcone (smaller), Snowmobile (extreme scale)  

### AWS Snowmobile
### 1. Definition
Massive data transfer truck for exabyte-scale migrations.

### Use-Cases
- Multi-petabyte or exabyte migrations  
- Data center evacuations  

### Confusable
- Snowball (smaller scale), DataSync (online transfers)  


---

## 04-databases


# Databases

## Amazon RDS
Managed relational database service supporting MySQL, PostgreSQL, MariaDB, Oracle, and SQL Server.

### 1. Definition
Amazon RDS automates database provisioning, patching, backups, monitoring, and replication for relational engines. It supports Multi-AZ failover, read replicas, and various instance classes optimized for memory or performance.

### 2. Use-Cases
- Traditional relational applications  
- OLTP workloads  
- Applications requiring managed backups and HA  

### 3. Additional Info
- Engines: MySQL, PostgreSQL, MariaDB, Oracle, SQL Server  
- Multi-AZ for failover; read replicas for read scaling  

### 4. Limitations
- Limited access to OS-level features  
- Some engines have licensing constraints  

### 5. Details
- **Characteristics:** Managed RDBMS; regional; supports replicas  
- **Capabilities:** Automated maintenance, backups, monitoring  
- **Pricing Model:** Instance-hours + storage + I/O  
- **Security/IAM:** KMS encryption; SGs; IAM auth for some engines  

### 6. Confusable Services
- Aurora (higher performance), DynamoDB (NoSQL), Redshift (analytics)  

### 7. Exam Notes
- Multi-AZ = HA; read replicas ≠ HA  

## Amazon Aurora
High-performance, cloud-native relational database compatible with MySQL and PostgreSQL.

### 1. Definition
Aurora is a distributed, fault-tolerant, high-performance relational database engine offering up to 5x performance of MySQL and 3x of PostgreSQL. Storage auto-expands and replicates across 6 copies in 3 AZs.

### 2. Use-Cases
- High-throughput relational workloads  
- SaaS applications with high scalability needs  
- Global databases  

### 3. Additional Info
- Serverless v2 for autoscaling  
- Aurora Global Database for low-latency global reads  

### 4. Limitations
- More expensive than RDS engines  
- Custom engine features limit portability  

### 5. Details
- **Characteristics:** Distributed storage; multi-AZ; high performance  
- **Capabilities:** Read replicas; global clusters; autoscaling  
- **Pricing Model:** Instance-hours + I/O + storage  
- **Security/IAM:** KMS; SGs; IAM auth  

### 6. Confusable Services
- RDS, DynamoDB, Redshift  

### 7. Exam Notes
- Aurora = performance + HA + replication across AZs  
- Global Aurora = lowest-latency global reads  

## Amazon DynamoDB
Fully managed NoSQL database providing single-digit millisecond performance at any scale.

### 1. Definition
DynamoDB is a serverless NoSQL key-value and document database supporting massive scale, consistent low latency, global tables, backups, streams, and DAX caching.

### 2. Use-Cases
- Serverless apps  
- Massive-scale workloads  
- Shopping carts, session data, metadata stores  

### 3. Additional Info
- On-demand or provisioned capacity  
- Streams enable event-driven patterns  

### 4. Limitations
- Not relational; no joins or complex queries  
- Hot partition risks  

### 5. Details
- **Characteristics:** NoSQL; serverless; regional  
- **Capabilities:** TTL, backups, streams, global tables  
- **Pricing Model:** Read/write units or on-demand  
- **Security/IAM:** Fine-grained IAM; KMS  

### 6. Confusable Services
- DocumentDB (Mongo-compatible), ElastiCache  

### 7. Exam Notes
- Partition keys, WCU/RCU, on-demand vs provisioned  

## Amazon DynamoDB Accelerator (DAX)
In-memory cache for DynamoDB delivering microsecond read latency.

### 1. Definition
DAX is a fully managed in-memory caching layer for DynamoDB that accelerates read-heavy workloads by caching responses.

### 2. Use-Cases
- Read-heavy workloads  
- Reducing DynamoDB read costs  
- Ultra-low-latency apps  

### 3. Additional Info
- API-compatible with DynamoDB SDKs  

### 4. Limitations
- Write-through behavior adds complexity  
- Cluster-based; not serverless  

### 5. Details
- **Characteristics:** In-memory cache; clustered; regional  
- **Capabilities:** Microsecond reads; write-through caching  
- **Pricing Model:** Node-hour pricing  
- **Security/IAM:** IAM auth; SGs  

### 6. Confusable Services
- ElastiCache (general-purpose caching), DynamoDB Streams  

### 7. Exam Notes
- Keyword: “microsecond latency for DynamoDB”  

## Amazon ElastiCache
Managed Redis and Memcached service for low-latency caching.

### 1. Definition
ElastiCache provides in-memory data stores using Redis or Memcached, improving application performance by reducing database load.

### 2. Use-Cases
- Caching layers for DB-heavy apps  
- Session storage  
- Real-time leaderboards or analytics  

### 3. Additional Info
- Supports Redis clustering  
- Fully managed patching and failover  

### 4. Limitations
- Volatile in-memory storage  
- Redis persistence not guaranteed  

### 5. Details
- **Characteristics:** In-memory store; multi-AZ for Redis  
- **Capabilities:** Sub-millisecond reads; replication; clustering  
- **Pricing Model:** Node-hour  
- **Security/IAM:** SGs; KMS (Redis)  

### 6. Confusable Services
- DAX (DynamoDB-specific cache), DynamoDB itself  

### 7. Exam Notes
- Redis = richer features; Memcached = simple, horizontal scale  

## Amazon DocumentDB
Managed document database service compatible with MongoDB workloads.

### 1. Definition
Amazon DocumentDB is a fully managed, scalable document database service designed for compatibility with MongoDB APIs. It decouples compute and storage for scalability and durability and supports automatic backups, replication, and monitoring.

### 2. Use-Cases
- JSON document storage  
- Migrating MongoDB workloads to AWS  
- Semi-structured data applications  

### 3. Additional Info
- Storage auto-scales up to 64 TB  
- Replica support for read scaling  

### 4. Limitations
- Not fully MongoDB feature-equivalent  
- Regional architecture (no global writes)  

### 5. Details
- **Characteristics:** Managed document DB; multi-AZ  
- **Capabilities:** Automatic backups; replicas; scaling  
- **Pricing Model:** Instance-hours + I/O + storage  
- **Security/IAM:** SGs; KMS; IAM auth for API  

### 6. Confusable Services
- DynamoDB (NoSQL key-value), Neptune (graph), MongoDB Atlas  

### 7. Exam Notes
- “MongoDB-compatible,” “JSON documents” → DocumentDB  


## Amazon Neptune
High-performance graph database for highly connected datasets.

### 1. Definition
Amazon Neptune is a fully managed graph database supporting Property Graph and RDF models using Gremlin and SPARQL queries. It is designed for relationship-heavy workloads.

### 2. Use-Cases
- Knowledge graphs  
- Fraud detection  
- Recommendation engines  
- Social network graphs  

### 3. Additional Info
- Millisecond-latency graph traversal  
- Read replicas supported  

### 4. Limitations
- Specialized use cases only  
- Requires understanding graph models  

### 5. Details
- **Characteristics:** Graph database; multi-AZ  
- **Capabilities:** ACID transactions; fast traversals  
- **Pricing Model:** Instance-hours + storage + I/O  
- **Security/IAM:** KMS; SGs; IAM for API  

### 6. Confusable Services
- DynamoDB (No), DocumentDB (No), Redshift (analytics)  

### 7. Exam Notes
- “Graph,” “relationships,” “Gremlin/SPARQL” → Neptune  


## Amazon Redshift
Fully managed, petabyte-scale cloud data warehouse for analytic workloads.

### 1. Definition
Amazon Redshift is a massively parallel processing (MPP) data warehouse optimized for large-scale analytics. It supports columnar storage, materialized views, RA3 storage layers, data sharing, Redshift Spectrum, and integration with data lakes.

### 2. Use-Cases
- Complex analytical queries  
- Business intelligence and dashboards  
- Large-scale data warehousing  
- Data lake + warehouse hybrid architectures  

### 3. Additional Info
- Redshift Spectrum queries S3 directly  
- RA3 nodes separate compute/storage  

### 4. Limitations
- Not suitable for OLTP  
- Requires table distribution/keys for optimization  

### 5. Details
- **Characteristics:** Columnar; MPP; scalable; regional  
- **Capabilities:** Data sharing; Spectrum; concurrency scaling  
- **Pricing Model:** Node-hours or serverless compute  
- **Security/IAM:** KMS; IAM; SGs; audit logging  

### 6. Confusable Services
- Athena (S3 querying), EMR (big data frameworks), RDS/Aurora (OLTP)  

### 7. Exam Notes
- “Analytics,” “columnar,” “MPP,” “Spectrum” → Redshift  
- Redshift is for OLAP, not OLTP  


---

## 05-ai_ml


# Machine Learning & AI

## Amazon Comprehend
Natural language processing (NLP) service using machine learning to extract insights from text.

### 1. Definition
Amazon Comprehend is a fully managed NLP service that performs entity recognition, sentiment analysis, key phrase extraction, language detection, and custom classification using machine learning models.

### 2. Use-Cases
- Text classification  
- Sentiment analysis in customer feedback  
- Entity extraction from documents  

### 3. Additional Info
- Supports custom classification and entity types  
- Integrates with S3 and other data ingestion tools  

### 4. Limitations
- Not for OCR (use Textract)  

### 5. Details
- **Characteristics:** Fully managed NLP; regional  
- **Capabilities:** Entity detection; sentiment; custom models  
- **Pricing Model:** Per-unit text processed  
- **Security/IAM:** KMS; IAM; VPC endpoints  

### 6. Confusable Services
- Textract (OCR), Kendra (search), Translate (translation)  

### 7. Exam Notes
- “Sentiment,” “entities,” “text analysis” → Comprehend  


## Amazon Polly
Text-to-speech (TTS) service that converts text into lifelike speech.

### 1. Definition
Amazon Polly generates natural-sounding speech using deep learning, supporting multiple languages and voices.

### 2. Use-Cases
- Voice-enabled applications  
- Automated audio content generation  
- Accessibility tools  

### 3. Additional Info
- Neural TTS and customizable lexicons  

### 4. Limitations
- Not speech recognition (use Transcribe)  

### 5. Details
- **Characteristics:** Managed TTS; multilingual  
- **Capabilities:** Speech synthesis; SSML support  
- **Pricing Model:** Per-character  
- **Security/IAM:** IAM; KMS for logs  

### 6. Confusable Services
- Transcribe (speech-to-text), Lex (chatbots)  

### 7. Exam Notes
- “Text to speech,” “voice output” → Polly  


## Amazon Transcribe
Automatic speech recognition (ASR) service converting speech to text.

### 1. Definition
Amazon Transcribe converts audio into text using machine learning, supporting speaker identification, timestamps, and multiple languages.

### 2. Use-Cases
- Call center transcription  
- Media subtitling  
- Voice analytics pipelines  

### 3. Additional Info
- Medical Transcribe for healthcare scenarios  

### 4. Limitations
- Not text-to-speech (Polly)  

### 5. Details
- **Characteristics:** Speech-to-text; regional  
- **Capabilities:** Timestamps; speaker diarization  
- **Pricing Model:** Per-second audio processed  
- **Security/IAM:** IAM; encryption  

### 6. Confusable Services
- Polly, Comprehend (downstream analysis)  

### 7. Exam Notes
- “Convert speech to text,” “ASR” → Transcribe  


## Amazon Translate
Neural machine translation service for fast and accurate language translation.

### 1. Definition
Amazon Translate uses neural networks to translate text between many languages at scale.

### 2. Use-Cases
- Localization workflows  
- Multilingual chat support  
- Content translation pipelines  

### 3. Additional Info
- Batch and real-time translation  

### 4. Limitations
- Not NLP analysis (Comprehend)  

### 5. Details
- **Characteristics:** Neural translation; global language support  
- **Capabilities:** Text translation; batch jobs  
- **Pricing Model:** Per-character  
- **Security/IAM:** IAM; encryption  

### 6. Confusable Services
- Comprehend; Transcribe; Polly  

### 7. Exam Notes
- “Translate text between languages” → Translate  


## Amazon Lex
Conversational AI service for building chatbots and voice assistants.

### 1. Definition
Amazon Lex enables the creation of conversational interfaces using the same deep learning technology as Alexa. It handles intent recognition, slot filling, and dialogue management.

### 2. Use-Cases
- Customer support chatbots  
- Voice assistants  
- Automated helpdesk flows  

### 3. Additional Info
- Integrates with Lambda for fulfillment  

### 4. Limitations
- Requires well-designed conversational models  

### 5. Details
- **Characteristics:** Conversational AI; ASR + NLU  
- **Capabilities:** Intents; slots; multi-turn dialogues  
- **Pricing Model:** Per speech/text request  
- **Security/IAM:** IAM; KMS  

### 6. Confusable Services
- Polly (speech output), Transcribe (speech input), Q Business  

### 7. Exam Notes
- “Build chatbots,” “conversational interface” → Lex  

## Amazon Rekognition
Image and video analysis service powered by deep learning.

### 1. Definition
Amazon Rekognition provides pre-trained and customizable computer vision capabilities, including object detection, facial analysis, text in images, unsafe content detection, and face comparison.

### 2. Use-Cases
- Content moderation  
- Image search  
- Facial recognition for authentication  
- Video analysis for compliance or metadata extraction  

### 3. Additional Info
- Supports both image and video streams  
- Can integrate with Kinesis Video Streams for real-time analysis  

### 4. Limitations
- Some advanced facial recognition features restricted by region/policy  

### 5. Details
- **Characteristics:** Managed CV; deep learning models  
- **Capabilities:** Labels; faces; celebrity ID; moderation; text detection  
- **Pricing Model:** Per-image or per-minute video analysis  
- **Security/IAM:** IAM; KMS; data privacy controls  

### 6. Confusable Services
- Textract (OCR), Kinesis Video Streams (ingestion), SageMaker CV models  

### 7. Exam Notes
- “Object detection,” “content moderation,” “face recognition” → Rekognition  


## Amazon Textract
OCR and document analysis service that extracts structured data from scanned documents.

### 1. Definition
Amazon Textract reads and extracts text, tables, forms, and key-value pairs from documents using machine learning.

### 2. Use-Cases
- Invoice and form processing  
- Automated document ingestion  
- OCR pipelines  

### 3. Additional Info
- Identifies relationships between detected text elements  

### 4. Limitations
- Not NLP analysis (use Comprehend)  

### 5. Details
- **Characteristics:** OCR + document intelligence  
- **Capabilities:** Form extraction; table extraction; handwriting support  
- **Pricing Model:** Per-page  
- **Security/IAM:** KMS; IAM  

### 6. Confusable Services
- Rekognition (images), Comprehend (text insights)  

### 7. Exam Notes
- “Forms,” “tables,” “OCR with key-value pairs” → Textract  


## Amazon Forecast
Time-series forecasting service using machine learning.

### 1. Definition
Amazon Forecast generates accurate forecasts using ML models trained on time-series data and related variables. Based on the same tech used at Amazon.com.

### 2. Use-Cases
- Demand forecasting  
- Capacity planning  
- Financial projections  

### 3. Additional Info
- Uses AutoML to select algorithms  

### 4. Limitations
- Requires curated datasets  

### 5. Details
- **Characteristics:** ML-based forecasting; serverless  
- **Capabilities:** Predictive models; AutoML; quantile forecasts  
- **Pricing Model:** Training-hour + inference usage  
- **Security/IAM:** IAM; KMS  

### 6. Confusable Services
- Personalize (recommendations), QuickSight ML insights  

### 7. Exam Notes
- “Demand planning,” “time-series” → Forecast  


## Amazon Personalize
Personalization and recommendation service based on ML.

### 1. Definition
Amazon Personalize builds custom recommendation models using behavioral data, similar to Amazon.com’s retail recommendation engine.

### 2. Use-Cases
- Product recommendations  
- Content personalization  
- Personalized search results  

### 3. Additional Info
- Uses interaction, item, and user datasets  

### 4. Limitations
- Training requires representative history  

### 5. Details
- **Characteristics:** Real-time personalization; ML-based  
- **Capabilities:** Recommendations; reranking; user segmentation  
- **Pricing Model:** Training-hour + inference  
- **Security/IAM:** IAM; KMS  

### 6. Confusable Services
- Forecast (time-series), Neptune (graph relations), SageMaker recommender models  

### 7. Exam Notes
- “Personalized recommendations,” “user-item interactions” → Personalize  


## Amazon Kendra
Enterprise search service powered by ML for natural language queries.

### 1. Definition
Amazon Kendra provides intelligent enterprise search with natural language understanding to retrieve accurate answers from organizational content.

### 2. Use-Cases
- Internal knowledge search  
- Customer support knowledge bases  
- Document search across repositories  

### 3. Additional Info
- Connectors for S3, SharePoint, Salesforce, Confluence, and more  

### 4. Limitations
- Indexing large content sets may incur cost  

### 5. Details
- **Characteristics:** Intelligent search; ML ranking  
- **Capabilities:** Semantic search; FAQs; document connectors  
- **Pricing Model:** Index capacity + query usage  
- **Security/IAM:** IAM; KMS; document-level access control  

### 6. Confusable Services
- OpenSearch (keyword search), Comprehend (text analysis)  

### 7. Exam Notes
- “Natural language enterprise search,” “FAQ matching” → Kendra  

## Amazon SageMaker
Fully managed machine learning platform for building, training, and deploying ML models at scale.

### 1. Definition
Amazon SageMaker provides a comprehensive ML workflow environment including data preparation, model training, tuning, deployment, MLOps automation, and monitoring. It supports built-in algorithms, custom containers, distributed training, notebooks, and fully managed endpoints.

### 2. Use-Cases
- End-to-end ML development  
- Large-scale distributed training  
- Deploying real-time or batch inference endpoints  

### 3. Additional Info
- Includes Studio, Notebooks, Training Jobs, Model Registry, Pipelines  

### 4. Limitations
- Complex service with many components  
- Higher operational cost than serverless AI services  

### 5. Details
- **Characteristics:** Full ML platform; regional; highly modular  
- **Capabilities:** Autopilot (AutoML), Pipelines, MLOps, hyperparameter tuning  
- **Pricing Model:** Separate pricing for compute, storage, training, endpoints  
- **Security/IAM:** IAM; KMS; VPC integration; encryption  

### 6. Confusable Services
- Bedrock (foundation models, not training from scratch)  
- Personalize/Forecast (domain-specific ML services)  

### 7. Exam Notes
- “End-to-end ML,” “training + deployment,” “MLOps” → SageMaker  


## SageMaker JumpStart
Pre-built ML solutions, models, and notebooks for rapid adoption.

### 1. Definition
SageMaker JumpStart provides ready-to-use ML templates, pretrained models, and solution accelerators for tasks like classification, forecasting, and NLP.

### 2. Use-Cases
- Quick-start ML development  
- Using pretrained models without custom training  
- Accelerating PoCs  

### 3. Additional Info
- Integrates directly with SageMaker Studio  

### 4. Limitations
- Not as customizable as full SageMaker setups  

### 5. Details
- **Characteristics:** Prebuilt ML assets; easy onboarding  
- **Capabilities:** One-click deployments; example notebooks  
- **Pricing Model:** Based on underlying SageMaker resources used  
- **Security/IAM:** IAM; KMS  

### 6. Confusable Services
- Bedrock (foundation models), Autopilot  

### 7. Exam Notes
- “Prebuilt templates,” “get started fast in SageMaker” → JumpStart  


## Amazon Bedrock
Managed generative AI service providing access to foundation models via API.

### 1. Definition
Amazon Bedrock offers a unified API to leading foundation models from AWS and third-party providers (Anthropic, Meta, Cohere, Stability AI, etc.), with tools for fine-tuning, retrieval-augmented generation (RAG), and guarded inference.

### 2. Use-Cases
- Building GenAI chatbots  
- Content generation  
- Knowledge retrieval with RAG  
- Fine-tuning models  

### 3. Additional Info
- Includes Agents, Knowledge Bases, Guardrails  

### 4. Limitations
- Not for training foundation models from scratch  

### 5. Details
- **Characteristics:** GenAI API platform; multi-model  
- **Capabilities:** Fine-tuning; embeddings; RAG; guardrails  
- **Pricing Model:** Per-token or per-inference usage  
- **Security/IAM:** IAM; KMS; VPC; Guardrails  

### 6. Confusable Services
- SageMaker (custom ML training), Q Business (enterprise assistant)  

### 7. Exam Notes
- “Foundation models,” “RAG,” “Agents,” “Guardrails” → Bedrock  


## Amazon Q Business
Enterprise-grade AI assistant for productivity and knowledge retrieval.

### 1. Definition
Amazon Q Business is a secure enterprise assistant that connects to internal systems and documentation to provide accurate, context-aware answers and automate workflows.

### 2. Use-Cases
- Internal knowledge base queries  
- Employee productivity assistants  
- Document summarization, insights, and automation  

### 3. Additional Info
- Integrates with enterprise apps like Jira, Confluence, Salesforce  

### 4. Limitations
- Requires proper document ingestion and permissions setup  

### 5. Details
- **Characteristics:** Enterprise AI assistant; knowledge-integrated  
- **Capabilities:** Q&A; RAG; workflow automation  
- **Pricing Model:** Per-user monthly + usage  
- **Security/IAM:** IAM Identity Center; document-level access control  

### 6. Confusable Services
- Kendra (search only), Bedrock (model platform), Q Developer  

### 7. Exam Notes
- “Enterprise assistant,” “secure knowledge retrieval” → Q Business  


## Amazon Q Developer
AI coding assistant for software development workflows.

### 1. Definition
Amazon Q Developer provides AI-assisted code generation, refactoring, debugging guidance, test creation, and architectural recommendations. It integrates with IDEs, AWS console, and CI/CD pipelines.

### 2. Use-Cases
- Accelerating software development  
- Automating code fixes and upgrades  
- Generating tests and documentation  

### 3. Additional Info
- Deep AWS service integration (IAM policies, CloudFormation, Lambda code)  

### 4. Limitations
- AWS-focused; not a general competitor to full IDEs  

### 5. Details
- **Characteristics:** Developer AI assistant; integration-focused  
- **Capabilities:** Code-gen; refactoring; troubleshooting; infra suggestions  
- **Pricing Model:** Per-user monthly  
- **Security/IAM:** IAM code permissions; enterprise governance  

### 6. Confusable Services
- GitHub Copilot (general coding), Bedrock models (raw inference)  

### 7. Exam Notes
- “AI coding assistant,” “generating AWS code,” “IDE integration” → Q Developer  


---

## 06-analytics


# Analytics

## Amazon Athena
Serverless interactive query service for analyzing data in Amazon S3 using standard SQL.

### 1. Definition
Amazon Athena is a serverless SQL query engine that analyzes data directly in Amazon S3 using Presto/Trino. It requires no infrastructure, supports schema-on-read, and integrates with the Glue Data Catalog.

### 2. Use-Cases
- Ad‑hoc SQL analysis on S3 data lakes  
- Querying logs, clickstreams, CSV/JSON/Parquet files  
- Cost‑efficient analytics without clusters  

### 3. Additional Info
- Uses Glue Data Catalog as the metastore  
- Supports many formats: Parquet, ORC, JSON, CSV  

### 4. Limitations
- Performance depends on file format and partitioning  
- Not optimized for complex ETL (use EMR/Glue)  

### 5. Details
- **Characteristics:** Serverless; S3-based; schema‑on‑read  
- **Capabilities:** SQL queries; partitions; federated queries  
- **Pricing Model:** Per TB scanned  
- **Security/IAM:** IAM; KMS; Lake Formation  

### 6. Confusable Services
- Redshift (data warehouse), EMR (big data processing)  

### 7. Exam Notes
- Optimize cost with Parquet + partitioning  
- Serverless S3 queries → Athena  


## Amazon Kinesis Data Streams
Real-time data ingestion and streaming platform for high-throughput event pipelines.

### 1. Definition
Kinesis Data Streams (KDS) ingests and processes real-time streaming data using shards that scale throughput linearly. Applications consume data with low latency.

### 2. Use-Cases
- Real-time analytics  
- Application telemetry ingestion  
- Clickstream processing  

### 3. Additional Info
- Producers push records; consumers read via KCL  

### 4. Limitations
- Manual shard scaling unless using On‑Demand mode  
- Retention up to 365 days  

### 5. Details
- **Characteristics:** Real-time streaming; shard-based  
- **Capabilities:** Parallel reads; enhanced fan-out; replay  
- **Pricing Model:** Shard-hour + PUT payload costs  
- **Security/IAM:** IAM; KMS; VPC endpoints  

### 6. Confusable Services
- Kinesis Firehose (no consumer apps), MSK (Kafka)  

### 7. Exam Notes
- Shards = capacity units; scaling requires shard splits/merges  


## Amazon Kinesis Data Firehose
Fully managed streaming delivery service that loads data into AWS destinations automatically.

### 1. Definition
Kinesis Firehose ingests streaming data and delivers it to S3, Redshift, OpenSearch, or HTTP endpoints with optional transformation via Lambda.

### 2. Use-Cases
- Streaming ETL to S3/Redshift  
- Log ingestion pipelines  
- No-consumer architecture  

### 3. Additional Info
- Autoscaling and near-real-time delivery  

### 4. Limitations
- Cannot build consumer apps (use KDS instead)  

### 5. Details
- **Characteristics:** Fully managed; near real-time  
- **Capabilities:** Transform; compress; batch to S3/Redshift  
- **Pricing Model:** Per GB ingested  
- **Security/IAM:** KMS; IAM; VPC  

### 6. Confusable Services
- KDS, MSK, Glue streaming  

### 7. Exam Notes
- “No shards,” “autoscaling,” “store data to S3/Redshift” → Firehose  


## AWS Glue
Serverless data integration service for ETL, transformation, and data cataloging.

### 1. Definition
AWS Glue provides managed ETL via Glue Jobs, Crawlers, Workflows, and the Data Catalog. Supports PySpark, Spark SQL, and Python shell jobs.

### 2. Use-Cases
- Data lake ETL pipelines  
- Data catalog creation  
- Batch transformations  

### 3. Additional Info
- Crawlers auto-detect schema  
- Glue Studio for visual ETL  

### 4. Limitations
- Cold starts and job spin-up time  
- Complex debugging for Spark jobs  

### 5. Details
- **Characteristics:** Serverless ETL; Spark-based  
- **Capabilities:** Jobs, Workflows, Crawlers, Catalog  
- **Pricing Model:** DPU-hour  
- **Security/IAM:** KMS; IAM; VPC  

### 6. Confusable Services
- EMR (full Hadoop/Spark), Glue DataBrew  

### 7. Exam Notes
- “Managed Spark ETL,” “crawlers,” “Data Catalog” → Glue  


## AWS Glue Data Catalog
Central metadata repository for analytics services.

### 1. Definition
Glue Data Catalog is a centralized, serverless metastore storing table schemas used by Athena, Redshift Spectrum, EMR, and Glue ETL.

### 2. Use-Cases
- Data lake metadata store  
- Schema governance  
- Unified catalog for query engines  

### 3. Additional Info
- Integrates with Lake Formation for permissions  

### 4. Limitations
- Table updates may require crawlers or manual definition  

### 5. Details
- **Characteristics:** Schema store; serverless  
- **Capabilities:** Partitions; versioning; permissions  
- **Pricing Model:** Small per-object fee  
- **Security/IAM:** IAM; KMS; Lake Formation  

### 6. Confusable Services
- Hive Metastore (EMR), Lake Formation  

### 7. Exam Notes
- “Shared schema for Athena/EMR/Redshift Spectrum”  


## Amazon EMR
Managed big data processing platform for Hadoop, Spark, Hive, Presto, and more.

### 1. Definition
Amazon EMR is a scalable cluster service for big data workloads, supporting Hadoop ecosystem tools and optimized for cost using Spot and autoscaling.

### 2. Use-Cases
- Large-scale ETL  
- Machine learning with Spark  
- Data lake transformations  

### 3. Additional Info
- EMR Serverless option available  

### 4. Limitations
- Cluster management can be complex  
- Not serverless unless EMR Serverless  

### 5. Details
- **Characteristics:** Cluster-based or serverless; big data  
- **Capabilities:** Spark/Hadoop processing; autoscaling  
- **Pricing Model:** Instance-hour or serverless compute  
- **Security/IAM:** IAM; KMS; SGs  

### 6. Confusable Services
- Glue (serverless ETL), Redshift (warehouse)  

### 7. Exam Notes
- “Hadoop,” “Spark,” “cluster,” or “serverless EMR” → EMR  


## Amazon QuickSight
Cloud-native BI and dashboarding tool.

### 1. Definition
Amazon QuickSight provides interactive dashboards, visualizations, ML-powered insights, and embedded analytics.

### 2. Use-Cases
- BI reporting  
- Embedded analytics in applications  
- ML-driven insights  

### 3. Additional Info
- Supports SPICE in-memory engine  

### 4. Limitations
- Complex modeling compared to full BI tools  

### 5. Details
- **Characteristics:** BI SaaS; scalable; serverless  
- **Capabilities:** Dashboards; ML insights; SPICE  
- **Pricing Model:** Per-user or per-session  
- **Security/IAM:** IAM; row-level security  

### 6. Confusable Services
- Redshift (data warehouse), Athena (query engine)  

### 7. Exam Notes
- “SPICE,” “BI dashboards,” “serverless analytics” → QuickSight  


## Amazon OpenSearch Service
Managed search, analytics, and log ingestion service.

### 1. Definition
Amazon OpenSearch Service provides full-text search, log analytics, dashboards, and distributed indexing using OpenSearch/Elasticsearch engines.

### 2. Use-Cases
- Log analytics (ELK stack)  
- Search engines for applications  
- Real-time observability dashboards  

### 3. Additional Info
- Integrates with Kinesis, Firehose, CloudWatch Logs  

### 4. Limitations
- Cluster scaling requires planning  
- Hot-warm tiering optional but complex  

### 5. Details
- **Characteristics:** Distributed search; indices; clusters  
- **Capabilities:** Full-text search; Kibana/OpenSearch Dashboards  
- **Pricing Model:** Instance-hour + storage  
- **Security/IAM:** Fine-grained access control; IAM; KMS  

### 6. Confusable Services
- CloudWatch Logs (log storage), Athena (ad-hoc queries)  

### 7. Exam Notes
- “Search,” “ELK,” “Kibana/OpenSearch dashboards” → OpenSearch  


---

## 07-security


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


---

## 08-management


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


---

## 09-app_integration


# Application Integration

## Amazon EventBridge
### 1. Definition
EventBridge is a serverless event bus for routing events between AWS services, SaaS apps, and custom applications.

### 2. Use-Cases
- Event-driven architectures  
- Decoupling microservices  
- Integrating SaaS event sources  

### 3. Additional Info
- Event buses: default, custom, partner  
- Schema registry available  

### 4. Limitations
- Not designed for high-throughput messaging like Kinesis  

### 5. Details
- **Characteristics:** Serverless event bus  
- **Capabilities:** Rules; filtering; buses; archives; replays  
- **Pricing Model:** Per-event publish/invoke  
- **Security/IAM:** IAM; resource policies  

### 6. Confusable
- SNS/SQS (messaging), Step Functions  

### 7. Exam Notes
- “Event bus,” “routing,” “SaaS events” → EventBridge  


## Amazon SQS
### 1. Definition
Simple Queue Service provides fully managed message queues for decoupling distributed systems.

### 2. Use-Cases
- Asynchronous workloads  
- Buffering requests  
- Reliable message delivery  

### 3. Additional Info
- Queue types: Standard and FIFO  

### 4. Limitations
- No push delivery (polling needed unless using Lambda triggers)  

### 5. Details
- **Characteristics:** Queue-based messaging  
- **Capabilities:** DLQs; visibility timeout; large messages  
- **Pricing Model:** Per-request  
- **Security/IAM:** IAM policies; SSE encryption  

### 6. Confusable
- SNS (pub/sub), EventBridge  

### 7. Exam Notes
- “Decoupling with queues,” “FIFO ordering” → SQS  


## Amazon SNS
### 1. Definition
SNS is a managed pub/sub messaging service for fanout delivery to multiple subscribers.

### 2. Use-Cases
- Broadcasting notifications  
- Fanout to SQS queues  
- Mobile push or email alerts  

### 3. Additional Info
- Supports topics, subscriptions, mobile push  

### 4. Limitations
- No message persistence (use SQS for that)  

### 5. Details
- **Characteristics:** Pub/Sub  
- **Capabilities:** SMS/email/mobile push; SQS fanout  
- **Pricing Model:** Per-request + delivery costs  
- **Security/IAM:** IAM; topic policies  

### 6. Confusable
- SQS (queue), EventBridge  

### 7. Exam Notes
- “Pub/sub,” “fanout,” “notifications” → SNS  


## Application Load Balancer (ALB)
### 1. Definition
ALB is a layer 7 load balancer that routes HTTP/HTTPS traffic based on content and application-level rules.

### 2. Use-Cases
- Routing for microservices  
- Path/host-based routing  
- Advanced request inspection  

### 3. Additional Info
- Supports WebSockets, gRPC, and authentication  

### 4. Limitations
- Not for TCP/UDP (use NLB)  

### 5. Details
- **Characteristics:** Layer 7 routing  
- **Capabilities:** Rules; host/path routing; auth; sticky sessions  
- **Pricing Model:** Per-LCU + hourly  
- **Security/IAM:** SGs; IAM for auth; WAF integration  

### 6. Confusable
- NLB (TCP/UDP), API Gateway  

### 7. Exam Notes
- “Layer 7,” “path-based routing,” “microservices” → ALB  


---

## 10-developer_tools


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


---

## 11-frontend_mobile


# Frontend & Mobile

## AWS Amplify
### 1. Definition
AWS Amplify is a frontend and mobile development platform that provides hosting, authentication, APIs, storage, and CI/CD for web and mobile apps.

### 2. Use-Cases
- Full-stack web/mobile app development  
- Fast backend provisioning with Amplify Studio  
- Managed hosting and deployments  

### 3. Additional Info
- Integrates with Cognito, AppSync, S3, Lambda, IAM  

### 4. Limitations
- Abstracted architecture may limit fine-grained control  

### 5. Details
- **Characteristics:** Frontend + backend development platform  
- **Capabilities:** Hosting; auth; DataStore; API generation; CI/CD  
- **Pricing Model:** Hosting + backend resource usage  
- **Security/IAM:** IAM roles; Cognito auth  

### 6. Confusable
- AppSync (GraphQL API), CloudFront (CDN hosting)  

### 7. Exam Notes
- “Frontend platform,” “hosting + auth,” “Amplify Studio” → Amplify  


## AWS AppSync
### 1. Definition
AWS AppSync is a fully managed GraphQL API service for building real-time, offline-capable applications.

### 2. Use-Cases
- Unified GraphQL APIs  
- Real-time apps with subscriptions  
- Offline-first mobile apps  

### 3. Additional Info
- Data sources: DynamoDB, Lambda, RDS, Elasticsearch, HTTP endpoints  

### 4. Limitations
- Requires GraphQL schema design expertise  

### 5. Details
- **Characteristics:** Managed GraphQL  
- **Capabilities:** Subscriptions; resolvers; caching  
- **Pricing Model:** Per-request + real-time messages  
- **Security/IAM:** IAM; API keys; Cognito; OIDC  

### 6. Confusable
- API Gateway (REST/HTTP), Amplify  

### 7. Exam Notes
- “GraphQL,” “real-time subscriptions,” “offline-ready apps” → AppSync  


---

## 12-business_apps


# Business Applications

## Amazon Connect
### 1. Definition
Amazon Connect is a cloud-based contact center service providing voice, chat, and omnichannel customer engagement with built-in analytics and AI-driven interactions.

### 2. Use-Cases
- Customer support centers  
- Automated call routing and IVR  
- AI-driven chat/voice bots via Lex  

### 3. Additional Info
- Integrates with Lex, Kinesis, Lambda, S3, Bedrock Q apps  

### 4. Limitations
- Requires configuration of call flows and telephony  

### 5. Details
- **Characteristics:** Cloud contact center; scalable  
- **Capabilities:** Call routing; analytics; real-time dashboards; recordings  
- **Pricing Model:** Pay-per-minute + telephony  
- **Security/IAM:** IAM; KMS; PCI compliance options  

### 6. Confusable
- SNS/SQS (messaging), Pinpoint (marketing)  

### 7. Exam Notes
- “Cloud contact center,” “IVR,” “omnichannel support” → Connect  


## Amazon Simple Email Service (SES)
### 1. Definition
SES is a scalable email platform for transactional, marketing, and bulk email sending with deliverability features.

### 2. Use-Cases
- Transactional emails (password resets, receipts)  
- Marketing campaigns  
- SMTP relay for applications  

### 3. Additional Info
- Supports DKIM, SPF, domain verification  

### 4. Limitations
- Sandbox mode limits sending until verified  

### 5. Details
- **Characteristics:** Email sending engine  
- **Capabilities:** SMTP interface; APIs; analytics; reputation management  
- **Pricing Model:** Per-email + data transfer  
- **Security/IAM:** IAM; encryption in-transit  

### 6. Confusable
- Pinpoint (marketing automation), SNS (notifications)  

### 7. Exam Notes
- “Transactional email,” “SMTP,” “deliverability” → SES  


---

## 13-end_user_computing


# End-User Computing

## Amazon AppStream 2.0
### 1. Definition
Amazon AppStream 2.0 is a managed application streaming service that streams desktop applications to users without needing local installation.

### 2. Use-Cases
- Delivering GPU/CPU-intensive apps  
- Secure access to corporate software  
- Reducing endpoint management overhead  

### 3. Additional Info
- Supports fleets, image builders, and scaling policies  

### 4. Limitations
- Requires network optimization for best user experience  

### 5. Details
- **Characteristics:** Application streaming; scalable  
- **Capabilities:** Multi-session streaming; GPU support; persistent settings  
- **Pricing Model:** Per-hour per-streaming-instance  
- **Security/IAM:** IAM; VPC; KMS; SSO integrations  

### 6. Confusable
- WorkSpaces (full desktops), WorkSpaces Secure Browser  

### 7. Exam Notes
- “Stream applications only,” “no full desktop” → AppStream 2.0  


## Amazon WorkSpaces
### 1. Definition
Amazon WorkSpaces is a managed Virtual Desktop Infrastructure (VDI) service providing Windows or Linux desktops in the cloud.

### 2. Use-Cases
- Remote workforce enablement  
- Secure desktop environments  
- BYOD or low-power devices  

### 3. Additional Info
- Supports persistent and non-persistent desktops  

### 4. Limitations
- Desktop management required unless using WorkSpaces Web/Secure Browser  

### 5. Details
- **Characteristics:** Managed VDI; persistent desktops  
- **Capabilities:** Directory integration; GPU bundles; multi-session  
- **Pricing Model:** Monthly or hourly per-desktop  
- **Security/IAM:** IAM; KMS; directory services; network isolation  

### 6. Confusable
- AppStream 2.0 (apps only), Secure Browser (lightweight)  

### 7. Exam Notes
- “Full desktop,” “Windows/Linux VDI” → WorkSpaces  


## WorkSpaces Secure Browser
### 1. Definition
WorkSpaces Secure Browser provides secure, isolated browser sessions streamed from AWS for accessing internal or SaaS applications.

### 2. Use-Cases
- Zero-trust secure browsing  
- Preventing data exfiltration via browser  
- Third-party contractor access  

### 3. Additional Info
- Replace for Amazon WorkSpaces Web (rebranded)  

### 4. Limitations
- Browser-only; no desktop or app streaming  

### 5. Details
- **Characteristics:** Managed isolated browser  
- **Capabilities:** Web isolation; policy controls; session logging  
- **Pricing Model:** Per-hour streaming session  
- **Security/IAM:** IAM; KMS; SSO; network controls  

### 6. Confusable
- AppStream 2.0 (apps), WorkSpaces (desktops)  

### 7. Exam Notes
- “Secure isolated browser,” “zero-trust access” → Secure Browser  


---

## 14-iot


# IoT

## AWS IoT Core
### 1. Definition
AWS IoT Core is a managed cloud service that connects IoT devices to AWS securely, supporting message routing, device shadows, MQTT, HTTP, and WebSockets.

### 2. Use-Cases
- Real-time IoT telemetry ingestion  
- Device management and state sync  
- Triggering downstream processing (Lambda, Kinesis, etc.)  

### 3. Additional Info
- Supports MQTT topics, rules engine, and Device Shadow service  

### 4. Limitations
- Does not run local compute on devices (use Greengrass)  

### 5. Details
- **Characteristics:** Managed device connectivity; event routing  
- **Capabilities:** Pub/sub messaging; rules; Shadows; Just-In-Time Registration  
- **Pricing Model:** Messaging, rules evaluations, device connectivity  
- **Security/IAM:** X.509 certificates; IAM policies; fine-grained topic access  

### 6. Confusable
- IoT Greengrass (local compute), Kinesis (streaming)  

### 7. Exam Notes
- “Device Shadows,” “MQTT,” “connect devices to AWS” → IoT Core  


## AWS IoT Greengrass
### 1. Definition
IoT Greengrass extends AWS to edge devices, enabling local compute, messaging, ML inference, and sync with the cloud.

### 2. Use-Cases
- Offline or intermittent connectivity workloads  
- Local ML inference on devices  
- Secure local messaging and device orchestration  

### 3. Additional Info
- Deploy Lambda functions, containers, and connectors to devices  

### 4. Limitations
- Requires capable edge hardware  
- Must manage software updates on devices  

### 5. Details
- **Characteristics:** Edge compute; offline-capable  
- **Capabilities:** Local messaging; ML inference; sync; container/Lambda execution  
- **Pricing Model:** Per-device tiering  
- **Security/IAM:** X.509 certs; IAM; secure local runtime  

### 6. Confusable
- IoT Core (cloud messaging), Snowball Edge (heavier compute)  

### 7. Exam Notes
- “Local compute,” “offline operation,” “edge ML” → Greengrass  


---

## 15-migration_transfer


# Migration & Transfer

## AWS Migration Hub
### 1. Definition
AWS Migration Hub provides a central location to track, orchestrate, and monitor application migrations across multiple AWS and partner tools.

### 2. Use-Cases
- Unified migration tracking  
- Visibility across DMS, Application Discovery Service, and partner tools  

### 3. Additional Info
- Does not perform migrations itself—tracks them  

### 4. Limitations
- Depends on integrated tools for actual migration tasks  

### 5. Details
- **Characteristics:** Central migration dashboard  
- **Capabilities:** Progress tracking; analytics; grouping resources  
- **Pricing Model:** Free  
- **Security/IAM:** IAM  

### 6. Confusable
- Application Discovery Service (data collection)  

### 7. Exam Notes
- “Single place to track migrations” → Migration Hub  


## AWS Application Discovery Service
### 1. Definition
Application Discovery Service collects on-premises server, application, and dependency data to help plan migrations.

### 2. Use-Cases
- Migration readiness assessment  
- Understanding server dependencies  
- Inventorying on-prem workloads  

### 3. Additional Info
- Agentless and agent-based modes  

### 4. Limitations
- Only for discovery; does not move workloads  

### 5. Details
- **Characteristics:** Discovery + dependency mapping  
- **Capabilities:** Performance data; dependency graphs  
- **Pricing Model:** Free  
- **Security/IAM:** IAM; encrypted data transfer  

### 6. Confusable
- Migration Hub (tracking), DMS (database migration)  

### 7. Exam Notes
- “Application dependency mapping,” “on-prem discovery” → ADS  


## AWS Database Migration Service (DMS)
### 1. Definition
DMS migrates and replicates databases to AWS with minimal downtime, supporting homogeneous and heterogeneous migrations.

### 2. Use-Cases
- Moving databases to AWS  
- Ongoing replication (CDC)  
- Cross-engine conversions (via SCT)  

### 3. Additional Info
- Requires a replication instance  

### 4. Limitations
- Schema conversion must be done with SCT  

### 5. Details
- **Characteristics:** Managed migration service  
- **Capabilities:** Full load + CDC; continuous replication  
- **Pricing Model:** Per-hour for replication instance  
- **Security/IAM:** IAM; KMS; network isolation  

### 6. Confusable
- SCT (schema change), DataSync (file-level)  

### 7. Exam Notes
- “Minimal downtime,” “CDC,” “replication instance” → DMS  


## AWS Schema Conversion Tool (SCT)
### 1. Definition
SCT converts database schemas and code objects for heterogeneous migrations (e.g., Oracle → Aurora).

### 2. Use-Cases
- Migrating between different DB engines  
- Automated schema conversion  

### 3. Additional Info
- Can assess conversion complexity  

### 4. Limitations
- Not a database migration engine (use DMS)  

### 5. Details
- **Characteristics:** Schema transformer  
- **Capabilities:** Schema/object conversion; assessment reports  
- **Pricing Model:** Free  
- **Security/IAM:** Local tool + IAM for cloud access  

### 6. Confusable
- DMS (data migration), ADS  

### 7. Exam Notes
- “Heterogeneous migrations,” “schema conversion” → SCT  


## Migration Evaluator
### 1. Definition
Migration Evaluator provides cost modeling and business case analysis for migrating workloads to AWS.

### 2. Use-Cases
- Estimating TCO for migrations  
- Right-sizing recommendations  
- Building migration business cases  

### 3. Additional Info
- Uses on-prem inventory + utilization data  

### 4. Limitations
- Assessment accuracy depends on data quality  

### 5. Details
- **Characteristics:** Migration cost assessment  
- **Capabilities:** TCO modeling; usage analytics  
- **Pricing Model:** Free  
- **Security/IAM:** IAM  

### 6. Confusable
- Pricing Calculator (manual estimates), ADS (discovery)  

### 7. Exam Notes
- “TCO report,” “migration business case” → Migration Evaluator  


---

## 16-marketplace_partners


# Marketplace & Partners

## AWS Marketplace
### 1. Definition
AWS Marketplace is a curated digital catalog that allows customers to find, purchase, deploy, and manage third‑party software on AWS.

### 2. Use-Cases
- Procuring security, networking, DevOps, and data software  
- One‑click deployment of AMIs, SaaS, and container products  
- Streamlined procurement and billing  

### 3. Additional Info
- Supports private offers and license management  
- Integrated metering and consolidated billing  

### 4. Limitations
- Products vary in support and compliance depending on vendor  

### 5. Details
- **Characteristics:** Third‑party software catalog  
- **Capabilities:** AMI/SaaS delivery; private marketplace; procurement workflows  
- **Pricing Model:** Pay‑as‑you‑go or subscription; billed via AWS  
- **Security/IAM:** IAM permissions; license governance  

### 6. Confusable
- Service Catalog (internal products), License Manager  

### 7. Exam Notes
- “Third‑party software acquisition,” “private offers,” “AWS‑billed SaaS” → Marketplace  


## AWS Partner Network (APN)
### 1. Definition
The AWS Partner Network is a global program for technology and consulting partners that build and integrate solutions on AWS.

### 2. Use-Cases
- Finding consulting partners for migration, ML, or modernization  
- Accessing partner software validated by AWS  
- Co‑selling and solution delivery with certified vendors  

### 3. Additional Info
- Includes tiers: Select, Advanced, Premier  
- Competency programs for specialization  

### 4. Limitations
- Requires evaluation for partner fit and competency  

### 5. Details
- **Characteristics:** Partner ecosystem  
- **Capabilities:** Consulting, technology integrations, funding programs  
- **Pricing Model:** No customer cost; partner fees vary internally  
- **Security/IAM:** Partners access via IAM/StS when needed  

### 6. Confusable
- Marketplace (software only), Professional Services  

### 7. Exam Notes
- “AWS partner ecosystem,” “competencies,” “consulting partners” → APN  


---

