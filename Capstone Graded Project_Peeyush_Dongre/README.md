**Problem Statement:

As a part of the Capstone project, we need to build an Intelligent Retail Decision Assistant that serves both internal business teams and end customers. The system should be able to analyse customer and product behaviour using classical machine learning, answer product and policy questions using retrieval-backed Generative AI, and intelligently route user requests through a simple agentic workflow.

The system starts with structured tabular machine learning, extends into retrieval-augmented generation (RAG), and finally integrates an agent/controller that selects the right tool or path based on the user’s query.

**Notebook Structure

We will be implementing the project accross various Notebooks , each of which is dedicated for specific outcome :

| Notebook | Purpose                 | Produces                         |
| -------- | ----------------------- | -------------------------------- |
| 01       | Data preparation / EDA  | Processed data                   |
| 02       | Classical ML + K-Means  | Prediction & segmentation models |
| 03       | Product RAG             | Product FAISS index              |
| 04       | Policy RAG              | Policy FAISS index               |
| **05**   | **LangGraph Assistant** | **End-to-end application**       |



**Installation Instruction:

1. Project Setup :

The assignment submission include the Project ZIP ( capstone_project.zip ).
Clone or download the project repository and open the project in Google Collab or a local Python environment.

The project structure is:

capstone_project/
├── data/
├── notebooks/
├── src/
├── outputs/
├── README.md
└── requirements.txt

2. Install Dependencies ( Environment Requirements ):

-- Python 3.13.x (developed and tested with Python 3.13.15)

( The Python version is specified separately because 'requirements.txt' contains the project's Python package dependencies, not the Python interpreter version.)

Install the dependencies that would be requiring to run the notebook:

pip install -r requirements.txt

#If using Google Colab, the same command can be executed in a notebook cell:

!pip install -r requirements.txt

3. Set the 'OpenAI Key' when prompted.

** Pre-generated Artifacts

The project package includes all artifacts generated during the notebook execution and required by the final Assistant.

The following artifacts are already populated in their respective folders:

- Trained ML model(s) used for purchase prediction
- Customer segmentation artifacts and cluster profiles
- Product FAISS vector index and associated documents
- Policy FAISS vector index and associated documents
- Execution and evaluation logs


** Execution Steps

To evaluate the project, I would propose two options:

**Option 1 – Complete Project Reproduction:

For a complete setup, proposing to run all the Notebooks (01–04) first to prepare the data and generate the required ML models and RAG indexes. Then run Notebook-05 to execute the complete LangGraph-based Retail Assistant.

Run the notebooks in the following order:

***Step 1 – Data Preparation and EDA

1) Open the notebook - notebooks/01_data_preparation.ipynb
2) Run all the cells in the order.

This notebook will performs the data loading, data cleaning, handling of missing values, exploratory data analysis, feature assessment, and preparation of the processed dataset required by subsequent notebooks.

***Step 2 – Classical ML and Customer Segmentation

1) Open the notebook - notebooks/02_classical_ml.ipynb
2) Run all the cells in the order.

This notebook will perform following tasks:

- Performs feature engineering
- Trains and evaluates the purchase prediction model
- Performs customer segmentation using K-Means
- Generates the required trained model artifacts

The artifacts will be saved in : output/models/

*** Step 3 – Product RAG

1) Open the notebook - notebooks/03_rag_recommendation.ipynb
2) Run all the cells in the order.

This notebook will perform following tasks :
- Prepares the product knowledge base.
- Creates text embeddings.
- Builds the Product FAISS index.
- Finally, build the Product RAG components as required by the final assistant.

The artifacts will be saved in : output/vector_stores/product_faiss_index

***Step 4 – Policy RAG

1) Open the notebook - notebooks/04_policy_qa.ipynb
2) Run all the cells in the order.

This notebook will perform following tasks :
- Prepares the policy knowledge base.
- Creates text embeddings.
- Builds the Policy FAISS index.
- Finally, build the Policy RAG components required by the final assistant.

The artifacts will be saved in : output/vector_stores/policy_faiss_index

***Step 5 – Unified Agentic Retail Assistant

1) Open the notebook - notebooks/05_agentic_assistant.ipynb
2) Run all the cells in the order.

This notebook integrates the components developed in the previous notebooks using a LangGraph workflow.

Following will be the Graph flow :

User Query -> Classification Router ------> Product Recommendation / Prediction ML / Segmenatation / Policy Assistance  ----- > Final Response

Notebook - 05 is the main entry point for interacting with the final Retail Assistant.

###############

**Option 2 – Evaluate the Final Retail Assistant
                                                                          
Use this option when the trained models and RAG indexes are already available in the submitted project. This option avoids repeating the complete data preparation, model training, and index-building process

I would propose here to run only the submitted the Notebook 05 (05_agentic_assistant.ipynb) using the artifacts those are already submitted.

***Open the Final Assistant

1) Open the notebook - notebooks/05_agentic_assistant.ipynb
2) Run all the cells in the order.

The notebook loads the pre-generated artifacts from the project directory, including:

- Purchase prediction model
- Customer segmentation artifacts
- Product FAISS index
- Policy FAISS index
- Supporting metadata/documents
- Initializes the LangGraph workflow

The notebook also provides the set of Test Queries to evaluate different capabiities.


**Recommended Evaluation Path

I would recommended Option 2 here for the evaluation of the final application because Notebook 05 is the end-to-end entry point for the Unified Agentic Retail Assistant.
Although, if required for the complete reproduction and verification of the development workflow, please refer Option 1 and execute Notebooks 01–05 sequentially.

**Agent / Controller Demo

The agent/controller flow is demonstrated in 05_agentic_assistant.ipynb.

As a prt of the Demo, a complete execution log is also provided in the outputs/logs directory, capturing the end-to-end routing flow for the supported capabilities:

Recommendation → Product RAG
Prediction → Classical ML
Policy → Policy RAG
Segmentation → Customer Segmentation

The log records the routed capability, query, relevant execution details, and the generated final response, providing an auditable view of the LangGraph controller's execution.

## All the required artifacts are pre-populated 