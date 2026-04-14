# Time Series Taxi Forecasting

A time series forecasting project built for **Sweet Lift Taxi**, predicting the number of hourly taxi orders at airports to help the company attract more drivers during peak hours.

---

## Project Overview

Sweet Lift Taxi needed a model to forecast taxi demand one hour ahead, enabling proactive driver dispatch. The project success criterion was achieving an **RMSE of 48 or below** on the test set.

---

## Dataset

Historical airport taxi order data stored in `taxi.csv`, resampled to hourly intervals.

| Column | Description |
|---|---|
| `num_orders` | Number of taxi orders per hour (target) |

---

## Feature Engineering

The following time-based and lag features were engineered from the hourly time series:

- `hour` — hour of day
- `dayofweek` — day of the week
- `lag_1` — orders from the previous hour
- `lag_24` — orders from 24 hours prior
- `rolling_mean_24` — 24-hour rolling average of orders

---

## Models Compared

| Model | RMSE |
|---|---|
| Naive Baseline | ~59 |
| **Linear Regression** | **~47 ✅** |
| Random Forest | Competitive |
| Gradient Boosting | Competitive |

---

## Key Results

**Linear Regression is the recommended model** — it achieved the best RMSE (~47), meeting the project requirement of ≤ 48, while remaining simple and interpretable. The naive baseline (RMSE ≈ 59) confirmed that feature engineering and modeling were necessary. Random Forest and Gradient Boosting were competitive but did not outperform Linear Regression on this dataset.

---

## Tech Stack

- **Python 3**
- **Pandas / NumPy** — data loading, resampling, feature engineering
- **Matplotlib** — time series visualization
- **statsmodels** — seasonal decomposition
- **Scikit-learn** — Linear Regression, Random Forest, Gradient Boosting, RMSE evaluation

---

## How to Run

1. Clone the repository
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib statsmodels scikit-learn
   ```
3. Place `taxi.csv` in a `/datasets/` directory (or update the load path in the notebook)
4. Open and run `time_series_taxi_forecasting.ipynb` in Jupyter Notebook or JupyterLab

---

## Project Structure

```
.
├── time_series_taxi_forecasting.ipynb   # Main project notebook
└── README.md                            # Project documentation
```

---

## Concepts Demonstrated

- Time series resampling and visualization
- Seasonal decomposition (trend, seasonality, residuals)
- Lag and rolling window feature engineering
- Regression modeling for time series forecasting
- Baseline comparison (naive forecast vs. ML models)
- RMSE evaluation against a business-defined threshold
