# **Imbalance-Aware Parameter-Efficient Fine-Tuning for Legal Rhetorical Role Classification**
## 📌 Overview

This repository contains the implementation of our proposed **imbalance-aware parameter-efficient fine-tuning (PEFT)** methods for **legal rhetorical role classification**:

### 🔹 Proposed Methods
- **RC-LoRA + UGR** *(Role-Constrained LoRA with Uncertainty-Guided Reweighting)*
- **DLR-PEFT** *(Dynamic Low-Rank Parameter-Efficient Fine-Tuning)*

---

### 🔹 Baselines

We benchmark our methods against:

- **Full Fine-Tuning**
  - InLegalBERT + HSLN  

- **Standard PEFT Methods**
  - LoRA  
  - QLoRA  
  - AdaLoRA  
  - SuperLoRA  
  - Prompt Tuning  

- **LLM-Based Approaches**
  - Mistral-7B  
  - Qwen-2.5  

---

### 🚀 Key Insight

Our proposed methods significantly improve **minority class performance** while maintaining strong overall accuracy, making them highly effective for **imbalanced legal NLP tasks**.
## 📦 Dataset

We use a **legal rhetorical role classification dataset** consisting of annotated sentences from legal case documents.

---

### ⚠️ Data Availability

Due to licensing restrictions:

- ❌ The dataset is not included in this repository  
- ✅ Users are required to place the dataset manually  

Expected directory structure:

---

### 📄 Expected Format

Each file should follow:


---

## 📊 Corpus Statistics (Summary)

| Split | Documents | Sentences | Tokens | Avg Tokens/Doc |
|------|----------|----------|--------|----------------|
| Train | 247 | 28,986 | 938K | 3797 |
| Validation | 30 | 2,879 | 88K | 2947 |
| Test (In-domain) | 50 | 4,158 | 134K | 2681 |
| Test (Out-domain) | 27 | 4,292 | 127K | 4722 |
| **Total** | **354** | **40,315** | **1.3M** | **3638** |

---

## 🧠 Task Definition

Legal documents are long and complex, with information distributed across sections.  
To enable structured understanding, documents are segmented into **Rhetorical Roles (RRs)** — semantically coherent units representing different functional parts of a legal judgment.

---

## 🏷️ Label Set (Rhetorical Roles)

We use **12 rhetorical roles + 1 NONE label**, refined from prior work with domain expert validation.

### 🔹 Core Labels

- **PREAMBLE**  
  Metadata such as court name, parties, judges, and headnotes.

- **FAC (Facts)**  
  Chronology of events leading to the case, including FIR, proceedings, and background.

- **RLC (Ruling by Lower Court)**  
  Decisions, reasoning, and judgments from lower courts.

- **ISSUE**  
  Legal questions framed by the court.

---

### 🔹 Arguments

- **ARG_PETITIONER**  
  Arguments made by petitioner’s lawyers.

- **ARG_RESPONDENT**  
  Arguments made by respondent’s lawyers.

---

### 🔹 Court Analysis

- **ANALYSIS**  
  Court’s reasoning, interpretation of facts, laws, and prior cases.

- **STA (Statute)**  
  References to laws, acts, sections, or legal provisions.

- **PRE_RELIED**  
  Precedent cases relied upon by the court.

- **PRE_NOT_RELIED**  
  Precedents discussed but not used in final reasoning.

---

### 🔹 Decision

- **RATIO**  
  Core reasoning behind the decision.

- **RPC (Ruling by Present Court)**  
  Final judgment, conclusion, and court order.

---

### 🔹 Other

- **NONE**  
  Sentences that do not belong to any defined category.

---

## 🎯 Key Characteristics

- Long documents (avg ~3600 tokens per document)
- Highly **imbalanced label distribution**
- Requires **context-aware modeling**
- Suitable for:
  - Legal NLP
  - Document understanding
  - Discourse modeling

---
