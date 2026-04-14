# Insurance Benefits Prediction — Linear Algebra & ML Project

A machine learning project analyzing insurance benefit prediction for **Sure Tomorrow Insurance Company**, demonstrating how Linear Algebra concepts power real-world ML workflows.

---

## Project Overview

This project applies linear algebra and machine learning techniques to four distinct insurance analytics tasks:

1. **Customer Similarity** — Find customers most similar to a given customer using k-Nearest Neighbors (kNN)
2. **Benefit Classification** — Predict whether a new customer is likely to receive an insurance benefit (binary classification)
3. **Benefit Count Regression** — Predict the number of insurance benefits a customer is likely to receive using a custom Linear Regression implementation
4. **Data Obfuscation** — Protect customer privacy by obfuscating personal data with matrix transformations while preserving model accuracy

---

## Dataset

The dataset (`insurance_us.csv`) contains anonymized customer records with the following features:

| Feature | Description |
|---|---|
| `gender` | Customer gender (binary: 0/1) |
| `age` | Customer age (integer) |
| `income` | Annual salary |
| `family_members` | Number of family members |
| `insurance_benefits` | Number of insurance benefits received (target) |

---

## Key Results

### Task 1 — kNN Customer Similarity
- Scaling is **essential**: without it, high-magnitude features like income dominate distance calculations and produce unreliable neighbors
- Both Euclidean and Manhattan distance metrics work well on scaled data; on scaled data they converge to nearly identical neighbor sets

### Task 2 — Insurance Benefit Classification
- kNN classifier with scaled data achieves **F1 scores of 0.89–0.94**, far outperforming a random dummy model
- Best performance at **k=3** with scaled features (F1 = 0.94)
- Unscaled data produces highly variable, poor F1 scores (0.02–0.60)

### Task 3 — Linear Regression (Custom Implementation)
- Custom closed-form linear regression built from scratch using NumPy matrix operations
- Scaling does **not** affect linear regression predictions — RMSE and R² are identical for scaled vs. unscaled data, as expected theoretically

### Task 4 — Data Obfuscation
- Customer features obfuscated by multiplying the feature matrix by a random invertible matrix **P**
- Analytically proven and computationally verified: obfuscation with an invertible matrix leaves linear regression predictions completely unchanged
- **RMSE = 0.3637**, **R² = 0.4227** — identical for both original and obfuscated data

---

## Tech Stack

- **Python 3**
- **NumPy** — matrix operations, custom linear regression
- **Pandas** — data loading and manipulation
- **Scikit-learn** — kNN, preprocessing, metrics
- **Matplotlib / Seaborn** — EDA visualizations

---

## How to Run

1. Clone the repository
2. Install dependencies:
   ```bash
   pip install numpy pandas scikit-learn matplotlib seaborn
   ```
3. Place `insurance_us.csv` in a `/datasets/` directory (or update the path in the notebook)
4. Open and run `Linear_Algebra_Project.ipynb` in Jupyter Notebook or JupyterLab

---

## Project Structure

```
.
├── Linear_Algebra_Project.ipynb   # Main project notebook
└── README.md                      # Project documentation
```

---

## Concepts Demonstrated

- k-Nearest Neighbors (kNN) for classification and similarity search
- Feature scaling (MaxAbsScaler, StandardScaler) and its impact on distance-based models
- Closed-form Linear Regression using the Normal Equation: **w = (XᵀX)⁻¹ Xᵀy**
- Matrix invertibility and determinant checking
- Data obfuscation via matrix multiplication and analytical proof of regression invariance
- Train/test splitting to prevent data leakage
- Evaluation metrics: F1 Score, Confusion Matrix, RMSE, R²
