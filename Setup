→Dependency Installation
------_------------------
in requirements.txt
fastapi
uvicorn
sentence-transformers
transformers
torch
faiss-cpu
PyPDF2
python-multipart
openai
run→ pip install -r requirements.txt
→API startup command
python -m uvicorn main:app –reload
Optional VectorDB Initialization Steps
----------------------------------------------------
No separate VectorDB initialization step is required for this project.
• The application uses FAISS as an in-memory vector database
• The FAISS index is automatically created at application startup
• Embeddings are added to the index dynamically during document upload
• No external service, configuration, or manual setup is needed
If the application restarts, the in-memory FAISS index is recreated automatically.
Virtual environment creation

→python3 -m venv venv
Activate virtual environment
venv\Scripts\activate
