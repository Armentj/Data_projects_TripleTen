# Used Car Price Prediction — Gradient Boosting & Numerical Methods

A machine learning project built for **Rusty Bargain**, a used car sales service, to predict market vehicle values based on historical listing data. The project benchmarks multiple models — including gradient boosting, ensemble, and linear methods — across prediction quality, training time, and inference speed.

---

## Project Overview

Rusty Bargain needed a model to power an in-app car valuation tool for customers. The key requirements were:

- **Prediction quality** — lowest possible RMSE
- **Training speed** — practical for retraining on new data
- **Prediction speed** — fast enough for real-time in-app use

Four models were trained, evaluated, and compared to determine the best fit.

---

## Dataset

Historical used car listing data containing:

- Technical specifications (engine size, mileage, power, etc.)
- Trim and model version details
- Registration year and vehicle age
- Listed prices (target variable)

---

## Models Compared

| Model | RMSE | Notes |
|---|---|---|
| **LightGBM** | ~912 | Best overall — low RMSE, fast train & predict |
| Random Forest | ~2,015 | Solid accuracy but very slow training (~342s) |
| Decision Tree | ~2,120 | Fast training (~5s) but weaker accuracy |
| Linear Regression | ~3,107 | Fastest, highest error — used as baseline |

---

## Key Results

**LightGBM is the recommended model** for Rusty Bargain's app. It achieves the lowest RMSE (~912), trains in seconds rather than minutes, and predicts fast enough for real-time use. Its error steadily decreased across boosting rounds, confirming strong learning capacity.

Random Forest is a viable backup benchmark but its ~342 second training time makes it impractical for regular retraining.

---

## Tech Stack

- **Python 3**
- **Pandas / NumPy** — data loading and preprocessing
- **Scikit-learn** — Linear Regression, Decision Tree, Random Forest, pipelines, preprocessing
- **LightGBM** — gradient boosting model
- **Scikit-learn Pipeline + ColumnTransformer** — clean preprocessing with OneHotEncoding

---

## How to Run

1. Clone the repository
2. Install dependencies:
   ```bash
   pip install pandas numpy scikit-learn lightgbm
   ```
3. Place the dataset in the expected path (or update the load path in the notebook)
4. Open and run `numerical_methods_ml.ipynb` in Jupyter Notebook or JupyterLab

---

## Project Structure

```
.
├── numerical_methods_ml.ipynb     # Main project notebook
└── README.md                      # Project documentation
```

---

## Concepts Demonstrated

- Gradient boosting (LightGBM) for regression
- Ensemble methods (Random Forest, Decision Tree)
- Scikit-learn Pipelines with ColumnTransformer for clean preprocessing
- Model benchmarking across RMSE, training time, and prediction speed
- Train/test splitting and RMSE evaluation
- Baseline modeling with Linear Regression
