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
