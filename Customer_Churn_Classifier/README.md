# Customer Churn Prediction — Supervised Learning

A supervised machine learning project that predicts whether a bank customer will churn (leave) based on their account behavior and demographics.

## Problem Statement

Beta Bank is losing customers each month. Retaining existing customers is significantly more cost-effective than acquiring new ones. This project builds a classification model that identifies customers at risk of churning so the bank can intervene proactively.

## Dataset

**File:** `datasets/Churn.csv` — 10,000 customer records  
**Target:** `Exited` — 1 = churned, 0 = retained (~20% churn rate, class imbalance present)

| Feature | Description |
|---|---|
| `CreditScore` | Customer credit score |
| `Geography` | Country of residence |
| `Gender` | Customer gender |
| `Age` | Customer age |
| `Tenure` | Years as a bank customer |
| `Balance` | Account balance |
| `NumOfProducts` | Number of bank products held |
| `HasCrCard` | Whether the customer has a credit card |
| `IsActiveMember` | Whether the customer is an active member |
| `EstimatedSalary` | Estimated annual salary |

## Approach

**Preprocessing:**
- Dropped non-predictive columns (`RowNumber`, `CustomerId`, `Surname`)
- Imputed missing `Tenure` values with the median
- One-hot encoded categorical features (`Geography`, `Gender`)
- Scaled features using `StandardScaler` (fit on training set only)
- Stratified 60 / 20 / 20 train / validation / test split

**Class Imbalance Handling (two strategies compared):**
1. Upsampling — minority class oversampled with replacement
2. Class weighting — `class_weight='balanced'` in the estimator

**Models Trained:**
- Logistic Regression (with GridSearchCV tuning)
- Random Forest (baseline, class-weighted, and upsampled variants)

## Results

| Model | Approach | Validation F1 | Validation AUC-ROC |
|---|---|---|---|
| Logistic Regression | Upsampled + Tuned | 0.513 | 0.792 |
| Random Forest | Baseline | 0.566 | 0.855 |
| **Random Forest** | **Class Weighting** | **0.629** | **0.867** |
| Random Forest | Upsampling | 0.595 | 0.858 |

**Final Test Performance (Random Forest — Upsampling + Threshold Optimization):**
- **F1 Score: 0.606** ✅ (threshold: 0.59)
- **AUC-ROC: 0.859**

## Tech Stack

- Python 3.9
- pandas
- scikit-learn

## Project Structure

```
├── customer_churn_classifier.ipynb   # Main notebook
├── datasets/
│   └── Churn.csv                     # Customer behavior data
└── README.md
```

## How to Run

1. Install dependencies:
   ```bash
   pip install pandas scikit-learn
   ```
2. Place `Churn.csv` in a `datasets/` folder.
3. Open and run `customer_churn_classifier.ipynb` top to bottom.
