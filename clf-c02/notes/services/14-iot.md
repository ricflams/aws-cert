
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
