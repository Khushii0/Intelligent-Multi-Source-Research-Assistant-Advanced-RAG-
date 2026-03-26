📚 Intelligent Multi-Source Research Assistant (Advanced RAG)

Overview:
This project implements an **Intelligent Multi-Source Research Assistant** using an **Advanced Retrieval-Augmented Generation (RAG)** pipeline.
The system allows users to upload **multiple document formats (PDF, CSV, Markdown)** and ask natural language questions. Instead of relying purely on LLM knowledge, the assistant **retrieves relevant information from the uploaded documents and generates grounded, explainable answers**.

---
## Objectives
* Build a **document-aware AI assistant**
* Enable **multi-source reasoning**
* Reduce hallucination using **RAG**
* Provide **transparent answers with citations**
* Dynamically handle different query types using **LLM tool routing**

---
## Supported Data Sources
* 📄 PDF (technical documentation)
* 📊 CSV / JSON (structured data, benchmarks)
* 📝 Markdown (unstructured notes)

---
##  Key Features
### 1. Hybrid Retrieval (Advanced)
Combines: **BM25 keyword search** and **Vector similarity search**
✔ Improves retrieval accuracy
✔ Handles both exact and semantic queries

---
### 2. Tool-Based LLM Architecture
Instead of a single LLM call, the system uses **specialized tools**:

| Tool                         | Purpose                           |
| ---------------------------- | --------------------------------- |
| 🧾 Factual QA Tool           | Direct answers from documents     |
| 📊 Comparative Analysis Tool | Compare metrics across sources    |
| 📝 Summary Tool              | Generate document/topic summaries |

✔ Better structured reasoning and More accurate outputs

---
### 🧠 3. Intelligent Router Agent
* Classifies user intent
* Automatically selects the correct tool

Example:
* “What is RAG?” → QA Tool
* “Compare models” → Comparative Tool
* “Summarize document” → Summary Tool

---
### 4. Clarification Agent (Ambiguity Handling)
Detects unclear queries like:
> “Which is the best model?”
Responds with:
> “Best in terms of accuracy, latency, or memory?”
✔ Prevents incorrect assumptions and Improves interaction quality

---
### 5. Multi-Source Reasoning
* Combines information from **PDF + CSV + Markdown**
* Enables cross-referencing between: explanations and structured metrics

---
### 6. Source Attribution (Explainability)
Each answer includes: File name, Page number (PDF) and Row index (CSV)
Example:
```
llm_system_design.pdf (page 2)
model_benchmarks.csv (row 3)
```

### 7. Confidence Scoring System
Confidence is computed based on:
* Number of supporting sources
* Retrieval strength (hybrid scores)
Example:
```
High (90%) — multiple strong sources  
Medium (60%) — moderate support  
Low (25%) — weak evidence  
```

✔ Also provides **source-level confidence**
---

### 🧾 8. Knowledge Base Awareness
* Generates a **summary of uploaded documents**
* Used by the clarification agent for context-aware decisions
---

### 🎛️ 9. Interactive Gradio UI
Users can:
* Upload documents dynamically
* Ask questions
* View:
  * Answer
  * Sources
  * Confidence
  * Tool used

---
## 🧪 Example Queries
### Factual
```
What is Retrieval Augmented Generation?
```
### Comparative
```
Which model has the lowest latency?
```
### Cross-source reasoning
```
Compare model performance using explanation and benchmark data
```
### Summary
```
Summarize the uploaded documents
```
### Ambiguous (Triggers Clarification)
```
Which is the best model?
```
---

## 🛠️ Tech Stack
* **LangChain** → orchestration
* **ChromaDB** → vector database
* **BM25 Retriever** → keyword search
* **Sentence Transformers (BGE)** → embeddings
* **OpenRouter / LLM APIs** → generation
* **Gradio** → UI

---
## Implementation Details
### 🔹 Chunking Strategy
* Chunk size: ~800
* Overlap: ~150
* Metadata: source file, page / row and chunk ID

---
### 🔹 Hybrid Retrieval Logic
```
BM25 match → +2 score
Vector match → +1 score
```
Top-k chunks are ranked and selected.
---

### 🔹 Error Handling
* Prevents querying before document upload
* Handles empty retrieval cases
* Avoids hallucination with grounded prompts

---
## How to Run the Project
### 1️⃣ Install Dependencies
```bash
pip install langchain langchain-community langchain-huggingface chromadb gradio sentence-transformers
```
### 2️⃣ Set API Key (if using OpenRouter / LLM)
```python
import os
os.environ["OPENAI_API_KEY"] = "your_api_key"
```
### 3️⃣ Run Notebook / Script
Run all cells **top to bottom**
### 4️⃣ Launch UI
```python
interface.launch(share=True)
```
### 5️⃣ Upload Documents
* PDF
* CSV
* Markdown
### 6️⃣ Ask Questions 🎯

## 🏆 Highlights (What Makes This Project Stand Out)
* ✅ Hybrid Retrieval (not just vector search)
* ✅ Tool-based modular LLM system
* ✅ Intelligent query routing
* ✅ Clarification agent for ambiguity
* ✅ Source-level confidence scoring
* ✅ Multi-format document ingestion
* ✅ Explainable AI (citations + metadata)
* ✅ Fully interactive UI

---
## 📌 Future Improvements
* Conversation memory (multi-turn QA)
* Better ranking using re-rankers
* Streaming responses
* Deployment (HuggingFace Spaces / FastAPI)

---
## 👩‍💻 Author
Khushi Aggarwal
B.Tech CSE (AI)

## ⭐ Final Note
This project demonstrates how combining **retrieval, reasoning, and modular LLM design** can create a reliable and explainable AI system for real-world document analysis.
