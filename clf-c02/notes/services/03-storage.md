
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
