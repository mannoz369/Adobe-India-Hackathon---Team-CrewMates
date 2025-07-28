# Persona-Driven Document Intelligence

**Adobe India Hackathon – Challenge 1B**

This repository presents a robust and scalable solution for **Challenge 1B** of the **Adobe India Hackathon**. The system intelligently analyzes large document collections and extracts **persona-specific insights** using an advanced **Retrieval-Augmented Generation (RAG)** pipeline. It is designed to work across diverse domains such as travel, learning resources, and recipes.

---

## 🔍 Problem Statement

Given multiple collections of documents, each associated with a specific user persona, build a pipeline that retrieves the **most relevant content** tailored to that persona’s needs. The solution must go beyond basic semantic search and include **context filtering**, **semantic ranking**, and **intelligent summarization**.

---

## 🚀 Key Features

### ✅ Two-Stage Retrieval for High Precision

To address challenges like **negative constraints** (e.g., "vegetarian" recipes excluding meat-related content), we use a **two-stage retrieval process**:

* **Stage 1: Keyword Filtering**
  Removes irrelevant or contradictory content using persona-based keyword constraints.

* **Stage 2: Semantic Ranking**
  Ranks the filtered content using a fine-tuned `sentence-transformers` model for contextual relevance.

### ✨ AI-Powered Title Generation

Titles are generated using a **local generative model** (`google/flan-t5-base`) instead of relying on heuristics or raw headers. This ensures each extracted section has a **clear, human-readable, and persona-aligned** title.

### 🌐 Global Ranking Across Documents

Rather than selecting top results per document, all matched sections across a collection are pooled and **globally ranked** to ensure **only the best insights are included** in the final output.

### ⚙️ Unified & Configurable Architecture

The entire system is managed via a single Python script – `run_analysis.py` – which accepts collection paths and persona details via CLI arguments. This ensures consistency, scalability, and ease of integration.

---

## 🧱 Project Structure

```
├── Collection_1/
│   ├── PDFs/
│   └── challenge1b_input.json
├── Collection_2/
│   ├── PDFs/
│   └── challenge1b_input.json
├── Collection_3/
│   ├── PDFs/
│   └── challenge1b_input.json
├── approach_explanation.md
├── Dockerfile
├── README.md
├── requirements.txt
└── run_analysis.py
```

---

## ⚙️ How to Run the Project

### Step 1: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 2: Execute the Analysis

Run the script by providing the path to any of the collections:

```bash
python run_analysis.py ./Collection_1/
```

This will generate the output file:

```
./Collection_1/challenge1b_output.json
```

Repeat similarly for other collections (`Collection_2`, `Collection_3`, etc.).

---

## 💡 Tech Stack

| Component        | Technology                                       |
| ---------------- | ------------------------------------------------ |
| Language         | Python 3.10+                                     |
| Retrieval Model  | `sentence-transformers/all-MiniLM-L6-v2`         |
| Title Generator  | `google/flan-t5-base` (HuggingFace Transformers) |
| PDF Parsing      | PyMuPDF (`fitz`)                                 |
| CLI Config       | `argparse`                                       |
| Containerization | Docker                                           |

---

## 📦 Docker Support

To run the project inside a Docker container:

```bash
docker build -t persona-doc-intel .
docker run -v $(pwd):/app persona-doc-intel python run_analysis.py ./Collection_1/
```

---

## ✅ Highlights

* 🔍 **Accuracy**: Combines rule-based filtering with semantic understanding for high precision.
* 📑 **Clarity**: AI-generated section titles make raw data highly digestible.
* 🧩 **Modular**: Designed for plug-and-play across various domains and use cases.
* 🧠 **Scalable**: Supports large-scale document collections without sacrificing performance.

---

