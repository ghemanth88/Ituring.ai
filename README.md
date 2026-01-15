 Document Question & Answer Microservice (RAG)

This project implements a **Document Question & Answer Microservice** using **Retrieval-Augmented Generation (RAG)**. The service enables users to upload documents (PDF/TXT) and ask questions, returning answers grounded in the uploaded document content.

---

Project Overview & Selected Task

The selected task is to design and implement a **document-based question answering system** using RAG principles. The application is built as a **single microservice** focused entirely on this functionality.

### Architecture Summary

```
User Uploads Document
        ↓
Text Extraction (PDF / TXT)
        ↓
Text Chunking
        ↓
Embedding Generation
        ↓
Vector Storage (FAISS)
        ↓
Metadata Storage (SQLite)

User Question
      ↓
Question Embedding
      ↓
Vector Similarity Search
      ↓
Relevant Chunks Retrieved
      ↓
Answer Generated (RAG)
```

---

## Tech Stack

* **Language**: Python 3.14.2
* **Framework**: FastAPI
* **Vector Store**: FAISS (In-memory)
* **Embeddings**: Sentence-Transformers / HuggingFace / OpenAI
* **Document Parsing**: PyPDF2
* **Database**: SQLite (Metadata)
* **Server**: Uvicorn

---

## Python Version

```
Python 3.14.2
```

---

## ⚙️ Environment Setup

### Create Virtual Environment

```
python -m venv venv
```

### Activate Environment

**Windows**

```
venv\Scripts\activate
```

**Linux / macOS**

```
source venv/bin/activate
```

---

## Dependency Installation

```
python -m pip install fastapi uvicorn sentence-transformers transformers torch faiss-cpu PyPDF2 python-multipart openai
```

---

## API Startup Command

```
python -m uvicorn main:app --reload
```

---

## How to Check Endpoints

### Health Check Endpoint

**GET** `/health`

```
http://127.0.0.1:8000/health
```

**Expected Response**

```json
{
  "status": "OK",
  "embedding_provider": "sentence_transformers"
}
```

---

## Upload Document Endpoint

**POST** `/upload`

**Purpose**: Upload a PDF or TXT document.

### Using Swagger UI (Recommended)

1. Open: `http://127.0.0.1:8000/docs`
2. Select **POST /upload**
3. Click **Try it out**
4. Choose a `.txt` or `.pdf` file
5. Click **Execute**

**Expected Response**

```json
{
  "message": "Document uploaded successfully",
  "filename": "sample.txt",
  "chunks_stored": 2
}
```

---

## Query Endpoint

**POST** `/query`

### Using Swagger UI

1. Select **POST /query**
2. Click **Try it out**
3. Enter request body:

```json
{
  "question": "What is this document about?"
}
```

4. Click **Execute**

**Expected Response**

```json
{
  "question": "What is this document about?",
  "answer": "...",
  "sources": [
    {
      "filename": "sample.txt",
      "content": "..."
    }
  ]
}
```

---

## Notes and Assumptions

* The application is implemented as a **single microservice** focused on document-based Q&A using RAG.
* Only **one embedding provider** is active at a time (Sentence-Transformers, HuggingFace, or OpenAI), selected via configuration.
* **FAISS** is used as an **in-memory vector database**; no external vector DB is required.
* Document metadata (filename and upload timestamp) is stored in **SQLite**.
* Text chunks and their source filenames are maintained in memory and aligned with FAISS index positions.
* Documents must be uploaded **before querying**; querying without documents may return empty or generic responses.
* PDF text extraction relies on **PyPDF2**; extraction quality depends on the source PDF structure.
* Answer generation is simplified and directly uses retrieved context; a full LLM-based generation can be added later.
* Environment variables are used for sensitive configurations (e.g., API keys).
* Designed for **local development and demonstration**, not large-scale production.
* Error handling and authentication are intentionally minimal for clarity.
* The modular architecture allows easy replacement of embedding models or storage layers.

---

## Vector Database Initialization

No manual VectorDB initialization is required:

* FAISS index is created automatically at application startup
* Embeddings are added dynamically during document upload
* No external services or configurations needed
* On application restart, the in-memory FAISS index is recreated

---

## Environment Variables

### OPENAI_API_KEY

* **Purpose**: Authenticate OpenAI embedding requests
* **Required**: Only if `EMBEDDING_PROVIDER = "openai"`
* **Used in Code**: `os.getenv("OPENAI_API_KEY")`
* **Reason**: Prevents hardcoding secrets and accidental exposure

### EMBEDDING_PROVIDER

* **Purpose**: Selects the embedding backend
* **Supported Values**:

  * `sentence_transformers`
  * `huggingface`
  * `openai`
* **Default**: `sentence_transformers`
* **Why Configurable**: Enables easy switching between local and cloud models

> Note: Currently set directly in code for simplicity, but recommended to move to environment variables for production.

---

## Deliverables

* Document-based Q&A microservice using RAG
* REST APIs for upload and query
* In-memory FAISS vector search
* SQLite-based metadata storage
* Configurable embedding providers

---

## 📜 License

MIT License

---

## 👤 Author

**GUTTA HEMANTH**
