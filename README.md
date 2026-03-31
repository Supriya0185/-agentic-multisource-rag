# -agentic-multisource-rag
Agentic Multi-Source RAG system that intelligently routes queries across structured CSV, unstructured data, and web content using semantic retrieval and source-aware decision logic.
# 🚀 Agentic Multi-Source RAG

A lightweight Agentic Multi-Source Retrieval-Augmented Generation (RAG) system that simulates how enterprise AI assistants retrieve knowledge from multiple data sources.

---

## 🧠 Overview

This project demonstrates how modern AI systems can combine multiple data sources and intelligently decide where to retrieve information from.

Unlike traditional RAG systems that search all sources blindly, this system introduces an **agent-like routing mechanism** that selects the most relevant source based on the user query.

---

## 📊 Data Sources

The system integrates three different types of data:

- 📊 **Structured Data (CSV)**  
  Employee dataset from Kaggle (e.g., employee, manager, department, project)

- 📝 **Unstructured Data (CSV/Text)**  
  Support or issue datasets (complaints, problem descriptions)

- 🌐 **Web Data**  
  FAQ pages or external knowledge from websites

---

## ⚙️ How It Works

```text
User Query
   ↓
Agent Router (decides source)
   ↓
Selected Retriever
   ↓
Semantic Search (FAISS)
   ↓
LLM (optional)
   ↓
Final Answer with Context
