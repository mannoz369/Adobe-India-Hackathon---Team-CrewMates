# Understand Your Document – Outline Extractor

**Adobe India Hackathon – Challenge 1A**

This repository contains a Dockerized solution for **Challenge 1A** of the **Adobe India Hackathon**. The task is to automatically extract a clean, structured outline (headings, subheadings, etc.) from PDF documents. The extracted outline is returned in a standardized JSON format to support downstream document understanding tasks like summarization, indexing, or retrieval.

---

## 📌 Problem Statement

In Challenge 1A, the goal is to create a system that accurately **extracts the structural outline** of any PDF document. This includes headings, subheadings, and their hierarchical levels, along with the page number where each appears.

---

## 🚀 Key Features

* ✅ **Multi-Level Heading Extraction**: Detects headings of various levels (e.g., H1, H2, H3) using font sizes, styles, and layout heuristics.
* 📄 **Page-Aware Mapping**: Each heading includes the **page number** for contextual referencing.
* ⚙️ **Dockerized for Portability**: Runs in a completely isolated Docker environment with **no external dependencies**.
* 🔐 **Offline and Secure**: Runs with `--network none` to ensure **full offline security** and privacy compliance.

---

## 🧱 Project Structure

```
├── input/           # Place your PDF files here
├── output/          # JSON output will be written here
├── Dockerfile       # Docker build configuration
├── main.py          # Outline extraction script
└── README.md        # You're here!
```

---

## 🐳 How to Run

### Step 1: Build the Docker Image

```bash
docker build --platform linux/amd64 -t adobe-outline-extractor .
```

### Step 2: Run the Solution

```bash
docker run --rm \
  -v $(pwd)/input:/app/input \
  -v $(pwd)/output:/app/output \
  --network none \
  adobe-outline-extractor
```

* 📂 Put your `.pdf` files into the `input/` folder.
* 📂 The extracted `.json` outlines will be saved to the `output/` folder.

---

## 📥 Input Format

Drop **raw PDF files** inside the `input/` directory. Example:

```
input/
├── sample_document.pdf
├── user_guide.pdf
```

---

## 📤 Output Format

Each PDF will generate a `.json` file in the following structure:

```json
{
  "title": "Document Title",
  "outline": [
    { "level": "H1", "text": "Introduction", "page": 1 },
    { "level": "H2", "text": "Motivation", "page": 2 },
    { "level": "H1", "text": "Methodology", "page": 3 },
    { "level": "H2", "text": "Approach", "page": 4 }
  ]
}
```

Each outline item includes:

* `level`: Heading level (e.g., H1, H2)
* `text`: The heading/subheading text
* `page`: Page number where the heading appears

---

## 💡 Tech Stack

| Component        | Technology                      |
| ---------------- | ------------------------------- |
| Programming Lang | Python 3.10+                    |
| PDF Parsing      | PyMuPDF (`fitz`)                |
| Text Heuristics  | Font size, font weight, layout  |
| Containerization | Docker                          |
| Security         | Runs offline (`--network none`) |

---

## 📦 Sample Run Output

For a file named `sample_document.pdf`:

```bash
input/
├── sample_document.pdf

output/
├── sample_document.json
```

Example `sample_document.json`:

```json
{
  "title": "Sample Document",
  "outline": [
    { "level": "H1", "text": "Overview", "page": 1 },
    { "level": "H2", "text": "Background", "page": 2 },
    { "level": "H1", "text": "Conclusion", "page": 5 }
  ]
}
```

---
