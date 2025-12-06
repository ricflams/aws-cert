
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
