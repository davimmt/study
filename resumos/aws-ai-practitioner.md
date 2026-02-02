# [AWS AI Practitioner Certification](https://aws.amazon.com/certification/certified-ai-practitioner/)

# Table of Contents

1. [Core AI/ML Concepts](#1-core-aiml-concepts)
2. [Data Fundamentals](#2-data-fundamentals)
3. [Machine Learning Fundamentals](#3-machine-learning-fundamentals)
4. [Generative AI Fundamentals](#4-generative-ai-fundamentals)
5. [Feature Engineering & Data Preparation](#5-feature-engineering--data-preparation)
6. [Model Training & Optimization](#6-model-training--optimization)
7. [Model Deployment & MLOps](#7-model-deployment--mlops)
8. [Model Evaluation Metrics](#8-model-evaluation-metrics)
9. [Model Fit Patterns](#9-model-fit-patterns)
10. [Responsible AI & Fairness](#10-responsible-ai--fairness)
11. [AWS AI/ML & GenAI Services](#11-aws-aiml--genai-services)
12. [Amazon SageMaker Deep Dive](#12-amazon-sagemaker-deep-dive)
13. [Amazon Bedrock Deep Dive](#13-amazon-bedrock-deep-dive)
14. [Key Algorithms & Techniques](#14-key-algorithms--techniques)
15. [Applications of Foundation Models](#15-applications-of-foundation-models)
16. [Prompt Engineering](#16-prompt-engineering)
17. [Training & Fine-tuning Foundation Models](#17-training--fine-tuning-foundation-models)
18. [Evaluating Foundation Model Performance](#18-evaluating-foundation-model-performance)
19. [Cost Optimization & Pricing](#19-cost-optimization--pricing)
20. [Security, Compliance & Governance for AI Systems](#20-security-compliance--governance-for-ai-systems)

Appendix A: [Summary & Key Takeaways](#a-summary--key-takeaways)<br>
Appendix B: [Keywords & Quick Reference](#b-keywords--quick-reference)<br>

# 1. Core AI/ML Concepts

## Fundamental Definitions
- **Artificial Intelligence (AI)**: Technology enabling computers to mimic human intelligence
- **Machine Learning (ML)**: Systems that learn from data without explicit programming
- **Deep Learning (DL)**: ML subset using neural networks for complex pattern recognition
- **Natural Language Processing (NLP)**: AI field focused on human-computer language interaction
- **Generative AI (GenAI)**: Systems that create new content based on training data
- **Foundation Models (FM)**: Large-scale, general-purpose pre-trained models serving as blueprints
- **Large Language Models (LLM)**: Deep learning models specialized in understanding and generating human language
  - Subset of both NLP and Foundation Models
  - Uses transformers and massive datasets
  - Analyzes and predicts word sequences with high versatility

---

# 2. Data Fundamentals

## Data Types

**Structured Data:**
- **Tabular**: Organized in rows and columns (databases, spreadsheets)
- **Time Series**: Data points indexed by time (graphs N/t)

**Unstructured Data:**
- Text documents
- Images and videos
- Audio files

---

# 3. Machine Learning Fundamentals

## ML Workflow
```
Data → ML Model → Output
         ↑
      Training
    (ML Algorithms)
```

## ML Types & Paradigms

**1. Supervised Learning** (Labeled Data)
- **Classification**: Categorizing into discrete classes
  - Binary classification (2 classes)
  - Multiclass classification (>2 classes)
- **Regression**: Predicting continuous numerical values

**2. Unsupervised Learning** (Unlabeled Data)
- **Clustering**: Grouping data by similar features
- **Anomaly Detection**: Identifying outliers and unusual patterns

**3. Semi-Supervised Learning**
- Combination of labeled and unlabeled data

**4. Self-Supervised Learning**
- Algorithm defines its own labels based on data insights

**5. Reinforcement Learning**
- Learning through trial-and-error with reward/penalty feedback

[Reference: AWS ML Comparison](https://aws.amazon.com/pt/compare/the-difference-between-machine-learning-supervised-and-unsupervised/)

---

# 4. Generative AI Fundamentals

## Core Concepts

**Tokens**
- Individual units of text (words, subwords, or characters) that LLMs process
- Text is broken down into tokens for model input

**Chunking**
- Breaks large datasets into smaller, manageable pieces
- Enables efficient processing of extensive information

**Context Windows**
- The maximum number of tokens an LLM can process at once
- Determines how much information the model can consider simultaneously

**Vectors**
- Numerical arrays in n-dimensional space
- Mathematical representation of data points

**Embeddings**
- Specially trained vectors that encode semantic meaning
- Capture relationships and context between words/concepts

## Transformer Architecture

**Transformer-based LLMs**
- Use neural networks to process input data
- Generate human-understandable output
- Enable attention mechanisms for context understanding
- Foundation of modern large language models

### Self-Attention Mechanism

**Self-Attention**
- Core mechanism allowing model to focus (token weight) on specific parts of input sequence
- Captures contextual relationships within sequence
- **Purpose**: Understand context and relationships within text
- Enables parallel processing (unlike sequential RNNs)

**Attention Weights**
- Computed for each token in relation to all other tokens
- Tell model how much "focus" or "attention" to give each token
- Enable dynamic prioritization of input parts
- Based on contextual relevance to current token being processed
- Core of self-attention mechanism
- **Quadratic complexity**: Pairwise calculations between all tokens (O(n²))

### Transformer Architectures

**Encoder-Decoder Architecture**
- Separate encoder (input processing) and decoder (output generation)
- **Excels at**: 
  - Text summarization
  - Machine translation
  - Sequence-to-sequence tasks
- Examples: T5, BART, original Transformer (Vaswani et al., 2017)

**Encoder-only Architecture**
- Only encoder component, no decoder
- Good for: Classification, sentiment analysis, named entity recognition
- Example: BERT

**Decoder-only Architecture**
- Only decoder component, no encoder
- Good for: Text generation, completion, creative writing
- Examples: GPT series, many modern LLMs

## Generative AI Model Types

**Foundation Models (FM)**
- Large-scale, general-purpose pre-trained models
- Serve as base for various downstream tasks
- Can be fine-tuned for specific applications

**Multi-modal Models**
- Extension of foundation models
- Handle and integrate multiple data types (text, images, audio, video)
- Enable cross-modal understanding and generation

**Multi-modal Embeddings**
- Power multi-modal search capabilities
- Enable recommendation systems
- Support personalization across different data types

**Diffusion Models**
- Primarily used for high-quality image generation
- Work through forward and reverse diffusion processes
- Transform noisy images into clear, detailed outputs

## Foundation Model Lifecycle

```
Data Selection → Model Selection → Pre-training → Fine-tuning → Evaluation → Deployment → Feedback
                                                                                          ↓
                                                                                    ← ← ← ←
```

**Stages:**
1. **Data Selection**: Curate and prepare training datasets
2. **Model Selection**: Choose appropriate architecture and size
3. **Pre-training**: Train on large-scale datasets
4. **Fine-tuning**: Adapt model to specific tasks or domains
5. **Evaluation**: Test performance and quality
6. **Deployment**: Release to production environment
7. **Feedback**: Collect usage data for continuous improvement

## Advantages of Generative AI

**Adaptability**
- Can be fine-tuned for various tasks and domains
- Flexible across different use cases

**Responsiveness**
- Generates contextually relevant outputs
- Adapts to user inputs dynamically

**Simplicity**
- Often requires minimal prompt engineering
- Accessible to non-technical users

## Challenges and Limitations

**Hallucinations**
- Models may generate plausible but incorrect information
- Require fact-checking and validation

**Lack of Interpretability**
- Difficult to understand decision-making process
- "Black box" nature of neural networks

**Nondeterminism**
- Same input may produce different outputs
- Can affect consistency and reliability

## Business Performance Metrics

**Efficiency**
- Related to resource utilization (compute, memory, time)
- Measures operational cost-effectiveness

**Accuracy**
- Percentage of correct predictions or outputs
- Quality of generated content

**Conversion Rate**
- Percentage of users taking desired actions
- Measures business impact of AI implementations

**Average Revenue per User (ARPU)**
- Financial metric tied to monetization
- Indicates revenue generation effectiveness

**Customer Lifetime Value (CLV)**
- Long-term value of AI impact on customer relationships
- Measures sustained business benefits

---

# 5. Feature Engineering & Data Preparation

## ML Model Development Lifecycle

### Complete Pipeline
```
Fetch → Clean → Prepare → Train/Tune → Evaluate → Deploy → Monitor
                                                              ↓
                                                         Feedback Loop
```

### Phase Descriptions

**Prepare (Feature Engineering)**
- Transform raw data into ML-friendly format
- Select and transform variables to enhance dataset quality

**Train/Tune**
- Apply algorithms to learn patterns
- Optimize parameters and hyperparameters

**Evaluate**
- Apply explainability techniques
- Measure prediction accuracy using metrics

**Monitor** (Post-Deployment)
- Identify data quality issues
- Detect feature drift, bias drift, and model drift

## Exploratory Data Analysis (EDA)
- **Purpose**: Identify patterns, correlations, and anomalies before training
- **Activities**: 
  - Formulate hypotheses
  - Create visual charts
  - Summarize features
- **Correlation Matrix**: Quantifies relationships between variables

## Feature Engineering

Feature engineering transforms raw data into ML-ready format by selecting and transforming variables to enhance dataset quality for training.

### Techniques

**Feature Selection**
- Filter relevant features from dataset

**Feature Extraction**
- Derive new features from existing variables

**Dimensionality Reduction**
- Simplify dataset by combining features
- Algorithm: Principal Component Analysis (PCA)

**Categorical Encoding**
- Convert categorical values to numerical format (ML models require numerical input)

**Handling Scale**
- **Normalization**: Rescale values to range [0, 1]
- **Standardization**: Transform data using mean and standard deviation

---

# 6. Model Training & Optimization

## Parameters
- **Definition**: Internal model values representing data relationships
- **Characteristics**:
  - Automatically learned during training
  - Model adjusts them to minimize error
  - Examples: Weights and biases in neural networks

## Hyperparameters
- **Definition**: Configuration settings specified before training
- **Characteristics**:
  - Manually set, fixed during training
  - Control learning algorithm behavior
  - Critical for model performance optimization

**Common Hyperparameters:**
- **Learning Rate**: Speed of weight/bias updates during training
- **Batch Size**: Number of examples processed before weight update
- **Number of Epochs**: Complete iterations through training data

**Hyperparameter Optimization Methods:**
- **Grid Search**: Tests all possible combinations (exhaustive but computationally expensive)
- **Random Search**: Randomly samples combinations (faster than grid search)
- **Bayesian Optimization**:
  - Advanced hyperparameter tuning method using probabilistic model
  - Learns from past evaluations to intelligently select next values to test
  - More efficient than Grid Search or Random Search
  - Iteratively assesses model performance at various points
  - Intelligently explores hyperparameter space
  - **Best for**: Complex models with numerous hyperparameters
  - Trade-off: More complex to implement, but much more efficient
- **AWS SageMaker Automatic Model Tuning (AMT)**: Automated optimization using Bayesian optimization

**Note**: Gradient Descent is used for training model parameters (weights/biases), NOT for tuning hyperparameters

---

# 7. Model Deployment & MLOps

## MLOps (Machine Learning Operations)

### Definition
Set of practices for managing the complete ML lifecycle

### Core Principles
- **Automation**: Streamline repetitive tasks
- **Consistency**: Standardized workflows
- **Reliability**: Robust production systems
- **Version Control**: Track models, data, and code
- **Continuous Deployment**: Automated model updates
- **Monitoring**: Track performance and detect drift

### Benefits
- Faster time-to-production
- Improved collaboration between teams
- Reduced operational risk
- Better model governance

---

# 8. Model Evaluation Metrics

**Note**: This section covers traditional ML metrics. For Foundation Model-specific evaluation metrics (ROUGE, BLEU, BERTScore), see [Section 18](#18-evaluating-foundation-model-performance).

## Classification Model Metrics

### Confusion Matrix Components

| Metric | Definition | Actual | Predicted |
|--------|-----------|--------|-----------|
| True Positive (TP) | Correctly identified positive | Positive | Positive |
| True Negative (TN) | Correctly identified negative | Negative | Negative |
| False Positive (FP) | Type I Error | Negative | Positive |
| False Negative (FN) | Type II Error | Positive | Negative |

### Key Performance Metrics

**Accuracy**
- Formula: `(TP + TN) / (TP + FP + FN + TN)`
- Percentage of correct predictions
- **Limitation**: Misleading for imbalanced datasets
- Rarely used in production
    ```
    Imbalanced Datasets:
    - One class significantly over-represented
    - Accuracy becomes unreliable metric

    When one class is much more common than others, accuracy can be misleading. A model that guesses only the majority class can achieve high accuracy but fail at detecting the minority class. Therefore, for imbalanced data, focus on Precision, Recall, or F1 Score for more meaningful evaluation.
    ```

**Precision**
- Formula: `TP / (TP + FP)`
- Proportion of correct positive predictions
- **Use Case**: Fraud detection (minimizing false alarms)

**Recall (Sensitivity)**
- Formula: `TP / (TP + FN)`
- Proportion of actual positives correctly identified
- **Use Case**: Medical diagnosis (minimizing missed cases)

**F1 Score**
- Formula: `(2 × Precision × Recall) / (Precision + Recall)`
- Harmonic mean balancing precision and recall

**AUC-ROC (Area Under the Curve - Receiver Operating Characteristic)**
- Graphical curve showing model's ability to distinguish between classes
- Plots True Positive Rate vs False Positive Rate
- Values closer to 1.0 indicate better performance

**AUC-PR (Area Under the Curve - Precision-Recall)**
- Plots Precision vs Recall across different thresholds
- More informative than AUC-ROC for imbalanced datasets
- Focuses on positive class performance
- Values closer to 1.0 indicate better performance

## Regression Model Metrics

**Mean Absolute Error (MAE)**
- Arithmetic mean of absolute differences: `|actual - predicted|`
- Same unit as target variable

**Mean Squared Error (MSE)**
- Arithmetic mean of squared differences: `(actual - predicted)²`
- Penalizes larger errors more heavily

**Root Mean Squared Error (RMSE)**
- Square root of MSE: `√MSE`
- Returns error to original scale
- More interpretable than MSE

**R² (R-Squared / Coefficient of Determination)**
- Measures how well model predictions fit actual data
- Range: [0, 1]
- Values close to 1 indicate strong predictive power
- Close to 0 means input variable provides little prediction value

## Training & Validation Metrics

**Training Loss**
- Error metric calculated on training data
- Model adjusts parameters to minimize this
- **Limitation**: Low training loss doesn't guarantee good generalization
- Can be misleading if model is overfitting
- Should be monitored alongside validation loss

**Validation Loss**
- Error metric calculated on unseen validation data
- **Key indicator** of model generalization ability
- Better predictor of real-world performance than training loss
- **Overfitting detection**: Training loss ↓ while validation loss ↑

**Validation Output Accuracy**
- Measures performance on unseen validation data
- **Key metric** for determining optimal number of epochs during fine-tuning
- Higher validation accuracy = better generalization
- Monitor to find peak performance point before overfitting
- More reliable than training accuracy for model selection

**Best Practice**: Always monitor validation loss/accuracy to stop training at optimal point and prevent overfitting

## Cross-Functional Metrics

- **Average Response Time**: Inference latency
- **Number of Training Sessions (Epochs)**: Training efficiency
- **Customer Satisfaction Score (CSAT)**: User feedback
- **Return on Investment (ROI)**: Business value
- **Cost per User**: Operational efficiency

---

# 9. Model Fit Patterns

## Underfitting
- **Problem**: Model doesn't learn enough from training data
- **Symptoms**: Poor performance on both training and testing data
- **Solution**: Increase model complexity, add features, train longer

## Overfitting
- **Problem**: Model learns noise and details specific to training data
- **Symptoms**: Excellent training performance, poor performance on unseen data
- **Solution**: Regularization, reduce complexity, increase training data, cross-validation

---

# 10. Responsible AI & Fairness

## Core Dimensions of Responsible AI

### Fairness and Bias Mitigation
- Ensure AI doesn't unfairly impact different subpopulations
- **Requirements for Fair AI**:
  - Diverse backgrounds and demographics in training data
  - Balanced representation (no over/under-represented groups)
  - High-quality sources with consistent labeling
  - Ethical labeling with neutral, objective annotators

### Explainability
- Understanding WHY a specific output was generated using post-hoc methods (SHAP, LIME).
- Explains predictions without needing model transparency.

### Interpretability  
- Understanding HOW the model works internally.
- Observe how inputs transform to outputs.
- Inherently clear models like decision trees.

### Transparency
- Open access to algorithms, training data, processes. Enables interpretability.

### Robustness and Veracity
- **Robustness**: Model adapts to challenging conditions
- **Veracity**: Decisions based on accurate, real-time information
- Ensures reliability and truthfulness

### Controllability
- AI systems align with human values
- Humans maintain ultimate control over decisions
- Override capabilities when needed

### Environmental Sustainability
- Choose energy-efficient infrastructure for training and inference
- **AWS Trainium**: Optimized for model training
- **AWS Inferentia**: Optimized for inference/production
- Balances performance with minimal energy consumption

## Bias and Variance

**Bias** = Gap between predicted and actual values  
- High Bias = **Underfitting** (too simple, poor on training + test)  
- Fix: More features, complex models, longer training

**Variance** = Sensitivity to training data changes  
- High Variance = **Overfitting** (too complex, learns noise, good on training but poor on test)  
- Fix: Fewer features, more data, data augmentation, regularization, cross-validation

**Goal**: Low bias + low variance = generalizes without memorizing

## Types of Bias in ML

**Measurement Bias**: Faulty data capture (e.g., uncalibrated devices)  
**Sampling Bias**: Unrepresentative training data; common in imbalanced datasets  
**Confirmation Bias**: Only using data supporting existing beliefs  
**Observer Bias**: Labeler's subjective opinions influence annotations  
**Training Data Bias**: Unequal demographic representation  
**Historical Bias**: Prejudice embedded in historical data  
**Algorithmic Bias**: Model architecture amplifies biases

**Mitigation Strategies:**
- Use diverse, representative datasets
- Employ bias detection tools (e.g., AWS SageMaker Clarify)
- Conduct regular fairness audits
- Perform subgroup analysis across protected attributes

## Interpretability vs Explainability Trade-offs

### High Interpretability Models
**Decision Trees**
- Easy to visualize and understand HOW the model works
- **Trade-off**: Lower performance (simpler models)

### Low Interpretability Models
**Neural Networks**
- Complex, "black box" architecture
- **Solution**: Use post-hoc explainability techniques (SHAP, LIME) to explain WHY
- **Trade-off**: Higher performance (capture intricate patterns)

### Performance Trade-offs
- **Interpretability ↑ = Performance ↓**: Simpler models are more understandable but less powerful
- **Complexity ↑ = Interpretability ↓**: Complex models perform better but harder to interpret
- **Transparency ↑ = Security ↓**: Exposing model details can reveal exploitable weaknesses

## Generative AI Risks

**Hallucinations**: Believable but false content; always fact-check  
**Prompt Leaking**: Reveals internal instructions or conversation history  
**Model Exposure**: Unintended release of training data or confidential info  
**Intellectual Property Infringement**: Replicating copyrighted materials from training data

## Human-Centered Design (HCD)

User-focused methodology ensuring AI is effective and aligned with human needs.

**Amplified Decision-Making**: AI assists (doesn't replace) with clarity, simplicity, usability  
**Unbiased Decision-Making**: Transparent, auditable processes  
**Cognitive Apprenticeship**: AI learns from human feedback (RLHF)
**Personalization**: Adapt to fit individual needs and styles 
**User-Centered**: Intuitive, accessible for diverse users

## AWS Tools for Responsible AI

**SageMaker Tools** (see [# 12. Amazon SageMaker Deep Dive](#12-amazon-sagemaker-deep-dive)):
- **Clarify**: Detect bias and provide model explainability (SHAP, LIME)
- **Ground Truth**: Data labeling with human-in-the-loop and active learning
- **Model Cards**: Document model purpose, risks, limitations, and performance
- **Model Monitor**: Continuous monitoring for data drift, bias drift, and performance degradation
- **A2I (Augmented AI)**: Human review via random sampling or confidence thresholds

**Bedrock Tools** (see [# 13. Amazon Bedrock Deep Dive](#13-amazon-bedrock-deep-dive)):
- **Guardrails**: Safety barriers against offensive content, PII, hallucinations, prompt attacks

**Foundation Model Evaluations (FMEval)**:
- Test and evaluate foundation models
- Detect prompt stereotyping (biases about gender, age, ethnicity)

## AI Governance

**Open-Source Models:**
- Publicly available architecture, training methods, and datasets
- Platforms: Hugging Face (NLP models), Kaggle (datasets and competitions)
- Open data licensing for reproducibility and validation

### Governance Tools
- **Model Cards**: Document model lifecycle and decisions
- **Model Monitor**: Track performance and drift
- **Version Control**: Track changes to models, data, and code
- **Audit Trails**: Maintain records of model decisions

---

# 11. AWS AI/ML & GenAI Services Portfolio

## Vision Services

**Amazon Rekognition**
- Analyze images and videos
- Face detection, object recognition, scene analysis
- Content moderation
- **Rekognition Custom Labels**: Train custom image recognition models with labeled data (uses SageMaker backend)

**Amazon Textract**
- Extract text and data from documents
- OCR with form and table understanding
- Automates document processing workflows

## Language Services

**Amazon Comprehend**
- NLP service for text analysis and classification
- **Tokenization**: Breaks text into words
- **Parts of Speech (POS)**: Identifies syntactic functions
- Sentiment analysis, entity recognition, key phrase extraction

**Amazon Translate**
- Neural machine translation
- Real-time and batch translation
- Supports 75+ languages

## Speech Services

**Amazon Transcribe**
- Automatic Speech Recognition (ASR)
- Speech-to-text conversion
- Custom vocabulary, speaker identification

**Amazon Polly**
- Text-to-speech (TTS)
- Lifelike voices in multiple languages
- SSML support for pronunciation control

## Specialized AI Services

**Amazon Lex**
- Build conversational interfaces (chatbots)
- Integration with Amazon Connect and Comprehend
- Natural language understanding

**Amazon Forecast**
- Time-series forecasting service
- Uses historical data to predict future trends
- Automated ML algorithms

**Amazon Kendra**
- Intelligent enterprise search
- NLP-powered to deliver accurate, relevant answers
- Semantic search capabilities

**Amazon Personalize**
- Real-time personalized recommendations
- Uses **Recipes** (algorithms) to generate recommendations
- Based on user activity and behavior patterns

## Contact Center & Customer Service

**Amazon Connect Contact Lens**
- Real-time analytics for contact center interactions
- Sentiment analysis and transcription

**Amazon Q in Connect**
- GenAI assistant embedded in Amazon Connect
- Provides real-time guidance for agents during calls
- Automates post-call documentation
- Reduces after-call work time

**Amazon Connect Wisdom**
- Knowledge management for contact center agents
- Real-time article recommendations during customer interactions

## Generative AI Services

**Amazon Bedrock**
- Fully managed foundation model service
- Access pre-trained GenAI models via API calls
- No infrastructure management required
- Supports multiple foundation model providers
- **PartyRock**: Interactive playground to test models and configurations without code
- **Bedrock Agents**: Automate multi-step workflows with memory retention and action schemas
- **Bedrock Guardrails**: Safety barriers to filter offensive content, PII, hallucinations, and prompt attacks
- **Bedrock Model Distillation**: Transfer knowledge from larger teacher model to smaller, more efficient student model
- **Bedrock Prompt Caching**: Cache prompts to reduce latency and costs for repeated or similar queries
- **Provisioned Throughput**: Reserved dedicated capacity with predictable costs, required for fine-tuned models

**Amazon Titan Models**
- **Amazon Titan Multimodal Embeddings G1**: 
  - Generates embeddings for both text and images
  - Enables multimodal search (search by text or image)
  - Captures semantic meaning across modalities
  - Used with OpenSearch for semantic search capabilities

**Amazon Q**
- AI-powered assistant for business and development

**Amazon Q Business (with QuickSight)**
- Dashboard generation
- Executive summaries
- Data stories and insights
- Natural language business intelligence

**Amazon Q Developer**
- Code generation and assistance
- Automation of development tasks
- Integration with development workflows
- Accelerates software development

**Amazon SageMaker**
- Fully managed platform for building, training, and deploying ML models at scale
- Write code in notebook environment
- End-to-end ML workflow management

---

# 12. Amazon SageMaker Deep Dive

## Overview
Comprehensive platform to prepare, build, train, tune, and deploy ML models from scratch

## SageMaker Studio
- Integrated Development Environment (IDE) for ML
- Unified workspace for entire ML workflow
- Jupyter notebooks, experiment tracking, debugging

## SageMaker Pipelines
- **Purpose**: Design, orchestrate, and automate end-to-end ML workflows
- **Features**:
  - Step-based architecture
  - Version control for pipelines
  - Integration with AutoML
  - CI/CD for ML models

## SageMaker AutoML (Autopilot)
- **Purpose**: Automate model selection and hyperparameter tuning
- **ML Workflow Stage**: Model training and tuning
- **Benefits**:
  - Minimal manual intervention
  - Quick model generation
  - Transparent explainability
  - Notebook code generation

## SageMaker JumpStart
- **Purpose**: Quick-start ML development with pre-built solutions
- **ML Workflow Stage**: Model selection and deployment
- **Features**:
  - Built-in algorithms and pre-trained models
  - Access to foundation models
  - Customizable solutions for common ML tasks
  - One-click deployment templates
  - Reduces time from idea to production

## SageMaker Data Wrangler
- **Purpose**: Transform raw data into ML-ready format
- **ML Workflow Stage**: Data preparation and feature engineering
- **Supported Data Types**: Tabular, images, text, time series
- **Workflow**: Import → Clean → Feature Engineering → EDA
- **Data Sources**: S3, Athena, Redshift
- **Features**: SQL support, 300+ built-in transformations
- **Keywords**: Clean, prepare, transform data

## SageMaker Feature Store
- **Purpose**: Centralized repository for ML features
- **ML Workflow Stage**: Feature engineering and model serving
- **Benefits**:
  - Share features across teams and models
  - Consistent feature computation
  - Low-latency serving for inference
- **Integration**: Can store features from Data Wrangler or create directly

## SageMaker Ground Truth
- **Purpose**: Data labeling for machine learning
- **ML Workflow Stage**: Data labeling (data preparation)
- **Features**:
  - Human-in-the-loop (Mechanical Turk, own team, third-party vendors)
  - Machine assistance (AI suggests labels, humans correct)
  - Active learning to minimize labeling effort and cost
  - Automated labeling after sufficient data collected
- **Ground Truth Plus**: Subject matter experts for complex labeling tasks

## SageMaker Clarify
- **Purpose**: Ensure fairness and explainability in ML models
- **ML Workflow Stage**: Model evaluation and monitoring
- **Features**:
  - Detect data and model bias
  - Identify underrepresented/overrepresented groups in datasets
  - Analyze features influencing predictions (feature importance)
  - Provide model interpretability tools (SHAP, LIME)
  - Visualize prediction distribution across groups
  - Show which factors contribute to decisions via charts

## SageMaker Model Cards
- **Purpose**: Document comprehensive model information
- **ML Workflow Stage**: Model documentation and governance
- **Includes**:
  - Model purpose and intended use
  - Risk ratings (high/medium/low/unknown)
  - Known limitations and ethical considerations
  - Performance metrics (accuracy, precision, recall, etc.)

## SageMaker Model Monitor
- **Purpose**: Continuous monitoring of deployed models to ensure ongoing quality and performance
- **ML Workflow Stage**: Post-deployment monitoring
- **Features**:
  - Compare production data to training data
  - Detect data drift and bias drift
  - Flag model performance degradation
  - Alert notifications

## Amazon Augmented AI (A2I)
- **Purpose**: Combine AI speed with human accuracy
- **ML Workflow Stage**: Model inference and quality assurance
- **Human Review Triggers**:
  - Random sampling (e.g., review 10% of predictions)
  - Confidence score threshold (e.g., review when confidence < 50%)
- **Reviewers**: Own employees, third-party providers, AWS Mechanical Turk

## SageMaker Deployment Options

**Real-time Endpoints (Synchronous Inference)**
- **Use Cases**: Chatbots, recommendations, fraud detection
- **Characteristics**: 
  - Instant response
  - Low latency (<100ms)
  - Predictable traffic patterns

**Asynchronous Inference**
- **Use Cases**: Process large files, images, videos, complex models
- **Characteristics**:
  - Background processing
  - Variable response time
  - Unpredictable workloads

**Batch Transform**
- **Use Cases**: Large datasets, overnight processing
- **Characteristics**:
  - Asynchronous processing of entire datasets
  - High latency acceptable
  - Cost-effective for bulk inference

**Serverless Inference**
- **Use Cases**: Sporadic traffic, prototypes, development phases
- **Characteristics**:
  - Auto-scaling (including to zero)
  - Pay-per-use pricing
  - Unpredictable usage patterns

---

# 13. Amazon Bedrock Deep Dive

## Overview
Fully managed service providing access to foundation models from multiple providers through a single API

## Foundation Model Access
- **Multi-Provider Support**: Amazon, AI21 Labs, Anthropic, Cohere, Meta, Mistral AI, Stability AI
- **Single API**: Unified interface for all models
- **Serverless**: No infrastructure management, automatic scaling
- **PartyRock**: No-code playground for testing models and configurations

## Bedrock Agents
- **Purpose**: Automate multi-step tasks using GenAI
- **Capabilities**:
  - Multi-step workflow orchestration
  - Memory retention across conversation turns
  - Custom action schema definition
  - API and database integration
- **Use Cases**: Customer service, data analysis, task automation

## Bedrock Guardrails
- **Purpose**: Safety barriers for responsible AI usage
- **Protection**:
  - Content filtering (offensive, biased, harmful content)
  - PII detection and masking
  - Hallucination prevention
  - Prompt attack defense (injection, jailbreaking, leaking)
  - Denied topics configuration

## Bedrock Model Distillation
- **Purpose**: Transfer knowledge from large "teacher" to efficient "student" model
- **Benefits**: Lower cost, faster inference, easier deployment
- **Use Cases**: Edge deployment, real-time apps, mobile/IoT

## Bedrock Prompt Caching
- **Purpose**: Reduce latency and costs for repeated queries
- **Benefits**:
  - Store and reuse prompt components
  - Pay once for cached tokens
  - Faster responses
- **Use Cases**: Chatbots with system prompts, RAG systems, multi-turn conversations

## Provisioned Throughput
- **Purpose**: Reserved dedicated capacity with predictable performance
- **Features**:
  - Guaranteed availability, no cold starts
  - Predictable costs (commitment-based pricing)
  - **Required for fine-tuned Bedrock models**
- **Use Cases**: High-volume production, consistent low latency, fine-tuned models

## Inference Parameters
Control model output behavior via Bedrock API calls:

**Temperature (0.0 - 1.0)**
- Controls randomness and creativity
- Low (0.0-0.3): Deterministic, predictable (coding, factual tasks)
- High (0.8-1.0): Creative, random (stories, marketing)

**Top-k (0-500)**
- Limits sampling to k most likely tokens
- Lower k = more focused, higher k = more diverse
- Typical: 20-50 for balanced output

**Top-p (0.0 - 1.0)**
- Nucleus sampling: cumulative probability cutoff
- Dynamic adaptation based on context
- Typical: 0.9-0.95 for natural text

## Model Customization Hierarchy

Ranked from lowest to highest cost. For detailed cost analysis, see [Cost Optimization & Pricing](#19-cost-optimization--pricing).

1. **Pre-trained** (Lowest cost): Use models as-is
2. **Prompt Engineering**: Optimize prompts, no retraining
3. **RAG**: Combine with external knowledge base
4. **Fine-tuning** (Highest cost): Customize with labeled data, requires provisioned throughput

---

# 14. Key Algorithms & Techniques

## Classification Algorithms

**Support Vector Machine (SVM)**
- Powerful supervised classification algorithm
- Handles high-dimensional data effectively
- Works well with non-linear relationships
- Effective for binary classification (e.g., churn prediction, fraud detection)
- Use case: Data is well-separated, complex decision boundaries needed

**Binary Classification**
- Classification with exactly two possible outcomes
- Algorithms: Logistic Regression, SVM, Decision Trees, Random Forest, Neural Networks
- Metrics: Precision, Recall, F1, AUC-ROC

## Clustering
**K-Means Clustering**
- Unsupervised learning algorithm
- Partitions data into K clusters
- Minimizes within-cluster variance
- Use case: Customer segmentation, pattern discovery

## Regression
**Linear Regression**
- Supervised learning for continuous predictions
- Models linear relationship between variables
- Simple, interpretable baseline model

## Dimensionality Reduction
**Principal Component Analysis (PCA)**
- Reduces feature space while preserving variance
- Creates uncorrelated principal components
- Used for visualization and preprocessing
- Addresses curse of dimensionality in high-dimensional data

## Pattern Discovery
**Association Rule Mining (e.g., Apriori)**
- Discovers relationships in transactional data
- Common in market basket analysis
- Identifies frequent itemsets and rules

## Model Evaluation & Experimentation

**A/B Testing**
- Controlled experiment comparing model variants
- Split users into groups (A and B)
- Evaluate performance on predefined metrics: accuracy, engagement, response quality, speed
- Determine which variant performs better
- Essential before full rollout
- **Multi-Model Hosting**: Support multiple model variants simultaneously in production

## Sequence Generation & Decoding

**Beam Search**
- Decoding strategy for generating text sequences
- Explores multiple candidate paths simultaneously
- Improves quality of generated sequences
- Trade-off: Better quality vs slower generation than greedy search
- Used in machine translation and text generation

**Greedy Search**
- Selects most probable token at each step
- Faster but may miss better overall sequences
- Good for real-time applications with latency constraints

## Model Compression Techniques

Model compression reduces size and computational requirements while maintaining acceptable performance. Critical for edge deployment, mobile devices, and cost optimization.

**Pruning**
- Remove redundant or less important parameters
- Techniques: Weight pruning, neuron pruning, structured pruning
- Reduces model size and computational requirements
- Trade-off: Minimal accuracy loss for significant size reduction
- AWS tools: SageMaker Debugger and Experiments

**Quantization**
- Reduce precision of model weights
- Convert high precision to lower precision (FP32 → FP16 → INT8)
- Decreases memory footprint significantly
- Enables faster inference
- Trade-off: Small accuracy loss for efficiency gains

**Knowledge Distillation**
- Transfer knowledge from large "teacher" model to small "student" model
- Student learns to mimic teacher's behavior and outputs
- Retains significant performance in compact model

---

# 15. Applications of Foundation Models

> **Foundation**: Builds on [Generative AI Fundamentals](#4-generative-ai-fundamentals), focusing on practical application and deployment.

## Design Considerations for Model Selection

### Selection Criteria

**Modality**
- Type of data the model handles (text, images, audio)
- **Claude (Bedrock)**: Chatbots, document summarization, translation
- **Rekognition**: Image recognition, face detection, content moderation
- **Transcribe**: Speech-to-text; **Polly**: Text-to-speech

**Latency**
- How quickly the model processes requests
- **Low latency**: Chatbots, real-time responses
- **High latency acceptable**: Batch data analysis

**Multilingual Support**
- Models supporting multiple languages for global audiences
- Critical for international applications

**Model Size**
- **Large models**: More accurate, require extensive computational resources
- **Small models**: More efficient, easier to deploy

**Model Complexity**
- **Simple tasks**: Lighter models
- **Complex tasks**: Robust multi-layer models

**Customization**
- Fine-tuning or few-shot learning capabilities
- Tied to cost and computational demand

**Input/Output Length**
- Models vary in capacity to handle input size
- Longer contexts = more computational resources and costs

### Inference Parameters

Control model output behavior during API calls. For detailed explanations of Temperature, Top-k, and Top-p, see [Bedrock Deep Dive - Inference Parameters](#inference-parameters).

**Quick Reference**:
- **Temperature** (0.0-1.0): Creativity/randomness control (low = predictable, high = creative)
- **Top-k** (0-500): Number of token candidates (lower = focused, higher = diverse)
- **Top-p** (0.0-1.0): Cumulative probability threshold (lower = confident, higher = exploratory)
- **Input/Output Length**: Impacts computational cost

## Retrieval-Augmented Generation (RAG)

### Definition
- Foundation model paired with external knowledge source
- Database, document repository, or structured data
- Model retrieves information and augments prompt with external data

### Knowledge Base
- Structured repository of information
- Company documents, FAQs, research papers, technical manuals
- Acts as external source during inference
- Can be built from data in **Amazon S3**
- **Supported AWS Services**: 
  - Amazon OpenSearch Service (vector database for semantic search)
  - Amazon Kendra (intelligent enterprise search)

### RAG Workflow Steps

**1. Retrieval Phase**
- Query vector database for semantically similar documents
- Use embedding models to convert query to vector
- Return top-k most relevant documents

**2. Prompt Augmentation**
- Enrich user query with relevant info from retrieved documents
- Improves accuracy and relevance without fine-tuning

**3. Generation Phase**
- Foundation model generates response using augmented prompt
- Reduces hallucinations with up-to-date data

### Use Cases
- **Customer support**: Answer questions using up-to-date FAQs/policies
- **Documentation**: Retrieve info from technical manuals
- **Research**: Query large databases for insights
- **Real-time knowledge**: Access current information without retraining

### Key Benefits
- Ensures up-to-date, context-aware, accurate responses
- No model retraining required for knowledge updates
- **Amazon Bedrock** supports seamless integration with external data
- Combines retrieval with generation
- Lower cost than fine-tuning for dynamic knowledge

## Vector Storage & Databases

### Vectors & Embeddings
- **Vectors**: Numerical array of embeddings
- **Embeddings**: Mathematical representations of data capturing semantic meaning
- Vector databases store and manage embeddings

### Vector Database Functionality
- Use vector search algorithms to index and query based on similarity
- Instead of exact matches, find semantically similar content
- Enable semantic search capabilities

### AWS Services for Vector Storage

**Amazon OpenSearch Service**
- Integration with full-text search
- Combines semantic and keyword-based searches
- Scalable for large vector datasets

**Amazon Aurora (PostgreSQL)**
- Extends relational DB to manage vector data
- Personalized recommendations
- Combines structured and vector data

**Amazon Neptune**
- Graph database with relationships between embeddings
- Connect entities through vector similarity

**Amazon DocumentDB**
- Flexible, schemaless storage for embeddings
- MongoDB-compatible

**Amazon RDS for PostgreSQL**
- **pgvector extension** for vector similarity search
- SQL-based vector operations

## Model Customization Approaches

Understanding different customization methods helps select the right approach based on requirements and budget. [See Cost Optimization & Pricing](#19-cost-optimization--pricing) for detailed cost analysis.

**Customization Ranking (Lowest to Highest Cost):**
1. **In-context Learning (Prompting)**: Use prompts to influence outputs without retraining
2. **RAG**: Combine pre-trained model with external data sources
3. **Fine-tuning**: Update pre-trained model with task-specific dataset (requires provisioned throughput in Bedrock)
4. **Pre-training**: Create model from scratch (only for specialized domains)

## Amazon Bedrock Agents

Automate multi-step workflows using generative AI. For detailed features, see [Bedrock Agents in Bedrock Deep Dive](#bedrock-agents).

**Key Capabilities**: Memory retention, action schema, RAG integration, multi-system orchestration  
**Example Use Case**: Customer asks order status → Agent retrieves from DB → Analyzes shipping data → Responds with real-time updates

---

# 16. Prompt Engineering

## Fundamentals

### Core Concepts

**Context**
- Frames task with relevant background information
- Increases relevance and accuracy of responses
- Example: "Explain cloud computing" vs "Explain cloud computing to a beginner"

**Instructions**
- Clear directions set expectations
- Define format, tone, and content
- Be specific: "Place red folder on top shelf" vs "Put folder somewhere easy to find"

**Negative Prompts**
- Explicitly guide what NOT to include
- Example: "Explain cloud computing without using technical terminology"
- Helps filter unwanted content

**Model Latent Space**
- Internal representation of knowledge
- Mental map connecting concepts
- Like library indexing system clustering related ideas

## Prompt Engineering Techniques

### Zero-shot Prompting
- Give task without any examples
- Relies on model's general knowledge
- Example: "Describe a dog" → broad, undirected answer

### Single-shot Prompting
- Provide ONE example in prompt
- Example: "Here's how to describe a cat: [example]. Now describe a dog"
- More focused response

### Few-shot Prompting
- Provide MULTIPLE examples (more than one)
- Guide model with pattern from examples
- Best when you know desired output format
- More examples = better pattern recognition

### Chain-of-thought Prompting
- Ask model to break down complex problem into logical steps
- Helps understand thought process leading to answer
- Example: "Describe a dog. Break down your explanation into smaller steps"
- Useful for math problems, complex reasoning

### Prompt Templates
- Standardize prompt generation process
- Translate user input into instructions
- Use placeholders for dynamic content
- Example: "Describe a [type of animal] including [specific traits]"
- Useful for customer support, repeated tasks

## Advanced Prompt Techniques

### Prompt Engineering vs Prompt Tuning

**Prompt Engineering**
- Manual, human-driven approach
- Iterative crafting of prompts
- Uses **hard prompts** (natural language instructions)
- Trial-and-error refinement process
- Requires domain expertise and creativity
- Flexible and interpretable
- Lower upfront cost, more time-consuming at scale

**Prompt Tuning**
- Automated, uses machine learning to learn optimal instructions for a task
- Uses **soft prompts** (virtual tokens prepended to input)
- Trains separate small model to generate soft prompts
- More efficient in context window usage
- Higher upfront cost, more efficient at scale

### Response Quality Improvement
- Be **specific and concise** with prompts
- Clear prompts = higher quality responses
- Avoid ambiguity

### Experimentation
- Try different prompts to discover best results
- Refine prompts iteratively
- Start basic, then refine based on outputs

### Guardrails
- Use explicit instructions to avoid unwanted results
- Example: "List benefits of renewable energy, but don't include political opinions"
- Reduces bias, keeps responses aligned
- For technical implementation, see [Bedrock Guardrails](#bedrock-guardrails)

### Multiple Comments
- Break complex ideas into smaller steps
- Use follow-up prompts instead of one long prompt
- Step-by-step queries improve depth and structure

## Risks and Limitations

For comprehensive security practices, see [Security, Compliance & Governance](#20-security-compliance--governance-for-ai-systems).

### Exposure
- Sensitive data inadvertently revealed through prompts
- **Mitigation**: Avoid prompts targeting sensitive/proprietary information

### Poisoning
- Maliciously inserting false/harmful data during training
- Causes biased, inaccurate, or dangerous outputs
- **Mitigation**: Filter training data, continuous evaluation, detect harmful data

### Hijacking
- Attacker manipulates prompt to divert model behavior
- Forces unintended or harmful outputs
- **Mitigation**: Enforce usage policies, monitor prompts for misuse

### Jailbreaking
- Using clever prompts to bypass safety constraints
- Attempts to override safeguards
- **Mitigation**: Train with robust guardrails, continuous testing for vulnerabilities

---

# 17. Training & Fine-tuning Foundation Models

## Key Elements

### Pre-training
- Initial stage: model learns from vast unstructured data
- Develops general capabilities (language patterns, coherent responses)
- Resource-intensive (requires massive compute)
- Typically done by large companies like AWS

### Fine-tuning
- Customize pre-trained model with task-specific data
- Refines knowledge for particular use case
- **In Bedrock**: Requires high-quality labeled datasets
- **Must purchase provisioned throughput** to use fine-tuned model

### Continuous Pre-training
- LLMs learn new information while retaining existing knowledge
- Keeps model updated over time
- Prevents becoming outdated
- Example: Chatbot updated with latest support tickets

## Fine-tuning Methods

### Full Fine-Tuning
- Updates ALL model parameters during training
- **Characteristics**:
  - Computationally expensive and memory-intensive
  - High GPU memory requirements
  - Risk of catastrophic forgetting
  - Better for massive datasets with abundant resources
  - Maximum customization potential
- **When to use**: Large datasets, abundant compute resources, need maximum performance

### PEFT (Parameter-Efficient Fine-Tuning)
- Updates only a small subset of model parameters (not all)
- **Characteristics**:
  - More computationally efficient than full fine-tuning
  - Significantly less GPU memory required
  - Mitigates catastrophic forgetting by keeping most parameters frozen
  - Creates smaller, specialized models from same base model
  - Preserves original model knowledge better
  - Easier to maintain and deploy multiple versions
- **Ideal use case**: Multiple tenants/use cases from single base model

### Instruction Tuning
- Further training with guidelines/directives
- Adapt nuanced understanding of specific tasks
- Follow instructions better
- Example: Tune chatbot to be more empathetic to complaints

### Domain Adaptation
- Take general-purpose model, train on industry-specific data
- Adapt for healthcare, finance, legal, etc.
- Specializes model for particular field
- Improves accuracy in domain-specific language

### Transfer Learning
- Take model pre-trained on one task, fine-tune for related task
- Reuse fundamental knowledge without training from scratch
- Works when tasks share similarities
- Example: Model trained on general text → fine-tune for finance equations

## Data Preparation for Fine-tuning

### Data Curation
- Select and organize relevant, accurate, high-quality data
- Remove noise and redundancy
- Focus on what's essential
- Example: Legal text model → filter out fiction/blogs

### Data Governance
- Policies, processes, practices for quality, accuracy, ethical use
- Adherence to privacy regulations
- Uphold ethical standards
- Maintain data lineage and documentation

### Data Size & Quality
- More data isn't always better
- **Quality matters more than quantity**
- **Representativeness** crucial (capture wide range of scenarios, prevent bias)
- Balanced datasets improve generalization

### Data Labeling
- Annotate data with tags/categories
- Help model understand specific patterns
- Example: Tag emails as "spam" or "not spam"
- High-quality labeling critical for supervised learning

### Reinforcement Learning from Human Feedback (RLHF)
- Train models to align with human preferences
- Human evaluators score responses
- Model adapts based on scores
- **Reward model** created to predict response quality
- Also called: **Cognitive Apprenticeship**
- Iterative improvement process

---

# 18. Evaluating Foundation Model Performance

**Note**: This section covers Foundation Model-specific evaluation metrics. For traditional ML metrics (Precision, Recall, F1, MAE, RMSE), see [Section 8](#8-model-evaluation-metrics).

## Evaluation Methods

### Human Evaluation
- People assess outputs based on specific criteria
- Judge relevance, quality, coherence
- Example: Rate chatbot for politeness, helpfulness
- **Pros**: Insightful, nuanced feedback
- **Cons**: Time-consuming, subjective, labor-intensive

### Benchmark Datasets
- Pre-built collections of labeled data
- Test against industry standards
- Predefined tasks model must complete
- **Pros**: Objective, scalable, faster, less biased
- **Cons**: Might lack specificity for niche applications
- Help detect bias

## Performance Metrics

### ROUGE (Recall-Oriented Understudy for Gisting Evaluation)
- Measures overlap between generated and reference texts
- Used for **summarization tasks**
- Emphasizes **recall** of critical phrases
- **ROUGE-N**: Number of matching n-grams
  - n=1 for unigrams (single words)
  - n=2 for bigrams (two-word sequences)
- **Remember**: ROUGE for **recall** (recallability)
- Tests: Can generated text recall reference text accurately?

### BLEU (Bilingual Evaluation Understudy)
- Primarily for **machine translation**
- Evaluates how closely translation matches reference
- Compares word sequences
- Evaluates overlap of n-grams
- Score ranges 0-1 (1 is best)
- Focuses on **quality of text**
- **Remember**: BLEU for **bilingual** (translation)

### BERTScore
- Newer metric using **embeddings**
- Leverages pre-trained BERT models
  - Bidirectional Encoder Representations from Transformers
- Compares **semantic similarity** between generated and reference
- Effective for tasks requiring nuanced understanding
- Works well for paraphrasing tasks
- Core meaning retained even with different word choice
- **Remember**: BERT is **bonding** (bond strength between related words/sentences)

### Perplexity
- Measures how well probability model predicts a sample
- **Lower perplexity = better model**
- Common metric for evaluating Large Language Models (LLMs)
- Indicates model's uncertainty in predictions
- Perplexity of 1 = perfect prediction (knows exactly what comes next)
- Higher perplexity = model is more "perplexed" or uncertain
- Used to compare different language models on same test set
- **Remember**: Lower is better - less perplexed = more confident predictions

## Business Objective Alignment

### Productivity
- How efficiently model performs tasks
- High-quality outputs with minimal human intervention
- Higher productivity = better alignment with business objectives
- Measure: Time saved, tasks automated

### User Engagement
- How often and deeply users interact with model
- Complexity of prompts provided
- Amount of active refinement of responses
- Higher engagement = model providing value
- User modifications/feedback = positive (guides to better results)

### Task Engineering
- How effectively model completes specific tasks aligned with business
- Smooth and accurate task completion = good alignment
- Measure: Success rate, error reduction, consistency

---

# 19. Cost Optimization & Pricing Models

## GenAI Pricing Strategies

**Token-Based Pricing**
- Pay per token processed (input and output)
- Scales with actual usage
- Common for API-based services
- Variable costs based on model size and complexity

**Provisioned Throughput**
- Reserve dedicated capacity
- Predictable performance and costs
- Better for consistent, high-volume workloads
- Guaranteed availability

**Custom Models**
- Pricing for fine-tuning and customization
- Training costs separate from inference
- Storage costs for custom model artifacts
- May include minimum commitment periods

## Model Customization Cost Analysis

### Pre-training (Highest Cost)
- **Approach**: Creating model from scratch using vast dataset
- **Cost**: Very High (massive compute power, storage, time)
- **Who**: Only large companies with significant resources
- **When to use**: Domain-specific needs where pre-trained models don't exist
- **Example**: Training a specialized medical diagnosis model from scratch

### Fine-tuning (Moderate Cost)
- **Approach**: Update pre-trained model with smaller task-specific dataset
- **Cost**: Moderate (leverages existing model weights)
- **AWS Requirement**: Must purchase provisioned throughput for fine-tuned Bedrock models
- **When to use**: Adapting general model to specialized tasks
- **Example**: Fine-tuning GPT for legal document analysis

### RAG - Retrieval-Augmented Generation (Lower Cost)
- **Approach**: Combine pre-trained model with external data sources
- **Cost**: Lower than fine-tuning (no model modification required)
- **When to use**: Real-time updates, proprietary data integration
- **Example**: Customer support chatbot with access to company knowledge base

### In-context Learning / Prompting (Lowest Cost)
- **Approach**: No model retraining, uses prompts to influence outputs
- **Cost**: Low (pay only for inference tokens)
- **When to use**: Flexible, quick adaptations without retraining
- **Example**: Few-shot prompting for specific formatting tasks

**Cost Ranking: Pre-training >> Fine-tuning > RAG > In-context Learning**

## Cost Optimization Best Practices

**Model Selection**
- Choose appropriate model size for task complexity
- Smaller models for simpler tasks reduce costs
- Balance performance vs. cost requirements

**Efficient Prompt Design**
- Minimize token usage with concise prompts
- Reduce context window requirements
- Optimize for token efficiency

**Caching and Reuse**
- Cache frequent queries and responses
- Reuse embeddings when possible
- Leverage feature stores for common features

**Monitoring and Optimization**
- Track usage patterns and costs
- Identify optimization opportunities
- Right-size infrastructure and throughput

---

# 20. Security, Compliance & Governance for AI Systems

## IAM (Identity and Access Management)

**IAM Policies**
- JSON-formatted documents attached to users, groups, roles
- Define granular access control to AWS resources
- Support conditional access and fine-grained permissions

**Access Control Models**
- **RBAC (Role-Based Access Control)**: Assign permissions based on job function, scales well
- **ABAC (Attribute-Based Access Control)**: Use tags for fine-grained control, dynamic access
- **Principle of Least Privilege**: Grant minimal access needed
- **Temporary Access**: Use IAM roles (recommended) vs long-term credentials (access keys)

## Security Services for AI Systems

**AWS KMS (Key Management Service)**
- Create, store, manage cryptographic keys
- **Key Types**:
  - Customer-managed keys: Full control, view metadata
  - AWS-managed keys: Manage keys, no metadata access
  - AWS-owned keys: AWS internal use, no customer access

**AWS CloudHSM**
- Dedicated hardware for cryptographic operations
- Required for government/defense compliance (FedRAMP)

**Amazon Macie**
- Discover, identify, classify sensitive data in S3
- Detect PII (phone, credit cards, SSN)
- Uses ML and managed/custom identifiers (RegEx)

**AWS PrivateLink**
- Private connectivity between VPCs and AWS services
- Avoid public internet traversal, reduces attack surface

**Shared Responsibility Model**
- **Customer Responsibilities**: Data, traffic, platforms, apps, OS, network config, firewalls, encryption, IAM
- **AWS Responsibilities**: Physical datacenters, compute, storage, networking, global infrastructure

## Data History & Lineage

**Data Origins**
- Where data was collected, cleaned, curated, processed, transformed
- Critical for identifying quality issues and potential biases

**Data Source Citation**
- Acknowledge source (datasets, web pages, databases)
- Identify terms of service, licensing, ensure legal compliance

**Data Lineage**
- Track complete data history: collection → transformation → movement through systems
- Enables documentation, transparency, and audit trails

**Data Cataloging**
- Organize datasets, models, terms of service, licensing, sources, metadata
- **SageMaker Model Cards**: Document origins, citations, lineage, training data details, performance metrics, intended use, risk rating

## Secure Data Engineering

**Data Quality & Integrity**
- **Accuracy**: Exclude misinformation, speculation, incorrect data
- **Completeness**: Ensure no missing critical information
- **Modification Monitoring**: Track and detect malicious data tampering

**Defense-in-Depth Strategy**
1. **IAM**: Manage identities, roles, groups with conditional access
2. **KMS**: Encryption for confidentiality
3. **Network Controls**: Firewalls, VPCs, NACLs, Security Groups
4. **Monitoring**: CloudTrail (API logging), CloudWatch (metrics/visibility)

**Privacy & Compliance Concepts**
- **PII (Personally Identifiable Information)**: Data that uniquely identifies an individual
- **PHI (Protected Health Information)**: Subset of PII, includes medical records

## Compliance Frameworks

**US Government & Industry**
- **NIST (National Institute of Standards and Technology)**:
  - SP 800 series: Security controls guidance
  - AI Risk Management Framework: Privacy and responsible AI
- **HIPAA (Health Insurance Portability and Accountability Act)**:
  - PHI protection for US citizens
  - Privacy Rule, Security Rule, Breach Notification Rule
- **PCI-DSS (Payment Card Industry Data Security Standard)**:
  - Payment card transaction security

**International Standards**
- **GDPR (General Data Protection Regulation)**:
  - EU regulation for online privacy and PII protection
  - Applies globally to orgs collecting EU citizen data
  - Data residency requirements
- **ISO/IEC Standards** (AWS certified):
  - **27001**: ISMS requirements (certification possible)
  - **27002**: Guidelines/best practices for 27001
  - **27017**: Cloud security
  - **27018**: Cloud privacy
- **SOC (System and Organization Controls)**:
  - **SOC 1**: Financial reporting
  - **SOC 2**: Trust services (CIA triad)
  - **SOC 3**: Public summary of SOC 2
  - **Type 1**: Point-in-time snapshot
  - **Type 2**: Time range report

**AI-Specific Regulations**
- **EU Artificial Intelligence Act**: First comprehensive AI legal framework
- **NYC Automated Decision Systems Law**: AI bias protection

**AWS Compliance Tools**
- **AWS Artifact**: Access compliance documents, reports, certifications
- **AWS Privacy Reference Architecture**: Guide for designing privacy controls

## Threat Detection & Response

**Threat Types**
- **Training Data Poisoning**: Inject false, biased, or malicious data into training process
- **AI System Misuse**: Manipulate input for copyrighted content, misinformation, malicious tasks
- **Misconfiguration**: Vulnerable IAM, encryption, network access controls

**AWS Security Services**

**Amazon GuardDuty**
- Intelligent threat detection using AI/ML
- Detect anomalies, malicious actions, model misuse
- Monitor for malicious input and unintended output
- **Input Sanitization**: Clean malicious input early in pipeline

**Amazon Inspector**
- Identify vulnerabilities across AWS infrastructure
- **Vulnerability Management Cycle**: Identify → Classify → Prioritize → Remediate → Mitigate
- Risk scoring for prioritization
- Security scanning, documentation, monitoring

**Amazon Detective**
- Security incident investigation
- Root cause identification
- Centralized view of security data from AWS logs

**NIST SP 800-61: Incident Response Lifecycle**
1. **Preparation**: Threat intelligence, deploy defensive controls
2. **Detection & Analysis**: Monitor and analyze security events
3. **Containment**: Limit spread of malicious activity
4. **Eradication**: Remove malware and threats
5. **Recovery**: Restore systems and services to normal operations
6. **Post-Incident**: Lessons learned, improve preparation

## Application Security

**OWASP Top 10 for LLM Applications**
1. **Prompt Injection**: Manipulate LLM with crafty inputs to perform unintended actions
2. **Insecure Output Handling**: LLM output blindly accepted (enables XSS, remote code execution)
3. **Training Data Poisoning**: Tamper with training data to compromise model learning

**Amazon Bedrock Guardrails** (Mitigation Strategies):
- Input sanitization and validation rules
- Pre-approved prompt templates (prevent manipulation)
- Fine-grained access controls
- Rate limiting (prevent model abuse)
- Output scanning and validation

**MLOps CI/CD Security Pipeline**
- **Data Preparation**: Validate data to prevent poisoning
- **Build & Test**: Security testing use cases during model development
- **Deployment**: Security scanning on test/stage before production
- **Post-Deployment**: Continuous monitoring and incident response preparation

**Secure Repository Management**
- Lock down access to data and development code
- Secure model artifacts
- Backup known good/secure trained models
- Enable rollback from corrupted/compromised versions

**AWS Application Security Services**

**AWS WAF (Web Application Firewall)**
- Protect OSI Layer 7 from web attacks
- Defends against XSS, SQL injection, remote code execution
- Web ACLs with custom rules

**AWS Shield**
- DDoS attack protection (availability)
- Shield Advanced: Access to AWS DDoS Response Team
- Integrates with CloudFront, Route 53

**Amazon Cognito**
- Customer identity and access management
- User sign up, sign in, access controls
- **Adaptive Protections**:
  - Bot detection (AWS WAF integration)
  - Credential protection (monitor compromised credentials)
  - Risk-based adaptive authentication (suspicious geolocation)
  - Advanced logging (auditing for PCI-DSS, HIPAA)

**Infrastructure Security Best Practices**
- **Encryption**: KMS for data at rest
- **IAM**: Strong access controls for compute platforms
- **Edge Devices**: Network segmentation to limit exposure

## Governance, Risk & Compliance (GRC)

**AWS Services for GRC**

**AWS Config**
- Track configuration changes of resources, services, identities
- Detect misconfigurations
- Support compliance audits

**AWS Audit Manager**
- Continually audit AWS environment
- Gather evidence for internal/external audits
- Centrally manage evidence (AWS, multi-cloud, on-prem)
- Monitor active assessments
- Track evidence modification (integrity)
- Generate compliance documents

**AWS Trusted Advisor**
- Evaluate environment for AWS Well-Architected Framework alignment
- **Six Pillars**: Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, Sustainability
- Recommend remediation actions
- Improve security posture

**AWS CloudTrail**
- Record all API activity (users and services)
- Log successful and failed calls
- Details: source IP, time, actions
- **CloudTrail Lake**: Managed data lake for CloudTrail events; enables SQL-based queries for advanced audit trail analysis and compliance investigations

**AWS Security Hub**
- Centralized dashboard for all security services
- Integration with SIEM platforms
- Continuous monitoring and aggregated findings
- Automated incident response (SOAR workflows)
- Cloud Security Posture Management (CSPM)
- Align to compliance frameworks (PCI-DSS, NIST SP 800-53)

## Data Governance Strategies

**Data Lifecycle Management**
1. **Collection**: Gather data from sources
2. **Processing**: Clean and transform
3. **Storage**: Secure storage with encryption
4. **Classification**: Based on sensitivity and compliance requirements
5. **Consumption**: Use for AI systems, share externally
6. **Archive**: S3 Intelligent Tiering, Glacier, Glacier Deep Archive
7. **Disposal**: Responsible deletion when no longer needed

**Data Residency & Sovereignty**
- **Data Residency**: Geolocation of servers (GDPR compliance requirement)
- **Data Sovereignty**: Legal governance within nation's borders (e.g., China data laws)

**S3 Object Locking (WORM Model)**
- Write-once-read-many for data integrity and immutability
- **Retention Modes**:
  - **Compliance Mode**: No deletion/modification (even root account) during retention period
  - **Governance Mode**: Allow deletion/modification with proper permissions
- **Legal Holds**: Restrict all users until lifted (legal discovery use cases)

**AWS Backup**
- Disaster recovery and business continuity
- Supports availability pillar
- Efficient backup of critical data

**Monitoring Best Practices**
- **Input/Output Behavior**: Detect prompt injection and model misuse
- **Performance Metrics**: Identify DDoS and availability attacks
- **Security Events**: Monitor failed logins, unauthorized data access
- **Infrastructure**: Compute, network, storage interactions
- **Compliance**: AI bias, copyright violations, PII exposure

## Governance Protocols

**Policy Framework**
- **Policy**: Overarching guideline aligned with org values, mission, compliance
- **Process**: High-level activities to achieve policy objectives
- **Procedure**: Detailed steps to support processes

**Policy Review Cadence**
- **Review Aspects**: Performance, data management, model training, human safety, responsible AI
- **Frequency**: Monthly, quarterly, semiannual, annual (based on risk assessment)
- **Stakeholders**: Technical teams, leadership, legal, SMEs, end users

**Review Strategies**
- **Technical Reviews**: Model performance, data quality, algorithms
- **Non-Technical Reviews**: Compliance, regulatory, legal, policy adherence
- **Testing**: Validate AI system output and function as intended
- **Decision-Making**: Clear intervention protocols (e.g., addressing AI bias)

**Transparency & Training**
- Publish training data, development process, model information
- Document intended use and limitations
- Maintain feedback channels (legal, dev, leadership, users)
- Ongoing team training on responsible/ethical AI practices
- Regular updates on regulatory/compliance changes

## GenAI Security Scoping Matrix

Framework for securing AI lifecycle based on control level and security responsibility:

**Application Scopes (Purchased AI Solutions)**
- **Scope 1: Public Consumer App**
  - Examples: PartyRock, ChatGPT
  - Control: Minimal (no control over model/data)
  - Security: Vendor-managed

- **Scope 2: Enterprise App**
  - Examples: Amazon Q
  - Control: Customization within vendor constraints
  - Features: Embedded in org apps, uses company data
  - Security: Shared responsibility

**Model Scopes (Built AI Solutions)**
- **Scope 3: Pre-trained Model**
  - Examples: Amazon Bedrock
  - Control: Build app with third-party FMs via APIs
  - Security: Org responsible for app layer

- **Scope 4: Fine-tuned Model**
  - Examples: SageMaker JumpStart, Bedrock custom models
  - Control: Fine-tune training data with org data
  - Security: Org responsible for data and fine-tuning

- **Scope 5: Self-trained Model**
  - Control: Full control (built from scratch)
  - Security: Full responsibility for entire AI lifecycle

**Security Principle**: Higher scope = More control = More security responsibility

---

# A. Summary & Key Takeaways

1. **AI/ML Fundamentals**
   - Understand the hierarchy: AI ⊃ ML ⊃ DL ⊃ GenAI
   - Know when to use supervised vs unsupervised learning
   - Grasp the complete ML lifecycle
   - Understand transformer architecture and LLMs

2. **Generative AI Concepts**
   - Foundation models and their lifecycle (data selection → model selection → pre-training → fine-tuning → evaluation → deployment → feedback)
   - Tokens, embeddings, and context windows
   - Multi-modal models and diffusion models
   - **Transformer Architecture**: Self-attention mechanism computing attention weights for each token
     - Attention weights: Tell model how much focus to give each token (quadratic complexity O(n²))
     - Encoder-Decoder: Best for summarization and translation (T5, BART)
     - Encoder-only: Classification tasks (BERT)
     - Decoder-only: Text generation (GPT series)
   - Advantages and limitations (hallucinations, nondeterminism)

3. **Foundation Model Applications**
   - Selection criteria: modality, latency, multilingual support, model size/complexity, customization, input/output length
   - Inference parameters: Temperature (creativity), Top-k (number of candidates), Top-p (percentage of candidates)
   - **RAG Workflow**: Retrieval → Prompt Augmentation → Generation → (Optional) Reranking
     - Prompt Augmentation: Core step enriching query with retrieved context (happens at inference time)
     - Reranking: Post-processing to enhance relevance and variety, reduce redundancy
   - Vector databases for semantic search (OpenSearch, Aurora, Neptune, DocumentDB, RDS PostgreSQL)
   - Knowledge base services: OpenSearch (vector DB), Kendra (intelligent search) - NOT S3 or RDS alone
   - Bedrock Agents for multi-step task automation
   - Customization cost ranking: Pre-training (highest) > Fine-tuning > RAG > In-context learning (lowest)

4. **Prompt Engineering & Advanced Techniques**
   - Techniques: Zero-shot, single-shot, few-shot, chain-of-thought, templates
   - Components: Context, instructions, negative prompts
   - **Prompt Engineering vs Prompt Tuning**: Manual (hard prompts) vs Automated (soft prompts/virtual tokens)
   - Soft prompts: ML-learned embeddings that guide behavior without modifying model weights
   - Best practices: Specific/concise, experimentation, guardrails, multiple comments
   - Risks: Exposure, poisoning, hijacking, jailbreaking

5. **Training & Fine-tuning Foundation Models**
   - **Full Fine-Tuning vs PEFT**: Full updates all parameters (expensive), PEFT updates subset (efficient)
   - **PEFT (Parameter-Efficient Fine-Tuning)**: Ideal for multiple tenants/use cases, mitigates catastrophic forgetting
   - **Catastrophic Forgetting**: Model forgets previous knowledge during fine-tuning, solved by freezing parameters
   - Fine-tuning methods: Instruction tuning, domain adaptation, transfer learning
   - RLHF (Reinforcement Learning from Human Feedback) / Cognitive Apprenticeship
   - Data preparation: Curation, governance, representativeness, labeling
   - Must purchase provisioned throughput for fine-tuned Bedrock models
   - Monitor validation loss/accuracy (not just training loss) to detect overfitting

6. **Foundation Model Evaluation**
   - ROUGE: Summarization tasks, focuses on recall
   - BLEU: Machine translation, evaluates overlap of n-grams (0-1 score)
   - BERTScore: Semantic similarity using embeddings
   - Perplexity: Model prediction confidence, lower = better (common for LLMs)
   - Human evaluation: Insightful but time-consuming
   - Benchmark datasets: Objective, scalable, industry standards
   - Business alignment: Productivity, user engagement, task engineering

7. **Data & Feature Engineering**
   - Data preparation is 70-80% of ML work
   - Feature engineering significantly impacts model performance
   - EDA identifies critical patterns before training
   - Chunking strategies for large datasets

8. **Model Evaluation (Traditional ML)**
   - Choose metrics appropriate to problem type
   - Understand confusion matrix deeply
   - Recognize when accuracy is misleading (imbalanced data)
   - Precision, Recall, F1 Score, AUC-ROC, AUC-PR
   - Regression metrics: MAE, RMSE, R²

9. **AWS Services Selection**
   - Match business problems to appropriate AWS AI services
   - **Vision**: Rekognition (image/video analysis), Rekognition Custom Labels (custom models), Textract (OCR)
   - **Language**: Comprehend (NLP), Translate (machine translation)
   - **Speech**: Transcribe (ASR), Polly (TTS)
   - **Specialized**: Lex (chatbots), Forecast (time-series), Kendra (semantic search), Personalize (recommendations)
   - **Contact Center**: Connect Contact Lens (analytics), Q in Connect (agent assistance), Connect Wisdom (knowledge management)
   - **GenAI**: Amazon Q Business (BI), Amazon Q Developer (code generation)
   - **Security**: CloudTrail Lake (SQL queries on audit logs)

10. **Amazon SageMaker Deep Dive**
   - Comprehensive ML platform for end-to-end workflows
   - Studio (IDE), Pipelines (workflow automation), AutoML/Autopilot (automated tuning)
   - JumpStart (pre-trained models), Data Wrangler (data prep), Feature Store (feature management)
   - Ground Truth (data labeling), Clarify (bias detection), Model Monitor (drift detection)
   - Deployment options: Real-time, Asynchronous, Batch Transform, Serverless
   - Know when to use each deployment type based on latency and traffic patterns
   - Use Bayesian Optimization for hyperparameter tuning (more efficient than Grid/Random Search)

11. **Amazon Bedrock Deep Dive**
   - Fully managed foundation model service with multi-provider support
   - PartyRock: No-code playground for testing models
   - **Amazon Titan Models**: Multimodal Embeddings G1 (text+image embeddings), Text Premier (fine-tunable)
   - **Inference Parameters**: Control model behavior via API (Temperature, Top-k, Top-p)
     - Temperature: Controls creativity/randomness (0=deterministic, 1=creative)
     - Top-k: Limits token pool to k most likely options
     - Top-p: Dynamic cutoff based on cumulative probability
   - **Bedrock Agents**: Automate multi-step workflows with memory and reasoning
   - **Bedrock Guardrails**: Safety barriers for content filtering, PII protection, hallucination prevention
   - **Model Distillation**: Transfer knowledge from large teacher to efficient student model
   - **Prompt Caching**: Reduce latency and costs for repeated/similar queries
   - **Provisioned Throughput**: Required for fine-tuned models, guaranteed capacity
   - Model customization hierarchy: Pre-trained < Prompt Engineering < RAG < Fine-tuning

12. **Algorithms & Model Optimization**
   - **Classification**: SVM (high-dimensional, non-linear data), Binary Classification (two outcomes)
   - **Experimentation**: A/B Testing with multi-model hosting for comparing variants
   - **Sequence Generation**: Beam Search (quality) vs Greedy Search (speed)
   - **Activation Functions**: Softmax (training, probabilities) vs Argmax (inference, selection)
   - **Model Compression**: Pruning (remove parameters), Quantization (reduce precision), Distillation (teacher→student)
   - **Hyperparameter Tuning**: Bayesian Optimization (efficient, learns from past), Grid Search (exhaustive), Random Search
   - Use case: Deploy efficient models on edge devices, reduce costs, faster inference

13. **Responsible AI**
   - Difference between Interpretability (HOW) and Explainability (WHY)
   - Transparency: Access to algorithms, data, processes
   - Understand bias vs variance (underfitting vs overfitting)
   - Know types of bias: Measurement, Sampling, Confirmation, Observer, Training Data, Historical, Algorithmic
   - GenAI risks: Hallucinations, Prompt leaking, Model exposure, IP infringement, Prompt stereotyping
   - AWS tools: Clarify (bias detection, explainability), Ground Truth (labeling), 
     Model Cards (documentation), Model Monitor (drift detection), A2I (human review),
     Bedrock Guardrails (content filtering), FMEval (prompt stereotyping)
   - Human-Centered Design principles

14. **MLOps Best Practices**
   - Continuous monitoring is essential (data drift, bias drift, model drift)
   - Version control for models and data
   - Automate ML workflows with SageMaker Pipelines
   - CI/CD for ML models

15. **Cost Optimization**
   - Understand pricing models (token-based, provisioned throughput, custom models)
   - Customization cost ranking: Pre-training (highest) > Fine-tuning > RAG > In-context learning (lowest)
   - Optimize prompt design for efficiency (minimize tokens)
   - Right-size models for use cases
   - Caching and reuse strategies
   - Monitor usage and costs

16. **Security, Compliance & Governance**
   - IAM best practices: RBAC, ABAC, principle of least privilege, temporary credentials
   - Security services: KMS (encryption), Macie (PII detection), GuardDuty (threat detection), Inspector (vulnerability management)
   - Compliance frameworks: NIST, HIPAA, GDPR, PCI-DSS, ISO 27001/27002, SOC 1/2/3
   - Data governance: Data lineage, cataloging, S3 Object Locking, lifecycle management
   - Application security: OWASP Top 10 for LLM, Bedrock Guardrails, WAF, Shield, Cognito
   - Incident response: NIST SP 800-61 lifecycle (Preparation → Detection → Containment → Eradication → Recovery → Post-Incident)
   - GenAI Security Scoping Matrix: 5 scopes from public consumer apps to self-trained models
   - AI bias types: Algorithmic, confirmation, selection bias - require diverse datasets and continuous monitoring
   - GRC tools: Config, Audit Manager, Trusted Advisor, CloudTrail, Security Hub

---

# B. Keywords & Quick Reference

## Core Concepts

**AI (Artificial Intelligence)**: Technology to mimic human intelligence  
**ML (Machine Learning)**: Systems learn from data, no explicit programming  
**DL (Deep Learning)**: ML using neural networks, complex patterns  
**NLP (Natural Language Processing)**: AI for human-computer language interaction  
**GenAI (Generative AI)**: AI systems create new content from training data  
**FM (Foundation Models)**: Large-scale, general-purpose, pre-trained models  
**LLM (Large Language Models)**: FM specialized in language, transformers, massive datasets  

**Supervised Learning**: Train with labeled data to predict outcomes  
**Unsupervised Learning**: Find patterns in unlabeled data  
**Reinforcement Learning**: Learn optimal actions through rewards/penalties  
**Semi-supervised Learning**: Train with mix of labeled + unlabeled data  
**Self-supervised Learning**: Model generates own labels from data

## Data Types

**Structured Data**: Organized in predefined format  
**Tabular Data**: Organized in rows and columns (databases, spreadsheets)  
**Time Series Data**: Data points indexed by time (graphs N/t)  
**Unstructured Data**: No predefined format or schema  
**Text Data**: Documents, emails, natural language  
**Image Data**: Photos, graphics, visual content  
**Audio Data**: Sound files, speech, music  
**Video Data**: Moving images with audio

## GenAI Concepts

**Tokens**: Individual text units (words, subwords, characters) for LLM processing  
**Tokenization**: Process of breaking text into tokens  
**Chunking**: Breaking large datasets into smaller manageable pieces  
**Context Window**: Maximum tokens LLM can process simultaneously  
**Vectors**: Numerical arrays representing data in n-dimensional space  
**Embeddings**: Vectors trained to encode semantic meaning and relationships  
**Multi-modal Models**: Models handling multiple data types (text, image, audio, video)  
**Diffusion Models**: Generate images using forward/reverse diffusion processes  
**Transformer**: Neural network architecture using attention mechanisms  
**Self-Attention**: Mechanism allowing model to focus on specific input parts by computing attention weights  
**Attention Weights**: Computed for each token vs all others, tells model how much focus to give each token  
**Encoder-Decoder Architecture**: Separate encoder (input processing) and decoder (output generation), excels at summarization and translation  
**Nondeterminism**: Same input can produce different outputs  
**High-Dimensional Data**: Data with many features/variables, requires algorithms like SVM  
**Non-Linear Relationships**: Complex patterns that don't follow straight lines, need sophisticated algorithms

## Responsible AI

**Interpretability**: Understanding HOW model works internally, observe inner workings  
**Explainability**: Understanding WHY specific output generated, post-hoc (SHAP & LIME)  
**Transparency**: Open disclosure about algorithms, data, training processes  
**Fairness**: No unfair impact on subpopulations, diverse balanced datasets  
**Robustness**: Model adapts to challenging conditions, maintains performance  
**Veracity**: Decisions based on accurate real-time information  
**Controllability**: Humans maintain ultimate control over AI systems  
**Environmental Sustainability**: Energy-efficient infrastructure (AWS Trainium, Inferentia)

## Bias & Variance

**Bias**: Gap between predicted and actual values, high bias = underfitting  
**Variance**: Model sensitivity to training data changes, high variance = overfitting  
**Underfitting**: Model too simple, poor performance on training + test data  
**Overfitting**: Model too complex, learns noise, good on training but poor on test  
**Data Augmentation**: Increase dataset size via transformations, preserve labels  
**Balanced Model**: Low bias + low variance, generalizes well to new data  
**Regularization**: Technique to reduce overfitting by penalizing complexity  
**Cross-validation**: Test model performance on multiple data splits

## Types of Bias

**Measurement Bias**: Faulty or inaccurate data capture (uncalibrated devices)  
**Sampling Bias**: Training data unrepresentative of population, imbalanced datasets  
**Confirmation Bias**: Focusing only on data supporting existing beliefs  
**Observer Bias**: Labeler's subjective opinions influence data recording  
**Training Data Bias**: Unequal demographic representation in training data  
**Historical Bias**: Prejudice embedded in historical data  
**Algorithmic Bias**: Model architecture/logic amplifies existing biases

## GenAI Risks

**Hallucinations**: Model generates believable but false content  
**Prompt Leaking**: Model reveals internal instructions or conversation history  
**Model Exposure**: Unintended release of sensitive training data or prompts  
**IP (Intellectual Property) Infringement**: Replicating copyrighted materials from training  
**Prompt Stereotyping**: Model encodes gender/age/ethnicity biases (test with FMEval)  
**Poisoning**: Malicious insertion of false/harmful data during training  
**Hijacking**: Attacker manipulates prompts to divert model behavior  
**Jailbreaking**: Using clever prompts to bypass safety constraints

## FM (Foundation Model) Applications & Inference

**Modality**: Type of data model handles (text, image, audio)  
**Latency**: Model processing speed, low latency = real-time responses  
**Temperature**: Controls randomness/creativity (0-1), low = predictable, high = creative  
**Top-k**: Number of most likely token candidates, lower = more likely outputs  
**Top-p**: Percentage of most likely token candidates for next token  
**RAG (Retrieval-Augmented Generation)**: FM paired with external knowledge source  
**Knowledge Base**: Structured info repository for RAG (company docs, FAQs)  
**Vector Database**: Stores and manages embeddings for similarity search

## Prompt Engineering

**Context**: Background information to frame the task  
**Instructions**: Clear directions setting format/tone/content expectations  
**Negative Prompts**: Explicit guidance on what NOT to include  
**Model Latent Space**: Internal representation of model's knowledge  
**Zero-shot Prompting**: Give task without examples, relies on general knowledge  
**Single-shot Prompting**: Provide ONE example to guide response  
**Few-shot Prompting**: Provide MULTIPLE examples to establish pattern  
**Chain-of-thought Prompting**: Ask model to break problem into logical steps  
**Prompt Templates**: Standardized prompts with placeholders for dynamic content  
**Prompt Engineering**: Manual human-driven approach using hard prompts (natural language)  
**Prompt Tuning**: Automated ML-driven approach using soft prompts (virtual tokens), doesn't modify model weights  
**Hard Prompts**: Natural language instructions manually created by humans  
**Soft Prompts**: Virtual tokens learned via ML, prepended to input, guides behavior without modifying weights  
**Virtual Tokens**: Learned embeddings (not actual words) prepended to input in prompt tuning

## Training & Customization

**Pre-training**: Train model from scratch on vast data, highest cost  
**Fine-tuning**: Customize pre-trained model with task-specific data, moderate cost  
**Full Fine-Tuning**: Update ALL model parameters, high cost, high performance, risk of catastrophic forgetting  
**PEFT (Parameter-Efficient Fine-Tuning)**: Update only small subset of parameters, efficient, lower memory, mitigates catastrophic forgetting  
**Catastrophic Forgetting**: Model forgets previous knowledge when learning new information, common in full fine-tuning  
**Continuous Pre-training**: LLM learns new information while retaining existing knowledge  
**In-context Learning**: Use prompts to influence outputs, no retraining, lowest cost  
**Instruction Tuning**: Further training to follow instructions better  
**Domain Adaptation**: Train general model on industry-specific data (healthcare, finance)  
**Transfer Learning**: Use pre-trained model, fine-tune for related task  
**Data Curation**: Select and organize relevant, accurate, high-quality data  
**Data Governance**: Policies for data quality, accuracy, ethical use, privacy compliance  
**RLHF (Reinforcement Learning from Human Feedback)**: Train models using human guidance (Cognitive Apprenticeship)  
**Reward Model**: Predicts response quality based on human evaluator scores

## Model Compression

**Pruning**: Remove redundant parameters to reduce model size with minimal accuracy loss  
**Quantization**: Reduce weight precision (FP32→FP16→INT8) to decrease memory footprint  
**Knowledge Distillation**: Transfer knowledge from large teacher to small student model for efficiency

## FM (Foundation Model) Evaluation Metrics

**ROUGE (Recall-Oriented Understudy for Gisting Evaluation)**: Measures overlap for summarization, emphasizes recall  
**BLEU (Bilingual Evaluation Understudy)**: Evaluates machine translation, n-grams overlap, score 0-1  
**BERTScore**: Uses embeddings to compare semantic similarity, effective for paraphrasing  
**Perplexity**: Measures how well probability model predicts sample, lower = better, common for LLMs  
**Human Evaluation**: People assess outputs, insightful but subjective and time-consuming  
**Benchmark Datasets**: Pre-built labeled collections to test against industry standards  
**Productivity**: How efficiently model performs tasks with minimal human intervention  
**User Engagement**: Frequency and depth of user interactions with model  
**Task Engineering**: How effectively model completes specific business-aligned tasks

## ML Workflow

**EDA (Exploratory Data Analysis)**: Find patterns, correlations, anomalies before training  
**Correlation Matrix**: Quantify relationships between variables  
**Feature Engineering**: Transform raw data → ML-ready format  
**Feature Selection**: Filter relevant features from dataset  
**Feature Extraction**: Derive new features from existing variables  
**Dimensionality Reduction**: Simplify dataset by combining features  
**PCA (Principal Component Analysis)**: Reduce dimensions, preserve variance  
**Categorical Encoding**: Convert categorical values → numerical format  
**Normalization**: Rescale values to range [0,1]  
**Standardization**: Transform data using mean/std (z-score)  
**Hyperparameters**: Settings before training (learning rate, batch size, epochs)  
**Parameters**: Values learned during training (weights, biases)  
**Grid Search**: Test all possible hyperparameter combinations  
**Random Search**: Randomly sample hyperparameter combinations  
**Active Learning**: Smart sample selection, minimize labeling effort

## Model Evaluation

**TP (True Positive)**: Model correctly predicted positive class  
**TN (True Negative)**: Model correctly predicted negative class  
**FP (False Positive)**: Model incorrectly predicted positive (Type I error)  
**FN (False Negative)**: Model incorrectly predicted negative (Type II error)  
**Confusion Matrix**: Table showing TP, TN, FP, FN for classification evaluation  
**Precision**: TP/(TP+FP), use for fraud detection (minimize false positives)  
**Recall (Sensitivity)**: TP/(TP+FN), use for medical diagnosis (minimize false negatives)  
**F1 Score**: Harmonic mean of precision and recall, balances both metrics  
**AUC-ROC (Area Under Curve - ROC)**: Plots TP rate vs FP rate, measures class distinction ability  
**AUC-PR (Area Under Curve - Precision-Recall)**: Plots Precision vs Recall, better for imbalanced datasets  
**Imbalanced Dataset**: One class significantly over-represented, makes accuracy unreliable  
**MAE (Mean Absolute Error)**: Average absolute differences between predicted and actual  
**RMSE (Root Mean Squared Error)**: Square root of MSE, penalizes larger errors more heavily  
**R² (R-Squared)**: Measures how well predictions fit actual data, ranges 0-1  
**MSE (Mean Squared Error)**: Average of squared differences between predicted and actual  
**Training Loss**: Error on training data, can be misleading if overfitting  
**Validation Loss**: Error on validation data, better indicator of generalization, detect overfitting when it increases  
**Validation Output Accuracy**: Key metric for determining optimal epochs, measures performance on unseen data

## AWS AI Services

**Rekognition**: Analyze images/videos for face detection, object recognition, content moderation  
**Rekognition Custom Labels**: Train custom image recognition models with labeled data  
**Textract**: OCR to extract text/data from documents, understands forms/tables  
**Comprehend**: NLP service for text analysis, sentiment, entity recognition, tokenization, POS  
**Translate**: Neural machine translation service supporting 75+ languages  
**Transcribe**: ASR to convert speech-to-text with custom vocabulary support  
**Polly**: TTS service converts text to lifelike voices in multiple languages  
**Lex**: Build conversational interfaces and chatbots  
**Forecast**: Time-series forecasting using historical data  
**Kendra**: Intelligent enterprise search using semantic search and NLP  
**Personalize**: Real-time personalized recommendations using Recipes (pre-built algorithms)  
**Amazon Q Business**: BI assistant for dashboard generation and executive summaries  
**Amazon Q Developer**: AI assistant for code generation and development automation

## AWS Contact Center Services

**Amazon Connect Contact Lens**: Real-time analytics, sentiment analysis, transcription for contact centers  
**Amazon Q in Connect**: GenAI assistant providing real-time agent guidance and post-call documentation automation  
**Amazon Connect Wisdom**: Knowledge management service with real-time article recommendations for agents

## Amazon Bedrock

**Bedrock**: Fully managed FM service with API access, no infrastructure management  
**PartyRock**: Interactive Bedrock playground for testing models without code  
**Bedrock Agents**: Automate multi-step workflows with memory retention and action schemas  
**Bedrock Guardrails**: Safety barriers filtering offensive content, PII, hallucinations, and prompt attacks  
**Bedrock Model Distillation**: Transfer knowledge from larger teacher model to smaller student model for efficiency  
**Bedrock Prompt Caching**: Cache prompts to reduce latency and costs for repeated similar queries  
**Provisioned Throughput**: Reserved dedicated capacity with predictable costs, required for fine-tuned Bedrock models  
**Amazon Titan Multimodal Embeddings G1**: Generate embeddings for text AND images for multimodal search  
**Amazon Titan Text Premier**: Foundation model on Bedrock that can be fine-tuned for specific tasks

## Amazon SageMaker

### SageMaker Development & Training

**Studio**: ML IDE with Jupyter notebooks, provides unified workspace for ML development  
**Pipelines**: Design and automate ML workflows with CI/CD and version control  
**AutoML (Autopilot)**: Automates model selection and hyperparameter tuning with minimal intervention  
**JumpStart**: Pre-trained models and FMs with one-click deployment templates  
**Data Wrangler**: Transform raw data to ML-ready format with 300+ built-in transformations  
**Feature Store**: Centralized repository for storing, managing, and sharing ML features  
**AMT (Automatic Model Tuning)**: Automates hyperparameter optimization process

### SageMaker Data & Model Management

**Ground Truth**: Data labeling service with human-in-the-loop annotation and active learning  
**Ground Truth Plus**: Provides subject matter experts for complex labeling tasks  
**Model Cards**: Documents model purpose, risks, limitations, ethics, and performance metrics  
**Model Monitor**: Continuously monitors deployed models, detects drift (data, bias, performance)

### SageMaker Deployment Options

**Synchronous (Real-time)**: Instant response with low latency (<100ms) for chatbots/fraud/recommendations  
**Asynchronous**: Background processing with variable response time for large files/images/videos  
**Batch Transform**: Process entire datasets asynchronously, cost-effective for overnight processing  
**Serverless**: Auto-scales to zero when idle, pay-per-use for sporadic traffic and prototypes  
**Endpoints**: Infrastructure for serving deployed models  
**Auto-scaling**: Automatically adjusts capacity based on traffic

### SageMaker Responsible AI

**Clarify**: Detects bias in datasets/models, provides explainability (WHY) using SHAP/LIME  
**A2I (Amazon Augmented AI)**: Combines AI with human review via random sampling or confidence threshold triggers

## Responsible AI Tools & Methods

**PII (Personally Identifiable Information)**: Sensitive personal data like SSN, address, phone number  
**FMEval (Foundation Model Evaluations)**: Library to test FMs, includes Prompt Stereotyping detection  
**SHAP (SHapley Additive exPlanations)**: Post-hoc method explaining predictions via feature importance  
**LIME (Local Interpretable Model-agnostic Explanations)**: Post-hoc method explaining individual local predictions

## Algorithms & Techniques

**SVM (Support Vector Machine)**: Classification algorithm for high-dimensional data with non-linear relationships, effective for binary classification  
**K-Means Clustering**: Unsupervised algorithm partitioning data into K clusters, minimizes within-cluster variance  
**Linear Regression**: Supervised learning for continuous predictions, models linear relationships  
**PCA (Principal Component Analysis)**: Reduces dimensionality while preserving variance  
**Apriori (Association Rule Mining)**: Discovers relationships in transactional data for market basket analysis  
**Decision Trees**: High interpretability model with flow chart structure, easy to visualize  
**Neural Networks**: Low interpretability "black box" model with high performance  
**Random Forests**: Ensemble of decision trees, reduces overfitting while maintaining performance  
**Binary Classification**: Two-class classification (yes/no, fraud/not fraud, churn/not churn)  
**A/B Testing**: Controlled experiment comparing model variants on predefined metrics  
**Multi-Model Hosting**: Host multiple model variants simultaneously for experimentation  
**Beam Search**: Decoding strategy exploring multiple paths simultaneously for better sequence generation quality  
**Greedy Search**: Select most probable token at each step, faster but may miss better sequences  
**Softmax**: Activation function converting logits to probability distribution, used during training  
**Argmax**: Select index with highest probability, used during inference for classification  
**Prompt Augmentation**: Core RAG step enriching user query with retrieved document context  
**Reranking**: Post-retrieval step refining results based on semantic similarity to enhance relevance and variety  
**Bayesian Optimization**: Advanced hyperparameter tuning using probabilistic model, learns from past evaluations  
**Gradient Descent**: Algorithm for training model parameters (NOT for hyperparameter tuning)

## MLOps

**MLOps (Machine Learning Operations)**: Practices for managing ML lifecycle with automation, consistency, version control  
**Data Drift**: When incoming production data differs significantly from training data  
**Bias Drift**: When model starts favoring certain groups over time  
**Feature Drift**: When feature distributions change in production environment  
**Model Drift**: When model performance degrades over time  
**CI/CD (Continuous Integration/Continuous Deployment)**: Automated integration and deployment pipelines for ML models

## Cost & Business Metrics

**Token-Based Pricing**: Pay per token processed (input tokens + output tokens)  
**Provisioned Throughput**: Reserved dedicated capacity with predictable costs for high-volume workloads  
**Custom Models Pricing**: Costs for fine-tuning, training, and storing custom model artifacts  
**ARPU (Average Revenue per User)**: Financial metric indicating revenue generation effectiveness per user  
**CLV (Customer Lifetime Value)**: Long-term value of AI impact on customer relationships  
**Conversion Rate**: Percentage of users taking desired actions, measures business impact  
**Efficiency**: Resource utilization metrics (compute, memory, time)  
**Accuracy**: Percentage of correct predictions or quality of generated content  
**CSAT (Customer Satisfaction)**: User satisfaction metric from surveys  
**ROI (Return on Investment)**: Financial return from AI investment  
**Response Time**: Model latency metric  
**Training Sessions**: Number of ML model training iterations

## Human-Centered Design

**HCD (Human-Centered Design)**: Methodology putting users at center to ensure effective, aligned AI  
**Cognitive Apprenticeship**: AI learns from human feedback through RLHF process  
**Amplified Decision-Making**: AI assists humans to make better choices with clarity/simplicity/usability  
**Subgroup Analysis**: Examine model performance across different demographic groups and protected attributes

## Security, Compliance & Governance

**RBAC (Role-Based Access Control)**: Permissions based on job function  
**ABAC (Attribute-Based Access Control)**: Fine-grained control using tags  
**Principle of Least Privilege**: Grant minimal access needed  
**PII (Personally Identifiable Information)**: Data uniquely identifying individuals  
**PHI (Protected Health Information)**: PII subset, medical records  
**NIST**: US govt standards (SP 800 series, AI Risk Management Framework)  
**HIPAA**: US regulation for PHI protection  
**GDPR**: EU regulation for PII protection, global applicability  
**PCI-DSS**: Payment card security standard  
**ISO/IEC 27001**: ISMS requirements, certification  
**ISO/IEC 27002**: ISMS guidelines/best practices  
**SOC 1/2/3**: Audit reports (financial/trust services/public summary)  
**Data Lineage**: Track data history from collection to AI system use  
**Data Residency**: Server geolocation compliance (GDPR requirement)  
**Data Sovereignty**: Legal governance within nation borders  
**OWASP Top 10 for LLM**: Prompt injection, insecure output handling, training data poisoning  
**NIST SP 800-61**: Incident Response Lifecycle (6 phases)  
**GenAI Security Scoping Matrix**: 5 scopes (consumer app to self-trained model)  
**Algorithmic Bias**: Discriminatory AI outcomes  
**Confirmation Bias**: Training data reinforces stereotypes  
**Selection Bias**: Training data doesn't represent population  
**EU AI Act**: First comprehensive AI legal framework  
**NYC Automated Decision Systems Law**: AI bias protection

## AWS Security Services

**IAM (Identity and Access Management)**: Manage users, roles, groups access to AWS resources  
**KMS (Key Management Service)**: Create, store, manage cryptographic keys for encryption  
**CloudHSM**: Dedicated hardware for cryptographic operations (FedRAMP compliance)  
**Amazon Macie**: Discover, classify PII in S3 using ML and RegEx identifiers  
**AWS PrivateLink**: Private VPC connectivity, avoids public internet  
**Amazon GuardDuty**: AI/ML-based threat detection, anomaly identification  
**Amazon Inspector**: Vulnerability management with risk scoring  
**Amazon Detective**: Security incident investigation, root cause analysis  
**AWS Config**: Track configuration changes, detect misconfigurations  
**AWS Audit Manager**: Continual GRC auditing, evidence gathering  
**AWS Trusted Advisor**: Well-Architected Framework alignment, remediation recommendations  
**AWS CloudTrail**: Log all API activity (users and services)  
**CloudTrail Lake**: Managed data lake for CloudTrail events with SQL-based querying for audit trail analysis  
**AWS Security Hub**: Centralized security dashboard, SIEM integration, SOAR workflows, CSPM  
**AWS WAF**: Web Application Firewall for Layer 7 protection  
**AWS Shield**: DDoS protection, Shield Advanced with DDoS Response Team  
**Amazon Cognito**: Customer identity management, adaptive protections (bot detection, risk-based auth)  
**S3 Object Locking**: WORM model (Write-Once-Read-Many), compliance/governance modes, legal holds  
**AWS Backup**: Disaster recovery, business continuity
**AWS Artifact**: Access compliance documents, reports, certifications

## Infrastructure & Governance

**Model Versioning**: Track changes to models over time for reproducibility  
**Audit Trails**: Maintain records of model decisions and changes for compliance  
**Open-Source Models**: Publicly available model architecture, training methods, and datasets  
**Open Data Licensing**: Clear rules defining how datasets can be used and shared  
**Hugging Face**: Repository platform for NLP models and transformers  
**Kaggle**: Hub for datasets, ML competitions, and community collaboration  
**AWS Trainium**: Specialized hardware optimized for ML model training with energy efficiency  
**AWS Inferentia**: Specialized hardware optimized for inference/production workloads with energy efficiency
