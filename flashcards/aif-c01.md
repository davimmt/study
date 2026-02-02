# Flashcards

## Set 1: Core Concepts

**Q1:** What is the difference between AI, ML, and DL?

<details>
<summary>Show Answer</summary>

AI = computers mimic human intelligence; ML = computers learn from data (subset of AI); DL = neural networks-based learning (subset of ML)

</details>

**Q2:** What is a Foundation Model?

<details>
<summary>Show Answer</summary>

A general-purpose, large-scale pre-trained model that serves as a blueprint for various downstream tasks

</details>

**Q3:** What distinguishes an LLM from general ML models?

<details>
<summary>Show Answer</summary>

LLMs are specialized deep learning models using transformers and massive datasets specifically for understanding and generating human language

</details>

---

## Set 2: ML Types & Learning

**Q4:** When should you use supervised learning?

<details>
<summary>Show Answer</summary>

When you have labeled data and need to predict specific outputs (classification or regression)

</details>

**Q5:** What's the difference between classification and regression?

<details>
<summary>Show Answer</summary>

Classification predicts discrete categories/classes; regression predicts continuous numerical values

</details>

**Q6:** What is reinforcement learning best suited for?

<details>
<summary>Show Answer</summary>

Problems requiring trial-and-error learning with reward/penalty feedback (e.g., game playing, robotics)

</details>

**Q7:** Give an example use case for unsupervised learning

<details>
<summary>Show Answer</summary>

Customer segmentation (clustering), fraud detection (anomaly detection), or discovering hidden patterns in unlabeled data

</details>

---

## Set 3: Feature Engineering

**Q8:** What is feature engineering and why is it important?

<details>
<summary>Show Answer</summary>

Transforming raw data into ML-friendly format by selecting and creating features; critical because it significantly impacts model performance

</details>

**Q9:** What's the difference between normalization and standardization?

<details>
<summary>Show Answer</summary>

Normalization rescales values to [0,1]; standardization transforms data using mean and standard deviation (z-score)

</details>

**Q10:** Why convert categorical variables to numerical format?

<details>
<summary>Show Answer</summary>

Most ML algorithms require numerical input to perform mathematical operations

</details>

---

## Set 4: Parameters & Training

**Q11:** What's the difference between parameters and hyperparameters?

<details>
<summary>Show Answer</summary>

Parameters are learned automatically during training (e.g., weights); hyperparameters are set manually before training (e.g., learning rate)

</details>

**Q12:** Name three common hyperparameters

<details>
<summary>Show Answer</summary>

Learning rate, batch size, number of epochs

</details>

**Q13:** What are three methods for hyperparameter optimization?

<details>
<summary>Show Answer</summary>

Grid search (exhaustive), random search (sampling), AWS SageMaker Automatic Model Tuning

</details>

---

## Set 5: Model Evaluation - Classification

**Q14:** What is a confusion matrix?

<details>
<summary>Show Answer</summary>

A table showing TP, TN, FP, FN to evaluate classification model performance

</details>

**Q15:** When is accuracy a misleading metric?

<details>
<summary>Show Answer</summary>

In imbalanced datasets where one class is significantly over-represented

</details>

**Q16:** What's the formula for precision and when is it prioritized?

<details>
<summary>Show Answer</summary>

Precision = TP/(TP+FP); prioritized in fraud detection to minimize false alarms

</details>

**Q17:** What's the formula for recall and when is it prioritized?

<details>
<summary>Show Answer</summary>

Recall = TP/(TP+FN); prioritized when missing positives is costly (e.g., disease diagnosis)

</details>

**Q18:** What does F1 Score balance?

<details>
<summary>Show Answer</summary>

F1 Score is the harmonic mean of precision and recall, balancing both metrics

</details>

**Q19:** What does AUC-ROC measure?

<details>
<summary>Show Answer</summary>

A model's ability to distinguish between classes by plotting TP rate vs FP rate; closer to 1.0 is better

</details>

**Q20:** What is AUC-PR and when is it preferred over AUC-ROC?

<details>
<summary>Show Answer</summary>

AUC-PR plots Precision vs Recall; more informative than AUC-ROC for imbalanced datasets as it focuses on positive class performance

</details>

---

## Set 6: Model Evaluation - Regression

**Q21:** What's the difference between MAE and RMSE?

<details>
<summary>Show Answer</summary>

MAE is the mean absolute error (same scale); RMSE is root mean squared error (penalizes larger errors more heavily)

</details>

**Q22:** What does R² (R-squared) measure?

<details>
<summary>Show Answer</summary>

How well model predictions fit actual data; ranges 0-1; closer to 1 indicates better fit

</details>

**Q23:** When would you prefer RMSE over MAE?

<details>
<summary>Show Answer</summary>

When you want to penalize large errors more heavily than small errors

</details>

---

## Set 7: Model Fit & Quality

**Q24:** What is overfitting?

<details>
<summary>Show Answer</summary>

When a model learns training data too well (including noise), performing poorly on new data

</details>

**Q25:** What is underfitting?

<details>
<summary>Show Answer</summary>

When a model doesn't learn enough from training data, performing poorly on both training and test data

</details>

**Q26:** Name three types of bias in ML

<details>
<summary>Show Answer</summary>

Training data bias, historical bias, algorithmic bias

</details>

---

## Set 8: MLOps

**Q27:** What is MLOps?

<details>
<summary>Show Answer</summary>

Set of practices for managing the ML lifecycle with automation, consistency, reliability, and version control

</details>

**Q28:** What should be monitored after model deployment?

<details>
<summary>Show Answer</summary>

Data quality, feature drift, bias drift, and model performance degradation

</details>

---

## Set 9: AWS Vision & Language Services

**Q29:** What does Amazon Rekognition do?

<details>
<summary>Show Answer</summary>

Analyzes images and videos for face detection, object recognition, and content moderation

</details>

**Q30:** What's the difference between Textract and Rekognition?

<details>
<summary>Show Answer</summary>

Textract extracts text/data from documents (OCR); Rekognition analyzes visual content

</details>

**Q31:** What is Amazon Comprehend used for?

<details>
<summary>Show Answer</summary>

NLP service for text analysis, classification, sentiment analysis, and entity recognition

</details>

**Q32:** Differentiate Amazon Transcribe and Amazon Polly

<details>
<summary>Show Answer</summary>

Transcribe = speech-to-text (ASR); Polly = text-to-speech (TTS)

</details>

---

## Set 10: AWS Specialized AI Services

**Q33:** What three services can Amazon Lex integrate with?

<details>
<summary>Show Answer</summary>

Amazon Connect, Amazon Comprehend, and other AWS services for building chatbots

</details>

**Q34:** What does Amazon Forecast do?

<details>
<summary>Show Answer</summary>

Time-series forecasting using historical data to predict future trends

</details>

**Q35:** How does Amazon Kendra differ from traditional search?

<details>
<summary>Show Answer</summary>

Kendra uses NLP for semantic search to deliver accurate, contextually relevant answers vs keyword matching

</details>

**Q36:** What are "Recipes" in Amazon Personalize?

<details>
<summary>Show Answer</summary>

Pre-built algorithms that generate personalized recommendations based on user activity

</details>

---

## Set 11: SageMaker Core Components

**Q37:** What is Amazon SageMaker Studio?

<details>
<summary>Show Answer</summary>

Integrated Development Environment (IDE) providing unified workspace for the entire ML workflow

</details>

**Q38:** What does SageMaker Pipelines do?

<details>
<summary>Show Answer</summary>

Designs, orchestrates, and automates ML workflows with version control and CI/CD capabilities

</details>

**Q39:** What is SageMaker AutoML (Autopilot)?

<details>
<summary>Show Answer</summary>

Automates model selection and hyperparameter tuning with minimal manual intervention

</details>

---

## Set 12: SageMaker Data Services

**Q40:** What is SageMaker Data Wrangler used for?

<details>
<summary>Show Answer</summary>

Transforming raw data into ML-ready format with 300+ built-in transformations, supporting tabular, image, text, and time series data

</details>

**Q41:** What data sources does Data Wrangler support?

<details>
<summary>Show Answer</summary>

Amazon S3, Athena, and Redshift

</details>

**Q42:** What is SageMaker Feature Store?

<details>
<summary>Show Answer</summary>

Centralized repository for storing, managing, and sharing ML features across teams and models

</details>

**Q43:** What's the relationship between Data Wrangler and Feature Store?

<details>
<summary>Show Answer</summary>

Data Wrangler can prepare features and store them in Feature Store for reuse

</details>

---

## Set 13: SageMaker Deployment

**Q44:** What are the four SageMaker deployment options?

<details>
<summary>Show Answer</summary>

Real-time endpoints (synchronous), asynchronous inference, batch transform, serverless inference

</details>

**Q45:** When should you use synchronous inference?

<details>
<summary>Show Answer</summary>

For chatbots, recommendations, fraud detection requiring instant response with low latency and predictable traffic

</details>

**Q46:** When is asynchronous inference appropriate?

<details>
<summary>Show Answer</summary>

Processing large files, images, videos, or complex models with unpredictable workloads and variable response time

</details>

**Q47:** What's the use case for Batch Transform?

<details>
<summary>Show Answer</summary>

Processing large datasets asynchronously (e.g., overnight) where high latency is acceptable

</details>

**Q48:** When should you choose serverless inference?

<details>
<summary>Show Answer</summary>

Sporadic traffic, prototypes, development phases, or unpredictable usage patterns requiring auto-scaling

</details>

---

## Set 14: SageMaker Advanced Tools

**Q49:** What is SageMaker Ground Truth?

<details>
<summary>Show Answer</summary>

Data labeling service using human-in-the-loop annotation with active learning to reduce costs

</details>

**Q50:** What does SageMaker Clarify detect?

<details>
<summary>Show Answer</summary>

Bias in datasets and models, plus provides model explainability and feature importance analysis

</details>

**Q51:** What does SageMaker Model Monitor track?

<details>
<summary>Show Answer</summary>

Data quality issues, feature drift, bias drift, and model performance degradation in deployed models

</details>

---

## Set 15: Algorithms

**Q52:** What is K-Means Clustering?

<details>
<summary>Show Answer</summary>

Unsupervised algorithm that partitions data into K clusters by minimizing within-cluster variance

</details>

**Q53:** What is PCA used for?

<details>
<summary>Show Answer</summary>

Principal Component Analysis reduces dimensionality while preserving variance for visualization and preprocessing

</details>

**Q54:** What is Association Rule Mining used for?

<details>
<summary>Show Answer</summary>

Discovering relationships in transactional data, commonly in market basket analysis (e.g., Apriori algorithm)

</details>

---

## Set 16: ML Lifecycle

**Q55:** List the ML lifecycle phases in order

<details>
<summary>Show Answer</summary>

Fetch → Clean → Prepare → Train/Tune → Evaluate → Deploy → Monitor (with feedback loop)

</details>

**Q56:** What happens during the Evaluate phase?

<details>
<summary>Show Answer</summary>

Apply explainability techniques and measure prediction accuracy using appropriate metrics

</details>

**Q57:** What is Exploratory Data Analysis (EDA)?

<details>
<summary>Show Answer</summary>

Identifying patterns, correlations, and anomalies before training through visualization and feature summarization

</details>

---

## Set 17: Practical Scenarios

**Q58:** You need real-time fraud detection with <100ms latency. Which SageMaker deployment?

<details>
<summary>Show Answer</summary>

Real-time endpoints (synchronous inference)

</details>

**Q59:** You need to process 1M images overnight. Which SageMaker deployment?

<details>
<summary>Show Answer</summary>

Batch Transform

</details>

**Q60:** Which AWS service would you use to add search to internal company documents?

<details>
<summary>Show Answer</summary>

Amazon Kendra

</details>

**Q61:** You need to build a customer service chatbot. Which AWS service?

<details>
<summary>Show Answer</summary>

Amazon Lex (can integrate with Comprehend and Connect)

</details>

**Q62:** You need to detect bias in your ML model before deployment. Which tool?

<details>
<summary>Show Answer</summary>

Amazon SageMaker Clarify

</details>

**Q63:** You need to monitor model performance after deployment. Which tool?

<details>
<summary>Show Answer</summary>

Amazon SageMaker Model Monitor

</details>

---

## Set 18: Best Practices

**Q64:** Why is monitoring important after model deployment?

<details>
<summary>Show Answer</summary>

To detect data quality issues, feature/bias/model drift, and performance degradation

</details>

**Q65:** What percentage of ML work is typically data preparation?

<details>
<summary>Show Answer</summary>

70-80% of ML work involves data preparation and feature engineering

</details>

**Q66:** When should you use Grid Search vs Random Search for hyperparameter tuning?

<details>
<summary>Show Answer</summary>

Grid Search for small hyperparameter spaces (exhaustive); Random Search for large spaces (more efficient)

</details>

---

## Set 19: Integration & Architecture

**Q67:** Which SageMaker component automates the entire ML workflow?

<details>
<summary>Show Answer</summary>

SageMaker Pipelines

</details>

**Q68:** How does SageMaker AutoML promote transparency?

<details>
<summary>Show Answer</summary>

By generating notebook code showing the model selection and tuning process

</details>

**Q69:** What format does Data Wrangler support for queries?

<details>
<summary>Show Answer</summary>

SQL queries for data transformation and preparation

</details>

---

## Set 20: Certification Focus

**Q70:** What's the relationship between precision and recall?

<details>
<summary>Show Answer</summary>

Inverse relationship - improving precision often decreases recall and vice versa; F1 Score balances both

</details>

**Q71:** When evaluating a medical diagnosis model, which metric is most critical?

<details>
<summary>Show Answer</summary>

Recall (sensitivity) - to minimize false negatives (missing actual positive cases)

</details>

**Q72:** What's the key consideration when choosing between AWS AI services?

<details>
<summary>Show Answer</summary>

Match the business problem and use case to the appropriate service based on data type, latency requirements, and desired outcome

</details>

**Q73:** What makes a dataset "imbalanced"?

<details>
<summary>Show Answer</summary>

One class is significantly more represented than others, making accuracy an unreliable metric

</details>

---

## Set 21: Generative AI Fundamentals

**Q74:** What are tokens in the context of LLMs?

<details>
<summary>Show Answer</summary>

Individual units of text (words, subwords, or characters) that LLMs process; text is broken down into tokens for model input

</details>

**Q75:** What is chunking in GenAI?

<details>
<summary>Show Answer</summary>

Breaking large datasets into smaller, manageable pieces to enable efficient processing of extensive information

</details>

**Q76:** What is a context window?

<details>
<summary>Show Answer</summary>

The maximum number of tokens an LLM can process at once; determines how much information the model can consider simultaneously

</details>

**Q77:** What's the difference between vectors and embeddings?

<details>
<summary>Show Answer</summary>

Vectors are numerical arrays in n-dimensional space; embeddings are specially trained vectors that encode semantic meaning and capture relationships between words/concepts

</details>

**Q78:** What are the stages of the Foundation Model Lifecycle?

<details>
<summary>Show Answer</summary>

Data Selection → Model Selection → Pre-training → Fine-tuning → Evaluation → Deployment → Feedback (loop back)

</details>

---

## Set 22: GenAI Models & Advantages

**Q79:** What are multi-modal models?

<details>
<summary>Show Answer</summary>

Extension of foundation models that can handle and integrate multiple data types (text, images, audio, video) for cross-modal understanding

</details>

**Q80:** What are diffusion models used for?

<details>
<summary>Show Answer</summary>

Primarily for high-quality image generation; work through forward and reverse diffusion processes to transform noisy images into clear outputs

</details>

**Q81:** Name three advantages of Generative AI

<details>
<summary>Show Answer</summary>

Adaptability (fine-tune for various tasks), Responsiveness (contextually relevant outputs), Simplicity (minimal prompt engineering needed)

</details>

**Q82:** What are three key challenges of Generative AI?

<details>
<summary>Show Answer</summary>

Hallucinations (plausible but incorrect info), Lack of Interpretability (black box nature), Nondeterminism (same input may produce different outputs)

</details>

---

## Set 23: Interpretability vs Explainability

**Q83:** What is Interpretability in AI?

<details>
<summary>Show Answer</summary>

Understanding HOW the model works internally; the degree to which humans can understand the internal mechanics and observe how inputs transform to outputs

</details>

**Q84:** What is Explainability in AI?

<details>
<summary>Show Answer</summary>

Understanding WHY a specific output was generated; uses post-hoc methods (SHAP, LIME) to explain predictions even if model is complex

</details>

**Q85:** A company must ensure it has a mechanism to observe the inner workings of a model understandable to humans. What is this concept?

<details>
<summary>Show Answer</summary>

Interpretability (NOT Explainability) - focuses on understanding the model's internal mechanics and decision-making process

</details>

**Q86:** What is Transparency in AI?

<details>
<summary>Show Answer</summary>

Being open about algorithms used, training data/processes, and decision-making criteria; enables interpretability

</details>

**Q87:** Which models have high interpretability and which have low?

<details>
<summary>Show Answer</summary>

High: Decision trees (easy to visualize, understand HOW). Low: Neural networks (black box, use explainability techniques to understand WHY)

</details>

---

## Set 24: Responsible AI & Bias Types

**Q88:** Name four types of bias in ML

<details>
<summary>Show Answer</summary>

Measurement bias (faulty data), Sampling bias (unrepresentative data), Confirmation bias (selective evidence), Observer bias (subjective influence)

</details>

**Q89:** What is sampling bias?

<details>
<summary>Show Answer</summary>

When training data is not representative of the entire population; causes model to fail on underrepresented groups

</details>

**Q90:** What is observer bias?

<details>
<summary>Show Answer</summary>

When the person collecting/labeling data allows their subjective opinions to influence how they record or interpret the data

</details>

**Q91:** What's the difference between high bias and high variance?

<details>
<summary>Show Answer</summary>

High bias = underfitting (too simple, poor on both training and test); High variance = overfitting (too complex, learns noise, poor on test data)

</details>

**Q92:** How do you fix underfitting?

<details>
<summary>Show Answer</summary>

Increase number of features, use more complex model (decision trees, random forests, neural networks), train longer

</details>

**Q93:** How do you fix overfitting?

<details>
<summary>Show Answer</summary>

Select fewer relevant features, get more training data, use data augmentation (artificially increase dataset by transforming existing data)

</details>

---

## Set 25: GenAI Risks

**Q94:** What are hallucinations in GenAI?

<details>
<summary>Show Answer</summary>

When GenAI creates believable but untrue content; AI predicts patterns without understanding, so always double-check responses

</details>

**Q95:** What is prompt leaking?

<details>
<summary>Show Answer</summary>

When the model discloses context/history of prior interactions or reveals internal instructions and system prompts

</details>

**Q96:** What is model exposure?

<details>
<summary>Show Answer</summary>

Unintended release of sensitive/confidential information from training data or previous prompts

</details>

**Q97:** What is IP infringement risk in GenAI?

<details>
<summary>Show Answer</summary>

Models trained on copyrighted materials may accidentally replicate copyrighted work, leading to legal issues

</details>

---

## Set 26: AWS GenAI Services

**Q98:** What is Amazon Bedrock?

<details>
<summary>Show Answer</summary>

Fully managed foundation model service; access pre-trained GenAI models via API without infrastructure management; supports multiple FM providers

</details>

**Q99:** What is PartyRock?

<details>
<summary>Show Answer</summary>

Interactive playground within Amazon Bedrock to test models and configurations without code

</details>

**Q100:** What does Amazon Q Business do?

<details>
<summary>Show Answer</summary>

AI assistant for business intelligence with QuickSight; generates dashboards, executive summaries, and data stories using natural language

</details>

**Q101:** What does Amazon Q Developer do?

<details>
<summary>Show Answer</summary>

Code generation and assistance, automation of development tasks, integration with development workflows to accelerate software development

</details>

**Q102:** What is SageMaker JumpStart?

<details>
<summary>Show Answer</summary>

Quick-start ML development with built-in algorithms, pre-trained models, access to foundation models, and one-click deployment templates

</details>

---

## Set 27: Responsible AI Tools

**Q103:** What does SageMaker Clarify provide?

<details>
<summary>Show Answer</summary>

Detects bias in data and predictions; provides explainability (WHY predictions made) using post-hoc methods; visualizes feature importance

</details>

**Q104:** What is SageMaker Ground Truth used for?

<details>
<summary>Show Answer</summary>

Data labeling with mix of human labelers and machine assistance; Ground Truth Plus uses subject matter experts for complex tasks

</details>

**Q105:** What are SageMaker Model Cards?

<details>
<summary>Show Answer</summary>

Documentation tool for model details: purpose, risk ratings, limitations, ethical considerations, and performance metrics

</details>

**Q106:** What is Amazon Augmented AI (A2I)?

<details>
<summary>Show Answer</summary>

Combines AI speed with human accuracy; triggers human review based on random sampling or low confidence scores (e.g., <50%)

</details>

**Q107:** What do Bedrock Guardrails protect against?

<details>
<summary>Show Answer</summary>

Offensive language, biased content, PII (block or mask), hallucinations, prompt attacks, denied topics, and profanity

</details>

**Q108:** What evaluation type tests if an LLM encodes biases about gender, age, or ethnicity?

<details>
<summary>Show Answer</summary>

Prompt Stereotyping (uses FMEval library to test if model treats people differently based on demographic characteristics)

</details>

---

## Set 28: Cost Optimization & Pricing

**Q109:** What are the three main GenAI pricing strategies?

<details>
<summary>Show Answer</summary>

Token-based pricing (pay per token processed), Provisioned throughput (reserve dedicated capacity), Custom models (fine-tuning and training costs)

</details>

**Q110:** When should you use token-based pricing?

<details>
<summary>Show Answer</summary>

For variable usage that scales with actual consumption; common for API-based services; costs vary by model size and complexity

</details>

**Q111:** When should you use provisioned throughput?

<details>
<summary>Show Answer</summary>

For consistent high-volume workloads needing predictable performance and costs; guaranteed availability with reserved capacity

</details>

**Q112:** Name three cost optimization strategies for GenAI

<details>
<summary>Show Answer</summary>

Choose appropriate model size for task, minimize token usage with concise prompts, cache frequent queries and reuse embeddings

</details>

---

## Set 29: Business Metrics for AI

**Q113:** What does Efficiency measure in AI systems?

<details>
<summary>Show Answer</summary>

Resource utilization (compute, memory, time); measures operational cost-effectiveness

</details>

**Q114:** What is Conversion Rate in AI context?

<details>
<summary>Show Answer</summary>

Percentage of users taking desired actions; measures business impact of AI implementations

</details>

**Q115:** What is Customer Lifetime Value (CLV)?

<details>
<summary>Show Answer</summary>

Long-term value of AI impact on customer relationships; measures sustained business benefits

</details>

**Q116:** What is ARPU in AI metrics?

<details>
<summary>Show Answer</summary>

Average Revenue per User; financial metric tied to monetization indicating revenue generation effectiveness

</details>

---

## Set 30: AWS Contact Center Services

**Q117:** What is Amazon Connect Contact Lens?

<details>
<summary>Show Answer</summary>

Provides real-time analytics, sentiment analysis, and transcription for contact center interactions to enhance GenAI outputs

</details>

**Q118:** What is Amazon Q in Connect?

<details>
<summary>Show Answer</summary>

Generative AI assistant embedded in Amazon Connect that provides real-time guidance for agents and automates post-call documentation

</details>

**Q119:** What is Amazon Connect Wisdom?

<details>
<summary>Show Answer</summary>

Knowledge management service integrated with Amazon Connect that provides real-time article recommendations for agents

</details>

---

## Set 31: AWS Advanced Services

**Q120:** What is CloudTrail Lake?

<details>
<summary>Show Answer</summary>

Managed data lake for storing and querying CloudTrail events using SQL; enables audit trail analysis for compliance and investigation

</details>

**Q121:** What is Amazon Titan Multimodal Embeddings G1?

<details>
<summary>Show Answer</summary>

ML model that generates embeddings for both text AND images, enabling multimodal search capabilities (search by text or image)

</details>

**Q122:** What is Amazon Titan Text Premier?

<details>
<summary>Show Answer</summary>

Foundation model on Bedrock that can be fine-tuned for specific tasks; requires provisioned throughput for fine-tuned versions

</details>

**Q123:** What is Amazon OpenSearch Serverless?

<details>
<summary>Show Answer</summary>

Serverless version of OpenSearch Service for search and analytics workloads with no infrastructure management

</details>

---

## Set 32: Classification Algorithms

**Q124:** What is Support Vector Machine (SVM)?

<details>
<summary>Show Answer</summary>

Powerful classification algorithm that handles high-dimensional data and non-linear relationships; effective for binary classification like churn prediction

</details>

**Q125:** What is Binary Classification?

<details>
<summary>Show Answer</summary>

Classification task with exactly two possible outcomes (e.g., churn: yes/no, fraud: yes/no, spam: yes/no)

</details>

**Q126:** When should you use SVM?

<details>
<summary>Show Answer</summary>

When data is well-separated, has high dimensions, or contains non-linear relationships; examples: fraud detection, churn prediction, image classification

</details>

---

## Set 33: ML Experimentation

**Q127:** What is A/B Testing in ML context?

<details>
<summary>Show Answer</summary>

Controlled experiment comparing model variants by splitting users into groups (A and B) to evaluate performance on predefined metrics before full rollout

</details>

**Q128:** What is Multi-Model Hosting?

<details>
<summary>Show Answer</summary>

Capability to host multiple model variants simultaneously for A/B testing and experimentation

</details>

**Q129:** What metrics are used in A/B Testing?

<details>
<summary>Show Answer</summary>

Accuracy, user engagement, response quality, speed; depends on specific objectives and use case

</details>

---

## Set 34: Sequence Generation

**Q130:** What is Beam Search?

<details>
<summary>Show Answer</summary>

Decoding strategy that explores multiple candidate paths simultaneously to improve quality of generated sequences; trade-off: better quality vs slower generation

</details>

**Q131:** What is Softmax?

<details>
<summary>Show Answer</summary>

Activation function that converts logits to probability distribution (sum = 1.0); used during training for loss computation

</details>

**Q132:** What is Argmax?

<details>
<summary>Show Answer</summary>

Function that selects the index with highest value/probability; used during inference for classification (more efficient than softmax for prediction)

</details>

---

## Set 35: Fine-Tuning Techniques

**Q133:** What is PEFT (Parameter-Efficient Fine-Tuning)?

<details>
<summary>Show Answer</summary>

Updates only a small subset of model parameters; more computationally efficient with lower memory requirements than full fine-tuning

</details>

**Q134:** When should you use PEFT vs Full Fine-Tuning?

<details>
<summary>Show Answer</summary>

PEFT: Multiple tenants/use cases from single base model, limited resources. Full: Massive datasets with abundant computational resources

</details>

**Q135:** What is Catastrophic Forgetting?

<details>
<summary>Show Answer</summary>

When model forgets previously learned knowledge during fine-tuning; PEFT mitigates this by keeping most parameters frozen

</details>

**Q136:** What are benefits of PEFT?

<details>
<summary>Show Answer</summary>

Lower GPU memory, faster training, easier to maintain multiple versions, preserves original knowledge, enables multi-tenant use cases

</details>

---

## Set 36: Advanced Prompt Engineering

**Q137:** What is Prompt Tuning?

<details>
<summary>Show Answer</summary>

Uses machine learning to learn optimal instructions (soft prompts) for a task; different from manual prompt engineering; doesn't modify model weights

</details>

**Q138:** What's the difference between Prompt Engineering and Prompt Tuning?

<details>
<summary>Show Answer</summary>

Engineering: Manual, human-driven, uses hard prompts (natural language). Tuning: Automated, ML-driven, uses soft prompts (virtual tokens)

</details>

**Q139:** What are Hard Prompts?

<details>
<summary>Show Answer</summary>

Natural language instructions manually created by humans for guiding model behavior

</details>

**Q140:** What are Soft Prompts?

<details>
<summary>Show Answer</summary>

Virtual tokens learned via ML and prepended to input; guides model behavior without modifying weights

</details>

**Q141:** What are Virtual Tokens?

<details>
<summary>Show Answer</summary>

Learned embeddings (not actual words from vocabulary) prepended to input prompt in prompt tuning technique

</details>

---

## Set 37: RAG Enhancement

**Q142:** What is Prompt Augmentation?

<details>
<summary>Show Answer</summary>

Core RAG step where user query is enriched with relevant information from retrieved documents to provide domain-specific context to the LLM

</details>

**Q143:** What is Reranking in RAG?

<details>
<summary>Show Answer</summary>

Post-processing step after initial retrieval that refines results based on semantic similarity to enhance relevance and variety; reduces redundancy

</details>

**Q144:** When does Prompt Augmentation happen?

<details>
<summary>Show Answer</summary>

At inference time (not training); provides context without fine-tuning the model

</details>

---

## Set 38: Model Compression

**Q145:** What is Pruning?

<details>
<summary>Show Answer</summary>

Removing redundant or less important parameters from model to reduce size and computational requirements with minimal accuracy loss

</details>

**Q146:** What is Quantization?

<details>
<summary>Show Answer</summary>

Reducing precision of model weights (e.g., FP32 → FP16 → INT8) to decrease memory footprint; example: 32-bit (4 bytes) → 8-bit (1 byte) = 75% reduction

</details>

**Q147:** What is Knowledge Distillation?

<details>
<summary>Show Answer</summary>

Training smaller "student" model to mimic larger "teacher" model's behavior; retains significant performance in compact model

</details>

**Q148:** What are the three main model compression techniques?

<details>
<summary>Show Answer</summary>

Pruning (remove parameters), Quantization (reduce precision), Knowledge Distillation (teacher → student model)

</details>

---

## Set 39: Transformer Architecture

**Q149:** What is Self-Attention in Transformers?

<details>
<summary>Show Answer</summary>

Mechanism that allows model to focus on specific parts of input sequence by computing attention weights for each token vs all others; captures contextual relationships

</details>

**Q150:** What are Attention Weights?

<details>
<summary>Show Answer</summary>

Computed for each token in relation to all other tokens; tells model how much "focus" to give each token based on contextual relevance (quadratic complexity O(n²))

</details>

**Q151:** What is Encoder-Decoder Architecture?

<details>
<summary>Show Answer</summary>

Model design with separate encoder (input processing) and decoder (output generation); excels at text summarization and machine translation

</details>

**Q152:** What is the primary purpose of Self-Attention?

<details>
<summary>Show Answer</summary>

To understand context and relationships within text by allowing model to focus on relevant parts of input sequence based on contextual relevance

</details>

---

## Set 40: Training Metrics & Optimization

**Q153:** What's the difference between Training Loss and Validation Loss?

<details>
<summary>Show Answer</summary>

Training Loss: Error on training data (can be misleading). Validation Loss: Error on validation data (better indicator of generalization)

</details>

**Q154:** How do you detect overfitting using loss metrics?

<details>
<summary>Show Answer</summary>

Training loss decreases but validation loss increases; indicates model is memorizing rather than generalizing

</details>

**Q155:** What is Validation Output Accuracy?

<details>
<summary>Show Answer</summary>

Percentage of correct predictions on unseen validation data; key metric for determining optimal number of epochs during fine-tuning

</details>

**Q156:** What is Bayesian Optimization?

<details>
<summary>Show Answer</summary>

Advanced hyperparameter tuning method using probabilistic model; learns from past evaluations to intelligently select next values to test; more efficient than Grid/Random Search

</details>

**Q157:** What is Gradient Descent used for?

<details>
<summary>Show Answer</summary>

Training model parameters (weights and biases), NOT for tuning hyperparameters; iteratively adjusts parameters to minimize loss function

</details>

---

## Set 41: GenAI Use Cases

**Q158:** What is Image-to-Text Generation?

<details>
<summary>Show Answer</summary>

Foundation model capability to generate descriptive captions or text descriptions from images; use case: video scene description, accessibility, content moderation

</details>

**Q159:** What are Scene Changes in video processing?

<details>
<summary>Show Answer</summary>

Technique to identify transitions between different scenes in video content using Amazon Rekognition; workflow: detect scenes → extract frames → generate captions

</details>

**Q160:** What is Action Item Extraction?

<details>
<summary>Show Answer</summary>

Process of identifying actionable tasks from unstructured text like customer reviews, meeting notes, or support tickets using GenAI

</details>

**Q161:** What is Post-Call Documentation?

<details>
<summary>Show Answer</summary>

Automated generation of call summaries after contact center interactions; reduces agent after-call work using Amazon Q in Connect and Contact Lens

</details>

**Q162:** What is Customer Segmentation?

<details>
<summary>Show Answer</summary>

Dividing customers into groups based on behavior patterns using K-Means clustering (unsupervised); use case: marketing campaigns, personalization, retention

</details>

---

## Set 42: AWS Patterns & Governance

**Q163:** What is Cross-Account Access pattern in AWS?

<details>
<summary>Show Answer</summary>

Secure pattern for accessing resources across AWS accounts: 1) Configure S3 bucket policy in Account A, 2) Create IAM role in Account B with read permissions, 3) Application assumes role

</details>

**Q164:** What is Data Lineage?

<details>
<summary>Show Answer</summary>

Detailed history tracking data's origin, transformations, and journey through ML pipeline; essential for debugging, reproducibility, auditing, and compliance

</details>

**Q165:** What AWS services support Knowledge Bases with GenAI?

<details>
<summary>Show Answer</summary>

Amazon OpenSearch Service (vector database) and Amazon Kendra (intelligent search); NOT S3 (object storage) or RDS (relational database)

</details>

**Q166:** When is PEFT ideal for multi-tenant scenarios?

<details>
<summary>Show Answer</summary>

When creating specialized model versions from same base model for different tenants/domains (legal, medical, financial); saves resources vs full fine-tuning each version

</details>
