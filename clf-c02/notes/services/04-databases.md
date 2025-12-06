
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
