# ⚖️ Contract Analysis System

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![HuggingFace](https://img.shields.io/badge/HuggingFace-Transformers-orange.svg)
![Gradio](https://img.shields.io/badge/Gradio-UI-green.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

> An NLP-powered Contract Analysis System inspired by **JPMorgan's legal document processing pipeline**. This system automatically classifies contract clauses, extracts obligor names, and identifies maturity dates from legal documents using **Legal-BERT** fine-tuned on the **LEDGAR dataset**.

---

## 📌 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Demo](#demo)
- [Dataset](#dataset)
- [Model](#model)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [How to Run](#how-to-run)
- [Results](#results)
- [Technologies Used](#technologies-used)
- [Team](#team)

---

## 📖 Overview

JPMorgan developed an NLP pipeline to process legal documents, using OCR for text extraction followed by transformer models to classify clauses like obligor names and maturity dates. This project replicates that system by:

- Training a **Legal-BERT** model on the **LEDGAR dataset** (60,000+ labeled contract provisions)
- Implementing **Named Entity Recognition (NER)** using SpaCy to extract obligor names and maturity dates
- Adding **OCR support** using pytesseract to extract text from scanned PDFs and images
- Deploying an interactive **Gradio web demo** for real-time contract analysis

---

## ✨ Features

| Feature | Description |
|---|---|
| 📌 **Clause Classification** | Classifies contract clauses into 60+ types like Termination, Payment, Governing Law |
| 👤 **Obligor Name Extraction** | Identifies persons and organizations mentioned as obligors |
| 📅 **Maturity Date Detection** | Extracts contract expiry and maturity dates using NER + Regex |
| 📁 **PDF / Image Upload** | OCR-based text extraction from scanned contracts |
| 📝 **Text Input** | Paste contract text directly for instant analysis |
| 📊 **Document Statistics** | Word count, sentence count and contract preview |
| 🌐 **Gradio Web Demo** | Interactive web interface for real-time analysis |

---

## 🎥 Demo

Run the Gradio demo by executing the final cell in the notebook. You will get a public shareable link:

```
Running on public URL: https://xxxxxx.gradio.live
```

**Sample Input:**
```
This Loan Agreement is entered into as of January 15, 2024,
by and between JPMorgan Chase & Co. and ABC Corporation,
and John Smith as the authorized obligor and guarantor.
The maturity date of this loan shall be December 31, 2026.
Either party may terminate this agreement upon 30 days written notice.
```

**Sample Output:**
```
📌 CLAUSE TYPE    : Termination
   CONFIDENCE     : 92.5%
👤 OBLIGOR NAMES  : JPMorgan Chase & Co., John Smith, ABC Corporation
📅 MATURITY DATES : December 31, 2026
```

---

## 📦 Dataset

**LEDGAR Dataset** (via LexGLUE Benchmark)

| Property | Details |
|---|---|
| Source | SEC (Securities and Exchange Commission) filings |
| Size | 60,000+ labeled contract provisions |
| Labels | 60+ clause types |
| Publisher | Stanford Law School |
| HuggingFace | `lex_glue` → `ledgar` |

```python
from datasets import load_dataset
dataset = load_dataset("lex_glue", "ledgar", trust_remote_code=True)
```

---

## 🤖 Model

**Legal-BERT** (`nlpaueb/legal-bert-base-uncased`)

- Pre-trained on large corpus of legal documents
- Fine-tuned on LEDGAR dataset for clause classification
- 60+ output labels for clause type prediction

**NER Model** — SpaCy (`en_core_web_sm`)
- Extracts PERSON and ORG entities as obligor names
- Extracts DATE entities as maturity dates
- Regex patterns for additional date formats

**OCR** — pytesseract
- Extracts text from scanned PDF contracts
- Supports PNG, JPG, JPEG image formats

---

## 📁 Project Structure

```
Contract-Analysis-System/
│
├── Contract_Analysis_System.ipynb   # Main Colab notebook
├── README.md                        # Project documentation
├── requirements.txt                 # Dependencies
├── sample_contract.pdf              # Sample contract for testing
└── ledgar_model_final/              # Saved fine-tuned model
    ├── config.json
    ├── model.safetensors
    └── tokenizer files
```

---

## ⚙️ Installation

```bash
pip install transformers datasets gradio torch scikit-learn seqeval
pip install pytesseract pillow pdf2image spacy
python -m spacy download en_core_web_sm
apt-get install tesseract-ocr
apt-get install poppler-utils
```

---

## 🚀 How to Run

### Option 1 — Google Colab (Recommended)
1. Open `Contract_Analysis_System.ipynb` in Google Colab
2. Go to **Runtime → Change runtime type → T4 GPU**
3. Run all cells from **Cell 1 to Cell 17**
4. Cell 17 launches the **Gradio demo** with a public link

### Option 2 — Local
```bash
git clone https://github.com/yourusername/contract-analysis-system.git
cd contract-analysis-system
pip install -r requirements.txt
jupyter notebook Contract_Analysis_System.ipynb
```

---

## 📊 Results

| Metric | Score |
|---|---|
| Accuracy | ~78% |
| F1 Score (Weighted) | ~76% |
| Training Samples | 2000 |
| Validation Samples | 300 |
| Test Samples | 300 |

**Confusion Matrix** — Generated during evaluation showing performance across all 60+ clause types.

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| **Legal-BERT** | Transformer model for legal text understanding |
| **LEDGAR Dataset** | 60,000+ labeled contract provisions |
| **HuggingFace Transformers** | Model loading and fine-tuning |
| **SpaCy** | Named Entity Recognition |
| **pytesseract** | OCR for PDF/Image text extraction |
| **Gradio** | Interactive web demo |
| **Google Colab** | Training environment with free GPU |
| **Python** | Core programming language |

---

## 🏢 Real World Inspiration

This project is inspired by **JPMorgan Chase's** NLP pipeline for legal document automation:

> *"JPMorgan developed an NLP pipeline to process legal documents, using OCR for text extraction followed by transformer models to classify clauses like obligor names and maturity dates."*

Our system replicates this by combining OCR, transformer-based clause classification, and NER into a single automated pipeline.

---

## 👥 Team

| Name | Role |
|---|---|
| Your Name | Model Training & Development |
| Team Member 2 | Data Preprocessing |
| Team Member 3 | UI & Deployment |

> **Subject:** Natural Language Processing (NLP) / Deep Learning
> **Institution:** Your College Name

---

## 📄 License

This project is licensed under the MIT License.

---

⭐ **If you found this helpful, please star the repository!**
