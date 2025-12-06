
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
