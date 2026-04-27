# BERT SQL Injection Detection

A fine-tuned BERT model for detecting SQL injection (SQLi) attacks in user input. The model is based on **BERT Base Cased** (L=12, H=768, A=12, 110M parameters) and achieves ~99.86% accuracy on the Test set with model of 512 tokens.

---
![Alt text](results/SQL_DETECTION_OVERVIEW.png)

## Setup

### 1. Clone repository
```bash
git clone https://github.com/viserionnina/bert-sqli-detection.git
cd bert-sqli-detection
```

### 2. Create virtual environment (Mac/Linux)
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

---

## Usage

**First time:** Run all cells in `fine_tuning_bert.ipynb` to train the model.

**With existing model:** Run cells 0–19 in `fine_tuning_bert.ipynb`, skip training cells (21, 22, 26, 27), then continue from cell 29 (loading model).

**Predictions:** Use `prediction.ipynb` to run predictions on custom SQL queries and visualize attention with BertViz.

---

## Dataset

Dataset source: [Kaggle — SQL Injection Dataset](https://www.kaggle.com/datasets/ayahkhaldi/sql-injection-dataset)

The dataset contains SQL queries labeled as:
- `0` — Non-SQL Injection
- `1` — SQL Injection

| Split | Samples |
|-------|---------|
| Train | 98,062 |
| Validation | 32,687 |
| Test | 32,688 |

---

## Model

Two fine-tuned versions are available (not included in the repository due to file size — trained locally):

| Version | Max Tokens | Notes |
|---------|-----------|-------|
| `bert_sqli_model_4_epochs_512_tokens` | 512 | Recommended for more acurate results |
| `bert_sqli_model_4_epochs_256_tokens` | 256 | Faster inference |

Fine-tuning was performed on a MacBook Pro 2021 (M1 Max, 64GB, 1TB).

---

## Best Results (512 tokens, softmax threshold 0.2)

| Metric | Score |
|--------|-------|
| Accuracy | 99.86% |
| Precision | 99.87% |
| Recall | 99.83% |
| F1 | 99.85% |

---

## Project Structure

```
bert-sqli-detection/
├── notebooks/
│   ├── fine_tuning_bert.ipynb   # BERT fine-tuning & initialization
│   └── prediction.ipynb        # Predictions & BertViz attention
├── dataset/
│   ├── Train.csv
│   ├── Val.csv
│   └── Test.csv
├── models/                      # Saved model (train locally)
├── results/                     # Generated plots & visualizations
└── requirements.txt
```

---

## Author

Nicole Ivanković  
University of Rijeka, Faculty of Engineering, Croatia
