# 🚀 Agentic Multi-Source RAG

An end-to-end implementation of an **Agentic Multi-Source Retrieval-Augmented Generation (RAG)** system that intelligently routes user queries to the most relevant data source.

---

# 🧠 What This Project Does

This project simulates an **enterprise AI assistant** capable of answering questions by retrieving information from multiple data sources.

Instead of searching all data blindly, the system:

👉 **Understands the query → Selects the correct data source → Retrieves relevant data → Generates an answer**

---

# ⚙️ End-to-End Flow (Input → Output)

## 🟢 Step 1 — User Input

User asks a question:

```
Who is manager of Rahul?
```

---

## 🟡 Step 2 — Agent Decision (Core Logic)

The system analyzes the query and decides:

```
This is an employee-related query → use employee dataset
```

---

## 🔵 Step 3 — Source Selection

The agent selects one of the following sources:

* Employee dataset (structured)
* Support dataset (unstructured)
* Website data (external knowledge)

---

## 🟣 Step 4 — Retrieval

The system retrieves relevant data from the selected source.

---

## 🔴 Step 5 — Semantic Search

* Convert query into embeddings
* Search similar data using FAISS
* Retrieve top relevant results

---

## 🟢 Step 6 — Answer Generation

* Combine retrieved context
* Optionally use LLM
* Generate final answer

---

## 🟢 Step 7 — Output

Example output:

```
Rahul works under manager Mehta (Source: Employee Dataset)
```

---

# 📊 Data Sources Used

## 📊 1. Employee Dataset (Structured)

* Source: Kaggle
* Fields:

  * Name
  * Department
  * Manager
  * Project

👉 Used for employee-related queries

---

## 📝 2. Support Dataset (Unstructured)

* Source: Kaggle
* Fields:

  * Issues
  * Complaints
  * Problem descriptions

👉 Used for issue-related queries

---

## 🌐 3. Website Data

* Source: FAQ pages (AWS / Oracle)
* Extracted using web scraping

👉 Used for general knowledge queries

---

# 🔄 ETL Pipeline

The system follows a lightweight ETL process:

### Extract

* Load CSV files
* Fetch website content

### Transform

* Convert rows into text
* Clean and preprocess data
* Split into chunks

### Load

* Convert text into embeddings
* Store in FAISS vector database

---

# 🤖 Agentic RAG Concept

### Traditional RAG

```
Search all data → retrieve → answer
```

### Agentic RAG

```
Decide source → retrieve → answer
```

---

## 🧠 Decision Logic

| Query Type        | Selected Source  |
| ----------------- | ---------------- |
| Employee-related  | Employee dataset |
| Issue / complaint | Support dataset  |
| General query     | Website data     |

---

# 🛠️ Implementation Details

## 1. Ingestion Layer

* Load CSV datasets
* Scrape website data
* Convert data into documents

---

## 2. Preprocessing

* Clean text
* Chunk large data

---

## 3. Vector Store

* Use FAISS
* Store embeddings

---

## 4. Retrievers

* Employee retriever
* Support retriever
* Web retriever

---

## 5. Agent Router

* Decides which retriever to use

---

## 6. Answer Generator

* Combines retrieved data
* Generates final response

---

## 7. UI (Streamlit)

* User inputs query
* Displays:

  * Selected source
  * Answer
  * Retrieved context

---

# 📁 Project Structure

```
agentic-multisource-rag/
│
├── app/                # Streamlit UI
├── data/               # Raw & processed data
│   ├── raw/
│   └── processed/
│
├── src/
│   ├── ingestion/      # Data loading & preprocessing
│   ├── retrieval/      # Vector DB and retrievers
│   ├── agent/          # Routing logic
│   ├── generation/     # Answer generation
│   └── utils/          # Helper functions
│
├── requirements.txt
├── README.md
└── .env
```

---

# ▶️ How to Run

## 1. Clone repository

```
git clone <your-repo-url>
cd agentic-multisource-rag
```

---

## 2. Create virtual environment

```
python -m venv .venv
```

---

## 3. Activate environment

```
.\.venv\Scripts\Activate.ps1
```

---

## 4. Install dependencies

```
pip install -r requirements.txt
```

---

## 5. Add datasets

Place files inside:

```
data/raw/
```

Required files:

* employees.csv
* support.csv

Create:

```
data/urls.txt
```

Add:

```
https://aws.amazon.com/faqs/
https://www.oracle.com/in/corporate/contact/faq/
```

---

## 6. Run application

```
streamlit run app/streamlit_app.py
```

---

# 💡 Example Queries

## 📊 Employee

* Who is manager of Rahul?
* Which project does Anita work on?

## 📝 Support

* What issues are reported about login failure?

## 🌐 Web

* What services does AWS provide?

---

# 📌 Use Case

This project simulates an **enterprise knowledge assistant** that can:

* Retrieve employee information
* Analyze support issues
* Answer company-related queries

---

# 🚀 Future Improvements

* Replace rule-based routing with LLM-based agent
* Add hybrid retrieval (BM25 + semantic search)
* Add graph-based RAG
* Enable multi-step reasoning
* Add evaluation framework

---


Built an end-to-end Agentic Multi-Source RAG system that dynamically routes queries across structured, unstructured, and web-based data sources using semantic retrieval and modular architecture.
