
# Machine Learning & AI

## Amazon Comprehend
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
- **Characteristics:** Fully managed NLP; regional  
- **Capabilities:** Entity detection; sentiment; custom models  
- **Pricing Model:** Per-unit text processed  
- **Security/IAM:** KMS; IAM; VPC endpoints  

### 6. Confusable Services
- Textract (OCR), Kendra (search), Translate (translation)  

### 7. Exam Notes
- “Sentiment,” “entities,” “text analysis” → Comprehend  


## Amazon Polly
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
- **Characteristics:** Managed TTS; multilingual  
- **Capabilities:** Speech synthesis; SSML support  
- **Pricing Model:** Per-character  
- **Security/IAM:** IAM; KMS for logs  

### 6. Confusable Services
- Transcribe (speech-to-text), Lex (chatbots)  

### 7. Exam Notes
- “Text to speech,” “voice output” → Polly  


## Amazon Transcribe
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
- **Characteristics:** Speech-to-text; regional  
- **Capabilities:** Timestamps; speaker diarization  
- **Pricing Model:** Per-second audio processed  
- **Security/IAM:** IAM; encryption  

### 6. Confusable Services
- Polly, Comprehend (downstream analysis)  

### 7. Exam Notes
- “Convert speech to text,” “ASR” → Transcribe  


## Amazon Translate
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
- **Characteristics:** Neural translation; global language support  
- **Capabilities:** Text translation; batch jobs  
- **Pricing Model:** Per-character  
- **Security/IAM:** IAM; encryption  

### 6. Confusable Services
- Comprehend; Transcribe; Polly  

### 7. Exam Notes
- “Translate text between languages” → Translate  


## Amazon Lex
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
- **Characteristics:** Conversational AI; ASR + NLU  
- **Capabilities:** Intents; slots; multi-turn dialogues  
- **Pricing Model:** Per speech/text request  
- **Security/IAM:** IAM; KMS  

### 6. Confusable Services
- Polly (speech output), Transcribe (speech input), Q Business  

### 7. Exam Notes
- “Build chatbots,” “conversational interface” → Lex  

## Amazon Rekognition
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
- **Characteristics:** Managed CV; deep learning models  
- **Capabilities:** Labels; faces; celebrity ID; moderation; text detection  
- **Pricing Model:** Per-image or per-minute video analysis  
- **Security/IAM:** IAM; KMS; data privacy controls  

### 6. Confusable Services
- Textract (OCR), Kinesis Video Streams (ingestion), SageMaker CV models  

### 7. Exam Notes
- “Object detection,” “content moderation,” “face recognition” → Rekognition  


## Amazon Textract
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
- **Characteristics:** OCR + document intelligence  
- **Capabilities:** Form extraction; table extraction; handwriting support  
- **Pricing Model:** Per-page  
- **Security/IAM:** KMS; IAM  

### 6. Confusable Services
- Rekognition (images), Comprehend (text insights)  

### 7. Exam Notes
- “Forms,” “tables,” “OCR with key-value pairs” → Textract  


## Amazon Forecast
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
- **Characteristics:** ML-based forecasting; serverless  
- **Capabilities:** Predictive models; AutoML; quantile forecasts  
- **Pricing Model:** Training-hour + inference usage  
- **Security/IAM:** IAM; KMS  

### 6. Confusable Services
- Personalize (recommendations), QuickSight ML insights  

### 7. Exam Notes
- “Demand planning,” “time-series” → Forecast  


## Amazon Personalize
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
- **Characteristics:** Real-time personalization; ML-based  
- **Capabilities:** Recommendations; reranking; user segmentation  
- **Pricing Model:** Training-hour + inference  
- **Security/IAM:** IAM; KMS  

### 6. Confusable Services
- Forecast (time-series), Neptune (graph relations), SageMaker recommender models  

### 7. Exam Notes
- “Personalized recommendations,” “user-item interactions” → Personalize  


## Amazon Kendra
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
- **Characteristics:** Intelligent search; ML ranking  
- **Capabilities:** Semantic search; FAQs; document connectors  
- **Pricing Model:** Index capacity + query usage  
- **Security/IAM:** IAM; KMS; document-level access control  

### 6. Confusable Services
- OpenSearch (keyword search), Comprehend (text analysis)  

### 7. Exam Notes
- “Natural language enterprise search,” “FAQ matching” → Kendra  

## Amazon SageMaker
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
- **Characteristics:** Full ML platform; regional; highly modular  
- **Capabilities:** Autopilot (AutoML), Pipelines, MLOps, hyperparameter tuning  
- **Pricing Model:** Separate pricing for compute, storage, training, endpoints  
- **Security/IAM:** IAM; KMS; VPC integration; encryption  

### 6. Confusable Services
- Bedrock (foundation models, not training from scratch)  
- Personalize/Forecast (domain-specific ML services)  

### 7. Exam Notes
- “End-to-end ML,” “training + deployment,” “MLOps” → SageMaker  


## SageMaker JumpStart
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
- **Characteristics:** Prebuilt ML assets; easy onboarding  
- **Capabilities:** One-click deployments; example notebooks  
- **Pricing Model:** Based on underlying SageMaker resources used  
- **Security/IAM:** IAM; KMS  

### 6. Confusable Services
- Bedrock (foundation models), Autopilot  

### 7. Exam Notes
- “Prebuilt templates,” “get started fast in SageMaker” → JumpStart  


## Amazon Bedrock
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
- **Characteristics:** GenAI API platform; multi-model  
- **Capabilities:** Fine-tuning; embeddings; RAG; guardrails  
- **Pricing Model:** Per-token or per-inference usage  
- **Security/IAM:** IAM; KMS; VPC; Guardrails  

### 6. Confusable Services
- SageMaker (custom ML training), Q Business (enterprise assistant)  

### 7. Exam Notes
- “Foundation models,” “RAG,” “Agents,” “Guardrails” → Bedrock  


## Amazon Q Business
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
- **Characteristics:** Enterprise AI assistant; knowledge-integrated  
- **Capabilities:** Q&A; RAG; workflow automation  
- **Pricing Model:** Per-user monthly + usage  
- **Security/IAM:** IAM Identity Center; document-level access control  

### 6. Confusable Services
- Kendra (search only), Bedrock (model platform), Q Developer  

### 7. Exam Notes
- “Enterprise assistant,” “secure knowledge retrieval” → Q Business  


## Amazon Q Developer
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
- **Characteristics:** Developer AI assistant; integration-focused  
- **Capabilities:** Code-gen; refactoring; troubleshooting; infra suggestions  
- **Pricing Model:** Per-user monthly  
- **Security/IAM:** IAM code permissions; enterprise governance  

### 6. Confusable Services
- GitHub Copilot (general coding), Bedrock models (raw inference)  

### 7. Exam Notes
- “AI coding assistant,” “generating AWS code,” “IDE integration” → Q Developer  
