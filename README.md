# RAG Help Center (CRM)

Retrieval-Augmented Generation backend for a CRM help center. Ingest help articles and support documents, embed and store them in a vector database, retrieve relevant context for a query, and generate grounded answers for agent and customer support workflows.

## What this project does

1. **Ingest** — load PDFs, plain text, and other help docs; parse and chunk them.
2. **Embed & store** — generate embeddings and persist them in a vector store (with Postgres for app/metadata).
3. **Retrieve** — find the most relevant chunks for a user or agent question.
4. **Generate** — build prompts from retrieved context and produce an answer grounded in your help content.

## Layout

| Path | Role |
|------|------|
| `app/main.py` | FastAPI entry point |
| `app/api/` | RAG, document upload/delete, and health endpoints |
| `app/middleware/` | Error handling, request logging, rate limiting |
| `app/rag/` | Pipeline, retrieval, generation, prompt building |
| `app/ingestion/` | File loading, parsing, chunking |
| `app/embeddings/` | Embedding generation |
| `app/vectorstore/` | Vector database operations |
| `app/db/` | Postgres connection and models |
| `app/config/` | Application settings |
| `app/utils/` | Shared helpers |
| `app/logs/` | Application and error log files |
| `tests/` | RAG pipeline and API tests |
| `docker/` | Dockerfile and compose for multi-container runs |
| `.github/workflows/` | CI pipeline |
| `.env` | Environment variable placeholders (no secrets) |
| `requirements.txt` | Python dependencies |
| `Makefile` | Common make targets |

This repo is a **scaffold only** — modules are stubbed with short description comments. Implementation comes next.

## Running later

Once dependencies and services are wired up:

- Install from `requirements.txt` and copy `.env` placeholders to real values locally (never commit secrets).
- Start supporting services (e.g. Postgres, vector DB) via `docker/docker-compose.yml`.
- Run the FastAPI app from `app/main.py` and exercise endpoints under `app/api/`.
- Use `Makefile` targets and `.github/workflows/ci.yml` once those files are filled in.

Exact install/run commands will land with the first implementation pass.
