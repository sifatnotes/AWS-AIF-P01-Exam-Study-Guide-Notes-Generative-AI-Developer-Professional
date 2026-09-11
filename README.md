# AWS-AIF-P01-Exam-Study-Guide-Notes-Generative-AI-Developer-Professional
Comprehensive community study guide, revision notes, practice tips, and resource repository for the AWS AIF-P01: Generative AI Developer Professional certification exam.
# AWS AIF-P01: Generative AI Developer Professional Study Guide

Welcome to the community-driven study guide for the **AWS AIF-P01: Generative AI Developer Professional** certification exam. 

This repository provides an end-to-end, technically detailed preparation roadmap for software engineers, ML developers, cloud architects, and AI practitioners looking to design, build, optimize, and secure production-grade Generative AI applications on Amazon Web Services.

---

## 📌 Exam Overview

The **AWS AIF-P01** exam validates advanced expertise in developing applications powered by Foundation Models (FMs), implementing Retrieval-Augmented Generation (RAG) pipelines, orchestrating AI Agents, and optimizing LLM workloads for cost, performance, and safety on AWS.

* **Exam Name:** AWS Certified Generative AI Developer - Professional
* **Exam Code:** AIF-P01 (also referenced alongside AIP-C01 tracks)
* **Question Count:** ~65 questions (multiple choice & multiple response)
* **Passing Score:** 750 / 1000
* **Duration:** 180 minutes (3 hours)
* **Target Role:** Generative AI Developer, ML Engineer, Cloud Solutions Architect

---

## 🎯 Who Should Take This Exam?

- **Generative AI Engineers & Developers:** Developers building LLM-backed web apps, enterprise chatbots, and internal tools.
- **Machine Learning & Cloud Engineers:** Engineers managing RAG architectures, vector store integrations, and fine-tuning workloads on AWS.
- **Solutions Architects:** Technical leads designing secure, cost-optimized, and resilient generative AI systems in cloud environments.
- **DevOps / MLOps Specialists:** Engineers responsible for automated LLM deployment pipelines, prompt monitoring, and model guardrails.

---

## 📊 Exam Objectives & Domain Breakdown

| Domain | Weightage |
| :--- | :--- |
| **Domain 1: Foundation Model Integration, Data Management, & Compliance** | 24% |
| **Domain 2: Implementation & System Integration** | 26% |
| **Domain 3: AI Safety, Security, & Governance** | 18% |
| **Domain 4: Operational Efficiency & Optimization for GenAI Apps** | 18% |
| **Domain 5: Testing, Validation, & Troubleshooting** | 14% |

---

## 🧠 Detailed Study Notes & Important Concepts

### Domain 1: Foundation Model Integration, Data Management, & Compliance (24%)

#### Amazon Bedrock Core Infrastructure
* **Foundation Model (FM) Selection:** Selecting models based on context window limits, latency, cost per token, and modalities (e.g., Anthropic Claude, Meta Llama, Amazon Titan, AI21 Labs).
* **Model Customization:**
  * **Continued Pre-training:** Unsupervised learning on massive unlabeled domain-specific datasets.
  * **Fine-tuning:** Supervised learning using labeled prompt-response pairs to adjust model weights for niche tasks.
  * **Parameter-Efficient Fine-Tuning (PEFT / LoRA):** Freezes base model weights and trains small adapter layers, reducing GPU memory overhead.
* **Amazon Bedrock Knowledge Bases (RAG):**
  * Automatically chunks, embeds, and indexes unstructured documents (S3) into vector databases.
  * **Chunking Strategies:** Fixed-size chunking, hierarchical (parent-child) chunking, and semantic chunking.
  * **Vector Database Integrations:** OpenSearch Serverless, Amazon Aurora PostgreSQL (pgvector), Pinecone, Redis Enterprise.

---

### Domain 2: Implementation & System Integration (26%)

#### Advanced RAG & Vector Architectures
* **Retrieval Techniques:**
  * **Dense Retrieval:** Uses vector embeddings to capture semantic similarity.
  * **Sparse Retrieval:** Key-phrase matching (BM25).
  * **Hybrid Search:** Combines dense and sparse search scores with reciprocal rank fusion (RRF) for optimal relevance.
* **Re-ranking & Context Management:** Using re-ranking models (e.g., Cohere Rerank) to filter and compress retrieved contexts before passing them to the LLM.

#### Agentic Frameworks & Function Calling
* **Agents for Amazon Bedrock:** Orchestrates multi-step reasoning tasks using the ReAct (Reason + Act) pattern.
* **Action Groups:** Connects Bedrock Agents to AWS Lambda functions defined by OpenAPI schemas to execute real-time business logic.
* **Code Interpreter & Memory:** Native Bedrock agent capabilities for code execution and multi-turn session persistence.

---

### Domain 3: AI Safety, Security, & Governance (18%)

#### Guardrails & Data Protection
* **Amazon Bedrock Guardrails:**
  * Filters denied topics, blocks PII (personally identifiable information), and halts prompt injection / jailbreak attacks.
  * Evaluates responses for hallucination and grounding metrics against source context.
* **Data Privacy Boundaries:**
  * Amazon Bedrock does **not** store customer data or use prompt data to train base models.
  * Data in transit is encrypted using TLS 1.2+, and data at rest is encrypted via AWS KMS customer-managed keys (CMK).
* **Identity & Access Management (IAM):**
  * Least-privilege policy enforcement for `bedrock:InvokeModel`, `bedrock:RetrieveAndGenerate`, and cross-service role execution.

---

### Domain 4: Operational Efficiency & Optimization (18%)

#### Performance Tuning & Cost Management
* **Provisioned Throughput:** Reserving dedicated capacity (Model Units) on Amazon Bedrock for predictable, low-latency production workloads.
* **Prompt Caching:** Caching static prompt prefixes (e.g., system instructions, large reference documents) to lower token costs and reduce time-to-first-token (TTFT).
* **Model Routing / Gateway Pattern:** Implementing smart routing rules to send simpler queries to lightweight models (e.g., Claude Haiku) and complex reasoning to larger models (e.g., Claude Sonnet).

---

### Domain 5: Testing, Validation, & Troubleshooting (14%)

#### Evaluation & Observability
* **Model Evaluation Jobs:**
  * **Automatic Evaluation:** Evaluates models on metrics like Accuracy, Robustness, and Toxicity using standard datasets.
  * **Human Evaluation:** Uses internal teams or AWS Ground Truth for subjective metrics (e.g., brand alignment, tone).
* **Observability Tools:**
  * **AWS X-Ray & CloudWatch:** Tracing latency across API calls, Lambda execution, vector store lookup, and model invocation.
  * **Invocation Logging:** Saving prompt/response payloads to S3 or CloudWatch Logs for compliance and post-hoc evaluation.

---

## 🛠️ Practical Hands-on Exercises (Labs)

Execute these four practical labs in your AWS sandbox to solidify your technical skills:

1. **Deploy a RAG Pipeline with Bedrock Knowledge Bases:**
   * Upload sample technical documentation into an S3 bucket.
   * Create an **Amazon Bedrock Knowledge Base** backed by an **OpenSearch Serverless** vector index.
   * Execute test queries using `RetrieveAndGenerate` API and compare response accuracy.
2. **Build an Agent with Action Groups:**
   * Create an AWS Lambda function that queries an Amazon DynamoDB table for user order status.
   * Define an **OpenAPI 3.0 schema** and attach it as an **Action Group** inside Amazon Bedrock Agents.
   * Test multi-turn conversational execution in the Bedrock console.
3. **Configure Guardrails for Content Safety:**
   * Build a **Bedrock Guardrail** blocking specific sensitive terms and enabling PII redaction.
   * Test prompt injection payloads to verify that the guardrail blocks malicious inputs before reaching the FM.
4. **Set Up CloudWatch Model Invocation Logging:**
   * Enable model invocation logging in Bedrock settings, directing logs to an S3 bucket encrypted with KMS.
   * Run several invocation API calls and inspect the logged request payloads and token usage metrics.

---

## 📅 30-Day Study Plan
