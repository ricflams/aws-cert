# Cloud Practitioner - AWS Services

## Table of Contents

<img src="icons/category/Arch-Category_16/Arch-Category_Compute_16.png" alt="icon" width="16" height="16"> [Compute](#-compute)
<img src="icons/category/Arch-Category_16/Arch-Category_Networking-Content-Delivery_16.png" alt="icon" width="16" height="16"> [Networking and Content Delivery](#-networking-and-content-delivery)
<img src="icons/category/Arch-Category_16/Arch-Category_Storage_16.png" alt="icon" width="16" height="16"> [Storage](#-storage)
<img src="icons/category/Arch-Category_16/Arch-Category_Database_16.png" alt="icon" width="16" height="16"> [Databases](#databases)
<img src="icons/category/Arch-Category_16/Arch-Category_Artificial-Intelligence_16.png" alt="icon" width="16" height="16"> [AI and Machine Learning](#-ai-and-machine-learning)
<img src="icons/category/Arch-Category_16/Arch-Category_Analytics_16.png" alt="icon" width="16" height="16"> [Analytics](#-analytics)
<img src="icons/category/Arch-Category_16/Arch-Category_Security-Identity-Compliance_16.png" alt="icon" width="16" height="16"> [Security, Identity, and Compliance](#-security-identity-and-compliance)
<img src="icons/category/Arch-Category_16/Arch-Category_Management-Governance_16.png" alt="icon" width="16" height="16"> [Management and Governance](#-management-and-governance)
<img src="icons/category/Arch-Category_16/Arch-Category_Application-Integration_16.png" alt="icon" width="16" height="16"> [Application Integration](#-application-integration)
<img src="icons/category/Arch-Category_16/Arch-Category_Developer-Tools_16.png" alt="icon" width="16" height="16"> [Developer Tools](#-developer-tools)
<img src="icons/category/Arch-Category_16/Arch-Category_Front-End-Web-Mobile_16.png" alt="icon" width="16" height="16"> [Frontend and Mobile](#-frontend-and-mobile)
<img src="icons/category/Arch-Category_16/Arch-Category_Business-Applications_16.png" alt="icon" width="16" height="16"> [Business Applications](#-business-applications)
<img src="icons/category/Arch-Category_16/Arch-Category_End-User-Computing_16.png" alt="icon" width="16" height="16"> [End-User Computing](#-end-user-computing)
<img src="icons/category/Arch-Category_16/Arch-Category_Internet-of-Things_16.png" alt="icon" width="16" height="16"> [Iot](#-iot)
<img src="icons/category/Arch-Category_16/Arch-Category_Migration-Modernization_16.png" alt="icon" width="16" height="16"> [Migration and Transfer](#-migration-and-transfer)
<img src="icons/service/Arch_General-Icons/16/Arch_AWS-Marketplace_Light_16.png" alt="icon" width="16" height="16"> [Marketplace and Partners](#-marketplace-and-partners)
✅ [Summary](#-summary)

---

# ![icon](icons/category/Arch-Category_16/Arch-Category_Compute_16.png) Compute

Compute is about **actually running your application’s code**—on servers, containers, or serverless functions.
It gives you the processing power your workloads need, whenever they need it.
Its core intent is to execute code efficiently, elastically, and in the form that best fits your architecture.

## ![icon](icons/service/Arch_Compute/16/Arch_Amazon-EC2_16.png) Amazon EC2

Amazon Elastic Compute Cloud (EC2) provides resizable compute capacity in the cloud.

### 1. Definition

Amazon EC2 is a web service that provides secure, resizable compute capacity using virtual machines called instances. It offers a wide selection of instance types optimized for compute, memory, storage, and GPU needs. EC2 gives deep OS-level control, customizable networking, and flexible purchasing models such as On-Demand, Reserved, Spot, and Savings Plans. It integrates closely with EBS for block storage, VPC for networking, IAM for security, and Auto Scaling for elasticity.

### 2. Use-Cases

- Lift-and-shift of on-prem servers
- Long-running workloads requiring OS-level customization
- High-performance computing, GPU workloads, enterprise applications

### 3. Additional Info

- Purchasing models, in order or how expensive they are:
  - Spot Instances: Deeply discounted spare EC2 capacity with the risk of termination; best for fault-tolerant or flexible workloads.
  - Savings Plans: Commit to a consistent hourly spend for 1–3 years; most flexible discount model covering EC2, Fargate, and Lambda usage.
  - Reserved Instances (RI): 1–3 year commitment for significant discounts; ideal for steady, predictable workloads requiring consistent capacity.
  - Convertible Reserved Instances: Like RIs but allow changing instance families, OS, or tenancy during the term; slightly smaller discount than Standard RIs.
  - Zonal Reserved Instances: Reserved Instances locked to a specific AZ, providing both a capacity reservation and a discount.
  - On-Demand Instances: Pay by the second or hour with no long-term commitment; best for unpredictable or short-lived workloads.
  - Capacity Reservations: Reserve capacity in a specific AZ without long-term commitment; ensures availability but still charged at On-Demand rates unless paired with RIs or Savings Plans.
  - Dedicated Instances: Instances running on hardware isolated to a single customer; provides tenancy isolation without the licensing benefits of Dedicated Hosts.
  - Dedicated Hosts: Physical servers fully allocated to you; required for certain licensing models and compliance where host-level visibility is needed.
- Instance types:
  - General Purpose (t3/t4g, m5/m6g): Balanced compute, memory, and networking; ideal default choice for most workloads needing general versatility.
  - Compute Optimized (c5/c6g): High-performance processors optimized for compute-intensive tasks like gaming servers, scientific modeling, and batch processing.
  - Memory Optimized (r5/r6g, x2idn/x2iedn, z1d): Designed for large, in-memory datasets such as databases, caching tiers, and real-time analytics.
  - Storage Optimized (i3/i4i, d2/d3, h1): Built for high-throughput and low-latency local NVMe storage; ideal for NoSQL databases, data warehousing, and Hadoop workloads.
  - Accelerated Computing (p3/p4, g4/g5, inf1/inf2, trn1): Use GPUs or specialized accelerators for machine learning training/inference, HPC simulations, and graphics workloads.
  - Burstable Performance (t3/t4g): Provide baseline CPU with the ability to burst; ideal for variable workloads that are mostly idle but occasionally need more CPU.
  - High Memory (u-6tb1, u-12tb1, u-24tb1): Extremely large memory instances for SAP HANA and other enterprise in-memory databases.
  - Density Storage (d2/d3/d3en): High-disk-capacity instances optimized for distributed storage workloads and large file systems.
  - HPC Instances (hpc6a/hpc7g): Specialized for tightly coupled, compute-heavy HPC workloads, offering high network throughput and low latency.
  - Arm-Based Instances (a1, m6g, c6g, r6g, t4g): Powered by AWS Graviton processors; cheaper and energy-efficient, recommended whenever workloads support Arm.
  - Instance Store Instances (i3/i4, d3/d3en): Provide ephemeral NVMe local storage with extremely high IOPS for temporary or scratch data.
  - Network Optimized (m5n/m6in, r5n/r6in): Provide increased network bandwidth for network-heavy applications or distributed workloads.

### 4. Limitations

- Requires OS and patch management
- Not serverless; scaling must be configured

### 5. Details

- Characteristics
  - Type: Virtual machine compute
  - Mode: Customer-managed OS, AWS-managed hardware
  - Performance: Depends on instance type; enhanced networking available
  - Durability/HA: AZ-specific; multi-AZ via Auto Scaling
  - Scope: Regional (instances run in specific AZs)
- Capabilities
  - Full OS access, custom AMIs
  - Flexible networking (ENIs, SGs, VPC)
  - Multiple purchasing models
  - Integration with EBS, SSM, Auto Scaling, ELB
- Pricing Model
  - Per-second or per-hour instance cost; varies by type, OS, region, model
- Security / IAM
  - IAM instance profiles, SGs, NACLs, encrypted EBS, SSM access

### 6. Confusable Services

- Amazon Lightsail: Both provide virtual servers, but Lightsail is simplified/prescribed while EC2 is fully flexible and configurable.
- AWS Lambda: Both run application code, but EC2 manages full servers while Lambda runs functions without managing instances.
- AWS Fargate: Both run application workloads, but EC2 exposes the underlying instances while Fargate abstracts them away for containers.
- Amazon ECS: Both are used for application hosting, but ECS is a container orchestration service that can use EC2 as the compute layer.
- Amazon EKS: Both can run scalable workloads, but EKS manages Kubernetes clusters while EC2 is just raw compute.
- AWS Elastic Beanstalk: Both host web applications, but Beanstalk is a PaaS layer that provisions and manages EC2 and related resources for you.

### 7. Exam Notes

- Reserved Instances vs Savings Plans: RIs apply mainly to EC2 while Savings Plans cover EC2, Fargate, and Lambda; exams often expect Savings Plans for flexibility.
- On-Demand vs Spot: If workload is “flexible”, “interruptible”, or “batch”, Spot is expected; otherwise use On-Demand or a discount model.
- On-Demand vs Savings Plans: 24/7 workloads almost never justify On-Demand; exam expects Savings Plans or RIs.
- Savings Plans Scope: Compute Savings Plans cover EC2, Fargate, and Lambda; Instance Savings Plans only apply to EC2 with instance-family and region restrictions.
- Dedicated Hosts vs Dedicated Instances: Dedicated Hosts expose physical host resources for licensing needs, while Dedicated Instances provide only tenancy isolation.
- Capacity Reservations: Reserve capacity but do not reduce cost unless paired with RIs or Savings Plans; common exam trick.
- Bursting Workloads: For spiky traffic needing guaranteed availability, choose On-Demand with Auto Scaling, not Spot.
- Predictable Workloads: Predictable, steady workloads are expected to use Reserved Instances or Savings Plans, not On-Demand.
- License-Restricted Workloads: Requirements like per-core/per-socket licensing imply the need for Dedicated Hosts.

## ![icon](icons/service/Arch_Compute/16/Arch_Amazon-EC2-Auto-Scaling_16.png) Amazon EC2 Auto Scaling

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

- Characteristics
  - Type: Automated capacity management for EC2
  - Mode: Metric-driven or schedule-based scaling
  - Performance: Responds to CloudWatch metrics
  - Durability/HA: Multi-AZ placement; automatic replacement of unhealthy instances
  - Scope: Regional
- Capabilities
  - Maintain desired EC2 instance count
  - Replace unhealthy instances automatically
  - Scale based on CPU, ALB request count, custom metrics
- Pricing Model
  - No cost for the scaling service; pay for EC2, ELB, and CloudWatch usage
- Security / IAM
  - IAM roles for ASG operations, instance profiles; SGs/NACLs control access

### 6. Confusable Services

- AWS Auto Scaling (generic): Both mention “Auto Scaling,” but EC2 Auto Scaling is specifically for EC2 groups while AWS Auto Scaling can handle multiple resource types and scaling plans.
- AWS Lambda: Both can react to demand, but Lambda scales functions automatically while EC2 Auto Scaling scales instance counts in an Auto Scaling Group.
- AWS Fargate with ECS/EKS: Both adjust capacity, but EC2 Auto Scaling changes instance counts while Fargate scales container tasks without visible instances.
- Elastic Load Balancing: Both appear in scalable architectures, but ELB distributes traffic while Auto Scaling adjusts the number of instances.

### 7. Exam Notes

- Keywords: “Maintain desired capacity,” “scale EC2 instances,” “replace unhealthy instances.”
- Use target tracking for simple, metric-based scaling.
- Multi-AZ HA requires ASG spanning multiple subnets.

## ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_Elastic-Load-Balancing_16.png) Elastic Load Balancing (ELB)

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

- Characteristics
  - Type: Managed load balancing service
  - Mode: Fully managed, scales automatically
  - Performance: High throughput; NLB supports millions of requests per second
  - Durability/HA: Multi-AZ distributed nodes
  - Scope: Regional
- Capabilities
  - Health checks and failover
  - HTTPS termination (ALB/NLB)
  - Routing rules, listener rules, WebSockets (ALB)
- Pricing Model
  - Charged per Load Balancer-hour + LCU (ALB/NLB) + data processing
- Security / IAM
  - Security groups (ALB), IAM for certificate management, integration with ACM and WAF

### 6. Confusable Services

- Amazon API Gateway: Both accept and route HTTP(S) requests, but ELB routes to services inside a VPC while API Gateway is an API management layer with features like throttling and auth.
- Amazon CloudFront: Both deal with incoming web traffic, but CloudFront is a CDN cache at the edge while ELB is a regional load balancer in front of backends.
- AWS Global Accelerator: Both improve client-to-application connectivity, but Global Accelerator provides static anycast IPs and routing on the AWS backbone while ELB is just the regional endpoint.
- Amazon Route 53: Both influence how clients reach your app, but Route 53 does DNS-based resolution while ELB actually terminates and distributes traffic.

### 7. Exam Notes

- ALB = path/host routing, HTTP/HTTPS, WebSockets.
- NLB = extreme performance, TCP/UDP, static IPs.
- ELB + Auto Scaling = high availability and elasticity.

## ![icon](icons/service/Arch_Compute/16/Arch_AWS-Lambda_16.png) AWS Lambda

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

- Characteristics
  - Type: Serverless function compute
  - Mode: Event-driven, fully managed
  - Performance: Auto-scales concurrency; cold starts possible
  - Durability/HA: Highly available across multiple AZs
  - Scope: Regional
- Capabilities
  - Run code in response to events or schedules
  - Integrate widely across AWS
  - Support layers, environment variables, versions/aliases
- Pricing Model
  - Pay per request + per GB-second of compute time
  - Optional charges for provisioned concurrency
- Security / IAM
  - IAM execution roles, VPC access, resource-based policies for triggers

### 6. Confusable Services

- AWS Fargate: Both are “serverless-like” compute options, but Lambda runs short-lived functions while Fargate runs long-lived containers.
- Amazon EC2: Both run application code, but EC2 requires instance management while Lambda is fully managed and event-driven.
- AWS Elastic Beanstalk: Both simplify app hosting, but Beanstalk manages servers while Lambda eliminates servers entirely.
- Amazon API Gateway: Often paired in diagrams, but API Gateway is the front-door for HTTP APIs while Lambda is the compute backend.

### 7. Exam Notes

- Keywords: “run code without servers,” “event-driven,” “pay only for compute time.”
- Common pairing: API Gateway + Lambda = serverless API.
- S3 upload triggers, DynamoDB/Kinesis stream processing often indicate Lambda.

## ![icon](icons/service/Arch_Containers/16/Arch_AWS-Fargate_16.png) AWS Fargate

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

- Characteristics
  - Type: Serverless container compute
  - Mode: Managed execution of ECS tasks or EKS pods
  - Performance: Automatic scaling without cluster capacity planning
  - Durability/HA: Multi-AZ support through ECS/EKS configuration
  - Scope: Regional
- Capabilities
  - Run containers without EC2 provisioning
  - Fine-grained task-level resource assignment
  - Full VPC networking for each task/pod
- Pricing Model
  - Pay per vCPU-second and GB-second for running tasks/pods
- Security / IAM
  - IAM roles for tasks; SGs and VPC networking; strong isolation boundaries

### 6. Confusable Services

- Amazon EC2: Both provide compute for applications, but EC2 exposes instances while Fargate hides them and just runs containers.
- AWS Lambda: Both are serverless compute options, but Lambda is function-level while Fargate is container-level.
- Amazon ECS: Fargate is often confused with ECS because both are mentioned together; ECS is the orchestrator, Fargate is the serverless runtime for ECS tasks.
- Amazon EKS: Fargate can also be used with EKS, leading to confusion between the managed Kubernetes control plane (EKS) and the serverless node runtime (Fargate).

### 7. Exam Notes

- Keywords: “run containers without managing servers,” “serverless containers.”
- Appears in questions involving ECS/EKS + no infrastructure management.
- Great answer when containerization is required but ops overhead must be minimized.

## ![icon](icons/service/Arch_Containers/16/Arch_Amazon-Elastic-Container-Service_16.png) Amazon Elastic Container Service (Amazon ECS)

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

- Characteristics
  - Type: Managed container orchestration
  - Mode: ECS control plane + EC2 or Fargate compute
  - Performance: Scales with number of containers and cluster resources
  - Durability/HA: Multi-AZ capable with load balancers and Auto Scaling
  - Scope: Regional
- Capabilities
  - Run, scale, and manage containerized applications
  - Integrated service discovery, auto scaling, deployment strategies
  - Task-level IAM roles and CloudWatch monitoring
- Pricing Model
  - ECS control plane is free; pay for EC2 or Fargate resources
- Security / IAM
  - Task roles, execution roles, SGs, VPC networking, encryption options

### 6. Confusable Services

- Amazon EKS: Both are container orchestration services, but ECS is AWS-native while EKS is managed Kubernetes.
- AWS Fargate: Both appear in container architectures, but ECS is the orchestrator while Fargate is one of the compute options (instead of EC2).
- AWS Lambda: Both can run microservices, but Lambda is function-based serverless while ECS is container-based.

### 7. Exam Notes

- ECS is often the answer when AWS-native container orchestration is desired.
- ECS + Fargate is common for fully managed container deployments.
- ECS + EC2 provides more control but requires node management.

## ![icon](icons/service/Arch_Containers/16/Arch_Amazon-Elastic-Kubernetes-Service_16.png) Amazon Elastic Kubernetes Service (Amazon EKS)

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

- Characteristics
  - Type: Managed Kubernetes control plane
  - Mode: Customer-managed workers; AWS-managed control plane
  - Performance: Highly available, auto-scaled control plane
  - Durability/HA: Multi-AZ control plane with automatic failover
  - Scope: Regional
- Capabilities
  - Run standard Kubernetes workloads
  - Integrate with VPC networking, IAM authentication, ALB/NLB ingress
  - Support EKS add-ons, cluster autoscaling, service mesh tools
- Pricing Model
  - Per-cluster fee + EC2 or Fargate costs for nodes/pods
- Security / IAM
  - IAM authentication for Kubernetes API
  - Security groups, network policies, service accounts (IRSA)

### 6. Confusable Services

- Amazon ECS: Both manage containers, but ECS is AWS-native orchestration while EKS is managed Kubernetes.
- AWS Fargate: Both are mentioned in “serverless containers” contexts, but EKS is the Kubernetes control plane while Fargate is an optional serverless data plane.
- Amazon EC2: Both appear when running worker nodes, but EC2 is just the instances while EKS is the cluster control plane running on top.

### 7. Exam Notes

- If the question explicitly mentions “Kubernetes,” “kubectl,” “Helm,” or multi-cloud portability → EKS.
- EKS control plane is fully managed by AWS; customers manage only nodes.
- IRSA (IAM Roles for Service Accounts) often appears in security questions.

## ![icon](icons/service/Arch_Containers/16/Arch_Amazon-Elastic-Container-Registry_16.png) Amazon Elastic Container Registry (Amazon ECR)

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

- Characteristics
  - Type: Managed container image registry
  - Mode: Fully managed with high availability
  - Performance: Optimized for low-latency pulls by ECS/EKS/Fargate
  - Durability/HA: Multi-AZ storage
  - Scope: Regional
- Capabilities
  - Store, pull, and push Docker images
  - Integrate with container orchestrators and build systems
  - Enforce lifecycle management and vulnerability scanning
- Pricing Model
  - Charged for storage + data transfer (pull/push)
- Security / IAM
  - IAM permissions for pushing/pulling
  - Encryption at rest (KMS optional)
  - Private or public repositories

### 6. Confusable Services

- Amazon S3: Both can store artifacts, but ECR is a container image registry whereas S3 is general-purpose object storage.
- AWS CodeArtifact: Both store software artifacts, but ECR is specifically for container images while CodeArtifact stores packages like npm, Maven, or PyPI libraries.
- Docker Hub: Often compared conceptually, but Docker Hub is a public third-party registry while ECR is a private AWS-native registry.

### 7. Exam Notes

- Phrases like “store and manage container images on AWS” → ECR.
- CI/CD questions often include ECR + CodeBuild/CodePipeline.
- IAM restrictions on image access are commonly tested.

## ![icon](icons/service/Arch_Compute/16/Arch_AWS-Batch_16.png) AWS Batch

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

- Characteristics
  - Type: Managed batch scheduler and compute orchestrator
  - Mode: Uses EC2 or Fargate compute
  - Performance: Scales automatically based on queue depth
  - Durability/HA: Multi-AZ compute environments
  - Scope: Regional
- Capabilities
  - Automatic provisioning and scaling of compute resources
  - Job queuing, priorities, dependencies, retries
  - Integration with Spot Instances for cost savings
- Pricing Model
  - No charge for Batch itself; pay for underlying EC2/Fargate resources
- Security / IAM
  - IAM roles for jobs, compute environments, and container access

### 6. Confusable Services

- Amazon ECS: Both run containerized workloads, but ECS is a general container orchestrator while Batch is specialized for batch jobs and queues.
- AWS Lambda: Both are used for asynchronous processing, but Batch is for large-scale, long-running batch jobs, whereas Lambda is for short-lived function invocations.
- AWS Step Functions: Both orchestrate work, but Step Functions orchestrate stateful workflows while Batch focuses on scheduling and running compute jobs.

### 7. Exam Notes

- Keywords: “batch,” “queue,” “large-scale processing,” “automatic provisioning.”
- Spot Instances + AWS Batch = common cost optimization scenario.
- Use Batch for scheduled or triggered batch jobs that need compute at scale.

## ![icon](icons/service/Arch_Compute/16/Arch_AWS-Elastic-Beanstalk_16.png) AWS Elastic Beanstalk

Fully managed Platform-as-a-Service (PaaS) for deploying and scaling web applications without managing underlying infrastructure.

### 1. Definition

AWS Elastic Beanstalk deploys and scales web applications and services. It is a managed application deployment service that automates infrastructure provisioning, application deployment, load balancing, scaling, and monitoring. Developers upload application code (e.g., Java, .NET, Node.js, Python, Go, PHP, Ruby), and Beanstalk provisions the required resources such as EC2, Auto Scaling groups, security groups, and Elastic Load Balancers. Users can still access and customize the underlying infrastructure if desired.

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

- Characteristics
  - Type: Managed PaaS for web applications
  - Mode: Orchestrates EC2, ASG, ELB, RDS (optional), CloudWatch
  - Performance: Based on underlying EC2 instance types
  - Durability/HA: Multi-AZ support for load-balanced environments
  - Scope: Regional
- Capabilities
  - Automated application deployment and environment management
  - Built-in scaling, load balancing, and health monitoring
  - Full infrastructure visibility and optional customization
- Pricing Model
  - No extra cost for Beanstalk; pay for underlying AWS resources
- Security / IAM
  - IAM roles for Beanstalk service and EC2 instances
  - Security groups, VPC integration, and optional HTTPS via ACM

### 6. Confusable Services

- Amazon EC2: Both run web applications, but Beanstalk is a PaaS layer that provisions and manages EC2 and related resources for you.
- AWS Lambda: Both can host web backends, but Beanstalk manages servers while Lambda is fully serverless and event-driven.
- Amazon ECS: Both are application-hosting options, but ECS is container-centric while Beanstalk is code/app-centric.

### 7. Exam Notes

- Keywords: “deploy web application quickly,” “managed environment,” “no need to provision servers.”
- Beanstalk is ideal when teams want simplicity but optional low-level control.
- Load-balanced environments = multi-AZ HA automatically.

## ![icon](icons/service/Arch_Compute/16/Arch_Amazon-Lightsail_16.png) Amazon Lightsail

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

- Characteristics
  - Type: Simplified VPS compute service
  - Mode: Preconfigured bundles and blueprints
  - Performance: Suitable for small to moderate workloads
  - Durability/HA: Basic failover; not multi-AZ by default
  - Scope: Regional
- Capabilities
  - Quick provisioning of VPS instances with prebuilt stacks
  - Managed databases, object storage, and DNS
  - Static IPs and basic load balancing
- Pricing Model
  - Flat monthly bundles based on instance size and data transfer
- Security / IAM
  - Simplified security model; IAM used for account-level control

### 6. Confusable Services

- Amazon EC2: Both provide virtual servers, but Lightsail is opinionated and simpler, while EC2 is feature-rich and fully flexible.
- Elastic Beanstalk: Both target simpler app deployment, but Beanstalk automates AWS primitives while Lightsail provides an all-in-one “VPS-like” experience.
- Amazon RDS: Lightsail offers simple managed databases, which can be confused with full-featured RDS, but RDS has deeper engine and scaling capabilities.

### 7. Exam Notes

- Keywords: “simple VPS,” “predictable pricing,” “quick deployment.”
- Not for large-scale architectures; for simplicity and small projects.
- Includes blueprints like WordPress and LAMP for rapid deployment.

## ![icon](icons/service/Arch_Compute/16/Arch_AWS-Outposts-family_16.png) AWS Outposts

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

- Characteristics
  - Type: Hybrid cloud infrastructure deployed on-premises
  - Mode: AWS-managed hardware + Region-integrated control plane
  - Performance: Low-latency on-prem execution
  - Durability/HA: Depends on local rack redundancy and facility power
  - Scope: Physical location tied to a specific AWS Region
- Capabilities
  - Run AWS services locally with consistent APIs
  - Integrate with VPC networking extended to on-prem
  - Seamless hybrid operations with AWS tools and monitoring
- Pricing Model
  - Typically based on hardware configuration and multi-year terms
- Security / IAM
  - IAM, security groups, KMS encryption, and AWS networking apply

### 6. Confusable Services

- Amazon EC2: Both provide compute capacity, but EC2 is in AWS Regions while Outposts brings AWS-managed hardware to on-premises locations.
- VMware on AWS: Both involve hybrid environments, but Outposts exposes native AWS services on-prem while VMware on AWS is a managed VMware stack in AWS.
- Direct Connect: Both appear in hybrid architectures, but DX is a network link while Outposts is physical AWS infrastructure in your data center.

### 7. Exam Notes

- Keywords: “AWS services on-premises,” “hybrid deployment,” “data residency.”
- Outposts = AWS hardware shipped to your data center.
- Ideal for hybrid workloads with consistent tooling across environments.

## ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_Amazon-API-Gateway_16.png) Amazon API Gateway

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

- Characteristics
  - Type: Managed API gateway and integration layer
  - Mode: Works with serverless or server-based backends
  - Performance: Highly scalable; caching improves latency
  - Durability/HA: Multi-AZ highly available
  - Scope: Regional or edge-optimized (via CloudFront)
- Capabilities
  - Request/response transformation, validation, rate limiting
  - Authentication via IAM, Cognito, Lambda authorizers
  - API versioning, stages, and usage plans
- Pricing Model
  - Pay per API call + optional cache capacity
- Security / IAM
  - IAM permissions, Cognito authentication, API keys, Lambda authorizers

### 6. Confusable Services

- Elastic Load Balancing (ALB): Both terminate HTTP(S) traffic and route requests, but API Gateway is an API management layer (auth, throttling, stages), while ALB is a pure L7 load balancer.
- Amazon CloudFront: Both can sit in front of APIs, but CloudFront is a CDN for caching while API Gateway is for API request management and integration.
- AWS AppSync: Both expose APIs over HTTP, but AppSync is specifically for GraphQL APIs, while API Gateway is for REST/HTTP or WebSocket APIs.

### 7. Exam Notes

- Key phrases: “serverless API,” “front door to backend services,” “authentication,” “throttling.”
- HTTP APIs = cheaper, simpler alternative to REST APIs.
- API Gateway + Lambda appears frequently in serverless application questions.

---

# ![icon](icons/category/Arch-Category_16/Arch-Category_Networking-Content-Delivery_16.png) Networking and Content Delivery

Networking controls **how data travels** between users, services, and systems.
It ensures your applications are reachable, secure, and fast no matter where your customers are.
Its core intent is to provide reliable connections and global content delivery with low latency.

## ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_Amazon-Virtual-Private-Cloud_16.png) Amazon VPC

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

- Characteristics
  - Type: Virtual network environment
  - Mode: Fully customer-defined networking
  - Performance: High-speed internal network
  - Durability/HA: Multi-AZ architecture via subnets
  - Scope: Regional
- Capabilities
  - Complete network configuration control
  - Segmentation using subnets
  - Hybrid connectivity with VPN/DX
- Pricing Model
  - VPC itself is free; IGW, NAT, endpoints incur charges
- Security / IAM
  - SGs (stateful), NACLs (stateless), IAM for resource access

### 6. Confusable Services

- AWS Transit Gateway: Both relate to network connectivity, but VPC is the isolated network itself while TGW is a central hub connecting many VPCs and on-prem networks.
- VPC Peering: Both connect networks, but a VPC is the network boundary and peering is simply a point-to-point connection between VPCs.
- AWS Direct Connect: Both show up in networking diagrams, but DX is a physical/private link to AWS while VPC is the logical network environment inside AWS.

### 7. Exam Notes

- Public subnet = route to IGW
- SGs = stateful; NACLs = stateless
- VPC is Regional; subnets are AZ-scoped

## 🟪 Network topics

Not services as such.

### 🔹Subnets (Public/Private)

Subnets divide a VPC into AZ-scoped network segments and determine internet accessibility based on routing.

Subnets are subdivisions of a VPC’s CIDR block. A subnet in a single AZ becomes **public** when its route table has a route to an Internet Gateway (IGW); it remains **private** when it does not. Subnets enforce application-tier separation and govern east–west and north–south traffic patterns.

#### 2. Use-Cases

- Public web tier vs. private application/database tiers
- AZ-based fault isolation
- Controlling outbound and inbound connectivity

#### 3. Additional Info

- Public subnet → IGW route
- Private subnet → no IGW route; outbound enabled via NAT

#### 4. Limitations

- Cannot span AZs
- IP exhaustion if CIDR sized too small

#### 5. Details

- Characteristics: Network segment; AZ-scoped; high-throughput internal networking
- Capabilities: Traffic segmentation; public/private tiering; NAT/IGW routing
- Pricing Model: No charge for subnets; routing components may incur costs
- Security/IAM: Works with SGs and NACLs

#### 6. Confusable Services

- Route Tables: Both control traffic patterns, but route tables define routing rules while subnets define the IP address range and isolation boundary within a VPC.
- Security Groups: Both deal with traffic, but security groups filter instance-level traffic while subnets group resources and determine public/private reachability.
- Network ACLs: Both apply at the subnet boundary, but NACLs are stateless packet filters while subnets are structural IP partitions.
- Availability Zones: Both appear in diagrams about resilience, but AZs are physical locations while subnets are logical IP ranges within a VPC mapped to AZs.

#### 7. Exam Notes

- Public = IGW route; private = no IGW route
- NAT enables outbound for private subnets

### 🔹Security Groups and NACLs

Security Groups protect individual resources, and NACLs protect entire subnets.

They are complementary tools, but SGs are used far more commonly.

#### Security Groups (SGs)

- **Stateful virtual firewalls** that control inbound and outbound traffic at the **instance/ENI level**.
- **Return traffic is automatically allowed**, even if no explicit outbound rule exists (because they are stateful).
- **Deny rules do not exist**; you only specify what is permitted.
- Rules can use **CIDR blocks, security group IDs, or prefix lists** as sources/destinations.
- Applied at the **Elastic Network Interface (ENI)**, not at the subnet boundary.
- Evaluate **all rules**, and if any rule matches, traffic is allowed.
- Associated with EC2, Lambda in VPC, RDS, EFS, and other ENI-based services.

##### Useful Comparisons

- **vs NACLs**: SGs are stateful and instance-focused; NACLs are stateless and subnet-focused.
- **vs WAF**: SGs filter network-layer traffic (Layers 3/4), while WAF filters **HTTP application-layer** requests (Layer 7).
- **vs IAM Policies**: SGs control network access, while IAM policies control **who can call AWS APIs** — an entirely different plane.
- **vs Resource Policies (S3, Lambda, API Gateway)**: SGs control traffic between network endpoints; resource policies control **which principals** can access a service.

#### Network ACLs (NACLs)

- **Stateless packet filters** that control inbound and outbound traffic at the **subnet boundary**.
- Require **explicit inbound and outbound rules** for return traffic because they are stateless.
- Support both **allow and deny** rules.
- Rules are evaluated **in order from lowest number to highest**, and the first match wins.
- Optional tool for controlling traffic between subnets or applying broad network restrictions.
- Each subnet must have a NACL; the default NACL allows all traffic (both in and out).

##### Useful Comparisons

- **vs Security Groups**: NACLs are stateless, ordered, subnet-level; SGs are stateful, unordered, and ENI-level.
- **vs WAF**: NACLs operate at the network/transport layers; WAF operates at the HTTP application layer.
- **vs VPC Route Tables**: NACLs filter packets; route tables determine **where** traffic is sent, not whether it is allowed.
- **vs Firewall Manager**: Firewall Manager manages policies for WAF, Shield, and SGs across multiple accounts; NACLs remain independently configured per VPC/subnet.

#### When to Use Each

- **Security Groups**: Primary mechanism for controlling workload-level access (e.g., “only ALB may reach EC2 instances”).
- **NACLs**: Rarely needed except for broad, subnet-level restrictions, blocking specific IPs, or serving as a second layer of defense.
- **WAF**: Use when filtering **HTTP traffic patterns**, not IP-level traffic (e.g., block SQL injection, rate limits, bot filtering).

#### Exam-Trap Notes

- SGs are stateful; NACLs are stateless — this is one of the most testable facts.
- SGs have only allow rules; NACLs have allow and deny rules.
- NACL rules are ordered; SG rules are not.
- WAF does not replace SGs/NACLs — entirely different layer of the OSI stack.
- IAM policies do not control network connectivity, only API permissions — a common misconception.

### 🔹Elastic Network Interface (ENI)

An Elastic Network Interface (ENI) is a virtual network card in AWS. It represents the network identity of an EC2 instance or any AWS service that attaches to a VPC.

Think of an ENI as the thing in AWS that owns an IP address, MAC address, security group membership, and network routing identity.

ENIs are what enable:

- An instance to have one or more IP addresses
- High availability failover of network identities
- Multiple network interfaces for firewalls, NAT appliances, or monitoring systems
- Lambda functions in a VPC to talk to private subnets
- Services like RDS, EFS, and ECS tasks to appear inside your VPC

## 🟪 Internet Gateway

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

- Characteristics: Internet connectivity; redundant; regional
- Capabilities: Public routing; inbound/outbound flows
- Pricing Model: No IGW cost; data transfer billed
- Security/IAM: SGs/NACLs control traffic

### 6. Confusable Services

- NAT Gateway: Both relate to internet access, but IGW enables inbound and outbound internet access for public subnets while NAT Gateway allows only outbound internet access for private subnets.
- VPC Endpoints: Both enable connectivity to AWS services, but endpoints keep traffic inside the AWS network while IGW routes traffic to/from the public internet.
- Virtual Private Gateway (VGW): Both attach to VPCs, but VGW provides hybrid connectivity via VPN/Direct Connect while IGW connects a VPC to the internet.

### 7. Exam Notes

- Public subnet = route to IGW
- IGW enables both inbound + outbound

## 🟪 Virtual Private Gateway

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

- Characteristics: Managed IPSec endpoint; regional
- Capabilities: Encrypted tunnels; failover with dual tunnels
- Pricing Model: VPN-hour + data transfer
- Security/IAM: VPN encryption; IAM for config

### 6. Confusable Services

- Internet Gateway: Both attach to a VPC, but IGW connects to the public internet while VGW connects to on-prem networks through Site-to-Site VPN or Direct Connect.
- Transit Gateway: Both can terminate VPNs, but TGW aggregates multiple VPCs and connections while VGW attaches to a single VPC.
- AWS Direct Connect: Both provide hybrid connectivity, but Direct Connect is the physical private link while VGW is the AWS endpoint for VPN/DX connections.

### 7. Exam Notes

- Two tunnels per VPN
- Good for fast hybrid setup

## 🟪 NAT Gateway

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

- Characteristics: Outbound internet; managed; AZ-scoped
- Capabilities: Outbound NAT translation; high throughput
- Pricing Model: Hourly + data processing fees
- Security/IAM: Routing + SG/NACL enforcement

### 6. Confusable Services

- Internet Gateway: Both provide outbound internet connectivity, but IGW allows inbound and outbound traffic for public subnets while NAT Gateway only allows outbound access for private subnets.
- NAT Instance: Both provide NAT functionality, but NAT Gateway is managed, scalable, and fault-tolerant while NAT instances require manual maintenance.
- VPC Endpoints: Both allow private access to AWS services, but endpoints avoid internet entirely while NAT Gateway still routes through the IGW to reach public endpoints.

### 7. Exam Notes

- Must be in a public subnet
- Private subnet → NAT → IGW

## ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_AWS-Client-VPN_16.png) AWS Client VPN

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

- Characteristics: Remote-access VPN; regional
- Capabilities: Identity-based auth; VPC routing
- Pricing Model: Endpoint-hour + connection-hour
- Security/IAM: IAM/AD auth; TLS; SGs

### 6. Confusable Services

- AWS Site-to-Site VPN: Both are VPN solutions, but Client VPN is for remote user endpoints, whereas Site-to-Site VPN is for entire network-to-network connections.
- AWS Direct Connect: Both provide access from on-premises to AWS, but Client VPN is secure remote user access over the internet while DX is a private, high-bandwidth link from a data center. Also, Client VPN is encrypted and Direct Connect is not.
- AWS WorkSpaces Secure Browser / AppStream 2.0: All enable remote access to workloads, but Client VPN connects the device to the VPC network, while WorkSpaces/AppStream provide remote desktops or streamed apps.

### 7. Exam Notes

- For remote individuals, not networks
- Requires authorization rules for subnets

## ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_AWS-Site-to-Site-VPN_16.png) AWS Site-to-Site VPN

Creates encrypted IPSec tunnels between on-prem networks and AWS VPCs.

### 1. Definition

AWS Site-to-Site VPN is a fully managed IPSec VPN connection that links your on-premises network (data center, office, branch site) to an Amazon VPC. It allows your internal corporate network to communicate securely with cloud resources using encrypted tunnels over the public internet.

### 2. Use-Cases

- Quickly connect on-prem networks to AWS
- Hybrid networking before Direct Connect is deployed
- Disaster recovery extensions (AWS as secondary site)
- Private access to RDS databases, EC2, internal services
- Branch office connections

### 3. Additional Info

- Two redundant tunnels per VPN
- Supports BGP for dynamic routing
- Many organizations start with VPN → upgrade to DX later.

### 4. Limitations

- Latency varies with internet
- Lower throughput than DX

### 5. Details

- Characteristics: IPSec VPN; regional endpoints
- Capabilities: Encrypted tunnels; failover; BGP routing
- Pricing Model: Connection-hour + data transfer
- Security/IAM: IPSec encryption; IAM for config

### 6. Confusable Services

- AWS Direct Connect: Both create hybrid connectivity from on-prem to AWS, but VPN is quick and internet-based while DX is private, dedicated, and more consistent.
- AWS Client VPN: Both are VPN offerings, but Site-to-Site VPN connects entire networks, whereas Client VPN connects individual users or devices.
- AWS Transit Gateway: Both appear in hybrid architectures, but Site-to-Site VPN is the tunnel itself while TGW can terminate and aggregate multiple VPN connections.

### 7. Exam Notes

- Requires a secure connection from an on-prem network to AWS → Site-to-Site VPN
- Unpredictable latency is acceptable → Site-to-Site VPN
- Remote employees need access → Client VPN
- Consistent, high-throughput link → Direct Connect
- Need hybrid + high availability → Direct Connect + VPN failover
- Connecting VPCs together → VPC Peering or Transit Gateway

## ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_AWS-Direct-Connect_16.png) AWS Direct Connect

Provides private, dedicated network connectivity between on-premises and AWS.

### 1. Definition

AWS Direct Connect establishes a private physical network connection that bypasses the public internet, enabling predictable latency and higher throughput. It is a private, dedicated physical network link between your on-premises data center and AWS.

### 2. Use-Cases

- High-throughput hybrid workloads
- Consistent low-latency connections
- Data migration at scale

### 3. Additional Info

- Private fiber connection (not over the internet)
- Extremely stable latency
- Speeds: 1/10/100 Gbps
- DX Gateway supports multiple VPCs

### 4. Limitations

- Requires physical installation
- Long provisioning times

### 5. Details

- Characteristics: Dedicated link; private routing
- Capabilities: Stable bandwidth; hybrid networking
- Pricing Model: Port-hour + discounted transfer
- Security/IAM: Private link; encryption optional

### 6. Confusable Services

- Site-to-Site VPN: Both connect on-prem networks to AWS, but VPN runs over the public internet while Direct Connect uses a private dedicated link.
- AWS Global Accelerator: Both are associated with performance, but Global Accelerator improves user-to-AWS traffic over the internet, while DX improves data center–to–AWS private connectivity.
- AWS Transit Gateway: Both appear in hybrid diagrams, but DX provides the physical/private connectivity while TGW is the routing hub that connects many VPCs and on-prem links together.

### 7. Exam Notes

- “Consistent,” “private,” “low-latency” → Direct Connect
- Combine DX + VPN for HA

## ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_AWS-PrivateLink_16.png) AWS PrivateLink

Provides private connectivity to AWS services and customer services over VPC endpoints without traversing the public internet.

### 1. Definition

AWS PrivateLink allows private communication between VPCs and AWS services or SaaS applications using interface VPC endpoints (ENIs) without using public IPs or internet paths. PrivateLink shares only a specific service endpoint, never the underlying VPC - this is why AWS PrivateLink is the backbone of most SaaS providers on AWS.

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

- Characteristics: Private service access; ENI-based
- Capabilities: Private connectivity; cross-account publishing
- Pricing Model: Endpoint-hour + data processing
- Security/IAM: SGs; IAM policy controls

### 6. Confusable Services

- VPC Endpoints (Gateway): Both are endpoints, but Gateway Endpoints support only S3 and DynamoDB with route-table entries, while PrivateLink (interface endpoints) supports many services via elastic network interfaces.
- VPC Peering: Both enable private connectivity, but peering connects two VPCs’ networks entirely while PrivateLink exposes only a specific service to consumers using an endpoint.
- Transit Gateway: Both connect VPCs, but TGW routes whole networks together while PrivateLink provides service-level connectivity without sharing entire VPCs.
- NAT Gateway: Both enable access to AWS services, but NAT Gateway sends traffic over the public internet to public endpoints while PrivateLink keeps traffic entirely within AWS’s private backbone.
- Internet Gateway: Both allow VPC traffic to reach AWS services, but IGW uses public IP connectivity over the internet while PrivateLink avoids the internet entirely.
- AWS Direct Connect: Both avoid the public internet, but Direct Connect links on-prem to AWS while PrivateLink provides private service endpoints inside AWS.

### 7. Exam Notes

- “Access AWS services privately” → PrivateLink
- Interface endpoints = PrivateLink

## ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_AWS-Transit-Gateway_16.png) AWS Transit Gateway

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

- Characteristics: Regional hub router; scalable
- Capabilities: VPC/VPN/DX attachments; centralized routing
- Pricing Model: Attachment-hour + data processing
- Security/IAM: IAM for config; SG/NACL still apply

### 6. Confusable Services

- VPC Peering: Both connect VPCs privately, but peering is 1-to-1 and does not scale well, while Transit Gateway is a hub-and-spoke architecture that connects many VPCs and networks through a single attachment.
- AWS PrivateLink: Both keep traffic off the public internet, but PrivateLink exposes specific services across VPCs while Transit Gateway connects entire networks—routing full traffic, not just service endpoints.
- Virtual Private Gateway (VGW): Both support hybrid connectivity from on-premise networks, but VGW attaches to one VPC, while TGW aggregates many VPCs and VPN/DX connections into one routing hub.
- NAT Gateway: Both enable VPC-to-external communication, but NAT Gateway is for outbound internet traffic from private subnets, while Transit Gateway connects VPCs to other VPCs or on-prem networks.
- Internet Gateway (IGW): Both appear in diagrams involving external traffic, but IGW provides internet access, while Transit Gateway provides private network connectivity only (no internet routing).
- AWS Direct Connect: Both participate in hybrid connectivity, but Direct Connect is the physical private link, while Transit Gateway is the routing hub that aggregates or distributes DX traffic to multiple VPCs.
- AWS VPN (Site-to-Site): Both connect on-prem networks to AWS, but VPN is the network tunnel, while Transit Gateway is the routing core that connects multiple VPNs and VPCs at scale.

### 7. Exam Notes

- “Many VPCs,” “centralized routing,” “hub-and-spoke” → TGW
- TGW != PrivateLink (service access)

## 🟪 VPC Endpoints (Gateway & Interface)

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

- Characteristics: Private connectivity; regional
- Capabilities: Remove public internet path; secure service access
- Pricing Model: Interface endpoint hourly + data; gateway free
- Security/IAM: Endpoint policies; SGs

### 6. Confusable Services

- Internet Gateway: Both allow VPC resources to reach AWS services, but IGW routes traffic over the public internet while endpoints keep traffic inside the AWS network.
- NAT Gateway: Both allow instances in private subnets to reach AWS services, but NAT Gateway sends traffic to public endpoints while endpoints provide private, non-internet connectivity.
- VPC Peering: Both enable private connectivity, but peering connects VPCs to each other while endpoints connect a VPC to AWS services.
- AWS PrivateLink: Interface endpoints use PrivateLink, causing confusion, but PrivateLink is the underlying service while an interface endpoint is its implementation inside a VPC.

### 7. Exam Notes

- Gateway = S3 & DynamoDB
- Interface = PrivateLink-based

## ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_Amazon-Route-53_16.png) Amazon Route 53

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

- Characteristics: Global DNS; highly available; low-latency
- Capabilities: DNS resolution, routing policies, health checks
- Pricing Model: Hosted zone fee + queries
- Security/IAM: DNSSEC support; IAM permissions

### 6. Confusable Services

- Elastic Load Balancing: Both are involved in directing traffic to applications, but Route 53 does DNS name resolution while ELB terminates and distributes traffic to targets.
- AWS Global Accelerator: Both can choose where traffic goes globally, but Route 53 operates at DNS level while Global Accelerator uses anycast IPs and the AWS network for routing.
- Amazon CloudFront: Both have global aspects, but CloudFront caches content at edge locations while Route 53 just resolves domain names.

### 7. Exam Notes

- Weighted = A/B testing; latency = user proximity
- Failover routing uses health checks

## ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_Amazon-CloudFront_16.png) Amazon CloudFront

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

- Characteristics: Global CDN; edge-based caching
- Capabilities: Content caching, TLS termination, global distribution
- Pricing Model: Data transfer + requests
- Security/IAM: WAF, Shield, signed URLs

### 6. Confusable Services

- Elastic Load Balancing: Both appear in front of web applications, but CloudFront is a CDN that caches content at the edge while ELB balances live traffic to backends.
- AWS Global Accelerator: Both use the AWS global network to improve performance, but CloudFront focuses on HTTP/HTTPS content caching, while GA optimizes TCP/UDP traffic routing with static IPs.
- Amazon S3 Static Website Hosting: Both can serve static websites, but S3 hosts the site’s files while CloudFront accelerates and caches delivery globally.

### 7. Exam Notes

- “Global CDN,” “edge caching,” “Lambda@Edge” → CloudFront
- Often paired with S3 static websites

## ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_AWS-Global-Accelerator_16.png) AWS Global Accelerator

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

- Characteristics: Anycast routing; global network acceleration
- Capabilities: Latency optimization; static IPs; multi-region failover
- Pricing Model: Data transfer + accelerator-hour
- Security/IAM: SG/NACLs; IAM config

### 6. Confusable Services

- Amazon CloudFront: Both improve global performance and use the AWS edge network, but CloudFront focuses on caching content while Global Accelerator optimizes connection routing to application endpoints.
- Amazon Route 53: Both can route users to regional endpoints, but Route 53 is DNS-based while Global Accelerator uses static anycast IPs and health-based routing on the AWS backbone.
- Elastic Load Balancing: Both are involved in directing traffic to applications, but Global Accelerator sits in front with global anycast IPs, while ELB is the regional load balancer behind it.

### 7. Exam Notes

- If question mentions “static Anycast IPs” → Global Accelerator
- Improves performance but does NOT cache content

---

# ![icon](icons/category/Arch-Category_16/Arch-Category_Storage_16.png) Storage

Storage is responsible for **keeping data safe and durable** for as long as needed.
It stores files, objects, backups, and block data across multiple storage models.
Its core intent is to provide scalable, reliable places to put data—short-term or forever.

## ![icon](icons/service/Arch_Storage/16/Arch_Amazon-Simple-Storage-Service_16.png) Amazon S3

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
  - S3 Standard — General-purpose storage for frequently accessed data with low latency and high throughput.
  - S3 Standard-IA (Infrequent Access) — Lower-cost storage for infrequently accessed data that still requires fast retrieval.
  - S3 One Zone-IA — Lowest-cost infrequent-access storage that stores data in a single Availability Zone instead of multiple AZs.
  - S3 Glacier Instant Retrieval — Archival storage for rarely accessed data that still requires milliseconds retrieval.
  - S3 Glacier Flexible Retrieval — Low-cost archival storage with minutes-to-hours retrieval, suitable for long-term backups and disaster recovery.
  - S3 Glacier Deep Archive — Lowest-cost storage for data accessed once or twice per year, with retrieval times of 12–48 hours.
  - S3 Intelligent-Tiering — Automatically moves objects between access tiers based on usage patterns without performance impact or operational overhead.
  - S3 Express One Zone — Ultra-low-latency single-AZ storage for performance-critical workloads needing microsecond access.
- Features: Versioning, lifecycle rules, replication, encryption, access points

### 4. Limitations

- Object-level access only (not POSIX)
- Eventual consistency for overwrite/delete

### 5. Details

- Characteristics: Object storage; serverless; regional with global access
- Capabilities: Events, replication, lifecycle, encryption, versioning
- Pricing Model: Storage, requests, retrieval, data transfer
- Security/IAM: IAM policies, bucket policies, ACLs, SSE-S3/KMS

### 6. Confusable Services

- Amazon EFS: Both provide storage for AWS workloads, but S3 is object storage while EFS is a shared POSIX-compliant file system.
- Amazon EBS: Both store data for compute resources, but EBS is block storage for a single EC2 instance while S3 is a globally accessible object store.
- Amazon FSx: Both store files, but FSx provides specialized high-performance file systems while S3 offers object-based storage.
- AWS Storage Gateway: Both provide hybrid storage, but Storage Gateway bridges on-premises environments to AWS, while S3 is the actual storage destination.
- Amazon Glacier (S3 Glacier): Both are S3 storage classes, but Glacier tiers are for archival use with retrieval delays.

### 7. Exam Notes

- “Object storage,” “11 9’s durability,” “data lake,” “static website” → S3
- Block public access prevents unintended exposure

## ![icon](icons/service/Arch_Storage/16/Arch_Amazon-Elastic-Block-Store_16.png) Amazon EBS

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

- Characteristics: Block storage; persistent; AZ-bound
- Capabilities: Snapshots, resizing, encryption, high IOPS options
- Pricing Model: Per GB-month + provisioned IOPS
- Security/IAM: KMS encryption; IAM for volume/snapshot access

### 6. Confusable Services

- Amazon EFS: Both provide persistent storage, but EBS is block storage for one instance, while EFS is a shared network file system for multiple instances.
- Amazon S3: Both store data reliably, but S3 is object storage decoupled from compute, while EBS is attached block storage for EC2.
- Amazon FSx: Both offer high-performance workloads, but FSx is distributed file storage, whereas EBS is local block storage.

### 7. Exam Notes

- EBS = persistent block storage; Instance Store = ephemeral
- gp3 default; io2 for highest IOPS

## ![icon](icons/service/Arch_Storage/16/Arch_Amazon-EFS_16.png) Amazon EFS

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

- Characteristics: NFS; multi-AZ; elastic; regional
- Capabilities: Shared file access; scaling; encryption; access points
- Pricing Model: Per GB-month; IA class reduces cost
- Security/IAM: SG-based access; POSIX permissions; IAM for API access

### 6. Confusable Services

- Amazon EBS: Both act as storage for EC2, but EBS is single-instance block storage while EFS is a multi-AZ shared file system.
- Amazon FSx: Both are file systems, but FSx is optimized for Windows or Lustre ecosystems with specific performance models, while EFS is elastic general-purpose NFS storage.
- Amazon S3: Both can store files, but EFS is a mountable POSIX file system while S3 is object storage with no directory tree or POSIX semantics.

### 7. Exam Notes

- Multi-AZ, POSIX = EFS
- Automatically scales with usage

## ![icon](icons/service/Arch_Storage/16/Arch_Amazon-FSx_16.png) Amazon FSx (Windows & Lustre)

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

- Characteristics: High-performance file systems; regional
- Capabilities: AD integration; high throughput; parallel file access
- Pricing Model: Throughput + storage + backups
- Security/IAM: KMS encryption; AD permissions; IAM for API

### 6. Confusable Services

- Amazon EFS: Both provide shared file systems, but EFS is general-purpose Linux NFS, while FSx offers specialized Windows SMB or Lustre HPC file systems.
- Amazon EBS: Both support high performance, but FSx is network-attached file storage while EBS is block storage directly attached to EC2.
- Amazon S3: FSx for Lustre integrates with S3 and may be confused for object storage, but FSx is a high-speed file system, not a data lake.

### 7. Exam Notes

- Windows SMB needs FSx Windows
- HPC parallel access → FSx Lustre

## ![icon](icons/service/Arch_Storage/16/Arch_AWS-Storage-Gateway_16.png) AWS Storage Gateway

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

- Characteristics: Hybrid storage; connects on-prem to AWS
- Capabilities: Cached/Stored volumes; virtual tapes; S3-backed file shares
- Pricing Model: Appliance-hour + data transfer
- Security/IAM: KMS; IAM roles; SSL

### 6. Confusable Services

- AWS DataSync: Both move data between on-prem and AWS, but Storage Gateway provides ongoing hybrid storage interfaces while DataSync is for large-scale one-time or periodic transfers.
- Amazon S3: Storage Gateway stores data in S3, leading to confusion, but Gateway is the hybrid access layer while S3 is the storage backend.
- AWS Transfer Family: Both ingest data into S3, but Transfer Family provides file transfer protocols like SFTP, while Storage Gateway provides local caching and hybrid storage modes.

### 7. Exam Notes

- File Gateway → S3-backed NFS/SMB
- Tape Gateway replaces physical tape libraries

## ![icon](icons/service/Arch_Storage/16/Arch_AWS-Backup_16.png) AWS Backup

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

- Characteristics: Centralized, policy-driven, multi-service coverage
- Capabilities: Scheduled backups, lifecycle policies, vaulting
- Pricing Model: Per-GB backup + restore charges
- Security/IAM: Backup Vault Lock, KMS, IAM policies

### 6. Confusable Services

- AWS Data Lifecycle Manager: Both automate data protection, but DLM manages EBS snapshots while Backup centralizes backups across many AWS services.
- Amazon S3 Versioning/Lifecycle: Both preserve data over time, but Backup is cross-service operational backup, while S3 lifecycle is storage-class transition.
- AWS Elastic Disaster Recovery: Both relate to resilience, but DRS replicates entire servers for failover while Backup preserves data copies.

### 7. Exam Notes

- “Centralize backups,” “policy-based retention,” “cross-region backup” → AWS Backup

## ![icon](icons/service/Arch_Migration-Modernization/16/Arch_AWS-DataSync_16.png) AWS DataSync

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

- Characteristics: High-speed transfer; automated scheduling
- Capabilities: Incremental syncs; bandwidth controls; filtering
- Pricing Model: Per-GB transferred
- Security/IAM: TLS; IAM roles; encryption in transit

### 6. Confusable Services

- AWS Storage Gateway: Both move data to AWS, but Storage Gateway provides hybrid storage access, while DataSync accelerates bulk data transfers.
- AWS Transfer Family: Both ingest data into AWS, but Transfer Family is protocol-based (SFTP/FTP), while DataSync is optimized for large-scale automated migrations.
- Amazon S3 Multipart Upload: Both involve data movement, but multipart upload is an S3 upload method, not a transfer orchestration service.

### 7. Exam Notes

- “Accelerated transfer,” “automated sync,” “NFS/SMB to S3/EFS” → DataSync

## ![icon](icons/service/Arch_Migration-Modernization/16/Arch_AWS-Transfer-Family_16.png) AWS Transfer Family

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

- Characteristics: Managed protocol servers; scalable
- Capabilities: Protocol endpoints; identity integration
- Pricing Model: Endpoint-hour + data transfer
- Security/IAM: IAM-based controls; VPC support

### 6. Confusable Services

- AWS DataSync: Both transfer data, but DataSync is optimized for massive automated migrations, while Transfer Family provides user-facing SFTP/FTP interfaces.
- AWS Storage Gateway: Both connect on-prem environments to AWS storage, but Gateway provides hybrid caching/file/volume interfaces, not transfer protocols.
- Amazon S3: Both involve ingesting data into AWS, but S3 is the destination while Transfer Family is the protocol service.

### 7. Exam Notes

- “SFTP/FTP to S3/EFS” → Transfer Family

## ![icon](icons/service/Arch_Storage/16/Arch_AWS-Elastic-Disaster-Recovery_16.png) AWS Elastic Disaster Recovery

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

- Characteristics: Continuous replication; low RPO/RTO
- Capabilities: Failover, failback, non-disruptive tests
- Pricing Model: Replication & storage costs + EC2 on failover
- Security/IAM: Encryption, IAM roles

### 6. Confusable Services

- AWS Backup: Both relate to recovery, but Backup protects data while DRS replicates entire servers for failover.
- Amazon RDS Multi-AZ: Both provide resilience, but RDS Multi-AZ is database-level high availability, while DRS is full-server disaster recovery.
- AWS Migration Hub: Both involve server replication, but Migration Hub tracks and coordinates migrations, not continuous failover replication.

### 7. Exam Notes

- “Fast failover,” “continuous replication,” “DR strategy” → DRS

## ![icon](icons/service/Arch_Storage/16/Arch_AWS-Snowball_16.png) AWS Snow Family

Physical devices for offline or edge data transfer and edge compute.

### 3. Additional Info

- AWS Snowcone: Small, rugged edge device for data transfer and lightweight compute at the edge.
  - Harsh environments
  - IoT/edge compute
  - Limited connectivity
- AWS Snowball: Rugged appliance for large-scale data transfer or edge compute workloads.
  - Mass data migration
  - Edge ML/compute workloads
- AWS Snowmobile: Massive data transfer truck for exabyte-scale migrations.
  - Multi-petabyte or exabyte migrations
  - Data center evacuations

### 6. Confusable Services

- AWS DataSync: Both move large datasets, but DataSync is network-based while Snowball/Snowmobile move data physically.
- AWS Storage Gateway: Both connect on-prem to AWS, but Snow devices are for migration/transport, not hybrid storage.
- Amazon S3 Transfer Acceleration: Both move data faster, but Transfer Acceleration speeds internet uploads, while Snow devices bypass networks completely.

---

# ![icon](icons/category/Arch-Category_16/Arch-Category_Database_16.png) Databases

Databases **organize and retrieve application data** with speed and correctness.
They structure data in tables, documents, key-value stores, graphs, or time‑series formats.
Their core intent is to deliver fast, consistent access to well-managed data.

## ![icon](icons/service/Arch_Database/16/Arch_Amazon-RDS_16.png) Amazon RDS

Managed relational database service supporting Amazon Aurora, MySQL, PostgreSQL, MariaDB, Oracle, SQL Server.

### 1. Definition

Amazon RDS automates database provisioning, patching, backups, monitoring, and replication for relational engines. It supports Multi-AZ failover, read replicas, and various instance classes optimized for memory or performance.

### 2. Use-Cases

- Traditional relational applications
- OLTP workloads
- Applications requiring managed backups and HA

### 3. Additional Info

- Multi-AZ for failover; read replicas for read scaling

### 4. Limitations

- Limited access to OS-level features
- Some engines have licensing constraints

### 5. Details

- Characteristics: Managed RDBMS; regional; supports replicas
- Capabilities: Automated maintenance, backups, monitoring
- Pricing Model: Instance-hours + storage + I/O
- Security/IAM: KMS encryption; SGs; IAM auth for some engines

### 6. Confusable Services

- Amazon Aurora: Both are relational managed databases, but Aurora is a cloud-native engine with distributed storage and higher scalability, while RDS provides managed traditional database engines like MySQL, PostgreSQL, MariaDB, Oracle, and SQL Server.
- Amazon DynamoDB: Both store structured data, but DynamoDB is NoSQL key-value/document while RDS is relational SQL with fixed schemas.
- Amazon Redshift: Both use SQL, but Redshift is an OLAP data warehouse optimized for analytics while RDS is OLTP optimized for transactional workloads.
- Amazon ElastiCache: Both improve application performance, but ElastiCache is an in-memory cache while RDS is a durable relational database.
- Amazon DocumentDB: Both resemble traditional database systems, but DocumentDB provides a MongoDB-compatible NoSQL document model while RDS is SQL-based.

### 7. Exam Notes

- Multi-AZ = HA; read replicas ≠ HA

## ![icon](icons/service/Arch_Database/16/Arch_Amazon-Aurora_16.png) Amazon Aurora

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
- Aurora is managed via RDS APIs and console
  - You create Aurora clusters through the RDS console.
  - Monitoring, parameter groups, subnet groups, snapshots, and backups are all RDS features used by Aurora.
- Aurora does not use the same storage model as classic RDS
  - Traditional RDS engines use EBS volumes for storage.
  - Aurora uses a distributed, multi-AZ, shared storage cluster that auto-scales up to 128 TiB.
- Aurora performance is far higher than RDS
  - Up to 5x MySQL performance
  - Up to 3x PostgreSQL performance
  - Fast failover (seconds vs minutes)

### 4. Limitations

- More expensive than RDS engines
- Custom engine features limit portability

### 5. Details

- Characteristics: Distributed storage; multi-AZ; high performance
- Capabilities: Read replicas; global clusters; autoscaling
- Pricing Model: Instance-hours + I/O + storage
- Security/IAM: KMS; SGs; IAM auth

### 6. Confusable Services

- Amazon RDS: Both provide managed relational databases, but Aurora is a cloud-native, distributed storage engine with higher performance and faster failover, while RDS offers traditional database engines with conventional storage.
- Amazon DynamoDB: Both scale well and offer high performance, but DynamoDB is NoSQL key-value/document storage while Aurora is fully relational with SQL support.
- Amazon Redshift: Both use SQL and store structured data, but Redshift is an OLAP data warehouse for analytics, while Aurora is an OLTP transactional database.
- Amazon Neptune: Both store relationships, but Neptune is a graph database optimized for graph queries while Aurora stores relational tables.
- Amazon ElastiCache: Both reduce latency for reads, but ElastiCache is an in-memory cache while Aurora is a persistent relational database with optional read replicas.

### 7. Exam Notes

- Aurora = performance + HA + replication across AZs
- Global Aurora = lowest-latency global reads

## ![icon](icons/service/Arch_Database/16/Arch_Amazon-DynamoDB_16.png) Amazon DynamoDB

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

- Characteristics: NoSQL; serverless; regional
- Capabilities: TTL, backups, streams, global tables
- Pricing Model: Read/write units or on-demand
- Security/IAM: Fine-grained IAM; KMS

### 6. Confusable Services

- Amazon RDS: Both store structured data, but RDS is relational SQL while DynamoDB is NoSQL key-value and document storage.
- Amazon Aurora Serverless: Both provide auto-scaling, but Aurora is relational while DynamoDB is NoSQL with partition-based scaling.
- Amazon ElastiCache: Both deliver fast lookup performance, but ElastiCache is a caching layer while DynamoDB is a persistent NoSQL database.
- Amazon DocumentDB: Both are document stores, but DynamoDB is schema-flexible NoSQL while DocumentDB mimics MongoDB’s API.

### 7. Exam Notes

- Partition keys, WCU/RCU, on-demand vs provisioned

## ![icon](icons/service/Arch_Database/16/Arch_Amazon-DynamoDB_16.png) Amazon DynamoDB Accelerator (DAX)

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

- Characteristics: In-memory cache; clustered; regional
- Capabilities: Microsecond reads; write-through caching
- Pricing Model: Node-hour pricing
- Security/IAM: IAM auth; SGs

### 6. Confusable Services

- Amazon ElastiCache: Both are caching layers, but ElastiCache supports Redis/Memcached while DAX provides DynamoDB-specific API-compatible caching.
- Amazon DynamoDB: Both return DynamoDB results, but DynamoDB is the underlying database while DAX is a performance accelerator.
- Amazon Aurora Read Replicas: Both improve read performance, but read replicas are for relational workloads while DAX is for DynamoDB.

### 7. Exam Notes

- Keyword: “microsecond latency for DynamoDB”

## ![icon](icons/service/Arch_Database/16/Arch_Amazon-ElastiCache_16.png) Amazon ElastiCache

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

- Characteristics: In-memory store; multi-AZ for Redis
- Capabilities: Sub-millisecond reads; replication; clustering
- Pricing Model: Node-hour
- Security/IAM: SGs; KMS (Redis)

### 6. Confusable Services

- DynamoDB DAX: Both improve read performance, but DAX is purpose-built for DynamoDB while ElastiCache is a general-purpose in-memory cache.
- Amazon RDS Read Replicas: Both improve read traffic distribution, but ElastiCache is a cache while replicas store actual relational data.
- Amazon MemoryDB: Both use Redis APIs, but MemoryDB is a durable Redis-compatible database while ElastiCache is an in-memory cache.

### 7. Exam Notes

- Redis = richer features; Memcached = simple, horizontal scale

## ![icon](icons/service/Arch_Database/16/Arch_Amazon-DocumentDB_16.png) Amazon DocumentDB

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

- Characteristics: Managed document DB; multi-AZ
- Capabilities: Automatic backups; replicas; scaling
- Pricing Model: Instance-hours + I/O + storage
- Security/IAM: SGs; KMS; IAM auth for API

### 6. Confusable Services

- Amazon DynamoDB: Both are NoSQL, but DynamoDB is key-value/document store while DocumentDB is a MongoDB-compatible document database.
- Amazon Neptune: Both are non-relational databases, but Neptune is a graph database while DocumentDB focuses on document models.
- Amazon RDS: Both appear in structured data diagrams, but RDS is relational while DocumentDB is NoSQL.

### 7. Exam Notes

- “MongoDB-compatible,” “JSON documents” → DocumentDB

## ![icon](icons/service/Arch_Database/16/Arch_Amazon-Neptune_16.png) Amazon Neptune

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

- Characteristics: Graph database; multi-AZ
- Capabilities: ACID transactions; fast traversals
- Pricing Model: Instance-hours + storage + I/O
- Security/IAM: KMS; SGs; IAM for API

### 6. Confusable Services

- Amazon DocumentDB: Both are non-relational and work with graph-like document structures, but Neptune is a graph database while DocumentDB is a document store.
- Amazon DynamoDB: Both handle relationships, but DynamoDB has no built-in graph querying—Neptune optimizes for graph traversal.
- Amazon OpenSearch Service: Both can analyze relationships, but OpenSearch is a search/analytics engine, not a graph database.

### 7. Exam Notes

- “Graph,” “relationships,” “Gremlin/SPARQL” → Neptune

## ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-Redshift_16.png) Amazon Redshift

Fully managed, petabyte-scale cloud data warehouse for analytic workloads.

### 1. Definition

Amazon Redshift is a massively parallel processing (MPP) data warehouse optimized for large-scale analytics. It supports columnar storage, materialized views, RA3 storage layers, data sharing, Redshift Spectrum, and integration with data lakes.

Amazon Redshift gives you the ability to analyze data that was collected from real-time sources. However, Amazon Redshift does not provide a way to collect or process real-time streaming data.

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

- Characteristics: Columnar; MPP; scalable; regional
- Capabilities: Data sharing; Spectrum; concurrency scaling
- Pricing Model: Node-hours or serverless compute
- Security/IAM: KMS; IAM; SGs; audit logging

### 6. Confusable Services

- Amazon Athena: Both query large datasets, but Redshift is a data warehouse cluster while Athena is serverless SQL over S3.
- Amazon RDS: Both use SQL, but RDS is transactional OLTP while Redshift is analytical OLAP.
- Amazon EMR: Both handle big data workloads, but EMR runs Hadoop/Spark ecosystems while Redshift uses columnar warehousing.

### 7. Exam Notes

- “Analytics,” “columnar,” “MPP,” “Spectrum” → Redshift
- Redshift is for OLAP (online analytical processing; smarter decision-making), not OLTP (online transactional processing; massive number of transactions)

---

# ![icon](icons/category/Arch-Category_16/Arch-Category_Artificial-Intelligence_16.png) AI and Machine Learning

AI and ML services **find patterns, make predictions, and automate decisions** using your data.
They offer everything from prebuilt AI APIs to full ML training and hosting platforms.
Their core intent is to bring intelligent behavior into applications without requiring deep ML expertise.

## ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Comprehend_16.png) Amazon Comprehend

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

- Characteristics: Fully managed NLP; regional
- Capabilities: Entity detection; sentiment; custom models
- Pricing Model: Per-unit text processed
- Security/IAM: KMS; IAM; VPC endpoints

### 6. Confusable Services

- Amazon Translate: Both work with text, but Translate converts languages while Comprehend analyzes sentiment, entities, and topics.
- Amazon Lex: Both process natural language, but Lex builds chatbots while Comprehend performs text understanding and classification.
- Amazon Kendra: Both search within textual content, but Kendra is an enterprise search engine while Comprehend performs NLP extraction and classification.

### 7. Exam Notes

- “Sentiment,” “entities,” “text analysis” → Comprehend

## ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Polly_16.png) Amazon Polly

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

- Characteristics: Managed TTS; multilingual
- Capabilities: Speech synthesis; SSML support
- Pricing Model: Per-character
- Security/IAM: IAM; KMS for logs

### 6. Confusable Services

- Amazon Translate: Both create text transformations, but Translate changes language while Polly converts text into lifelike speech.
- Amazon Transcribe: Both involve speech, but Transcribe converts speech → text while Polly converts text → speech.
- Amazon Lex: Both appear in conversational AI apps, but Lex handles conversational logic while Polly handles voice output.

### 7. Exam Notes

- “Text to speech,” “voice output” → Polly

## ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Transcribe_16.png) Amazon Transcribe

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

- Characteristics: Speech-to-text; regional
- Capabilities: Timestamps; speaker diarization
- Pricing Model: Per-second audio processed
- Security/IAM: IAM; encryption

### 6. Confusable Services

- Amazon Polly: Both relate to speech, but Transcribe converts speech → text while Polly converts text → speech.
- Amazon Lex: Both appear in voice-interactive systems, but Lex handles dialogue while Transcribe handles transcription.
- Amazon Comprehend: Both process text, but Transcribe creates text from audio while Comprehend analyzes text for meaning.

### 7. Exam Notes

- “Convert speech to text,” “ASR” → Transcribe

## ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Translate_16.png) Amazon Translate

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

- Characteristics: Neural translation; global language support
- Capabilities: Text translation; batch jobs
- Pricing Model: Per-character
- Security/IAM: IAM; encryption

### 6. Confusable Services

- Amazon Comprehend: Both work with text content, but Translate translates languages while Comprehend extracts meaning from text.
- Amazon Polly: Both produce natural-language output, but Translate converts languages while Polly converts text into speech.
- Amazon Lex: Both enable natural-language applications, but Lex handles conversational logic, not text translation.

### 7. Exam Notes

- “Translate text between languages” → Translate

## ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Lex_16.png) Amazon Lex

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

- Characteristics: Conversational AI; ASR + NLU
- Capabilities: Intents; slots; multi-turn dialogues
- Pricing Model: Per speech/text request
- Security/IAM: IAM; KMS

### 6. Confusable Services

- Amazon Comprehend: Both perform NLP tasks, but Comprehend analyzes text while Lex builds conversational bots using intents and slots.
- Amazon Transcribe: Both handle spoken interactions, but Transcribe transcribes speech while Lex interprets intent and manages dialogue.
- Amazon Connect: Both appear in call center architectures, but Lex provides chat/voice bots while Connect manages contact flows.

### 7. Exam Notes

- “Build chatbots,” “conversational interface” → Lex

## ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Rekognition_16.png) Amazon Rekognition

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

- Characteristics: Managed CV; deep learning models
- Capabilities: Labels; faces; celebrity ID; moderation; text detection
- Pricing Model: Per-image or per-minute video analysis
- Security/IAM: IAM; KMS; data privacy controls

### 6. Confusable Services

- Amazon Textract: Both analyze images/documents, but Rekognition identifies objects, faces, and scenes while Textract extracts text from documents.
- Amazon Comprehend: Both perform content understanding, but Rekognition handles visual understanding while Comprehend handles text NLP.
- Amazon Kendra: Both support content search/analysis, but Kendra is an enterprise search engine while Rekognition focuses on image/video analysis.

### 7. Exam Notes

- “Object detection,” “content moderation,” “face recognition” → Rekognition

## ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Textract_16.png) Amazon Textract

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

- Characteristics: OCR + document intelligence
- Capabilities: Form extraction; table extraction; handwriting support
- Pricing Model: Per-page
- Security/IAM: KMS; IAM

### 6. Confusable Services

- Amazon Rekognition: Both analyze visual inputs, but Textract extracts structured text from documents while Rekognition identifies images and faces.
- Amazon Comprehend: Both process text, but Textract extracts text from images/PDFs while Comprehend analyzes text for meaning.
- Amazon S3 Select: Both extract data, but S3 Select extracts rows from S3 objects while Textract extracts text from scanned documents.

### 7. Exam Notes

- “Forms,” “tables,” “OCR with key-value pairs” → Textract

## ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Forecast_16.png) Amazon Forecast

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

- Characteristics: ML-based forecasting; serverless
- Capabilities: Predictive models; AutoML; quantile forecasts
- Pricing Model: Training-hour + inference usage
- Security/IAM: IAM; KMS

### 6. Confusable Services

- Amazon Personalize: Both use ML for predictions, but Forecast predicts time-series values while Personalize predicts user-item preferences.
- Amazon SageMaker: Both build ML models, but Forecast is a fully managed forecasting application while SageMaker requires custom ML pipelines.
- Amazon Lookout for Metrics: Both detect patterns, but Forecast predicts the future while Lookout detects anomalies in existing data.

### 7. Exam Notes

- “Demand planning,” “time-series” → Forecast

## ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Personalize_16.png) Amazon Personalize

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

- Characteristics: Real-time personalization; ML-based
- Capabilities: Recommendations; reranking; user segmentation
- Pricing Model: Training-hour + inference
- Security/IAM: IAM; KMS

### 6. Confusable Services

- Amazon Forecast: Both do ML-driven predictions, but Forecast predicts numeric time-series values while Personalize predicts user recommendations.
- Amazon SageMaker: Both can build ML models, but Personalize is a fully managed recommender system while SageMaker is a general-purpose ML platform.
- Amazon Kendra: Both deliver content to users, but Kendra performs search while Personalize gives personalized recommendations.

### 7. Exam Notes

- “Personalized recommendations,” “user-item interactions” → Personalize

## ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Kendra_16.png) Amazon Kendra

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

- Characteristics: Intelligent search; ML ranking
- Capabilities: Semantic search; FAQs; document connectors
- Pricing Model: Index capacity + query usage
- Security/IAM: IAM; KMS; document-level access control

### 6. Confusable Services

- Amazon OpenSearch Service: Both provide search capabilities, but OpenSearch is general-purpose search while Kendra uses ML to deliver semantic enterprise search.
- Amazon Comprehend: Both understand text, but Comprehend performs NLP analysis while Kendra provides ML-powered search across documents.
- Amazon Neptune: Both help explore relationships, but Neptune is a graph database while Kendra is semantic search.

### 7. Exam Notes

- “Natural language enterprise search,” “FAQ matching” → Kendra

## ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-SageMaker_16.png) Amazon SageMaker

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

- Characteristics: Full ML platform; regional; highly modular
- Capabilities: Autopilot (AutoML), Pipelines, MLOps, hyperparameter tuning
- Pricing Model: Separate pricing for compute, storage, training, endpoints
- Security/IAM: IAM; KMS; VPC integration; encryption

### 6. Confusable Services

- Amazon Bedrock: Both involve ML, but SageMaker is for building/training/hosting custom ML models while Bedrock provides managed foundation models for GenAI.
- Amazon Comprehend: Both offer NLP capabilities, but Comprehend is fully managed AI while SageMaker requires model training or hosting.
- Amazon EMR: Both perform data processing, but EMR is for distributed data analytics while SageMaker focuses on ML training and inference.

### 7. Exam Notes

- “End-to-end ML,” “training + deployment,” “MLOps” → SageMaker

## ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-SageMaker_16.png) SageMaker JumpStart

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

- Characteristics: Prebuilt ML assets; easy onboarding
- Capabilities: One-click deployments; example notebooks
- Pricing Model: Based on underlying SageMaker resources used
- Security/IAM: IAM; KMS

### 6. Confusable Services

- Amazon SageMaker: Both support machine learning workloads, but SageMaker JumpStart provides pre-built models, notebooks, and solution templates while SageMaker enables fully custom model training, tuning, and deployment.
- Amazon Bedrock: Both provide access to powerful AI models, but Bedrock offers foundation models/LLMs for generative AI while JumpStart offers task-specific models and example workflows for traditional ML problems.
- Amazon Comprehend: Both perform NLP tasks, but Comprehend is an API-based managed AI service requiring no ML expertise while JumpStart provides pre-trained models that still run within the SageMaker ecosystem.

### 7. Exam Notes

- “Prebuilt templates,” “get started fast in SageMaker” → JumpStart

## ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Bedrock_16.png) Amazon Bedrock

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

- Characteristics: GenAI API platform; multi-model
- Capabilities: Fine-tuning; embeddings; RAG; guardrails
- Pricing Model: Per-token or per-inference usage
- Security/IAM: IAM; KMS; VPC; Guardrails

### 6. Confusable Services

- Amazon SageMaker: Both work with ML models, but SageMaker is for custom ML and Bedrock is for foundation-model inference.
- Amazon Lex: Both can generate conversational experiences, but Lex is a single managed service while Bedrock supports multiple foundation LLMs.
- Amazon Rekognition: Both are “AI services,” but Rekognition is image-focused while Bedrock handles text-based generative AI.

### 7. Exam Notes

- “Foundation models,” “RAG,” “Agents,” “Guardrails” → Bedrock

## ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Q_16.png) Amazon Q Business

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

- Characteristics: Enterprise AI assistant; knowledge-integrated
- Capabilities: Q&A; RAG; workflow automation
- Pricing Model: Per-user monthly + usage
- Security/IAM: IAM Identity Center; document-level access control

### 6. Confusable Services

- Amazon Kendra: Both provide enterprise search, but Kendra focuses on semantic search while Q Business adds generative answers, reasoning, and business knowledge integration.
- Amazon Bedrock: Both use LLMs, but Bedrock is a foundation-model platform while Q Business applies LLMs specifically to organizational knowledge workflows.
- Amazon QuickSight Q: Both answer questions in natural language, but QuickSight Q is analytics-focused while Q Business is enterprise knowledge + generative reasoning.

### 7. Exam Notes

- “Enterprise assistant,” “secure knowledge retrieval” → Q Business

## ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Q_16.png) Amazon Q Developer

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

- Characteristics: Developer AI assistant; integration-focused
- Capabilities: Code-gen; refactoring; troubleshooting; infra suggestions
- Pricing Model: Per-user monthly
- Security/IAM: IAM code permissions; enterprise governance

### 6. Confusable Services

- Amazon CodeWhisperer: Both generate code suggestions, but Q Developer provides broader development assistance including debugging, documentation, and multi-file reasoning.
- Amazon Bedrock: Both use LLMs, but Bedrock is a general-purpose model platform while Q Developer specifically accelerates software development tasks.
- AWS Cloud9: Both assist developers, but Cloud9 is an IDE while Q Developer is an AI assistant integrated into tools and workflows.

### 7. Exam Notes

- “AI coding assistant,” “generating AWS code,” “IDE integration” → Q Developer

---

# ![icon](icons/category/Arch-Category_16/Arch-Category_Analytics_16.png) Analytics

Analytics services **collect, process, and interpret data** at any scale.
They let you query massive datasets, stream real-time information, and build dashboards.
Their core intent is to turn raw data into insights you can act on.

## ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-Athena_16.png) Amazon Athena

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

- Characteristics: Serverless; S3-based; schema‑on‑read
- Capabilities: SQL queries; partitions; federated queries
- Pricing Model: Per TB scanned
- Security/IAM: IAM; KMS; Lake Formation

### 6. Confusable Services

- Amazon Redshift: Both run SQL analytics, but Athena is serverless SQL on S3 while Redshift is a provisioned data warehouse cluster.
- Amazon EMR: Both process large datasets, but EMR uses distributed compute frameworks (Spark/Hadoop) while Athena is a simple SQL query service.
- Amazon OpenSearch Service: Both can analyze data, but OpenSearch is for search and log analytics, while Athena is for querying S3 data lakes using SQL.

### 7. Exam Notes

- Optimize cost with Parquet + partitioning
- Serverless S3 queries → Athena

## ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-Kinesis-Data-Streams_16.png) Amazon Kinesis Data Streams

Real-time data ingestion and streaming platform for high-throughput event pipelines.

### 1. Definition

Kinesis Data Streams (KDS) ingests and processes real-time streaming data using shards that scale throughput linearly. Applications consume data with low latency.

Kinesis can ingest real-time data from video, audio, application logs, and website clickstreams. Additionally, Kinesis can ingest IoT telemetry data for machine learning, analytics, and other applications.

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

- Characteristics: Real-time streaming; shard-based
- Capabilities: Parallel reads; enhanced fan-out; replay
- Pricing Model: Shard-hour + PUT payload costs
- Security/IAM: IAM; KMS; VPC endpoints

### 6. Confusable Services

- Amazon Kinesis Data Firehose: Both are Kinesis services for streaming data, but Streams gives fine-grained control and Firehose is fully managed ingestion.
- Amazon SQS: Both handle messages, but Kinesis Streams is real-time ordered streaming while SQS is a queue for decoupling.
- Amazon MSK (Kafka): Both are streaming platforms, but Streams is AWS-native while MSK is managed Kafka.

### 7. Exam Notes

- Shards = capacity units; scaling requires shard splits/merges

## ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-Data-Firehose_16.png) Amazon Kinesis Data Firehose

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

- Characteristics: Fully managed; near real-time
- Capabilities: Transform; compress; batch to S3/Redshift
- Pricing Model: Per GB ingested
- Security/IAM: KMS; IAM; VPC

### 6. Confusable Services

- Kinesis Data Streams: Both handle streaming data, but Firehose is fully managed delivery with no consumer logic while Streams requires application-side processing.
- AWS Glue ETL: Both prepare or transform data, but Firehose is lightweight streaming transformation while Glue handles full ETL jobs.
- Amazon S3 Lifecycle: Both move data into storage, but Firehose is real-time ingestion while lifecycle is background object transition.

### 7. Exam Notes

- “No shards,” “autoscaling,” “store data to S3/Redshift” → Firehose

## ![icon](icons/service/Arch_Analytics/16/Arch_AWS-Glue_16.png) AWS Glue

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

- Characteristics: Serverless ETL; Spark-based
- Capabilities: Jobs, Workflows, Crawlers, Catalog
- Pricing Model: DPU-hour
- Security/IAM: KMS; IAM; VPC

### 6. Confusable Services

- AWS DataSync: Both move/prepare data, but DataSync transfers data between storage systems while Glue performs ETL and cataloging.
- AWS Glue Data Catalog: Both involve metadata, but the Data Catalog is Glue’s metadata component, not the processing engine.
- Amazon EMR: Both run data processing jobs, but EMR uses open-source distributed tools (Spark/Hadoop) while Glue is serverless managed ETL.

### 7. Exam Notes

- “Managed Spark ETL,” “crawlers,” “Data Catalog” → Glue

## ![icon](icons/service/Arch_Analytics/16/Arch_AWS-Glue_16.png) AWS Glue Data Catalog

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

- Characteristics: Schema store; serverless
- Capabilities: Partitions; versioning; permissions
- Pricing Model: Small per-object fee
- Security/IAM: IAM; KMS; Lake Formation

### 6. Confusable Services

- AWS Lake Formation: Both involve metadata governance, but Data Catalog stores metadata while Lake Formation adds permissions and governance.
- Amazon Athena: Both use Glue metadata, leading to confusion, but Athena queries data while the Data Catalog stores the schema.
- Amazon Redshift Spectrum: Both integrate with S3 data lakes, but Spectrum queries Redshift + S3 while the Catalog only stores metadata.

### 7. Exam Notes

- “Shared schema for Athena/EMR/Redshift Spectrum”

## ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-EMR_16.png) Amazon EMR

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

- Characteristics: Cluster-based or serverless; big data
- Capabilities: Spark/Hadoop processing; autoscaling
- Pricing Model: Instance-hour or serverless compute
- Security/IAM: IAM; KMS; SGs

### 6. Confusable Services

- Amazon Athena: Both query big datasets, but EMR uses distributed compute frameworks (Spark/Hadoop) while Athena is serverless SQL.
- AWS Glue: Both can run Spark jobs, but Glue is serverless ETL while EMR gives full cluster-level control.
- Amazon Redshift: Both support analytical workloads, but EMR is a general-purpose big data platform while Redshift is a dedicated data warehouse.

### 7. Exam Notes

- “Hadoop,” “Spark,” “cluster,” or “serverless EMR” → EMR

## ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-QuickSight_16.png) Amazon QuickSight

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

- Characteristics: BI SaaS; scalable; serverless
- Capabilities: Dashboards; ML insights; SPICE
- Pricing Model: Per-user or per-session
- Security/IAM: IAM; row-level security

### 6. Confusable Services

- Amazon Athena: Both analyze data, but Athena is SQL querying while QuickSight is BI dashboards and visualization.
- Amazon Redshift: Both support reporting, but Redshift stores data while QuickSight visualizes it.
- Amazon OpenSearch Dashboards: Both visualize data, but OpenSearch is optimized for logs and search analytics while QuickSight targets BI dashboards.

### 7. Exam Notes

- “SPICE,” “BI dashboards,” “serverless analytics” → QuickSight

## ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-OpenSearch-Service_16.png) Amazon OpenSearch Service

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

- Characteristics: Distributed search; indices; clusters
- Capabilities: Full-text search; Kibana/OpenSearch Dashboards
- Pricing Model: Instance-hour + storage
- Security/IAM: Fine-grained access control; IAM; KMS

### 6. Confusable Services

- Amazon Elasticsearch (legacy): Both share a lineage, but OpenSearch is AWS’s fork and replacement for Elasticsearch.
- Amazon Athena: Both search/analyze data, but OpenSearch is for indexing/searching while Athena is for SQL querying in S3.
- Amazon EMR: Both process logs, but EMR uses distributed computing while OpenSearch provides search indexing and real-time log analysis.

### 7. Exam Notes

- “Search,” “ELK,” “Kibana/OpenSearch dashboards” → OpenSearch

---

# ![icon](icons/category/Arch-Category_16/Arch-Category_Security-Identity-Compliance_16.png) Security, Identity and Compliance

Security services **control access, protect data, and detect threats** across your cloud environment.
They enforce identities, permissions, encryption, logging, and compliance requirements.
Their core intent is to keep workloads safe and aligned with organizational and regulatory standards.

## ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Identity-and-Access-Management_16.png) AWS Identity and Access Management (IAM)

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

- Characteristics: Centralized authZ/authN; global
- Capabilities: Roles; MFA; policy evaluation
- Pricing Model: Free
- Security/IAM: IAM itself

### 6. Confusable Services

- IAM Identity Center: Both manage identities, but IAM manages AWS-level permissions while Identity Center manages workforce SSO and federated access.
- AWS Organizations: Both involve governance, but Organizations controls account structure while IAM controls permissions within accounts.
- AWS KMS: Both restrict access to sensitive operations, but IAM defines who can do things, while KMS protects keys used to encrypt data.

### 7. Exam Notes

- IAM is free; roles used for AWS service access

## 🟥 IAM Policy Simulator

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

- Characteristics: Testing utility
- Capabilities: Policy evaluation
- Pricing Model: Free
- Security/IAM: IAM

### 6. Confusable Services

- AWS IAM: Both are about permissions, but IAM manages policies while Policy Simulator tests them without applying.
- AWS CloudTrail: Both help understand access behavior, but CloudTrail logs real actions while Policy Simulator predicts allowed/denied outcomes.
- IAM Access Analyzer: Both analyze permissions, but Access Analyzer scans external access paths while Simulator tests specific evaluations.

### 7. Exam Notes

- Used to test IAM permissions offline

## ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-IAM-Identity-Center_16.png) IAM Identity Center

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

- Characteristics: Org-wide identity; regional
- Capabilities: SSO; IdP integration
- Pricing Model: Free
- Security/IAM: IAM; MFA

### 6. Confusable Services

- AWS IAM: Both define identity access, but IAM Identity Center handles workforce identity and federated app access while IAM is per-account permissions.
- Amazon Cognito: Both manage login for users, but Cognito is primarily for application end-user authentication while Identity Center is for workforce SSO.
- AWS Organizations: Both integrate with account governance, but Organizations manages accounts while Identity Center manages user access to them.

### 7. Exam Notes

- "Workforce SSO" = Identity Center

## ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Key-Management-Service_16.png) AWS Key Management Service (KMS)

### 1. Definition

AWS KMS is a managed service to create and control the encryption keys used to encrypt your data.

AWS KMS makes it easy to create and manage cryptographic keys and control their use across a wide range of AWS services, for instance CloudTrail data.

### 2. Use-Cases

- Encrypting data at rest
- Envelope encryption
- HSM-backed security

### 3. Additional Info

- Supports CMKs; automatic rotation
- Supports symmetric and asymmetric keys.

### 4. Limitations

- Throughput limits

### 5. Details

- Characteristics: FIPS-compliant; regional
- Capabilities: Key creation; grants; rotation
- Pricing Model: Key-hour + request charges
- Security/IAM: IAM + key policies

### 6. Confusable Services

- AWS Secrets Manager: Both store sensitive material, but KMS manages encryption keys while Secrets Manager holds application secrets.
- AWS Certificate Manager (ACM): Both relate to cryptography, but ACM manages SSL/TLS certificates, while KMS handles encryption keys and encryption APIs.
- AWS CloudHSM: Both manage cryptographic keys, but CloudHSM provides a dedicated hardware appliance while KMS is fully managed.

### 7. Exam Notes

- Key policies govern access

## ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Secrets-Manager_16.png) AWS Secrets Manager

### 1. Definition

Stores, rotates, and retrieves application secrets such as API keys and passwords for databases and other services.

### 2. Use-Cases

- Secret rotation
- Secure retrieval in apps

### 3. Additional Info

- Automatic rotation via Lambda

### 4. Limitations

- Costlier than SSM Parameter Store
- Does not provide dedicated hardware appliances; that's CloudHSM.

### 5. Details

- Characteristics: Secret storage; encrypted
- Capabilities: Rotation; versioning
- Pricing Model: Per-secret + API calls
- Security/IAM: KMS encryption

### 6. Confusable Services

- AWS Systems Manager Parameter Store: Both store secrets and configuration, but Secrets Manager adds rotation and lifecycle management while Parameter Store is simpler and cheaper.
- KMS: Both touch cryptography, but Secrets Manager stores application secrets while KMS stores and uses keys for encryption.
- AWS Vault (external): Both handle secrets, but Vault is multi-environment while Secrets Manager is AWS-native, leading to conceptual overlap.
- CloudHSM: CloudHSM helps you comply with corporate, contractual, and regulatory compliance requirements for data security by using dedicated hardware security module (HSM) appliances within the AWS Cloud.

### 7. Exam Notes

- Automatic rotation = Secrets Manager

## ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Shield_16.png) AWS Shield

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

- Characteristics: Managed DDoS protection
- Capabilities: Layer 3/4 detection
- Pricing Model: Free
- Security/IAM: Integrated with CloudFront/Route53

### 6. Confusable

- AWS WAF: Both protect web applications, but WAF filters traffic at Layer 7 while Shield protects against DDoS attacks at layers 3/4.
- AWS Firewall Manager: Both manage protection across accounts, but Shield is the DDoS mitigation engine while Firewall Manager is the orchestration layer.
- AWS Global Accelerator: GA includes basic DDoS protection at the edge, but Shield is the dedicated protection service.

### 7. Exam Notes

- “DDoS basic protection” → Shield Standard

## ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Shield_16.png) AWS Shield Advanced

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

- Characteristics: Premium DDoS; global
- Capabilities: Advanced L3–L7 metrics
- Pricing Model: Monthly subscription
- Security/IAM: IAM; integration with WAF

### 6. Confusable

- AWS Shield Standard: Both protect against DDoS, but Shield Advanced provides enhanced detection, 24/7 response team access, and cost protection while Standard provides baseline protections.
- AWS WAF: Both mitigate threats, but WAF blocks application-layer attacks while Shield Advanced focuses on DDoS protection at lower network layers.
- AWS Global Accelerator: Both protect at the edge, but GA improves performance and reliability while Shield Advanced specifically mitigates large DDoS attacks.

### 7. Exam Notes

- SLA + cost protection → Advanced

## ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-WAF_16.png) AWS WAF

### 1. Definition

Web application firewall filtering malicious HTTP/S traffic at layer 7.

AWS WAF gives you control over how traffic reaches your applications. AWS WAF gives you the ability to create security rules that control network traffic and block common attack patterns.

### 2. Use-Cases

- Blocking SQLi/XSS
- Rate limiting
- Protecting APIs and web apps

### 3. Additional Info

- Works with ALB, API Gateway, CloudFront

### 4. Limitations

- Requires designed rule sets

### 5. Details

- Characteristics: Layer 7 filtering
- Capabilities: Rules; managed rule groups
- Pricing Model: Per-rule + request fees
- Security/IAM: IAM; logging

### 6. Confusable

- AWS Shield: Both secure web-facing resources, but Shield mitigates DDoS attacks while WAF filters specific HTTP request patterns.
- AWS Firewall Manager: Both manage security rules, but Firewall Manager is central policy management while WAF is the actual rules engine.
- Amazon CloudFront: Both are used together for web protection, leading to confusion, but CloudFront is a CDN while WAF is a firewall.

### 7. Exam Notes

- SQLi/XSS mitigation → WAF
- An AWS WAF rule can filter traffic carrying SQL injection attacks.

## ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_Amazon-Inspector_16.png) Amazon Inspector

### 1. Definition

Amazon Inspector is an automated, continuous security-assessment service that scans AWS workloads for software vulnerabilities, network exposures, and unintended risk by analyzing EC2 instances, Lambda functions, and container images in Amazon ECR.

It continuously monitors infrastructure for CVEs, network reachability, and configuration weaknesses using AWS-native intelligence feeds, automatically rescanning resources whenever there are changes such as new deployments, updated packages, or new CVEs discovered. Inspector produces prioritized security findings—with exploitability scoring and contextual metadata—sent directly to Security Hub or EventBridge for remediation workflows.

It is fully managed, agent-based for EC2 (via SSM Agent), agentless for Lambda and ECR, and requires no manual scheduling because assessments are continuous.

### 2. Use-Cases

- CVE detection
- Runtime security posture
- Container image scanning

### 3. Additional Info

- Integrates with ECR

### 4. Limitations

- Requires IAM setup for scanning

### 5. Details

- Characteristics: Continuous scanning
- Capabilities: CVE checks; risk scoring
- Pricing Model: Per-resource scan
- Security/IAM: IAM; KMS

### 6. Confusable

- Amazon GuardDuty: Both detect threats, but Inspector analyzes vulnerabilities in workloads while GuardDuty analyzes logs and behavior anomalies.
- AWS Security Hub: Both summarize security posture, but Security Hub aggregates findings while Inspector generates vulnerability findings.
- AWS Config: Both monitor resources, but Config checks configuration compliance while Inspector checks security posture.

### 7. Exam Notes

- “Vulnerability scanning” → Inspector

## ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_Amazon-GuardDuty_16.png) Amazon GuardDuty

### 1. Definition

A continuous, intelligent threat-detection service that analyzes AWS account activity, network traffic, and data access patterns to identify malicious behavior, compromised resources, and unauthorized access.

It uses machine learning, anomaly detection, and threat intelligence feeds—such as malware signatures, botnet indicators, and known malicious IPs—to continuously evaluate CloudTrail events, VPC Flow Logs, DNS logs, EKS runtime events, and S3 data events.

### 2. Use-Cases

- Detect account compromise
- Detect anomalous traffic

### 3. Additional Info

- Monitors CloudTrail, VPC Flow Logs, DNS logs

### 4. Limitations

- Read-only detection; no automatic remediation

### 5. Details

- Characteristics: Threat detection; regional
- Capabilities: Anomaly detection; intel feeds
- Pricing Model: Usage-based
- Security/IAM: IAM; encrypted logs

### 6. Confusable

- AWS Inspector: Both generate findings, but GuardDuty detects threats from logs and events while Inspector scans for vulnerabilities.
- AWS Security Hub: Both appear in security dashboards, but GuardDuty feeds into Security Hub while Security Hub aggregates multiple sources.
- Amazon Macie: Both analyze data security, but Macie focuses on sensitive data classification while GuardDuty focuses on threat detection.

### 7. Exam Notes

- “Anomalous API calls,” “threat intel” → GuardDuty

## ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_Amazon-Macie_16.png) Amazon Macie

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

- Characteristics: ML-based data classification
- Capabilities: PII detection; automated discovery
- Pricing Model: Per-GB inspected + object inventory
- Security/IAM: IAM; KMS for encrypted buckets

### 6. Confusable

- Amazon GuardDuty: Both look for threats or risks, but Macie specifically identifies sensitive data exposure while GuardDuty looks for malicious activity.
- S3 Access Logs: Both relate to S3 security, but S3 logs are raw data while Macie automatically identifies sensitive data risks.
- AWS Config: Both relate to compliance, but Config checks resource configuration while Macie checks data classification.

### 7. Exam Notes

- “PII in S3,” “sensitive data discovery” → Macie

## ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Security-Hub_16.png) AWS Security Hub

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

- Characteristics: Aggregator; multi-account
- Capabilities: Findings normalization; insights; compliance scoring
- Pricing Model: Per-finding and check
- Security/IAM: IAM; cross-account roles

### 6. Confusable

- GuardDuty: Both appear in security workflows, but GuardDuty is a threat detection engine while Security Hub is a central findings aggregator.
- AWS Inspector: Both produce findings, but Inspector scans software while Security Hub presents consolidated security posture.
- AWS Config: Both evaluate compliance, but Config is rule-based resource compliance, while Security Hub blends compliance with threat detection.

### 7. Exam Notes

- “Centralize findings,” “compliance score” → Security Hub

## ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_Amazon-Cognito_16.png) Amazon Cognito

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

- Characteristics: CIAM; scalable auth
- Capabilities: Hosted UI; MFA; custom auth flows
- Pricing Model: MAU-based
- Security/IAM: IAM roles for Identity Pools

### 6. Confusable

- IAM Identity Center: Both handle identity, but Cognito is for application end-user authentication while Identity Center is for employee SSO.
- IAM: Both authenticate users, but IAM is for AWS principals while Cognito is for application users.
- API Gateway Authorizers: Both appear in API authentication, but API Gateway invokes Cognito as one of multiple identity provider options.

### 7. Exam Notes

- “User Pools = authentication,” “Identity Pools = AWS access”

## ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Certificate-Manager_16.png) AWS Certificate Manager (ACM)

### 1. Definition

ACM helps you to provision, manage, and deploy SSL/TLS certificates on AWS managed resources. SSL/TLS certificates are used to encrypt data traveling across a network.

### 2. Use-Cases

- Enabling HTTPS on ALB, CloudFront, API Gateway
- Automatic certificate renewal

### 3. Additional Info

- Supports public and private certificates

### 4. Limitations

- Cannot export public certs (only private CA certs)

### 5. Details

- Characteristics: Managed PKI; global for CloudFront
- Capabilities: Auto-renewal; DNS validation
- Pricing Model: Public certs free; ACM PCA billed
- Security/IAM: IAM; ACM PCA permissions

### 6. Confusable

- Amazon CloudFront: Both deal with HTTPS certificates, but CloudFront uses certificates while ACM manages, issues, and renews them.
- AWS IAM Server Certificates: Both hold certificates, but IAM certificates are legacy and not recommended vs ACM-managed certs.
- AWS KMS: Both deal with cryptography, but KMS manages encryption keys while ACM manages TLS certificates.

### 7. Exam Notes

- “Free certs,” “automatic renewal” → ACM

## ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Artifact_16.png) AWS Artifact

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

- Characteristics: Compliance documentation hub
- Capabilities: Reports; certifications; agreements
- Pricing Model: Free
- Security/IAM: IAM policies for access

### 6. Confusable

- AWS Config: Both relate to compliance, but Artifact provides AWS compliance reports while Config checks your own resource compliance.
- AWS Audit Manager: Both provide compliance evidence, but Audit Manager manages evidence collection while Artifact provides compliance documents.
- AWS Organizations: Both help manage enterprise governance, but Artifact is about documentation, not account structuring.

### 7. Exam Notes

- “Compliance reports,” “AWS certifications” → Artifact

## ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Config_16.png) AWS Config

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

- Characteristics: Compliance + configuration history
- Capabilities: Rules; remediation; timeline views
- Pricing Model: Per-rule evaluation + configuration items
- Security/IAM: IAM; KMS for logs

### 6. Confusable

- AWS CloudTrail: Both track resource-related activity, but CloudTrail logs API calls while Config logs configuration changes.
- AWS Security Hub: Both relate to governance, but Security Hub aggregates findings while Config checks compliance rules.
- AWS Audit Manager: Both support audits, but Audit Manager prepares evidence packages while Config captures configuration histories.
- Trusted Advisor provides real-time guidance to help you follow AWS best practices to provision resources, but does does not audit and monitor changes to AWS resources.

### 7. Exam Notes

- “Configuration history,” “compliance rules” → Config

## ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Audit-Manager_16.png) AWS Audit Manager

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

- Characteristics: Compliance automation
- Capabilities: Evidence collection; assessment workflows
- Pricing Model: Per-assessment + evidence storage
- Security/IAM: IAM; encryption

### 6. Confusable

- AWS Config: Both support compliance, but Config monitors configuration while Audit Manager organizes compliance evidence for audits.
- AWS Artifact: Both deal with compliance information, but Artifact provides AWS certs/reports while Audit Manager gathers internal evidence.
- Security Hub: Both appear in governance dashboards, but Security Hub aggregates security findings while Audit Manager focuses on audits.

### 7. Exam Notes

- “Automated compliance evidence” → Audit Manager

## 🟥 IAM Access Analyzer

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

- Characteristics: Access analyzer; policy review
- Capabilities: Public access detection; cross-account alerts
- Pricing Model: Free
- Security/IAM: IAM-managed

### 6. Confusable

- IAM Policy Simulator: Both analyze permissions, but Policy Simulator tests policies while Access Analyzer discovers unintended external access.
- AWS Config: Both check security posture, but Config inspects configuration resources while Access Analyzer inspects trust boundaries.
- AWS Organizations Service Control Policies (SCPs): Both concern permission boundaries, but SCPs enforce restrictions while Access Analyzer flags access issues.

### 7. Exam Notes

- “Detect unintended public or cross-account access” → Access Analyzer

---

# ![icon](icons/category/Arch-Category_16/Arch-Category_Management-Governance_16.png) Management and Governance

Management and Governance tools **monitor, optimize, and standardize cloud operations**.
They help you control cost, enforce policies, manage configurations, and view operational health.
Their core intent is to run AWS environments predictably, efficiently, and at scale.

## ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-CloudFormation_16.png) AWS CloudFormation

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

- Characteristics: IaC; declarative
- Capabilities: Drift detection; change sets
- Pricing Model: Free (pay for resources)
- Security/IAM: IAM roles; stack policies

### 6. Confusable

- Terraform: Both are IaC tools, but CloudFormation is AWS-native while Terraform is multi-cloud and uses a different configuration language.
- AWS CDK: Both define AWS infrastructure, but CDK uses real programming languages that synthesize CloudFormation templates.
- AWS Service Catalog: Both provision resources, but Service Catalog manages approved product portfolios while CloudFormation directly deploys infrastructure templates.

### 7. Exam Notes

- “Infrastructure as Code,” “StackSets” → CloudFormation

## ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Systems-Manager_16.png) AWS Systems Manager

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

- Characteristics: Ops management suite
- Capabilities: Automation; Run Command; Patch Manager
- Pricing Model: Free for many features
- Security/IAM: IAM; KMS; secure tunnels

### 6. Confusable

- AWS CloudFormation: Both configure infrastructure, but CloudFormation defines resources while SSM manages them post-deployment.
- AWS OpsWorks: Both manage configurations, but OpsWorks uses Chef/Puppet metaphors while SSM is the modern unified management ecosystem.
- AWS Config: Both track changes, but Config logs configuration state while Systems Manager executes commands, automations, and patching.

### 7. Exam Notes

- “Run Command,” “Session Manager (no SSH)” → SSM

## ![icon](icons/service/Arch_Management-Governance/16/Arch_Amazon-CloudWatch_16.png) Amazon CloudWatch

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

- Characteristics: Observability; regional
- Capabilities: Metrics; Logs Insights; alarms
- Pricing Model: Per-metric, log ingestion, dashboards
- Security/IAM: IAM; KMS

### 6. Confusable

- AWS CloudTrail: Both provide operational visibility, but CloudWatch logs metrics, logs, alarms, and dashboards while CloudTrail records API activity.
- AWS X-Ray: Both provide observability, but X-Ray traces request paths while CloudWatch aggregates logs and metrics.
- AWS Config: All appear in compliance dashboards, but Config monitors resource configuration state while CloudWatch tracks operational performance.

### 7. Exam Notes

- “Metrics + Logs + Alarms” → CloudWatch

## ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-CloudTrail_16.png) AWS CloudTrail

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

- Characteristics: API logging; multi-region
- Capabilities: Trails; insights; event history
- Pricing Model: Per-event for org trails
- Security/IAM: IAM; KMS

### 6. Confusable

- Amazon CloudWatch: Both track activity, but CloudWatch logs/metrics monitor system behavior while CloudTrail records API calls and user actions.
- AWS Config: Both relate to governance, but Config records configuration changes while CloudTrail records operational API events.
- IAM Access Analyzer: Both provide insight into access issues, but Access Analyzer evaluates policies while CloudTrail shows who actually invoked actions.

### 7. Exam Notes

- “API calls,” “audit logs,” “governance” → CloudTrail

## ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Organizations_16.png) AWS Organizations

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

- Characteristics: Multi-account governance
- Capabilities: SCPs; consolidated billing
- Pricing Model: Free
- Security/IAM: IAM; SCPs

### 6. Confusable

- AWS Control Tower: Both manage multi-account governance, but Control Tower provides prescriptive guardrails while Organizations provides the raw account/group structure.
- IAM Identity Center: Both distribute access, but Identity Center manages workforce authentication while Organizations manages the account hierarchy.
- AWS Service Catalog: Both govern provisioning, but Service Catalog approves product templates while Organizations governs accounts and SCPs.
- IAM: While IAM governs permissions within an account, Organizations governs what accounts are allowed to do at all

### 7. Exam Notes

- “SCPs restrict, do not grant permissions” → Organizations

## ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Control-Tower_16.png) AWS Control Tower

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

- Characteristics: Turnkey landing zone
- Capabilities: Guardrails; account factory
- Pricing Model: Free (resources billed)
- Security/IAM: SCPs; IAM; Config rules

### 6. Confusable

- AWS Organizations: Both manage multi-account environments, but Organizations is the underlying structure while Control Tower adds automated guardrails and opinionated best practices.
- AWS Service Catalog: Both enforce governance, but Service Catalog governs provisioning while Control Tower governs accounts and infrastructure baselines.
- AWS Config: Both monitor compliance, but Control Tower uses Config rules to enforce guardrails automatically.

### 7. Exam Notes

- “Landing zone,” “guardrails” → Control Tower

## ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Service-Catalog_16.png) AWS Service Catalog

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

- Characteristics: Product governance
- Capabilities: Portfolios; versioning
- Pricing Model: Free
- Security/IAM: IAM; constraints

### 6. Confusable

- AWS CloudFormation: Both deploy infrastructure, but Service Catalog manages approved products while CloudFormation handles raw IaC templates.
- AWS Marketplace: Both publish products, but Marketplace is commercial procurement while Service Catalog is internal organizational governance.
- AWS Organizations: Both impose governance, but Organizations controls accounts while Service Catalog controls allowable provisioning patterns.

### 7. Exam Notes

- “Approved products,” “governed self-service” → Service Catalog

## ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-License-Manager_16.png) AWS License Manager

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

- Characteristics: License governance
- Capabilities: Rules; tracking; enforcement
- Pricing Model: Free
- Security/IAM: IAM

### 6. Confusable

- AWS Service Catalog: Both handle governance, but License Manager enforces license usage while Service Catalog governs provisioning of templates.
- AWS Marketplace: Both involve third-party software, but Marketplace distributes products while License Manager governs compliance and entitlements.
- AWS Config: Both track resource states, but Config tracks configurations while License Manager ensures licensing rules aren't violated.

### 7. Exam Notes

- “Track licenses,” “BYOL governance” → License Manager

## ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Health-Dashboard_16.png) AWS Health Dashboard

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

- Characteristics: AWS service health visibility
- Capabilities: Outage alerts; maintenance notices
- Pricing Model: Free
- Security/IAM: IAM

### 6. Confusable

- Amazon CloudWatch: Both provide operational insights, but CloudWatch monitors your resources while Health Dashboard reports AWS service-level events that may impact you.
- AWS Personal Health Dashboard (legacy): Both report AWS health, but the unified dashboard aggregates both organizational and account-specific impact notifications.
- AWS Trusted Advisor: Both provide operational guidance, but Trusted Advisor gives optimization recommendations while Health Dashboard reports service health events.

### 7. Exam Notes

- “Service disruptions,” “maintenance events” → Health Dashboard

## ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Trusted-Advisor_16.png) AWS Trusted Advisor

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

- Characteristics: Best-practice advisor
- Capabilities: Recommendations; dashboards
- Pricing Model: Included with support tier
- Security/IAM: IAM

### 6. Confusable

- AWS Config: Both generate compliance findings, but Config enforces resource-level rules while Trusted Advisor provides best-practice optimization checks.
- AWS Health Dashboard: Both report issues, but Health shows AWS service disruptions while Trusted Advisor shows configuration or cost inefficiencies.
- AWS Compute Optimizer: Both suggest cost/performance improvements, but Compute Optimizer focuses on EC2/RDS rightsizing while Trusted Advisor covers broader categories.

### 7. Exam Notes

- “Cost optimization,” “support plan required” → Trusted Advisor
- Trusted Advisor checks the root account and warns if MFA is not enabled.
- Trusted Advisor does not provide notifications about software patches for EC2 instances.

## ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Compute-Optimizer_16.png) AWS Compute Optimizer

Machine learning–powered recommendations to rightsize AWS resources for better performance and cost efficiency.

### 1. Definition

AWS Compute Optimizer is fundamentally about:

- Rightsizing resources
- Reducing cost
- Improving cost-to-performance efficiency
- Using utilization data (from CloudWatch) to inform decisions
- Supporting the Cost Optimization pillar of the Well-Architected Framework

AWS Compute Optimizer is a fully managed recommendation service that analyzes historical utilization metrics from Amazon CloudWatch and suggests optimal configurations for EC2 instances, Auto Scaling groups, EBS volumes, and Lambda functions. It identifies over-provisioned and under-provisioned resources to reduce cost and improve performance.

### 2. Use-Cases

- Rightsizing EC2 instances for cost savings
- Improving performance by identifying under-provisioned compute
- Selecting better EBS volume types (e.g., gp2 → gp3)
- Optimizing Lambda memory allocation
- Pre-migration workload assessment
- Helping organizations meet Cost Optimization pillar goals

### 3. Additional Info

- Uses 14 days+ of CloudWatch metrics for analysis
- Provides instance family recommendations (e.g., CPU architecture changes)
- Offers resource-level savings estimates
- Integrates with AWS Organizations for cross-account visibility
- Supports EC2 Auto Scaling groups recommendations

### 4. Limitations

- Requires enough metric history to make accurate recommendations
- Does not automatically apply changes — manual adjustment required
- Only supports certain resource types (no RDS, DynamoDB, etc.)
- Recommendations may not reflect application-specific constraints

### 5. Details

#### Characteristics

- ML-driven optimization service
- Analyzes CloudWatch utilization trends
- Supports EC2, ASGs, EBS volumes, Lambda

#### Pricing Model

- Free tier for basic recommendations
- Advanced tier (optional): additional insights for a fee per resource

#### Security / IAM

- Uses IAM permissions for visibility and cross-account analysis
- Works with KMS for encrypted CloudWatch metric data (if enabled)
- Integrates with AWS Organizations for centralized governance

### 6. Confusable Services

- AWS Trusted Advisor use broader checklist-based best-practice checks, while CO use ML-based deep rightsizing
- AWS Cost Explorer analyzes spending trends, while CO analyzes utilization for rightsizing
- Amazon EC2 Auto Scaling adjusts capacity, while CO recommends optimal instance configurations
- AWS Pricing Calculator estimates future cost, while CO recommends configurations based on usage data

### 7. Exam Notes

- Keywords: rightsizing, ML-based recommendations, over/under-provisioned, CloudWatch metrics
- Use Compute Optimizer when questions mention:
  - “Reduce cost by selecting the right instance size”
  - “Analyze instance utilization automatically”
  - “Optimize Lambda memory configuration”
  - “Identify overprovisioned resources”
  - “Reduce cost using recommendations”
  - “Choose optimal instance type based on utilization”

## 🟩 AWS Pricing Calculator

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

- Characteristics: Cost modeling tool
- Capabilities: Multi-service estimates; templates
- Pricing Model: Free
- Security/IAM: Public tool; optional save via account

### 6. Confusable

- AWS Cost Explorer: Both estimate costs, but Pricing Calculator forecasts hypothetical workloads while Cost Explorer analyzes actual historical spending.
- AWS Budgets: Both deal with cost planning, but Budgets enforces threshold alerts while Pricing Calculator models expected cost scenarios.
- Migration Evaluator: Both estimate costs, but Migration Evaluator analyzes existing on-prem workloads while Pricing Calculator models cloud-native architectures.

### 7. Exam Notes

- “Estimate costs before deployment” → Pricing Calculator

## 🟩 AWS Data Lifecycle Manager

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

- Characteristics: Snapshot automation
- Capabilities: Policies; retention; tagging
- Pricing Model: Free
- Security/IAM: IAM; KMS for snapshots

### 6. Confusable

- AWS Backup: Both automate data retention, but Backup orchestrates cross-service backups while DLM focuses specifically on EBS snapshot lifecycle policies.
- Amazon S3 Lifecycle Policies: Both automate data transitions, but S3 lifecycle manages object storage tiers while DLM manages EBS snapshot creation/deletion.
- AWS Elastic Disaster Recovery: Both relate to resilience, but DRS replicates full servers while DLM manages only snapshots of EBS volumes.

### 7. Exam Notes

- “Automate EBS snapshots” → DLM

## 🟩 AWS Billing and Cost Management

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

- Characteristics: Billing overview
- Capabilities: Invoices; budgets; alerts
- Pricing Model: Free
- Security/IAM: IAM billing permissions

### 6. Confusable

- AWS Cost Explorer: Both show spending, but Cost Explorer provides visual analytics while the Billing Dashboard provides high-level billing information and payment management.
- AWS Budgets: Both help control cost, but Budgets triggers alerts when thresholds are exceeded while the Billing Dashboard shows current spending summaries.
- AWS Cost & Usage Report (CUR): Both present cost insights, but CUR is raw, detailed billing data while Billing Dashboard is a high-level interface.

### 7. Exam Notes

- “Billing details,” “invoices,” “payment methods” → Billing Dashboard

## ![icon](icons/service/Arch_Cloud-Financial-Management/16/Arch_AWS-Budgets_16.png) AWS Budgets

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

- Characteristics: Budgeting & alerting
- Capabilities: Alerts; forecasting; reports
- Pricing Model: Per-budget
- Security/IAM: IAM

### 6. Confusable

- AWS Cost Explorer: Both analyze cost patterns, but Cost Explorer visualizes spending while Budgets sets limits and alerts based on thresholds.
- AWS Billing Dashboard: Both show cost information, but Budgets enforces proactive cost control while Billing Dashboard is informational.
- AWS Budgets Reports vs CUR: Budgets uses summarized cost data while CUR exposes granular line-item cost records.

### 7. Exam Notes

- “Alert when cost exceeds threshold” → Budgets

## ![icon](icons/service/Arch_Cloud-Financial-Management/16/Arch_AWS-Cost-Explorer_16.png) AWS Cost Explorer

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

- Characteristics: Visualization + analysis tool
- Capabilities: Filtering; trends; recommendations
- Pricing Model: Free (detailed data may incur cost)
- Security/IAM: IAM

### 6. Confusable

- AWS Budgets: Both manage costs, but Budgets sets alerts while Explorer analyzes past spending trends visually.
- AWS Cost & Usage Report (CUR): Both show usage, but CUR provides raw granular billing data while Explorer aggregates and visualizes trends.
- AWS Pricing Calculator: Both estimate costs, but the Calculator forecasts future workloads while Explorer analyzes real historical usage.

### 7. Exam Notes

- “Analyze past spend,” “RI recommendations” → Cost Explorer

## ![icon](icons/service/Arch_Cloud-Financial-Management/16/Arch_AWS-Cost-and-Usage-Report_16.png) AWS Cost and Usage Reports (CUR)

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

- Characteristics: Raw cost data; hourly granularity
- Capabilities: Line-item details; multi-service analytics
- Pricing Model: Free (S3 storage billed)
- Security/IAM: IAM; encryption

### 6. Confusable

- AWS Cost Explorer: Both analyze cost, but Explorer summarizes trends while CUR provides detailed line-item billing data for advanced analysis.
- AWS Billing Dashboard: Both show billing information, but the Billing Dashboard is high-level while CUR is the most granular billing dataset.
- AWS Budgets: Both use cost data, but CUR is a raw export while Budgets reads summarized cost records to enforce thresholds.

### 7. Exam Notes

- “Most detailed cost data,” “S3-exported” → CUR

## ![icon](icons/service/Arch_Cloud-Financial-Management/16/Arch_AWS-Billing-Conductor_16.png) AWS Billing Conductor

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

- Characteristics: Internal billing governance
- Capabilities: Pricing rules; billing groups
- Pricing Model: Per-billing record
- Security/IAM: IAM

### 6. Confusable

- AWS Cost Explorer: Both analyze cost, but Explorer summarizes trends while CUR provides detailed line-item billing data for advanced analysis.
- AWS Billing Dashboard: Both show billing information, but the Billing Dashboard is high-level while CUR is the most granular billing dataset.
- AWS Budgets: Both use cost data, but CUR is a raw export while Budgets reads summarized cost records to enforce thresholds.
- Cost Explorer (analysis), CUR (raw data)

### 7. Exam Notes

- “Internal chargeback,” “billing groups” → Billing Conductor

---

# ![icon](icons/category/Arch-Category_16/Arch-Category_Application-Integration_16.png) Application Integration

Application Integration services **connect independent systems** using messages, events, and workflows.
They let components communicate without depending directly on each other.
Their core intent is to build distributed systems that are resilient, loosely coupled, and scalable.

## ![icon](icons/service/Arch_App-Integration/16/Arch_Amazon-EventBridge_16.png) Amazon EventBridge

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

- Characteristics: Serverless event bus
- Capabilities: Rules; filtering; buses; archives; replays
- Pricing Model: Per-event publish/invoke
- Security/IAM: IAM; resource policies

### 6. Confusable

- Amazon SNS: Both deliver events/messages, but SNS is pub/sub messaging while EventBridge routes events from AWS services, SaaS apps, and custom apps with filtering rules.
- Amazon SQS: Both move messages, but EventBridge is event routing and orchestration while SQS is a decoupling queue with no filtering logic.
- AWS Step Functions: Both coordinate workflows, but EventBridge routes events while Step Functions manages stateful workflows.

### 7. Exam Notes

- “Event bus,” “routing,” “SaaS events” → EventBridge

## ![icon](icons/service/Arch_App-Integration/16/Arch_Amazon-Simple-Queue-Service_16.png) Amazon SQS

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

- Characteristics: Queue-based messaging
- Capabilities: DLQs; visibility timeout; large messages
- Pricing Model: Per-request
- Security/IAM: IAM policies; SSE encryption

### 6. Confusable

- Amazon SNS: Both are messaging services, but SNS is pub/sub broadcast while SQS is point-to-point queueing with message persistence.
- Amazon EventBridge: Both handle event messages, but EventBridge is an event bus with filtering while SQS is a simple messaging queue.
- AWS Lambda: Often paired in diagrams, but Lambda processes messages while SQS stores them.

### 7. Exam Notes

- “Decoupling with queues,” “FIFO ordering” → SQS

## ![icon](icons/service/Arch_App-Integration/16/Arch_Amazon-Simple-Notification-Service_16.png) Amazon SNS

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

- Characteristics: Pub/Sub
- Capabilities: SMS/email/mobile push; SQS fanout
- Pricing Model: Per-request + delivery costs
- Security/IAM: IAM; topic policies

### 6. Confusable

- Amazon SQS: Both are messaging solutions, but SNS pushes messages to many subscribers while SQS stores messages for consumers to poll.
- Amazon EventBridge: Both offer event-driven patterns, but EventBridge is rules-based routing while SNS is simple pub/sub.
- AWS Lambda: SNS can trigger Lambda, causing confusion, but SNS is the broadcaster, Lambda the compute invoker.

### 7. Exam Notes

- “Pub/sub,” “fanout,” “notifications” → SNS

## ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_Elastic-Load-Balancing_16.png) Application Load Balancer (ALB)

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

- Characteristics: Layer 7 routing
- Capabilities: Rules; host/path routing; auth; sticky sessions
- Pricing Model: Per-LCU + hourly
- Security/IAM: SGs; IAM for auth; WAF integration

### 6. Confusable

- Network Load Balancer (NLB): Both distribute traffic, but ALB operates at Layer 7 with HTTP/HTTPS routing while NLB operates at Layer 4 for ultra-low-latency TCP/UDP.
- Gateway Load Balancer (GWLB): Both forward traffic, but GWLB inserts security appliances while ALB handles application-level routing rules.
- Amazon API Gateway: Both route HTTP requests, but ALB is a load balancer for web workloads while API Gateway is an API management platform with throttling, auth, and transformations.

### 7. Exam Notes

- “Layer 7,” “path-based routing,” “microservices” → ALB

---

# ![icon](icons/category/Arch-Category_16/Arch-Category_Developer-Tools_16.png) Developer Tools

Developer Tools **automate building, testing, and deploying software** for consistent CI/CD workflows.
They manage source code, track changes, and streamline releases.
Their core intent is to help teams ship software faster, safer, and with repeatable processes.

## ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-Cloud9_16.png) AWS Cloud9

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

- Characteristics: Browser IDE
- Capabilities: Terminal; debugger; EC2/SSH environments
- Pricing Model: EC2/storage costs
- Security/IAM: IAM; VPC access controls

### 6. Confusable

- AWS CloudShell: Both provide cloud-based command environments, but Cloud9 is a full IDE while CloudShell is a lightweight terminal for AWS CLI usage.
- Amazon EC2: Cloud9 environments can run on EC2, leading to confusion, but EC2 provides compute while Cloud9 provides a development environment.
- AWS CodeCommit: Both involve code, but CodeCommit is a repository while Cloud9 is an editing environment.

### 7. Exam Notes

- “Cloud IDE,” “collaboration” → Cloud9

## ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-CloudShell_16.png) AWS CloudShell

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

- Characteristics: Browser shell
- Capabilities: CLI; SDKs; persistent home directory
- Pricing Model: Free
- Security/IAM: IAM

### 6. Confusable

- AWS Cloud9: Both are browser-based tools, but CloudShell is a terminal-only environment, not a full IDE.
- AWS CLI: CloudShell includes the CLI, but the CLI is a command-line tool while CloudShell is a browser-hosted environment to run it.
- AWS Systems Manager Session Manager: Both give shell access, but Session Manager connects to EC2 instances while CloudShell is a local cloud terminal.

### 7. Exam Notes

- “Ready-to-use CLI in browser” → CloudShell

## ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-CodeCommit_16.png) AWS CodeCommit

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

- Characteristics: Managed Git
- Capabilities: Branching; pull requests; triggers
- Pricing Model: Per-active-user
- Security/IAM: IAM; KMS

### 6. Confusable

- GitHub: Both host Git repositories, but CodeCommit is AWS-native with IAM integration while GitHub is a third-party SaaS platform.
- AWS CodeArtifact: Both store code-related content, but CodeArtifact stores build artifacts/packages while CodeCommit stores Git repositories.
- AWS CodeBuild: Both appear in CI/CD pipelines, but CodeBuild performs builds while CodeCommit hosts source code.

### 7. Exam Notes

- “Private Git repos on AWS” → CodeCommit

## ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-CodeBuild_16.png) AWS CodeBuild

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

- Characteristics: Managed CI
- Capabilities: Parallel builds; cache; reports
- Pricing Model: Build-time minutes
- Security/IAM: IAM; VPC builds

### 6. Confusable

- AWS CodePipeline: Both appear in CI/CD pipelines, but CodePipeline orchestrates stages while CodeBuild performs the build/test steps.
- AWS CodeDeploy: Both deploy artifacts, but CodeDeploy handles deployments while CodeBuild compiles and packages code.
- AWS Lambda: Both can execute code, but Lambda is serverless compute while CodeBuild is build automation.

### 7. Exam Notes

- “CI builds,” “buildspec” → CodeBuild

## ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-CodePipeline_16.png) AWS CodePipeline

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

- Characteristics: CI/CD orchestration
- Capabilities: Stages; approvals; automation
- Pricing Model: Per-pipeline
- Security/IAM: IAM

### 6. Confusable

- AWS Step Functions: Both orchestrate tasks, but Step Functions runs general workflows while CodePipeline orchestrates CI/CD stages.
- AWS CodeBuild: Both appear in CI/CD, but CodeBuild builds artifacts while CodePipeline sequences build/test/deploy.
- AWS CodeDeploy: Both are part of deployment workflows, but CodePipeline is orchestration while CodeDeploy performs rollout.

### 7. Exam Notes

- “Pipeline orchestration,” “automate deployments” → CodePipeline

## ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-CodeDeploy_16.png) AWS CodeDeploy

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

- Characteristics: Deployment automation
- Capabilities: Blue/green; canary; hooks
- Pricing Model: Free (EC2/Lambda usage billed)
- Security/IAM: IAM; instance profiles

### 6. Confusable

- AWS Elastic Beanstalk: Both deploy applications, but Beanstalk manages infrastructure while CodeDeploy focuses on deployment mechanics.
- AWS CodePipeline: Both run deployments, but CodePipeline coordinates workflows while CodeDeploy performs updates to servers/instances.
- AWS AppConfig: Both roll out changes, but AppConfig deploys configuration while CodeDeploy deploys application code.

### 7. Exam Notes

- “Blue/green deployments,” “AppSpec” → CodeDeploy

## ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-CodeArtifact_16.png) AWS CodeArtifact

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

- Characteristics: Managed artifact repo
- Capabilities: Package domains/repos; upstream caching
- Pricing Model: Storage + data transfer
- Security/IAM: IAM; KMS

### 6. Confusable

- Amazon ECR: Both store software artifacts, but ECR holds container images while CodeArtifact holds package dependencies (npm, Maven, PyPI).
- AWS CodeCommit: Both store code-related items, but CodeCommit is a Git repository while CodeArtifact is a dependency/package repository.
- Amazon S3: Both can store files, but S3 is general purpose while CodeArtifact provides package-management workflows.

### 7. Exam Notes

- “Package repository,” “npm/Maven/PyPI” → CodeArtifact

## ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-X-Ray_16.png) AWS X-Ray

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

- Characteristics: Tracing + observability
- Capabilities: Segments; subsegments; sampling
- Pricing Model: Trace storage and retrieval
- Security/IAM: IAM; KMS

### 6. Confusable

- Amazon CloudWatch: Both monitor applications, but CloudWatch handles metrics/logs while X-Ray provides end-to-end distributed tracing.
- AWS CloudTrail: Both provide diagnostic data, but CloudTrail logs AWS API calls while X-Ray traces application requests.
- AWS CodeGuru: Both help debug performance issues, but CodeGuru provides code-level insights while X-Ray maps runtime request paths.

### 7. Exam Notes

- “Distributed tracing,” “service map” → X-Ray

## ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-AppConfig_16.png) AWS AppConfig

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

- Characteristics: Config release management
- Capabilities: Validation; controlled rollout
- Pricing Model: Per-configuration deployment
- Security/IAM: IAM; KMS

### 6. Confusable

- AWS Systems Manager Parameter Store: Both manage configuration values, but AppConfig controls deployment and validation of configurations.
- AWS CodeDeploy: Both perform staged rollouts, but CodeDeploy deploys code while AppConfig deploys configuration.
- AWS CloudFormation: Both handle application setup, but CloudFormation defines infrastructure while AppConfig handles runtime configuration changes.

### 7. Exam Notes

- “Feature flags,” “safe config rollouts” → AppConfig

---

# ![icon](icons/category/Arch-Category_16/Arch-Category_Front-End-Web-Mobile_16.png) Frontend and Mobile

Frontend and Mobile services **host and support user-facing applications** across web and mobile platforms.
They provide managed backends, APIs, and hosting environments designed for modern client apps.
Their core intent is to deliver responsive, scalable user experiences.

## ![icon](icons/service/Arch_Front-End-Web-Mobile/16/Arch_AWS-Amplify_16.png) AWS Amplify

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

- Characteristics: Frontend + backend development platform
- Capabilities: Hosting; auth; DataStore; API generation; CI/CD
- Pricing Model: Hosting + backend resource usage
- Security/IAM: IAM roles; Cognito auth

### 6. Confusable

- AWS AppSync: Both support mobile/web apps, but AppSync provides GraphQL APIs while Amplify provides the full development framework/toolchain.
- AWS Elastic Beanstalk: Both simplify deployment, but Amplify is optimized for frontend/mobile and serverless backends while Beanstalk targets general web apps on EC2.
- Amazon API Gateway: Both expose APIs, but Amplify generates front-end–friendly tooling while API Gateway is a general-purpose API front door.

### 7. Exam Notes

- “Frontend platform,” “hosting + auth,” “Amplify Studio” → Amplify

## ![icon](icons/service/Arch_App-Integration/16/Arch_AWS-AppSync_16.png) AWS AppSync

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

- Characteristics: Managed GraphQL
- Capabilities: Subscriptions; resolvers; caching
- Pricing Model: Per-request + real-time messages
- Security/IAM: IAM; API keys; Cognito; OIDC

### 6. Confusable

- Amazon API Gateway: Both expose APIs, but API Gateway serves REST/HTTP/WebSocket while AppSync provides managed GraphQL.
- AWS Amplify: Both appear in mobile architectures, but Amplify is a frontend toolkit while AppSync is a backend API service.
- Amazon DynamoDB: Often paired with AppSync for GraphQL resolvers, but DynamoDB is the database while AppSync is the GraphQL engine.

### 7. Exam Notes

- “GraphQL,” “real-time subscriptions,” “offline-ready apps” → AppSync

---

# ![icon](icons/category/Arch-Category_16/Arch-Category_Business-Applications_16.png) Business Applications

Business Applications provide **ready-made solutions** for communication, customer engagement, and internal workflows.
They run fully managed, so teams can operate them without infrastructure overhead.
Their core intent is to solve business needs quickly using turnkey cloud tools.

## ![icon](icons/service/Arch_Business-Applications/16/Arch_Amazon-Connect_16.png) Amazon Connect

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

- Characteristics: Cloud contact center; scalable
- Capabilities: Call routing; analytics; real-time dashboards; recordings
- Pricing Model: Pay-per-minute + telephony
- Security/IAM: IAM; KMS; PCI compliance options

### 6. Confusable

- Amazon SES: Both are communication services, but Connect is for call centers while SES is for email delivery.
- AWS Lambda: Both appear in Connect workflows, but Lambda powers logic while Connect provides the contact center system.
- Amazon Chime SDK: Both support voice/video, but Chime is for conferencing while Connect is for contact center operations.

### 7. Exam Notes

- “Cloud contact center,” “IVR,” “omnichannel support” → Connect

## ![icon](icons/service/Arch_Business-Applications/16/Arch_Amazon-Simple-Email-Service_16.png) Amazon Simple Email Service (SES)

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

- Characteristics: Email sending engine
- Capabilities: SMTP interface; APIs; analytics; reputation management
- Pricing Model: Per-email + data transfer
- Security/IAM: IAM; encryption in-transit

### 6. Confusable

- Amazon SNS: Both send notifications, but SNS is pub/sub messaging while SES is email delivery.
- Amazon Pinpoint: Both send messages to users, but Pinpoint is multi-channel (SMS, email, push) with analytics while SES is focused on high-volume email sending.
- Amazon Connect: Both handle customer communications, but Connect is for voice/call workflows while SES handles email.

### 7. Exam Notes

- “Transactional email,” “SMTP,” “deliverability” → SES

---

# ![icon](icons/category/Arch-Category_16/Arch-Category_End-User-Computing_16.png) End-User Computing

End-User Computing **delivers virtual desktops and applications** to users anywhere.
It centralizes data and apps while enabling secure remote access.
Its core intent is to support scalable, secure remote work without managing physical devices.

## ![icon](icons/service/Arch_End-User-Computing/16/Arch_Amazon-AppStream-2_16.png) Amazon AppStream 2.0

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

- Characteristics: Application streaming; scalable
- Capabilities: Multi-session streaming; GPU support; persistent settings
- Pricing Model: Per-hour per-streaming-instance
- Security/IAM: IAM; VPC; KMS; SSO integrations

### 6. Confusable

- Amazon WorkSpaces: Both provide remote user environments, but WorkSpaces is full desktop streaming while AppStream streams individual applications.
- Amazon WorkSpaces Secure Browser: Both stream UI sessions, but Secure Browser is limited to browser-based apps while AppStream supports full Windows applications.
- AWS Client VPN: Both support remote users, but Client VPN provides network access while AppStream provides streamed applications.

### 7. Exam Notes

- “Stream applications only,” “no full desktop” → AppStream 2.0

## ![icon](icons/service/Arch_End-User-Computing/16/Arch_Amazon-WorkSpaces-Family_16.png) Amazon WorkSpaces

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

- Characteristics: Managed VDI; persistent desktops
- Capabilities: Directory integration; GPU bundles; multi-session
- Pricing Model: Monthly or hourly per-desktop
- Security/IAM: IAM; KMS; directory services; network isolation

### 6. Confusable

- Amazon AppStream 2.0: Both stream desktops/apps, but WorkSpaces provides full persistent virtual desktops while AppStream streams individual applications.
- Amazon WorkSpaces Secure Browser: All provide remote access, but Secure Browser offers isolated browser sessions while WorkSpaces provides full desktops.
- AWS Client VPN: Both enable remote work, but Client VPN connects devices to VPCs while WorkSpaces provides a cloud-hosted desktop.

### 7. Exam Notes

- “Full desktop,” “Windows/Linux VDI” → WorkSpaces

## ![icon](icons/service/Arch_End-User-Computing/16/Arch_Amazon-WorkSpaces-Family_16.png) WorkSpaces Secure Browser

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

- Characteristics: Managed isolated browser
- Capabilities: Web isolation; policy controls; session logging
- Pricing Model: Per-hour streaming session
- Security/IAM: IAM; KMS; SSO; network controls

### 6. Confusable

- Amazon WorkSpaces: Both provide remote desktop-like access, but Secure Browser gives only an isolated browser while WorkSpaces gives a full desktop.
- Amazon AppStream 2.0: Both stream UI interactions, but Secure Browser is browser-only while AppStream streams full applications.
- AWS Client VPN: Both enable remote connectivity, but Client VPN provides network tunneling while Secure Browser provides an isolated browsing environment.

### 7. Exam Notes

- “Secure isolated browser,” “zero-trust access” → Secure Browser

---

# ![icon](icons/category/Arch-Category_16/Arch-Category_Internet-of-Things_16.png) IoT

IoT services **connect physical devices to the cloud** and manage their data securely.
They allow sensors and hardware to interact with cloud applications in real time.
Their core intent is to bridge the physical and digital worlds for monitoring, automation, and intelligence.

## ![icon](icons/service/Arch_Internet-of-Things/16/Arch_AWS-IoT-Core_16.png) AWS IoT Core

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

- Characteristics: Managed device connectivity; event routing
- Capabilities: Pub/sub messaging; rules; Shadows; Just-In-Time Registration
- Pricing Model: Messaging, rules evaluations, device connectivity
- Security/IAM: X.509 certificates; IAM policies; fine-grained topic access

### 6. Confusable

- AWS IoT Greengrass: Both are part of the IoT ecosystem, but IoT Core is cloud-based messaging while Greengrass runs local compute on edge devices.
- Amazon SNS: Both deliver messages, but SNS is pub/sub for apps while IoT Core handles MQTT-based messaging for IoT devices.
- Amazon Kinesis: Both process real-time streams, but IoT Core focuses on device telemetry while Kinesis handles general streaming data.

### 7. Exam Notes

- “Device Shadows,” “MQTT,” “connect devices to AWS” → IoT Core

## ![icon](icons/service/Arch_Internet-of-Things/16/Arch_AWS-IoT-Greengrass_16.png) AWS IoT Greengrass

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

- Characteristics: Edge compute; offline-capable
- Capabilities: Local messaging; ML inference; sync; container/Lambda execution
- Pricing Model: Per-device tiering
- Security/IAM: X.509 certs; IAM; secure local runtime

### 6. Confusable

- AWS IoT Core: Both handle IoT workloads, but IoT Core is cloud messaging while Greengrass runs local compute and device-side logic.
- AWS Lambda: Both run functions, but Greengrass runs them on devices while Lambda runs them in the AWS cloud.
- Amazon ECS Anywhere: Both run workloads outside AWS, but Greengrass runs on IoT edge devices while ECS Anywhere targets general-purpose servers.

### 7. Exam Notes

- “Local compute,” “offline operation,” “edge ML” → Greengrass

---

# ![icon](icons/category/Arch-Category_16/Arch-Category_Migration-Modernization_16.png) Migration and Transfer

Migration services **move applications, servers, and data into AWS** reliably.
They support discovery, replication, bulk transfer, and modernization efforts.
Their core intent is to make cloud adoption smooth, accurate, and low-risk.

## ![icon](icons/service/Arch_Migration-Modernization/16/Arch_AWS-Migration-Hub_16.png) AWS Migration Hub

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

- Characteristics: Central migration dashboard
- Capabilities: Progress tracking; analytics; grouping resources
- Pricing Model: Free
- Security/IAM: IAM

### 6. Confusable

- AWS Application Discovery Service: Both help with migration insights, but Discovery Service collects server metadata while Migration Hub aggregates and tracks migration progress.
- AWS Database Migration Service (DMS): Both handle migration workflows, but DMS focuses on data migration while Migration Hub coordinates overall migration activities.
- AWS Elastic Disaster Recovery: Both replicate servers, but DRS is for failover resilience, not migration tracking.

### 7. Exam Notes

- “Single place to track migrations” → Migration Hub

## ![icon](icons/service/Arch_Migration-Modernization/16/Arch_AWS-Application-Discovery-Service_16.png) AWS Application Discovery Service

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

- Characteristics: Discovery + dependency mapping
- Capabilities: Performance data; dependency graphs
- Pricing Model: Free
- Security/IAM: IAM; encrypted data transfer

### 6. Confusable

- Migration Hub: Both relate to migration inventory, but Discovery collects data while Migration Hub presents and tracks it.
- AWS DMS: Both are migration tools, but DMS migrates databases, not servers or inventories.
- AWS Systems Manager Inventory: Both catalog resources, but SSM Inventory catalogs AWS/EC2 resources while Discovery catalogs on-prem resources.

### 7. Exam Notes

- “Application dependency mapping,” “on-prem discovery” → ADS

## ![icon](icons/service/Arch_Database/16/Arch_AWS-Database-Migration-Service_16.png) AWS Database Migration Service (DMS)

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

- Characteristics: Managed migration service
- Capabilities: Full load + CDC; continuous replication
- Pricing Model: Per-hour for replication instance
- Security/IAM: IAM; KMS; network isolation

### 6. Confusable

- AWS Schema Conversion Tool (SCT): Both handle database migrations, but SCT converts schemas while DMS migrates live data.
- AWS DataSync: Both move data, but DataSync handles files and objects while DMS handles relational/noSQL database migration.
- Amazon Aurora Global Database: Both replicate data, but Aurora Global Database is for cross-region HA/DR, not heterogeneous database migration.

### 7. Exam Notes

- “Minimal downtime,” “CDC,” “replication instance” → DMS

## 🟪 AWS Schema Conversion Tool (SCT)

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

- Characteristics: Schema transformer
- Capabilities: Schema/object conversion; assessment reports
- Pricing Model: Free
- Security/IAM: Local tool + IAM for cloud access

### 6. Confusable

- AWS DMS: Both are used for database migrations, but SCT converts schemas while DMS migrates the actual data.
- AWS Glue: Both transform data, but Glue is ETL for analytics while SCT is schema conversion for migrations.
- Amazon Athena: Both work with SQL structures, but Athena is a query engine while SCT is a schema transformation tool.

### 7. Exam Notes

- “Heterogeneous migrations,” “schema conversion” → SCT

## ![icon](icons/service/Arch_Migration-Modernization/16/Arch_AWS-Migration-Evaluator_16.png) Migration Evaluator

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

- Characteristics: Migration cost assessment
- Capabilities: TCO modeling; usage analytics
- Pricing Model: Free
- Security/IAM: IAM

### 6. Confusable

- AWS Migration Hub: Both assist migration planning, but Migration Evaluator estimates cost models while Migration Hub tracks the migration process.
- AWS Pricing Calculator: Both estimate costs, but Migration Evaluator analyzes existing workloads while Calculator models hypothetical ones.
- AWS Application Discovery Service: Both collect data for planning, but Migration Evaluator focuses on cost estimation rather than environment inventory.

### 7. Exam Notes

- “TCO report,” “migration business case” → Migration Evaluator

---

# ![icon](icons/service/Arch_General-Icons/16/Arch_AWS-Marketplace_Light_16.png) Marketplace and Partners

Marketplace and Partners **extend AWS with third‑party software and expert services**.
They let organizations add capabilities instantly instead of building them from scratch.
Their core intent is to accelerate adoption and reduce time‑to‑value through external solutions.

## ![icon](icons/service/Arch_General-Icons/16/Arch_AWS-Marketplace_Light_16.png) AWS Marketplace

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

- Characteristics: Third‑party software catalog
- Capabilities: AMI/SaaS delivery; private marketplace; procurement workflows
- Pricing Model: Pay‑as‑you‑go or subscription; billed via AWS
- Security/IAM: IAM permissions; license governance

### 6. Confusable

- AWS Service Catalog: Both help manage third-party or curated solutions, but Marketplace is a purchasing platform while Service Catalog is an internal provisioning system.
- AWS Partner Network (APN): Both involve third-party solutions, but APN manages partnerships and competencies while Marketplace is the storefront.
- AWS CloudFormation: Many Marketplace products deploy via CloudFormation, causing confusion, but Marketplace is procurement while CloudFormation is infrastructure-as-code.

### 7. Exam Notes

- “Third‑party software acquisition,” “private offers,” “AWS‑billed SaaS” → Marketplace

## ⬛ AWS Partner Network (APN)

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

- Characteristics: Partner ecosystem
- Capabilities: Consulting, technology integrations, funding programs
- Pricing Model: No customer cost; partner fees vary internally
- Security/IAM: Partners access via IAM/StS when needed

### 6. Confusable

- AWS Marketplace: Both involve external vendors, but APN is about partner competencies and programs while Marketplace is the purchasing catalog.
- AWS Service Catalog: Both manage solutions, but Service Catalog is internal governance while APN is partner enablement.
- AWS Support Plans: Both involve enterprise enablement, but APN enables partners while Support Plans enable customers.

### 7. Exam Notes

- “AWS partner ecosystem,” “competencies,” “consulting partners” → APN

# ✅ Summary

All services.

## ![icon](icons/category/Arch-Category_16/Arch-Category_Compute_16.png) Compute

- ![icon](icons/service/Arch_Compute/16/Arch_Amazon-EC2_16.png) **Amazon EC2** — Flexible virtual servers you size, tune, and script to run almost any workload.
- ![icon](icons/service/Arch_Compute/16/Arch_Amazon-EC2-Auto-Scaling_16.png) **Amazon EC2 Auto Scaling** — Automatically adjusts EC2 capacity to maintain steady performance at the lowest cost.
- ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_Elastic-Load-Balancing_16.png) **Elastic Load Balancing (ELB)** — Distributes incoming traffic across instances or containers to keep apps reliable.
- ![icon](icons/service/Arch_Compute/16/Arch_AWS-Lambda_16.png) **AWS Lambda** — Runs your code on demand with zero servers to manage.
- ![icon](icons/service/Arch_Containers/16/Arch_AWS-Fargate_16.png) **AWS Fargate** — Serverless compute for containers so you focus only on tasks, not infrastructure.
- ![icon](icons/service/Arch_Containers/16/Arch_Amazon-Elastic-Container-Service_16.png) **Amazon ECS** — AWS-native container orchestration for running and scaling Docker workloads.
- ![icon](icons/service/Arch_Containers/16/Arch_Amazon-Elastic-Kubernetes-Service_16.png) **Amazon EKS** — Fully managed Kubernetes control plane for large-scale container workloads.
- ![icon](icons/service/Arch_Containers/16/Arch_Amazon-Elastic-Container-Registry_16.png) **Amazon ECR** — Secure, private Docker image registry integrated with IAM and CI/CD.
- ![icon](icons/service/Arch_Compute/16/Arch_AWS-Batch_16.png) **AWS Batch** — Runs batch computing jobs efficiently using dynamically provisioned compute.
- ![icon](icons/service/Arch_Compute/16/Arch_AWS-Elastic-Beanstalk_16.png) **Elastic Beanstalk** — Quickly deploy applications with automatic provisioning, scaling, and monitoring.
- ![icon](icons/service/Arch_Compute/16/Arch_Amazon-Lightsail_16.png) **Amazon Lightsail** — Simplified VPS hosting for small applications with predictable pricing.
- ![icon](icons/service/Arch_Compute/16/Arch_AWS-Outposts-family_16.png) **AWS Outposts** — Extends AWS hardware and services directly into your datacenter.
- ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_Amazon-API-Gateway_16.png) **Amazon API Gateway** — Manages, secures, and scales APIs for serverless and backend services.

## ![icon](icons/category/Arch-Category_16/Arch-Category_Networking-Content-Delivery_16.png) Networking and Content Delivery

- ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_Amazon-Virtual-Private-Cloud_16.png) **Amazon VPC** — Build your own isolated AWS network with full control over routing and security layers.
- 🟪 **Network topics** — Core VPC concepts that define how cloud networks segment, isolate, and route traffic.
- 🟪 **Internet Gateway** — The VPC’s path to the public internet for outbound and inbound connections.
- 🟪 **Virtual Private Gateway** — VPN termination point enabling secure inbound tunnels from on‑premises.
- 🟪 **NAT Gateway** — Lets private subnets reach the internet while keeping them unreachable from outside.
- ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_AWS-Client-VPN_16.png) **AWS Client VPN** — Fully managed VPN for users to securely access AWS and on‑prem resources.
- ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_AWS-Site-to-Site-VPN_16.png) **AWS Site-to-Site VPN** — Encrypted IPSec tunnels linking datacenters directly to AWS VPCs.
- ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_AWS-Direct-Connect_16.png) **AWS Direct Connect** — Low-latency private circuits that bypass the public internet for cloud traffic.
- ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_AWS-PrivateLink_16.png) **AWS PrivateLink** — Private, secure access to AWS and SaaS services without crossing the public internet.
- ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_AWS-Transit-Gateway_16.png) **AWS Transit Gateway** — Central hub simplifying large-scale VPC and on‑prem network connectivity.
- 🟪 **VPC Endpoints (Gateway & Interface)** — Connect privately to AWS services from within your VPC.
- ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_Amazon-Route-53_16.png) **Amazon Route 53** — Highly available DNS and traffic steering for global applications.
- ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_Amazon-CloudFront_16.png) **Amazon CloudFront** — Edge-based CDN delivering content faster to users worldwide.
- ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_AWS-Global-Accelerator_16.png) **AWS Global Accelerator** — Routes user traffic over AWS’s global backbone for consistent low latency.

## ![icon](icons/category/Arch-Category_16/Arch-Category_Storage_16.png) Storage

- ![icon](icons/service/Arch_Storage/16/Arch_Amazon-Simple-Storage-Service_16.png) **Amazon S3** — Durable, scalable object storage for any data at any scale.
- ![icon](icons/service/Arch_Storage/16/Arch_Amazon-Elastic-Block-Store_16.png) **Amazon EBS** — High-performance block storage volumes for EC2 instances.
- ![icon](icons/service/Arch_Storage/16/Arch_Amazon-EFS_16.png) **Amazon EFS** — Fully managed shared file system that grows and shrinks automatically.
- ![icon](icons/service/Arch_Storage/16/Arch_Amazon-FSx_16.png) **Amazon FSx (Windows & Lustre)** — High-performance file systems for Windows apps and HPC workloads.
- ![icon](icons/service/Arch_Storage/16/Arch_AWS-Storage-Gateway_16.png) **AWS Storage Gateway** — Hybrid storage bridge integrating on-prem systems with cloud storage.
- ![icon](icons/service/Arch_Storage/16/Arch_AWS-Backup_16.png) **AWS Backup** — Centralized, automated backup service for AWS and on-prem workloads.
- ![icon](icons/service/Arch_Migration-Modernization/16/Arch_AWS-DataSync_16.png) **AWS DataSync** — Accelerates data transfer between on-prem storage and AWS.
- ![icon](icons/service/Arch_Migration-Modernization/16/Arch_AWS-Transfer-Family_16.png) **AWS Transfer Family** — Managed SFTP, FTPS, and FTP endpoints backed by S3 storage.
- ![icon](icons/service/Arch_Storage/16/Arch_AWS-Elastic-Disaster-Recovery_16.png) **AWS Elastic Disaster Recovery** — Rapidly recovers servers to AWS after unexpected outages.
- ![icon](icons/service/Arch_Storage/16/Arch_AWS-Snowball_16.png) **AWS Snow Family** — Rugged edge and data transfer devices for offline migrations and remote computing.

## ![icon](icons/category/Arch-Category_16/Arch-Category_Database_16.png) Databases

- ![icon](icons/service/Arch_Database/16/Arch_Amazon-RDS_16.png) **Amazon RDS** — Managed relational databases with automated backups, patching, and scaling.
- ![icon](icons/service/Arch_Database/16/Arch_Amazon-Aurora_16.png) **Amazon Aurora** — High-performance cloud-native relational database compatible with MySQL and PostgreSQL.
- ![icon](icons/service/Arch_Database/16/Arch_Amazon-DynamoDB_16.png) **Amazon DynamoDB** — Fully managed NoSQL key–value database delivering single-digit millisecond performance.
- ![icon](icons/service/Arch_Database/16/Arch_Amazon-DynamoDB_16.png) **Amazon DynamoDB Accelerator (DAX)** — In-memory caching that boosts DynamoDB reads from milliseconds to microseconds.
- ![icon](icons/service/Arch_Database/16/Arch_Amazon-ElastiCache_16.png) **Amazon ElastiCache** — Managed Redis and Memcached for ultra-fast in-memory caching layers.
- ![icon](icons/service/Arch_Database/16/Arch_Amazon-DocumentDB_16.png) **Amazon DocumentDB** — Scale-out document database compatible with MongoDB workloads.
- ![icon](icons/service/Arch_Database/16/Arch_Amazon-Neptune_16.png) **Amazon Neptune** — Purpose-built graph database optimized for connected-data queries.
- ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-Redshift_16.png) **Amazon Redshift** — Fully managed petabyte-scale data warehouse for fast analytical queries.

## ![icon](icons/category/Arch-Category_16/Arch-Category_Artificial-Intelligence_16.png) AI and Machine Learning

- ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Comprehend_16.png) **Amazon Comprehend** — NLP service that extracts insights and meaning from unstructured text.
- ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Polly_16.png) **Amazon Polly** — Converts text into lifelike speech in dozens of voices and languages.
- ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Transcribe_16.png) **Amazon Transcribe** — Automatically transforms speech into accurate text transcripts.
- ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Translate_16.png) **Amazon Translate** — Neural machine translation for fast, natural multilingual text conversion.
- ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Lex_16.png) **Amazon Lex** — Build conversational chatbots using ASR and NLU technology from Alexa.
- ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Rekognition_16.png) **Amazon Rekognition** — Image and video analysis to detect objects, faces, text, and scenes.
- ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Textract_16.png) **Amazon Textract** — Uses ML to extract text, forms, and tables from scanned documents.
- ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Forecast_16.png) **Amazon Forecast** — ML-powered time-series forecasting for demand and capacity planning.
- ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Personalize_16.png) **Amazon Personalize** — Real-time personalization and recommendation engine based on your data.
- ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Kendra_16.png) **Amazon Kendra** — Intelligent enterprise search powered by machine learning.
- ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-SageMaker_16.png) **Amazon SageMaker** — End-to-end platform for building, training, and deploying ML models at scale.
- ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-SageMaker_16.png) **SageMaker JumpStart** — Prebuilt models and solutions that accelerate ML experimentation.
- ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Bedrock_16.png) **Amazon Bedrock** — Foundation model platform providing secure access to top-tier generative AI models.
- ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Q_16.png) **Amazon Q Business** — Enterprise AI assistant tailored for organizational data and workflows.
- ![icon](icons/service/Arch_Artificial-Intelligence/16/Arch_Amazon-Q_16.png) **Amazon Q Developer** — AI coding assistant that accelerates software development and automation tasks.

## ![icon](icons/category/Arch-Category_16/Arch-Category_Analytics_16.png) Analytics

- ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-Athena_16.png) **Amazon Athena** — Serverless SQL queries directly against data in S3 using standard SQL.
- ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-Kinesis-Data-Streams_16.png) **Amazon Kinesis Data Streams** — Real-time data ingestion pipeline for high-throughput event streams.
- ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-Data-Firehose_16.png) **Amazon Kinesis Data Firehose** — Fully managed streaming delivery to S3, Redshift, OpenSearch, and third-party tools.
- ![icon](icons/service/Arch_Analytics/16/Arch_AWS-Glue_16.png) **AWS Glue** — Serverless ETL service that automates data discovery, transformation, and loading.
- ![icon](icons/service/Arch_Analytics/16/Arch_AWS-Glue_16.png) **AWS Glue Data Catalog** — Centralized metadata store indexing datasets for analytics and ETL jobs.
- ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-EMR_16.png) **Amazon EMR** — Managed big data clusters running Hadoop, Spark, Hive, and Presto at scale.
- ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-QuickSight_16.png) **Amazon QuickSight** — Cloud-native BI dashboards with fast, in-memory SPICE queries.
- ![icon](icons/service/Arch_Analytics/16/Arch_Amazon-OpenSearch-Service_16.png) **Amazon OpenSearch Service** — Managed search and analytics engine for real-time log and data exploration.

## ![icon](icons/category/Arch-Category_16/Arch-Category_Security-Identity-Compliance_16.png) Security, Identity, and Compliance

- ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Identity-and-Access-Management_16.png) **AWS Identity and Access Management (IAM)** — Controls who can access what in your AWS environment.
- 🟥 **IAM Policy Simulator** — Test and validate IAM policies to ensure permissions behave as intended.
- ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-IAM-Identity-Center_16.png) **IAM Identity Center** — Centralized workforce identity and SSO for AWS accounts and applications.
- ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Key-Management-Service_16.png) **AWS Key Management Service (KMS)** — Securely create and manage encryption keys for your applications.
- ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Secrets-Manager_16.png) **AWS Secrets Manager** — Stores and rotates sensitive credentials automatically and securely.
- ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Shield_16.png) **AWS Shield** — Always-on DDoS protection for AWS applications.
- ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Shield_16.png) **AWS Shield Advanced** — Enhanced DDoS protection with real-time engagement and cost safeguards.
- ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-WAF_16.png) **AWS WAF** — Web application firewall blocking malicious bots, exploits, and attacks.
- ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_Amazon-Inspector_16.png) **Amazon Inspector** — Automated vulnerability scanning for EC2 and container workloads.
- ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_Amazon-GuardDuty_16.png) **Amazon GuardDuty** — Intelligent threat detection and continuous security monitoring.
- ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_Amazon-Macie_16.png) **Amazon Macie** — ML-powered discovery of sensitive data and anomalies in S3.
- ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Security-Hub_16.png) **AWS Security Hub** — Unified dashboard to monitor and score your overall AWS security posture.
- ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_Amazon-Cognito_16.png) **Amazon Cognito** — Managed user authentication with hosted sign-in and MFA.
- ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Certificate-Manager_16.png) **AWS Certificate Manager (ACM)** — Automated provisioning and renewal of TLS certificates.
- ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Artifact_16.png) **AWS Artifact** — On-demand access to compliance reports and security documentation.
- ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Config_16.png) **AWS Config** — Tracks configuration changes and checks resource compliance over time.
- ![icon](icons/service/Arch_Security-Identity-Compliance/16/Arch_AWS-Audit-Manager_16.png) **AWS Audit Manager** — Simplifies audits by mapping evidence to compliance frameworks automatically.
- 🟥 **IAM Access Analyzer** — Detects unintended external access to IAM roles, S3 buckets, and more.

## ![icon](icons/category/Arch-Category_16/Arch-Category_Management-Governance_16.png) Management and Governance

- ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-CloudFormation_16.png) **AWS CloudFormation** — Automates infrastructure deployment using templates for repeatable, versioned environments.
- ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Systems-Manager_16.png) **AWS Systems Manager** — Unified operational console for patching, automation, fleet management, and configuration.
- ![icon](icons/service/Arch_Management-Governance/16/Arch_Amazon-CloudWatch_16.png) **Amazon CloudWatch** — Observability platform for metrics, logs, and alarms across AWS resources.
- ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-CloudTrail_16.png) **AWS CloudTrail** — Governance and auditing for all API activity across AWS accounts.
- ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Organizations_16.png) **AWS Organizations** — Centralized multi-account management with SCPs, billing consolidation, and governance.
- ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Control-Tower_16.png) **AWS Control Tower** — Blueprinted landing zone setup with automated guardrails and best practices.
- ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Service-Catalog_16.png) **AWS Service Catalog** — Curate approved application portfolios with governed self-service deployment.
- ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-License-Manager_16.png) **AWS License Manager** — Track, control, and enforce software license usage across AWS and on‑prem.
- ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Health-Dashboard_16.png) **AWS Health Dashboard** — Personalized view of AWS service health events affecting your resources.
- ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Trusted-Advisor_16.png) **AWS Trusted Advisor** — Recommendations to improve cost efficiency, performance, security, and resilience.
- ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-Compute-Optimizer_16.png) **AWS Compute Optimizer** — ML-powered right-sizing recommendations for EC2, Lambda, and containers.
- 🟩 **AWS Pricing Calculator** — Estimate and compare AWS service costs before deploying workloads.
- 🟩 **AWS Data Lifecycle Manager** — Automates EBS and EC2 snapshot retention and lifecycle policies.
- 🟩 **AWS Billing and Cost Management** — Central billing console for budgets, payments, and account charges.
- ![icon](icons/service/Arch_Cloud-Financial-Management/16/Arch_AWS-Budgets_16.png) **AWS Budgets** — Set cost and usage thresholds with alerts when you exceed or forecast to exceed them.
- ![icon](icons/service/Arch_Cloud-Financial-Management/16/Arch_AWS-Cost-Explorer_16.png) **AWS Cost Explorer** — Visualize and analyze AWS spending trends over time.
- ![icon](icons/service/Arch_Cloud-Financial-Management/16/Arch_AWS-Cost-and-Usage-Report_16.png) **AWS Cost and Usage Reports (CUR)** — Detailed, hourly-level AWS cost and usage datasets for analysis.
- ![icon](icons/service/Arch_Cloud-Financial-Management/16/Arch_AWS-Billing-Conductor_16.png) **AWS Billing Conductor** — Customizable cost allocation tooling for complex billing arrangements.

## ![icon](icons/category/Arch-Category_16/Arch-Category_Application-Integration_16.png) Application Integration

- ![icon](icons/service/Arch_App-Integration/16/Arch_Amazon-EventBridge_16.png) **Amazon EventBridge** — Event bus for routing application events between AWS services and SaaS apps.
- ![icon](icons/service/Arch_App-Integration/16/Arch_Amazon-Simple-Queue-Service_16.png) **Amazon SQS** — Fully managed message queues decoupling producers from consumers at any scale.
- ![icon](icons/service/Arch_App-Integration/16/Arch_Amazon-Simple-Notification-Service_16.png) **Amazon SNS** — Pub/sub messaging for fan-out notifications and event-driven systems.
- ![icon](icons/service/Arch_Networking-Content-Delivery/16/Arch_Elastic-Load-Balancing_16.png) **Application Load Balancer (ALB)** — Layer 7 load balancer for HTTP/S traffic with routing, auth, and advanced rules.

## ![icon](icons/category/Arch-Category_16/Arch-Category_Developer-Tools_16.png) Developer Tools

- ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-Cloud9_16.png) **AWS Cloud9** — Cloud-based IDE for writing, debugging, and collaborating on code from anywhere.
- ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-CloudShell_16.png) **AWS CloudShell** — Browser-based shell with AWS CLI preconfigured for quick command execution.
- ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-CodeCommit_16.png) **AWS CodeCommit** — Managed Git repositories with high availability and security.
- ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-CodeBuild_16.png) **AWS CodeBuild** — Fully managed build service that compiles code, runs tests, and produces artifacts.
- ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-CodePipeline_16.png) **AWS CodePipeline** — Continuous delivery pipelines automating build, test, and deploy workflows.
- ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-CodeDeploy_16.png) **AWS CodeDeploy** — Automated deployment engine for EC2, Lambda, and on-prem servers.
- ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-CodeArtifact_16.png) **AWS CodeArtifact** — Secure artifact and dependency repository for build systems and package managers.
- ![icon](icons/service/Arch_Developer-Tools/16/Arch_AWS-X-Ray_16.png) **AWS X-Ray** — Distributed tracing that reveals bottlenecks and dependencies in your applications.
- ![icon](icons/service/Arch_Management-Governance/16/Arch_AWS-AppConfig_16.png) **AWS AppConfig** — Feature flag and configuration rollout service for safe, gradual application changes.

## ![icon](icons/category/Arch-Category_16/Arch-Category_Front-End-Web-Mobile_16.png) Frontend and Mobile

- ![icon](icons/service/Arch_Front-End-Web-Mobile/16/Arch_AWS-Amplify_16.png) **AWS Amplify** — Streamlines building, hosting, and scaling full-stack web and mobile applications.
- ![icon](icons/service/Arch_App-Integration/16/Arch_AWS-AppSync_16.png) **AWS AppSync** — Managed GraphQL service for real-time data sync across apps and devices.

## ![icon](icons/category/Arch-Category_16/Arch-Category_Business-Applications_16.png) Business Applications

- ![icon](icons/service/Arch_Business-Applications/16/Arch_Amazon-Connect_16.png) **Amazon Connect** — Cloud contact center enabling scalable, personalized customer interactions.
- ![icon](icons/service/Arch_Business-Applications/16/Arch_Amazon-Simple-Email-Service_16.png) **Amazon Simple Email Service (SES)** — Reliable, scalable email sending for applications and marketing.

## ![icon](icons/category/Arch-Category_16/Arch-Category_End-User-Computing_16.png) End-User Computing

- ![icon](icons/service/Arch_End-User-Computing/16/Arch_Amazon-AppStream-2_16.png) **Amazon AppStream 2.0** — Streams desktop applications securely to any device.
- ![icon](icons/service/Arch_End-User-Computing/16/Arch_Amazon-WorkSpaces-Family_16.png) **Amazon WorkSpaces** — Managed virtual desktops for secure remote work.
- ![icon](icons/service/Arch_End-User-Computing/16/Arch_Amazon-WorkSpaces-Family_16.png) **WorkSpaces Secure Browser** — Isolated browser environment protecting users from web-based threats.

### ![icon](icons/category/Arch-Category_16/Arch-Category_Internet-of-Things_16.png) IoT

- ![icon](icons/service/Arch_Internet-of-Things/16/Arch_AWS-IoT-Core_16.png) **AWS IoT Core** — Securely connects IoT devices to the cloud and routes their data to AWS services.
- ![icon](icons/service/Arch_Internet-of-Things/16/Arch_AWS-IoT-Greengrass_16.png) **AWS IoT Greengrass** — Brings cloud capabilities like ML inference and messaging to edge devices.

## ![icon](icons/category/Arch-Category_16/Arch-Category_Migration-Modernization_16.png) Migration and Transfer

- ![icon](icons/service/Arch_Migration-Modernization/16/Arch_AWS-Migration-Hub_16.png) **AWS Migration Hub** — Centralizes tracking and visibility for application migration projects.
- ![icon](icons/service/Arch_Migration-Modernization/16/Arch_AWS-Application-Discovery-Service_16.png) **AWS Application Discovery Service** — Identifies on-prem servers and dependencies to plan migrations.
- ![icon](icons/service/Arch_Database/16/Arch_AWS-Database-Migration-Service_16.png) **AWS Database Migration Service (DMS)** — Migrates databases to AWS with minimal downtime.
- 🟪 **AWS Schema Conversion Tool (SCT)** — Converts database schemas to match target engines such as Aurora or PostgreSQL.
- ![icon](icons/service/Arch_Migration-Modernization/16/Arch_AWS-Migration-Evaluator_16.png) **Migration Evaluator** — Provides right-sizing and cost projections for migrating workloads to AWS.

## ![icon](icons/service/Arch_General-Icons/16/Arch_AWS-Marketplace_Light_16.png) Marketplace and Partners

- ![icon](icons/service/Arch_General-Icons/16/Arch_AWS-Marketplace_Light_16.png) **AWS Marketplace** — Curated digital catalog of third-party software you can deploy directly into AWS.
- ⬛ **AWS Partner Network (APN)** — Global community of partners offering solutions, integrations, and services on AWS.
