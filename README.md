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

