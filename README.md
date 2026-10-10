# JurisDraft: Agentic AI Contract Drafting Assistant

[![Python Version](https://img.shields.io/badge/Python-3.11%2B-3776AB?logo=python&logoColor=white)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.111%2B-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![LangGraph](https://img.shields.io/badge/LangGraph-Multi--Agent-FF4F00?logo=langchain&logoColor=white)](https://langchain-ai.github.io/langgraph/)
[![ChromaDB](https://img.shields.io/badge/ChromaDB-Vector_Storage-FC521F)](https://trychroma.com)

> **Deterministic Multi-Agent Orchestration & Statutory RAG under the Thai Civil and Commercial Code (ป.พ.พ.)**  
> *legal engineering platform designed to eliminate hallucinations in contract generation.*

---

## Project Overview

Traditional generative AI models frequently fabricate statutory articles, omit mandatory procedural formalities, or cross-contaminate draft terms with historical training data. In legal drafting, a single hallucinated article or omitted statutory clause can render an agreement legally void (*ตกเป็นโมฆะ*).

**JurisDraft** solves this fundamental limitation. Built specifically for the **Thai Civil and Commercial Code (ประมวลกฎหมายแพ่งและพาณิชย์ - ป.พ.พ.)**, JurisDraft replaces unconstrained generation with a **hard-coded, deterministic multi-agent stategraph** combined with **Retrieval-Augmented Generation (RAG)**. The platform strictly separates blank structural skeletons from user-verified facts and enforces statutory compliance through a 3-tier legal checklist.

---

## Key Highlights & Engineering Features

- **Zero-Hallucination Legal Guardrails**: Deterministic requirement checklists enforce Thai Civil Code constraints before drafting begins (e.g., verifying written evidence rules under CCC Art. 653 and statutory interest rate caps of 15% under CCC Art. 654).
- **3-Agent LangGraph StateGraph**: Specialized cyclic pipeline (Agent 1: Collection & Normalization ➔ Agent 2: Structural Drafting ➔ Agent 3: Validation & Citation Cross-Verification).
- **Hybrid Statutory RAG Engine**: Indexes official Thai Council of State (*สำนักงานคณะกรรมการกฤษฎีกา*) statutes and vetted blank templates. Employs dense vector embeddings combined with Thai morphological BM25 search.

---

## Supported Official Contract Types

JurisDraft covers 5 primary contractual categories under Book 3 of the Thai Civil and Commercial Code:

| # | Contract Type | Statutory Basis (Example) | Mandatory Statutory Rules (Example) |
| :-: | :--- | :--- | :--- |
| **1** | **สัญญากู้ยืมเงิน**<br/>*(Loan Agreement)* | ป.พ.พ. มาตรา 650, 653, 654 | • Principal > 2,000 THB requires written evidence<br/>• Interest rate strictly capped at 15% per annum |
| **2** | **สัญญาเช่าอสังหาริมทรัพย์**<br/>*(Real Estate Lease)* | ป.พ.พ. มาตรา 537, 538 | • Leases up to 3 years require written evidence<br/>• Leases > 3 years require registration with land officer |
| **3** | **สัญญาจะซื้อจะขายที่ดิน**<br/>*(Sale & Purchase Agreement)* | ป.พ.พ. มาตรา 456 วรรคสอง | • Written evidence, earnest deposit (*มัดจำ*), or partial payment<br/>• Clear land title deed identification (โฉนดที่ดิน) |
| **4** | **สัญญาจ้างทำของ**<br/>*(Hire of Work / Service)* | ป.พ.พ. มาตรา 587, 591, 600 | • Clear milestones, deliverables, and remuneration<br/>• Statutory defect liability (*ความรับผิดเพื่อชำรุดบกพร่อง*) |
| **5** | **หนังสือมอบอำนาจ**<br/>*(Power of Attorney)* | ป.พ.พ. มาตรา 797, 798 | • Scope of authority explicitly specified<br/>• Duty to act in writing if underlying transaction requires it |

---

## Tech Stack

| Layer | Technologies | Purpose |
| :--- | :--- | :--- |
| **Frontend** | defined later | defined later |
| **Backend API** | FastAPI, Pydantic v2, Python-docx | High-throughput REST API, validation, `.docx` rendering |
| **Agent Orchestration** | LangGraph, LangChain Core | StateGraph workflow, cyclic clarification loops |
| **Vector DB & Retrieval** | ChromaDB, Sentence-Transformers, PyThaiNLP, Rank-BM25 | Dense embeddings + Thai tokenized sparse BM25 |
| **Local Inference** | LM Studio | Offline execution of open-weight models (Development stage) |
