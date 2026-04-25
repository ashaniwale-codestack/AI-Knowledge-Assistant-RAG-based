# AI Knowledge Assistant (GitHub & Web RAG System) - coming soon
An AI-powered assistant that can scan GitHub repositories (single or entire organizations) and answer questions using a Retrieval-Augmented Generation (RAG) pipeline.

--------------------------------------

## 🚀 What This Project Does

This system allows users to:

🔍 Scan a GitHub repository or an entire organization
📦 Extract and process code/files recursively
🧩 Split content into meaningful chunks
🧠 Convert text into embeddings
⚡ Store embeddings in a FAISS vector database
💬 Ask natural language questions about the codebase
🤖 Generate answers using a local LLM (Ollama - phi3)

----------------------------------------

## 🧠 Architecture Overview
React (Frontend - optional)
        ↓
FastAPI Backend
        ↓
Data Ingestion Layer
   ├── GitHub Scanner (recursive)
   └── (Future) Website Scanner
        ↓
Chunking
        ↓
Embeddings (sentence-transformers)
        ↓
Vector Store (FAISS - in memory)
        ↓
LLM (Ollama - phi3)
        ↓
Answer

-------------------------

## 🛠️ Tech Stack
Backend
FastAPI (Python)
Uvicorn
AI / ML
sentence-transformers (embeddings)
FAISS (vector similarity search)
Ollama (phi3 model for local LLM)
Data Processing
GitHub REST API
Requests
Recursive file traversal

------------------------------------------------

## 📁 Project Structure

backend/
│
├── app/
│   ├── main.py
│   │
│   ├── routes/
│   │   ├── ingest.py      # GitHub ingestion APIs
│   │   └── chat.py        # Chat (RAG) API
│   │
│   ├── services/
│   │   ├── github_loader.py
│   │   ├── embedding.py
│   │   ├── vector_store.py
│   │   ├── chunker.py
│   │
│   └── models/
│
├── venv/
└── requirements.txt

--------------------------------------------


## ⚙️ Setup Instructions
1️⃣ Clone Repository
git clone <your-repo-url>
cd backend
2️⃣ Create Virtual Environment
python -m venv venv
venv\Scripts\activate   # Windows
3️⃣ Install Dependencies
pip install -r requirements.txt
4️⃣ Install & Run Ollama

Download and install: Ollama

ollama pull phi3
ollama serve
5️⃣ Run Backend
uvicorn app.main:app --reload
6️⃣ Open Swagger UI
http://localhost:8000/docs
🔌 API Endpoints
📥 Ingest GitHub Repository
POST /ingest/github
📥 Ingest Entire GitHub Owner/Org
POST /ingest/github/owner
Request:
{
  "owner": "facebook"
}
💬 Ask Questions
POST /chat
Request:
{
  "question": "Where is authentication implemented?"
}

------------------------------

## 🔄 How It Works (RAG Pipeline)
Fetch GitHub repository data (recursive)
Split files into chunks
Convert chunks into embeddings
Store embeddings in FAISS
User asks a question
System retrieves relevant chunks
LLM generates answer based on context

-------------------------------------

## ⚠️ Current Limitations
❌ FAISS index is stored in memory (not persistent)
❌ Data is lost when server restarts
❌ No database integration yet
❌ No authentication or multi-user support
❌ No streaming responses
❌ Limited file filtering and preprocessing

----------------------------------

## 🚧 Upcoming Improvements
### 🔥 High Priority

Persist FAISS index to disk (avoid re-indexing)

Load vector store on startup

Improve chunking strategy (semantic chunking)

### ⚡ Performance & Quality

Filter irrelevant files (binary, large files)

Add caching mechanism

Improve retrieval ranking

### 🤖 AI Enhancements

Multi-model support (Ollama + cloud fallback)

Streaming responses (real-time chat)

Better prompt engineering

----------------------------------------------------

## 🌐 Features

Website ingestion

UI integration (React frontend)

Chat history support

------------------------------------------

## 💡 Design Highlights
Modular architecture (routes + services separation)
Pluggable LLM design (local + future cloud support)
RAG-based system for accurate contextual answers
Recursive GitHub ingestion for full codebase understanding

### 🚀 Use Cases
Understand unfamiliar codebases
Developer onboarding assistant
AI-powered documentation explorer
Multi-repo knowledge assistant

### 🧠 Key Learning Outcomes
Built a full RAG pipeline from scratch
Implemented vector search using FAISS
Integrated local LLM (Ollama)
Designed scalable backend architecture
Worked with embeddings and semantic search

------------------------------------------

## 📌 Future Vision

Transform this into a multi-source AI knowledge platform:

GitHub + Websites + Documents + APIs → Unified AI Assistant

-----------------------------------------------------------------------

⭐ If you found this useful, feel free to star the repo!

-----------------------------------------------------------------------------------
