 1)Project overview and selected task.
#
# This project implements a Document Question & Answer Microservice using Retrieval-Augmented Generation (RAG).
#
# Architecture summary
# User Uploads Document
#         ↓
# Text Extraction (PDF / TXT)
#         ↓
# Text Chunking
#         ↓
# Embedding Generation
#         ↓
# Vector Storage (FAISS)
#         ↓
# Metadata Storage (SQLite)
#
# User Question
#       ↓
# Question Embedding
#       ↓
# Vector Similarity Search
#       ↓
# Relevant Chunks Retrieved
#       ↓
# Answer Generated (RAG)
#
# python version
# Python 3.14.2

# Environment Creation
# python -m venv venv
# venv\Scripts\activate
#Dependency installation
# python -m pip install fastapi uvicorn sentence-transformers transformers torch faiss-cpu PyPDF2 python-multipart openai




#How to run API
#python -m uvicorn main:app --reload
