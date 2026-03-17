#  **Imbalance-Aware Parameter-Efficient Fine-Tuning for Legal Rhetorical Role Classification**

---

##  1. Overview

This repository contains the implementation of our proposed **imbalance-aware parameter-efficient fine-tuning (PEFT)** methods for **legal rhetorical role classification**.

---

### 🔹 1.1 Proposed Methods

- **RC-LoRA + UGR** *(Role-Constrained LoRA with Uncertainty-Guided Reweighting)*
- **DLR-PEFT** *(Dynamic Low-Rank Parameter-Efficient Fine-Tuning)*

---

### 🔹 1.2 Baselines

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

###  1.3 Key Insight

Our proposed methods significantly improve **minority class performance** while maintaining strong overall accuracy, making them highly effective for **imbalanced legal NLP tasks**.

---

#  2. Dataset

We use a **legal rhetorical role classification dataset** consisting of annotated sentences from legal case documents.

---

###  2.1 Data Availability

We use the publicly available **Legal Rhetorical Role dataset**:

🔗 https://legal-nlp-ekstep.github.io/Competitions/Rhetorical-Role/

- ❌ Dataset is not redistributed in this repository  
- ✅ Users must download it from the official source  

---

###  2.2 Dataset Directory Structure
build_jsonl/
├── build_train.jsonl # Training set
├── build_dev.jsonl # Validation set
└── build_test.jsonl # Test set

---

###  2.3 File Paths Used in Code

```python
TRAIN_PATH = "build_jsonl/build_train.jsonl"
DEV_PATH   = "build_jsonl/build_dev.jsonl"
TEST_PATH  = "build_jsonl/build_test.jsonl"



### 📄 2.4 Expected Format

Each file is in **JSONL format**, where each line represents one document:

```json
{
  "id": "doc_0",
  "sentences": [
    "PETITIONER: THE COMMISSIONER OF INCOME-TAX...",
    "DATE OF JUDGMENT: 05/05/1961...",
    "It entered into transactions...",
    "The assessee claimed deduction..."
  ],
  "labels": [
    "PREAMBLE",
    "PREAMBLE",
    "FACTS",
    "FACTS"
  ]
}

###  2.5 Corpus Statistics (Summary)

| Split              | Documents | Sentences | Tokens | Avg Tokens/Doc |
|--------------------|----------|-----------|--------|----------------|
| Train              | 247      | 28,986    | 938K   | 3,797          |
| Validation         | 30       | 2,879     | 88K    | 2,947          |
| Test (In-domain)   | 50       | 4,158     | 134K   | 2,681          |
| Test (Out-domain)  | 27       | 4,292     | 127K   | 4,722          |
| **Total**          | **354**  | **40,315**| **1.3M** | **3,638**     |

##  3. Task Definition

Legal documents are long and complex, with information distributed across sections.  
To enable structured understanding, documents are segmented into **Rhetorical Roles (RRs)** — *semantically coherent units representing different functional parts of a legal judgment.*

---

###  3.1 Label Set (Rhetorical Roles)

We use **12 rhetorical roles + 1 NONE label**:

- **PREAMBLE** – Metadata *(court, parties, judges, headnotes)*
- **FAC** – Facts and case background chronology
- **RLC** – Ruling and reasoning by lower courts
- **ISSUE** – Legal questions framed by the court
- **ARG_PETITIONER** – Arguments by petitioner
- **ARG_RESPONDENT** – Arguments by respondent
- **ANALYSIS** – Court’s reasoning and discussion
- **STA** – Statutes, acts, and legal provisions
- **PRE_RELIED** – Precedents relied upon
- **PRE_NOT_RELIED** – Precedents not relied upon
- **RATIO** – Core reasoning behind the decision
- **RPC** – Final ruling by present court
- **NONE** – Sentences not belonging to any category

---

###  3.2 Key Characteristics

-  Long documents (~3600 tokens per document)
-  Highly **imbalanced label distribution**
-  Requires **context-aware modeling**

---

##  4. Installation

### 4.1 Clone Repository

```bash
git clone https://github.com/pavithraneelamegam/CLASS-IMBALANCE-AWARE-PEFT.git
cd CLASS-IMBALANCE-AWARE-PEFT

### 4.2 Install Dependencies

```bash
pip install torch transformers peft datasets scikit-learn pandas numpy matplotlib seaborn bitsandbytes






##  5. How to Run

### 5.1 Baseline Models

Run the following notebooks:

- `BASELINE-INLEGALBERT-HSLN.ipynb`
- `BASELINE+LORA.ipynb`
- `BASELINE+QLORA.ipynb`
- `BASELINE+ADALORA.ipynb`
- `BASELINE+SUPERLORA.ipynb`
- `BASELINE+PROMPT TUNING.ipynb`

---

### 5.2 Proposed Methods

- `RC-LORA+UGR.ipynb`
- `DLR-PEFT.ipynb`

---

### 5.3 LLM-Based Methods

- `MISTRAL 7B-Fewshot.ipynb`
- `QWEN - Fewshot.ipynb`
- `QWEN- SFT.ipynb`

##  6. Evaluation Metrics

We report:

- Accuracy  
- Macro-F1  
- Weighted-F1  
- Minority Macro-F1 *(important for imbalance evaluation)*

---

## 7. Acknowledgement

We thank:

**Bhattacharya et al. (2019, 2021)**  
for introducing rhetorical role annotations for legal documents.
