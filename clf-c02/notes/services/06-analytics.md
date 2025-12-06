
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
