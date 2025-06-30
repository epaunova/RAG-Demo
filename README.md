# Retrieval-Augmented Generation (RAG) Quick-Start Demo

**Author – Eva Paunova • June 2025**  
RAG-Demo
A minimal, end-to-end example of a Retrieval-Augmented Generation (RAG) pipeline using Python, LangChain, OpenAI, and pgvector. It shows how to ingest unstructured documents, index them for semantic search, and answer user queries by combining retrieved context with an LLM.

Features
Document Ingestion

Load PDF and HTML files from data/

Split them into manageable “chunks” for embedding

Vector Indexing

Generate embeddings via a Hugging Face model

Store and query embeddings in PostgreSQL with pgvector

RetrievalQA

Use LangChain’s RetrievalQA to fetch top-k relevant chunks

Append retrieved text to the LLM prompt for accurate answers

Performance Metrics

Measure per-query latency and cost

Log timings and token usage in a results table



## One-click Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/epaunova/RAG-Demo/blob/main/rag_demo_full.ipynb)

---

## Project layout

rag-demo/
├── rag_demo.ipynb ← Main notebook (RAG pipeline)
├── requirements.txt ← Minimal Python deps
├── docker-compose.yml ← 1-click Postgres + pgvector
└── data/ ← Sample PDFs / HTML

yaml
Copy
Edit

---

## Quick start (local)

> **Prereqs**: Python ≥ 3.9 · Docker · an OpenAI API key

```bash
git clone https://github.com/epaunova/rag-demo.git
cd rag-demo
docker compose up -d          # spins pgvector on port 5432
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter lab rag_demo.ipynb
Inside the notebook set:

python
Copy
Edit
os.environ['OPENAI_API_KEY'] = 'sk-…'
CONN_STR = 'postgresql://rag_user:rag_pass@localhost:5432/ragdemo'
Run all cells – you’ll get a working RAG answer plus latency & cost read-out.

