# Customer Support Ticket Intelligence System

## 📌 Project Overview
Customer support teams handle thousands of tickets daily. Manually categorizing and prioritizing these tickets delays response times and impacts customer satisfaction.

This project builds an **end-to-end NLP system** that:
- Automatically classifies customer support tickets into issue categories
- Predicts ticket priority (Low / Medium / High / Critical)
- Provides a short AI-generated summary for quick understanding
- Exposes predictions via a REST API

The solution is designed to be **fast, scalable, and deployable within hackathon constraints**.

---

## 📂 Dataset
**Source:** Kaggle – Customer Support Ticket Dataset  
**Size:** 8,469 records  

### Key Columns Used
| Purpose | Column Name |
|------|-----------|
| Input Text | `Ticket Description` |
| Category Label | `Ticket Type` |
| Priority Label | `Ticket Priority` |

### Columns Ignored
- Customer PII (Name, Email)
- Resolution text (high missing values)
- Time-based columns (not required for MVP)

---

## 🧠 Problem Formulation
This is a **Supervised NLP Classification Problem**:
- **Input:** Unstructured customer ticket text
- **Outputs:**
  - Ticket Category (multi-class classification)
  - Ticket Priority (multi-class classification)

---

## 🏗️ Pipeline Design (Finalized)
````````````
Raw Ticket Text
→ Light Text Cleaning
→ TF-IDF Vectorization
→ ML Classification Models
├── Category Classifier
└── Priority Classifier
→ Pretrained Text Summarization
→ FastAPI REST Service
→ Deployment
`````````````````````

---

## ⚙️ Technical Choices & Justification

### Text Preprocessing
- Lowercasing
- Removal of URLs and special characters
- No aggressive stopword removal or stemming

**Reason:** Preserve domain-specific semantics in customer complaints.

---

### Feature Engineering
**TF-IDF Vectorization**
- n-grams (1,2)
- Limited feature size for speed and stability

**Reason:**  
TF-IDF performs well on short-to-medium support ticket text and trains extremely fast.

---

### Models
| Task | Model |
|----|------|
| Category Classification | Logistic Regression |
| Priority Prediction | Logistic Regression |

**Reason:**  
Linear models are efficient, interpretable, and reliable for TF-IDF features.

---

### NLP Intelligence
**Pretrained Text Summarization**
- Model: `facebook/bart-large-cnn`
- Used at inference time only

**Reason:**  
Adds AI intelligence without training overhead.

---

## 🔌 API Design
**Endpoint:** `/predict`

### Input
```json
{
  "ticket_text": "My internet has not been working for two days"
}
````
---
### Output
```json
{
  "predicted_category": "Technical issue",
  "predicted_priority": "Critical",
  "summary": "Customer reports prolonged internet connectivity issue."
}

````

---
