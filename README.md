# Employee Handbook Q&A Microservice

A Retrieval-Augmented Generation (RAG)-based microservice to answer questions from an employee handbook PDF using a **local LLM** (e.g., Gemma:2b via [Ollama](https://ollama.com)).

---

## ✅ Features

- Query HR policies from a company handbook
- Uses vector embeddings + similarity search (RAG)
- Runs **fully locally** using:
  - 📄 PyMuPDF for PDF parsing
  - 🧠 SentenceTransformers for embeddings
  - 📦 ChromaDB for vector storage
  - 🤖 Ollama for LLM-powered responses
  - ⚙️ FastAPI for serving the endpoint

---

## 📁 Folder Structure

```
employee-handbook-rag-api/
├── main.py # FastAPI microservice
├── rag.py # Embedding, vector search, response generation
├── ingest.py # One-time PDF embedding script
├── chroma/ # ChromaDB vector store (auto-created)
├── employee_handbook.pdf # Your employee handbook
├── requirements.txt
└── README.md
```

---

## ⚙️ Installation & Setup

---

### 1. Clone the Repo

```bash
git clone https://github.com/FaisalZulfiqarr/handbook-rag.git
cd handbook-rag
mkdir chroma
```

---

### 2. Setup Python Environment

```
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

---

### 3. Install Ollama & Pull Model

Install from: https://ollama.com/download

Then pull a model:

```
ollama pull gemma:2b
```

---

### 4. Ingest the PDF

Replace employee_handbook.pdf with your file and run:

```
python ingest.py
```

This parses the PDF, chunks it, embeds it, and stores it in a local vector database.

---

### 5. Run the Microservice

```
uvicorn main:app --reload

```
