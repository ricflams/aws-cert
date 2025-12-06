
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
