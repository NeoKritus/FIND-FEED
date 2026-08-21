# FIND&FEED — Intelligent Knowledge Retrieval & RAG Architecture

FIND&FEED is a document-focused AI platform that lets users upload PDFs and ask questions about their content. It combines document processing, semantic retrieval, local vector search, and local language models to generate context-aware answers with source references.

---

## Key Features

* **Multi-PDF Knowledge Retrieval**: Upload and manage multiple PDF documents, then search across selected documents to find relevant information.

* **Retrieval-Augmented Generation (RAG)**: Retrieves relevant document content before generating an answer, keeping responses grounded in the uploaded knowledge.

* **Semantic Search**: Converts document sections into embeddings and uses similarity search to identify content relevant to the user's question.

* **Source-Grounded Answers**: Connects generated responses with relevant document sources, helping users identify where the information came from.

* **Multi-Query Retrieval**: Creates alternative versions of a question to improve retrieval when the original wording does not directly match the document.

* **Local AI Processing**: Uses Ollama for local language-model and embedding processing, reducing dependency on external AI services.

* **Interactive AI Chat**: Provides a conversational interface where users can select documents and ask questions within an ongoing chat.

* **Document Management**: Supports PDF upload, processing, document listing, selection, and deletion through the application.

---

## Why This Architecture?

* **Knowledge-Grounded Responses**: Relevant document content is retrieved before generation, helping the model answer from the user's documents rather than relying only on general knowledge.

* **Local & Private AI**: Ollama enables local model execution, allowing document content and AI processing to remain on the user's system.

* **Better Retrieval**: Semantic search and multi-query retrieval help find relevant information even when the user's question uses different wording.

* **Modular Design**: Document processing, retrieval, AI generation, storage, and the user interface are separated into distinct components.

---

## System Architecture & Workflow (How It Works)

1. **Document Ingestion**: Users upload PDF documents, which are extracted and divided into smaller searchable text sections.

2. **Embedding & Indexing**: The text sections are converted into embeddings using a local embedding model and stored in ChromaDB for semantic search.

3. **Question Retrieval**: The user's question is expanded into relevant queries and matched against the stored document embeddings to retrieve useful sections.

4. **Contextual Generation**: Retrieved sections are provided to a local Ollama model, which generates an answer based on the selected document context.

5. **Source Delivery**: Relevant document information is returned with the response so users can identify the supporting content.

---

## RAG Workflow Design

### Document Processing

`PDF → Text Extraction → Chunking → Embeddings → Vector Storage`

PDF content is extracted and divided into searchable sections before being converted into vector representations.

### RAG Question Answering

`Question → Query Expansion → Semantic Retrieval → Context → Local LLM → Answer`

Relevant document sections are retrieved and provided to the local model for context-aware answer generation.

### Multi-PDF Retrieval

`Question → Selected PDFs → Retrieval → Relevant Chunks → Combined Context → Answer`

The system can search across multiple selected PDFs and combine relevant content before generating the final response.

---

## Tech Stack

| Domain                  | Technologies                                       |
| :---------------------- | :------------------------------------------------- |
| **Frontend**            | Next.js, React, TypeScript, Tailwind CSS           |
| **Backend & API**       | Python, FastAPI, Uvicorn                           |
| **RAG Framework**       | LangChain                                          |
| **Local AI**            | Ollama, Local LLMs, Ollama Embeddings              |
| **Vector Search**       | ChromaDB                                           |
| **Document Processing** | PDFPlumber, Unstructured, LangChain Text Splitters |
| **Database**            | SQLite, SQLAlchemy                                 |
| **Development**         | Git, GitHub, pnpm                                  |

---

## Prerequisites

* Python 3.10+
* Node.js 18+
* pnpm
* Ollama
* A local Ollama language model
* `nomic-embed-text` or another compatible embedding model
* Git
