# Intelligent Retail Decision Assistant
The project is an end-to-end intelligent retail decision assistant combining Classical Machine Learning, Customer Segmentation, Retrieval-Augmented Generation (RAG), Vector Search, and Agentic AI orchestration ( through LangGraph ) to support retail customer interactions.

The project was developed as an AI/ML capstone and demonstrates the integration of traditional machine learning with modern Generative AI and agentic workflows.

# Overview

The Intelligent Retail Decision Assistant is designed to handle multiple types of retail-related user queries through a unified AI assistant.

Depending on the user's request, the system can:

* Predict the likelihood of a customer purchasing a product
* Segment customers based on purchasing behavior
* Recommend relevant products using semantic search
* Answer questions using retail policy documents
* Route queries to the appropriate capability using a LangGraph-based orchestration workflow
* Combine retrieved information, ML predictions, and LLM reasoning to generate the final response

The project demonstrates how Classical ML, RAG, and Agentic AI can be combined within a single application architecture.

# Key Capabilities
# 1. Purchase Prediction

A supervised machine learning pipeline predicts the probability that a customer will purchase a given product.

** Model** : XGBoost

The pipeline includes:

* Feature preprocessing
* Numerical and categorical feature handling
* Model training and tuning
* Probability prediction
* Classification based on a decision threshold

The trained model and preprocessing pipeline are persisted as an artifact and reused during inference.

# 2. Customer Segmentation

Customer purchasing behavior is analyzed using K-Means clustering.

Customer segments are created using behavioral features such as:

* Total orders
* Average order value
* Days since last purchase
* Average time on page

The final implementation uses five customer clusters, allowing the assistant to incorporate customer-level behavioral information into the retail workflow.

# 3. Product Recommendation using RAG

Product recommendations are implemented using a Retrieval-Augmented Generation approach.

Product information is converted into searchable documents and indexed using FAISS with embedding-based semantic similarity.

The product retrieval process considers information such as:

* Product title
* Description
* Category / sub-category
* Brand
* Base Price
* Final Price
* Discount
* Color
* Style
* Occasion
* Season
* Customer review

The retrieved product context is then provided to the LLM to generate the final recommendation.

# 4. Policy Question Answering using RAG

Retail policy documents are indexed separately to support policy-related questions.

The policy RAG workflow:

* Receives the user's policy question
* Retrieves relevant policy content
* Provides the retrieved context to the LLM
* Generates an answer grounded in the retrieved policy information

This helps to separate policy knowledge retrieval from product recommendation and machine learning capabilities.

# 5. Agentic AI / LangGraph Orchestration

A LangGraph-based workflow acts as the orchestration layer for the assistant.

The workflow determines the appropriate capability based on the user's query and routes the request to the corresponding component.

# Technology Stack

| Area | Technology |
| :--- | :--- |
| Programming Language | Python |
| Data Processing | Pandas, Numpy |
| Classical ML | XGBoost |
| Customer Segmentation | K-Means |
| Vector Search | FAISS |
| Embeddings | OpenAI Embeddings |
| Generative AI | OpenAI |
| RAG | LangChain |
| Agentic Orchestration | LangGraph |
| Data Validation | Pydantic |
| Model Persistence | Joblib |
| Development Environment | Google Collab |

# Project Architecture

The repository contains the file with the detailed architecture flow of the system.

# Notebook Outcomes

Each notebook in the repository mentioned the detailed outcome at the end. That explains the activities performed in the specific notebook along with the outputs produced ( if any ).

# Pre-generated Artifacts

The notebooks have already been executed as part of the capstone implementation.

The repository therefore includes pre-generated artifacts such as:

* Trained purchase prediction model
* Trained customer segmentation model
* Product FAISS index
* Policy FAISS index
* Execution logs
* Processed project artifacts

These artifacts are included so that the implementation and evaluated results can be inspected without requiring the complete training and indexing workflow to be reproduced from scratch.

# Running the Project

The notebooks are designed to run in Google Colab.

The project uses the following expected project location:

/content/capstone_project/

The repository structure mirrors this project directory.

# Suggested notebook execution order

01_data_preparation
        ↓
02_classical_ml
        ↓
03_rag_recommendation
        ↓
04_policy_qa
        ↓
05_agentic_assistant

The last notebook consume artifacts generated by the earlier stages.

