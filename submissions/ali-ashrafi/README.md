# project-01-data-cleaning

## E-Commerce Customer Data Integrity & Cleaning Pipeline
---
[![Python](https://img.shields.io/badge/Python-3.12%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)


An end-to-end data auditing, validation, and remediation pipeline for e-commerce transactional customer data. This project systematically addresses missingness, demographic range violations, and financial reconciliation discrepancies while preserving operational edge cases for downstream analysis.

---

## 📌 Executive Summary

Raw tabular business datasets frequently suffer from upstream recording failures, manual entry errors, and arithmetic inconsistencies. This repository documents a deterministic data cleaning pipeline designed to guarantee strict data integrity before exploratory data analysis (EDA) and feature modeling.

### Key Remediation Highlights:
- **Deduplication & Index Integrity:** Dropped exact duplicate records and verified primary key uniqueness across `customer_id`.
- **Demographic Normalization:** Flagged physiologically impossible age records ($age > 120$) and imputed missing demographic values using the robust median ($45.0$).
- **Deterministic Revenue Reconciliation:** Reconstructed corrupt and missing aggregate expenditures deterministically via:
  $$S_{\text{total}} = N_{\text{purchases}} \times \bar{V}_{\text{order}}$$

- **Operational Edge-Case Handling:** Preserved and logged ambiguous operational records satisfying the anomaly condition:
  $$N_{\text{returned}} > N_{\text{purchases}}$$

---

## 🛠️ Data Quality Audit Matrix

| Metric / Check | Raw State | Remediation Action | Cleaned State |
| :--- | :--- | :--- | :--- |
| **Row Count** | 61 records | Removed exact duplicate entry | 60 validated records |
| **Demographic Outliers** | `age = 145` | Capped & imputed with sample median ($45.0$) | $0 < \text{age} \le 120$ |
| **Missing Values** | Nulls in `age`, `total_spending` | Median & deterministic recalculation | 0 unhandled nulls |
| **Revenue Consistency** | Arithmetic discrepancies in spending | Re-computed using Ground-Truth Order Value | 100% mathematically verified |
| **Data Types** | String dates & implicit float types | Cast to native `datetime64[ns]` and `int64` | Optimized native dtypes |

---

## 📁 Repository Structure
```text
ali-ashrafi/
│
├── .gitignore
├── requirements.txt
├── README.md
│
├── data/
│   ├── raw/
│   │   └── first_dataset.xlsx
│   └── processed/
│       └── cleaned_customers.xlsx
│
└── notebooks/
└── 01_data_cleaning_ali-ashrafi.ipynb
```
---

## 🚀 Quickstart & Reproducibility

**1. Clone the Repository**

```bash
git clone https://github.com/<your-username>/ecommerce-data-cleaning.git
cd ecommerce-data-cleaning
```


**2.Environment Setup**


```bash
#Create a virtual environment
python -m venv venv
```
```bash
#Activate the virtual environment

#On Linux / WSL:
source venv/bin/activate

#On Windows (PowerShell):
.\venv\Scripts\Activate.ps1
```
```bash
#Install exact locked dependencies
pip install -r requirements.txt
```

**3. Run the Pipeline**
Launch Jupyter Lab/Notebook and execute the cleaning workflow:

```bash
jupyter notebook notebooks/cleaned_dataset_ali_ashrafi.ipynb
```

## Getting Started

```bash
# 1. Create and activate a virtual environment
python -m venv .venv
source .venv/bin/activate        # Linux / macOS
.venv\Scripts\activate           # Windows

# 2. Install dependencies
pip install -r requirements.txt

# 3. Launch Jupyter Lab
jupyter lab notebook/analysis_notebook_clean.ipynb
```











## 🛠️ Built With 
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)


## 👤 Author & Contact
  * 🐙 **GitHub:** [@ali-ashrafi](https://github.com/ali-ashrafi)
  * ✉️ **Email:** [eng.a.ashrafi@gmail.com](mailto:your.email@gmail.com)
  * 📍 **Location:** Iran *(Open to Relocation / Remote)*






