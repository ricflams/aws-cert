
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
