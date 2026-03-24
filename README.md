# Contract-Analysis-System
NLP based Contract Analysis System using Legal-BERT
# ⚖️ Contract Analysis System

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![HuggingFace](https://img.shields.io/badge/HuggingFace-Transformers-orange.svg)
![Gradio](https://img.shields.io/badge/Gradio-UI-green.svg)
![Legal-BERT](https://img.shields.io/badge/Model-Legal--BERT-purple.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

> An NLP-powered Contract Analysis System inspired by **JPMorgan's legal document 
> processing pipeline**. Automatically classifies contract clauses, extracts obligor 
> names and identifies maturity dates using **Legal-BERT** fine-tuned on **LEDGAR dataset**.

---

## 📸 Screenshots

### 🖥️ Gradio Web Interface
![Demo Screenshot](demo(1).png)

### 📊 Sample Output
![Output Screenshot](image(4).png)



---

## 📌 Table of Contents
- [Overview](#overview)
- [Features](#features)
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

JPMorgan developed an NLP pipeline to process legal documents, using OCR for text 
extraction followed by transformer models to classify clauses like obligor names and 
maturity dates. This project replicates that system by:

- Training **Legal-BERT** on the **LEDGAR dataset** (60,000+ labeled contract provisions)
- Implementing **NER** using SpaCy to extract obligor names and maturity dates
- Adding **OCR support** using pytesseract for scanned PDFs and images
- Deploying an interactive **Gradio web demo** for real-time contract analysis

---

## ✨ Features

| Feature | Description |
|---|---|
| 📌 Clause Classification | 60+ clause types — Termination, Payment, Governing Law |
| 👤 Obligor Name Extraction | Identifies persons and organizations as obligors |
| 📅 Maturity Date Detection | Extracts contract expiry and maturity dates |
| 📁 PDF / Image Upload | OCR-based text extraction from scanned contracts |
| 📝 Text Input | Paste contract text directly for instant analysis |
| 📊 Document Statistics | Word count, sentence count and contract preview |
| 🌐 Gradio Web Demo | Interactive web interface for real-time analysis |

---

## 📦 Dataset

**LEDGAR Dataset** (via LexGLUE Benchmark)

| Property | Details |
|---|---|
| Source | SEC filings |
| Size | 60,000+ labeled contract provisions |
| Labels | 60+ clause types |
| Publisher | Stanford Law School |
```python
from datasets import load_dataset
dataset = load_dataset("lex_glue", "ledgar", trust_remote_code=True)
```

---

## 🤖 Model Architecture
```
Contract Text (Input)
        ↓
   OCR Extraction
  (pytesseract)
        ↓
   Tokenization
  (Legal-BERT)
        ↓
  Fine-tuned Model
        ↓
  ┌─────────────────────────┐
  │                         │
Clause              Named Entity
Classification      Recognition
(60+ types)         (SpaCy NER)
  │                         │
Clause Type         Obligor Names
+ Confidence        + Maturity Dates
  └─────────────────────────┘
        ↓
   Gradio Demo
   (Output)
```

---

## 📁 Project Structure
```
Contract-Analysis-System/
│
├── Contract_Analysis_System.ipynb   ← Main Colab notebook
├── README.md                        ← Project documentation
├── requirements.txt                 ← Dependencies
├── sample_contract.pdf              ← Sample contract for testing
├── demo(1).png                     ← Gradio UI screenshot
├── image(4).png                   ← Sample output screenshot

```

---

## ⚙️ Installation
```bash
pip install -r requirements.txt
python -m spacy download en_core_web_sm
apt-get install tesseract-ocr
apt-get install poppler-utils
```

---

## 🚀 How to Run

### Google Colab (Recommended)
1. Open `Contract_Analysis_System.ipynb` in Google Colab
2. Go to **Runtime → Change runtime type → T4 GPU**
3. Run all cells from **Cell 1 to Cell 17**
4. Cell 17 launches **Gradio demo** with public link

---

## 📊 Results

| Metric | Score |
|---|---|
| Accuracy | ~78% |
| F1 Score (Weighted) | ~76% |
| Training Samples | 2000 |
| Test Samples | 300 |

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Legal-BERT | Transformer model for legal text |
| LEDGAR Dataset | 60,000+ labeled contract provisions |
| HuggingFace Transformers | Model loading and fine-tuning |
| SpaCy | Named Entity Recognition |
| pytesseract | OCR for PDF/Image extraction |
| Gradio | Interactive web demo |
| Google Colab | Training with free GPU |

---

## 👥 Team

| Name | Role |
|---|---|
| Your Name | Model Training & Development |
| Team Member 2 | Data Preprocessing |
| Team Member 3 | UI & Deployment |

> **Subject:** Natural Language Processing / Deep Learning
> **Institution:** Your College Name

---

## 📄 License
MIT License
```

-
