# Telecom Customer Churn Prediction

An end-to-end machine learning project predicting customer churn for a telecom provider. The project spans a full data science workflow: solution planning, feature engineering, model training, and a final written report. The target metric was an **AUC-ROC score of 0.85 or above**.

---

## Project Structure

This notebook is organized into three parts:

| Part | Description |
|---|---|
| **Part 1 – Solution Plan** | Dataset exploration, preprocessing strategy, feature engineering plan, and proposed work plan |
| **Part 2 – Solution Code** | Full implementation: data loading, EDA, feature engineering, model training, and evaluation |
| **Part 3 – Final Report** | Written summary of steps performed, difficulties encountered, and final model results |

---

## Dataset

Four CSV files from a telecom provider, joined on `customerID`:

| File | Description |
|---|---|
| `contract.csv` | Contract type, payment method, billing info, start/end dates |
| `personal.csv` | Customer demographics (gender, age, dependents) |
| `internet.csv` | Internet service features |
| `phone.csv` | Phone service features |

**7,043 customers** — churn rate ~26%.

---

## Feature Engineering

- **Churn target:** Binary flag derived from `EndDate` (1 = churned, 0 = active)
- **Tenure:** Months between contract start and end (or reference date `2020-02-01` for active customers)
- Column standardization, datetime parsing, `TotalCharges` numeric conversion
- One-hot encoding for categoricals, binary encoding for Yes/No fields

---

## Models Compared

| Model | Validation AUC-ROC |
|---|---|
| **Logistic Regression** | **Best** |
| Random Forest | Competitive |
| XGBoost | Competitive |

All models trained with class weighting to handle the ~26% churn imbalance.

---

## Final Results

**Final Model: Logistic Regression** (retrained on train + validation, evaluated once on test set)

| Metric | Score |
|---|---|
| **AUC-ROC** | **0.837** |
| Accuracy | 0.733 |

The model provides strong churn risk ranking and serves as a reliable baseline for business decision-making.

---

## Key Challenges & Solutions

- **Data type issues** — `TotalCharges` stored as object; fixed with `pd.to_numeric(errors='coerce')`
- **Churn definition** — Active customers stored `'No'` instead of a date; replaced with `NaT` and tenure calculated using a fixed reference date
- **Data leakage** — Initial evaluation used the test set for model comparison; fixed by implementing a proper **train/validation/test split**
- **Class imbalance** — Addressed with `class_weight='balanced'` in Logistic Regression/Random Forest and `scale_pos_weight` in XGBoost

---

## Tech Stack

- **Python 3**
- **Pandas / NumPy** — data loading, merging, feature engineering
- **Matplotlib / Seaborn** — EDA visualizations
- **Scikit-learn** — Logistic Regression, Random Forest, Pipeline, ColumnTransformer, AUC-ROC
- **XGBoost** — gradient boosting classifier

---

## How to Run

1. Clone the repository
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn xgboost
   ```
3. Place the four dataset files in `/datasets/final_provider/` (or update load paths in the notebook)
4. Open and run `telecom_customer_churn_prediction.ipynb` in Jupyter Notebook or JupyterLab

---

## Project Structure

```
.
├── telecom_customer_churn_prediction.ipynb   # Combined notebook (plan + code + report)
└── README.md                                 # Project documentation
```

---

## Concepts Demonstrated

- End-to-end ML project planning and execution
- Multi-table data merging and feature engineering
- Churn target creation from transactional date data
- Train/validation/test splitting to prevent data leakage
- Class imbalance handling
- Model benchmarking with AUC-ROC
- Scikit-learn Pipelines with ColumnTransformer
- Written project reporting and findings communication
