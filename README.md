# 📘 Daily Notes – AI & RAG Learning

*A continuously updated repository of daily notes, concepts, and explanations related to AI, RAG (Retrieval-Augmented Generation), LangChain, Vector Databases, Embeddings, and more.*

---

## 🚀 Overview

This repository contains my **daily learning notes**, explanations, and practical insights about modern AI development—especially around **RAG pipelines**, **document ingestion**, **LLM context**, **similarity search**, and **LangChain document structure**.

The notes are updated daily to track continuous learning and progress.

---

## 📅 Daily Topics Covered So Far

### 🔵 Retrieval-Augmented Generation (RAG)

RAG = *LLM + external knowledge source*
The model retrieves relevant information from a vector database and uses it to generate accurate answers.

### 🔹 Before RAG

Models relied only on training data → outdated & hallucinations.

### 🔹 After RAG

Models use **external documents** (PDF, Docs, HTML, SQL, etc.) through a retrieval pipeline.

---

## 🧩 Key Concepts Learned

### ✅ **1. Context**

The relevant information retrieved from your vector DB that the LLM uses to answer a query.
Example:
User: *What is the leave policy?*
Retrieved text: *Employees get 24 annual leaves…*

---

### ✅ **2. Similarity Search (Top-K)**

* Converts query → vector
* Compares it with stored vectors
* Returns top-K most relevant chunks
* Uses **cosine similarity**

  * +1 → perfect match
  * 0 → not related
  * –1 → opposite

---

### ✅ **3. Query vs Prompt**

| Query               | Prompt                                |
| ------------------- | ------------------------------------- |
| User’s raw question | Query + Context + System Instructions |
| “Leave policy?”     | Full formatted input sent to LLM      |

---

## 🏗️ Pipelines

### 🔵 **Data Ingestion Pipeline** (Offline)

Runs **before** user asks anything.

Steps:

1. Load documents
2. Parse
3. Chunk
4. Embed
5. Store in vector DB

Goal → Prepare the knowledge base.

---

### 🔴 **Retrieval Pipeline** (Online)

Runs **when user asks a question**.

Steps:

1. Query → embedding
2. Similarity search
3. Retrieve chunks
4. Build prompt
5. Generate answer

Goal → Use the knowledge base.

---

## 📦 Document Structure in LangChain

Every document =

```python
Document(
    page_content="Actual text",
    metadata={"source": "file.pdf", "page": 2}
)
```

Components:

* **page_content** → text
* **metadata** → source, page, section, etc.

---

## 🧪 LangChain Example Code

### **Chunking Example**

```python
from langchain.text_splitter import RecursiveCharacterTextSplitter

splitter = RecursiveCharacterTextSplitter(chunk_size=40, chunk_overlap=0)
chunks = splitter.split_documents(docs)
```

### **Embedding Example**

```python
from langchain_openai import OpenAIEmbeddings
embedder = OpenAIEmbeddings()
vectors = embedder.embed_documents([c.page_content for c in chunks])
```

### **Vector Store**

```python
from langchain.vectorstores import Chroma
store = Chroma.from_documents(chunks, embedder)
```

---

## 🧠 Tokens & LLM Context

✔ Token = small piece of text
✔ 100,000 tokens ≈ 150 pages of text
✔ Important for RAG because **context window is limited**

---

## 📈 What This Repository Tracks

* Daily concepts
* Notes from courses
* Code snippets
* Architecture diagrams
* RAG workflows
* LangChain experiments
* Vector DB insights
* And more…
---

## ✨ Purpose

To serve as:
✔ My personal learning log
✔ A reference for AI/RAG concepts
✔ A structured repository anyone can learn from

---
✅ convert notes into markdown files
Just tell me!
