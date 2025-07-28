# 🔍 Adobe India Hackathon 2025 – Round 2

**Team Name:** `CrewMates`
**Challenges:**

* ✅ Challenge 1A – *Understand Your Document (Outline Extraction)*
* ✅ Challenge 1B – *Persona-Driven Document Intelligence*

---

## 👨‍💻 Team Details

| Name                   | College                             |
| ---------------------- | ----------------------------------- |
| Manoj Sri Sai Bodapudi | Amrita Vishwa Vidyapeetham, Chennai |
| Vaka Tharun Kumar      | Amrita Vishwa Vidyapeetham, Chennai |
| Yendluri Sathvika      | Amrita Vishwa Vidyapeetham, Chennai |


## 🧠 Overview of Our Submission

### 🔹 Challenge 1A – **Outline Extraction from PDFs**

We built a **secure, offline, Dockerized pipeline** that extracts structured outlines (headings, subheadings) from PDF documents.
The output is clean, hierarchical, and paginated—ideal for TOC generation, summarization, and search indexing.

* 📄 Input: Raw PDFs
* 📤 Output: JSON file with title + outline (H1, H2, etc.)
* 🔒 Security: No external calls; `--network none` in Docker
* ⚙️ Output ready for downstream semantic processing

**Key Technologies:** PyMuPDF, Font Heuristics, Docker

📁 Detailed README: [`Challenge 1A`](./Challenge_1a/README.md)

---

### 🔹 Challenge 1B – **Persona-Driven Document Intelligence (RAG Pipeline)**

We implemented an advanced **Retrieval-Augmented Generation (RAG)** pipeline that tailors content extraction based on **user personas** like vegetarian users, learners, or travelers.

#### 💡 Features:

* 🔍 **Two-Stage Retrieval**:

  * **Keyword Filtering** removes persona-violating sections (e.g., meat items for vegetarian users).
  * **Semantic Ranking** using `sentence-transformers` ensures contextually relevant results.
* 🧠 **Generative AI Title Generator**: Clean section titles using `google/flan-t5-base`.
* 🌐 **Global Scoring** across entire document collections.
* 🧰 **CLI + Modular Design**: A single Python script handles all personas and collections dynamically.

**Key Technologies:** SentenceTransformers, HuggingFace Transformers, Flan-T5, PyMuPDF, Python

📁 Detailed README: [`Challenge 1B`](./Challenge_1b/README.md)

## 📌 Final Notes

This submission reflects a **modular**, **secure**, and **intelligent document understanding system**. It is:

* ✅ Persona-aware
* ✅ Scalable
* ✅ Ready for downstream AI tasks
* ✅ Built with production-grade engineering practices

We thank Adobe for this amazing opportunity to innovate on real-world document intelligence challenges.
