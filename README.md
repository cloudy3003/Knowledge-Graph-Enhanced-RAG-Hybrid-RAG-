# Knowledge Graph-Enhanced Retrieval-Augmented Generation (RAG)

A Retrieval-Augmented Generation system that combines **vector search, knowledge graph-based retrieval, and Large Language Models (LLMs)** to deliver context-aware answers from PDF documents.

## Overview

This project explores an enhanced RAG architecture that integrates semantic search with knowledge graph retrieval to improve information discovery and contextual understanding.

Built using LangChain and Neo4j, the system processes PDF documents, generates vector embeddings, extracts entities from user queries, and retrieves relevant information through both vector similarity search and graph-based relationships.

The retrieved context is passed to a language model to generate responses grounded in the source documents.

The Hitman game franchise serves as the knowledge base for implementing and experimenting with the retrieval pipeline.

## Key Features

- **Document Ingestion:** Extracts and processes content from PDF documents using LangChain.
- **Vector Embeddings:** Generates document embeddings using Ollama's Llama 3.2 embedding model.
- **Semantic Search:** Retrieves relevant document chunks using vector similarity.
- **Knowledge Graph Integration:** Uses Neo4j to represent and retrieve relationships between entities.
- **Entity Extraction:** Leverages Gemini 2.5 Flash with structured output to identify entities from user queries.
- **Hybrid Retrieval:** Combines semantic vector search and structured knowledge graph retrieval.
- **Context-Aware Generation:** Uses retrieved information to generate relevant responses through an LLM.
- **Retrieval Evaluation:** Implements Precision@K and Recall@K to assess retrieval relevance.
- **Performance Monitoring:** Measures retrieval latency, generation latency, total response time, and token usage.

## Architecture

The system follows a multi-stage RAG pipeline:

1. **Document Processing:** PDF documents are loaded, extracted, and split into smaller text chunks.
2. **Embedding Generation:** Text chunks are converted into vector embeddings using Ollama.
3. **Knowledge Storage:** Document embeddings and entity relationships are stored and managed in Neo4j.
4. **Query Processing:** User queries are analyzed using Gemini 2.5 Flash to extract relevant entities.
5. **Hybrid Retrieval:** Relevant information is retrieved through vector similarity search and knowledge graph-based entity relationships.
6. **Context Integration:** Structured graph information and unstructured document content are combined.
7. **Response Generation:** The retrieved context is passed to Llama 3.2 to generate the final response.

## Technology Stack

| Category | Technologies |
|---|---|
| Programming Language | Python |
| RAG Framework | LangChain |
| Graph Database | Neo4j |
| Vector Search | Neo4j Vector Index |
| Embedding Model | Ollama (Llama 3.2) |
| Language Models | Ollama Llama 3.2, Google Gemini 2.5 Flash |
| Document Processing | PyPDFLoader |
| Structured Output | Pydantic |
| Evaluation | Precision@K, Recall@K |
| Performance Monitoring | Latency and Token Tracking |
| Development Environment | Jupyter Notebook |

## Retrieval Approaches

### 1. Vector-Based Retrieval

Document chunks are converted into embeddings and stored in Neo4j. Given a user query, the system retrieves the most semantically relevant chunks using vector similarity search.

### 2. Knowledge Graph-Based Retrieval

The system uses Gemini 2.5 Flash to extract entities from user queries.

These entities are matched against Neo4j full-text indexes to retrieve connected nodes and their relationships, providing additional structured context.

### 3. Hybrid Retrieval

The hybrid retrieval approach combines:

- **Unstructured retrieval:** Semantically relevant document chunks retrieved through vector search.
- **Structured retrieval:** Entity relationships and connected information retrieved from the knowledge graph.

Combining these retrieval approaches provides the language model with both relevant document content and contextual relationships.

## Evaluation and Performance Monitoring

The project includes retrieval evaluation and performance monitoring to examine the behavior of the RAG pipeline.

**Retrieval Evaluation**
- Precision@K
- Recall@K
- Retrieval experiments across different K values (5, 20, 50).
- Keyword-based relevance checks against expected information.

**Performance Monitoring**
- Retrieval latency.
- LLM generation latency.
- Total pipeline execution time.
- Prompt and completion token usage.

## Project Structure

```text
Knowledge-Graph-RAG/
│
├── data/
│   └── documents.pdf
│
├── rag.ipynb
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```

## Installation and Setup

### Prerequisites

- Python 3.10+
- Neo4j Database
- Ollama
- Google Gemini API Key

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/Knowledge-Graph-RAG.git

cd Knowledge-Graph-RAG
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Set Up Ollama

Install Ollama and pull the required model:

```bash
ollama pull llama3.2
```

Ensure the Ollama service is running before executing the notebook.

### 4. Configure Environment Variables

Configure the Neo4j connection details and Google Gemini API key in the environment configuration.

### 5. Run the Project

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open `rag.ipynb` and execute the cells sequentially.

## Learning Outcomes

- Designed and implemented an end-to-end RAG pipeline.
- Explored vector databases and semantic search.
- Integrated Neo4j for knowledge graph-based information retrieval.
- Implemented structured entity extraction using LLMs.
- Combined graph-based and vector-based retrieval strategies.
- Evaluated retrieval performance using Precision@K and Recall@K.
- Explored latency measurement and token usage monitoring in LLM applications.

## Author

**Aishwarya R.**

Interested in Generative AI, Retrieval-Augmented Generation, Knowledge Graphs, and building practical AI applications.