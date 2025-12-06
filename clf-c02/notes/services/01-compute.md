
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
