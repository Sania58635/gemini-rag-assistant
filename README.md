# Gemini RAG Starter — “Ask Your Docs” (FastAPI + Chroma)

> A production-minded, internship-ready Retrieval-Augmented Generation starter using **Gemini** for generation and **Chroma** for embeddings storage. Built for clarity, safety, and reproducibility.

![App Screenshot](docs/screenshots/app_home.png)
![Answer Screenshot](docs/screenshots/answer_with_citations.png)
![Architecture](docs/diagrams/architecture.png)

## ✨ Features
- **RAG pipeline**: ingest → embed → store → retrieve → generate with **citations**
- **Gemini** for responses; **Google Embeddings** (configurable)
- **FastAPI** service with `/query` and `/ingest` endpoints
- **Chroma** vector DB (persistent on disk)
- **Typed Python**, tests, pre-commit (lint & format), `.env` config
- **Safety**: guardrails for disallowed content, answer-with-sources template
- **Optionals**: hybrid retrieval (BM25), reranker, RAG evaluation notebook

## 📐 Architecture (high level)
1. **Ingest**: parse files from `data/` → chunk → embed → upsert to Chroma  
2. **Retrieve**: embed user question → top-k similarity (optionally + BM25)  
3. **Generate**: Gemini composes a grounded answer using retrieved chunks  
4. **Return**: answer + citations (file + chunk ids) + token/latency metrics

## 🧱 Tech Stack
- **Backend**: Python 3.11+, FastAPI, Uvicorn
- **LLM**: Gemini via `google-generativeai` (model configurable)
- **Embeddings/Store**: Google Embeddings (`text-embedding-004`, configurable) + Chroma
- **Testing/Quality**: pytest, mypy, ruff, black, pre-commit
- **Eval (optional)**: ragas, jupyter

## 📂 Repo Structure
