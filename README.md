# Retrieval-Augmented Generation (RAG) Quick-Start Demo

**Author – Eva Paunova • June 2025**  
Minimal, end-to-end example that shows how to:

1. Ingest unstructured docs  
2. Chunk and embed them with **Hugging Face**  
3. Store vectors in **pgvector** (PostgreSQL)  
4. Query via **LangChain RetrievalQA**  
5. Capture latency & cost metrics

The notebook is designed as a **take-home / interview demo**: recruiters can run it in < 10 min on a laptop or Colab.

---

## Folder structure

rag-demo/
├── rag_demo.ipynb ← Main notebook (RAG pipeline)
├── requirements.txt ← Minimal Python deps
├── docker-compose.yml ← Optional 1-click Postgres + pgvector
└── data/ ← Place sample PDFs / HTML here

yaml
Copy
Edit

---

## Quick start (local)

> **Prereqs**  
> * Python ≥ 3.9  
> * Docker (for Postgres)  
> * An OpenAI API key (or drop-in any compatible LLM)

```bash
git clone https://github.com/epaunova/rag-demo.git
cd rag-demo

# spin up Postgres + pgvector (port 5432)
docker compose up -d

# create venv & install deps
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt

# launch Jupyter
jupyter lab rag_demo.ipynb
Set environment variables inside the notebook:

python
Copy
Edit
import os
os.environ["OPENAI_API_KEY"] = "sk-..."
CONN_STR = "postgresql://rag_user:rag_pass@localhost:5432/ragdemo"
Run the cells top-to-bottom – you’ll end with a working RAG query and a tiny cost/latency report.

One-click run on Google Colab

Use Colab’s “Start a Postgres server” magic or switch to an in-memory FAISS index by uncommenting the relevant lines.
