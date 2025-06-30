# Retrieval-Augmented Generation (RAG) Quick-Start Demo

**Author – Eva Paunova • June 2025**  
Minimal, end-to-end example that shows how to:

1. Ingest unstructured docs  
2. Chunk and embed them with **Hugging Face**  
3. Store vectors in **pgvector** (PostgreSQL)  
4. Query via **LangChain RetrievalQA**  
5. Capture latency & cost metrics---

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

