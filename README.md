# 📄 Document Question & Answer Microservice (RAG)

This project implements a **Document Question & Answer Microservice** using **Retrieval-Augmented Generation (RAG)**. It allows users to upload documents (PDF/TXT), ask questions, and receive accurate answers grounded in the document content.

---

## 🚀 Project Overview

The system extracts text from uploaded documents, splits it into chunks, generates embeddings, and stores them in a vector database. When a user asks a question, the system retrieves the most relevant chunks using vector similarity search and generates a contextual answer using a language model.

This architecture ensures:

* Reduced hallucinations
* Context-aware answers
* Scalable document-based Q&A

---

## 🏗️ Architecture Flow

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

## 🛠️ Tech Stack

* **Programming Language**: Python 3.14.2
* **API Framework**: FastAPI
* **Vector Database**: FAISS
* **Embeddings**: Sentence-Transformers
* **LLM**: Transformers / OpenAI
* **Document Parsing**: PyPDF2
* **Database**: SQLite
* **Server**: Uvicorn

---

## 📦 Dependencies

Install the required dependencies using pip:

```
python -m pip install fastapi uvicorn sentence-transformers transformers torch faiss-cpu PyPDF2 python-multipart openai
```

---

## 🐍 Python Version

```
Python 3.14.2
```

---

## ⚙️ Environment Setup

### 1️⃣ Create Virtual Environment

```
python -m venv venv
```

### 2️⃣ Activate Virtual Environment

**Windows**

```
venv\Scripts\activate
```

**Linux / macOS**

```
source venv/bin/activate
```

---

## ▶️ Running the API

Start the FastAPI server using Uvicorn:

```
python -m uvicorn main:app --reload
```

Once running, access:

* API: `http://127.0.0.1:8000`
* Swagger Docs: `http://127.0.0.1:8000/docs`
* ReDoc: `http://127.0.0.1:8000/redoc`

---

## 📂 Supported File Types

* PDF (`.pdf`)
* Text (`.txt`)

---

## ✨ Key Features

* Document upload and parsing
* Automatic text chunking
* Semantic search using embeddings
* Fast similarity search with FAISS
* Context-aware answers using RAG
* RESTful API with FastAPI

---

## 📌 Use Cases

* Document-based Q&A systems
* Knowledge base assistants
* Internal document search
* Research paper querying
* Enterprise data assistants

---

## 🔮 Future Enhancements

* Support for DOCX and HTML files
* Authentication & user management
* Persistent vector storage
* Streaming responses
* UI integration (React / Streamlit)

---

## 🤝 Contributing

Contributions are welcome! Feel free to fork this repository and submit a pull request.

---

## 📜 License

This project is licensed under the MIT License.

---

## 👤 Author

**GUTTA HEMANTH**

