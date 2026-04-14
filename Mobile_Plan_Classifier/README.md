# Mobile Plan Recommendation — Classification Model

A supervised machine learning project that predicts whether a mobile subscriber should be recommended the **Ultra** or **Smart** plan based on their usage behavior.

## Problem Statement

Megaline, a mobile carrier, wants to migrate legacy-plan subscribers to one of two newer plans. Instead of manually reviewing each account, this model automates the recommendation by learning patterns from subscribers who have already switched.

## Dataset

**File:** `datasets/users_behavior.csv`  
**Records:** 3,214 subscribers  
**Target:** `is_ultra` — 1 = Ultra plan, 0 = Smart plan (class imbalance: ~69% Smart, ~31% Ultra)

| Feature | Description |
|---|---|
| `calls` | Number of calls made per month |
| `minutes` | Total call duration (minutes) |
| `messages` | Number of text messages sent |
| `mb_used` | Internet traffic used (MB) |
| `is_ultra` | Target label |

## Approach

The dataset is split into **train / validation / test** sets (60 / 20 / 20) and three classifiers are trained and compared:

- **Decision Tree** — depth tuned from 1–19
- **Random Forest** — grid search over estimator count and max depth
- **Logistic Regression** — baseline linear model

## Results

| Model | Validation Accuracy |
|---|---|
| Decision Tree | 79.6% |
| **Random Forest** ✅ | **81.3%** |
| Logistic Regression | 74.0% |

The **Random Forest** model was selected and evaluated on the held-out test set:

- **Test Accuracy: 81.0%** (exceeds the 75% project threshold)
- Strong precision and recall for Smart plan users (F1 = 0.87)
- Reasonable performance for Ultra plan users (F1 = 0.65)

## Tech Stack

- Python 3.9
- pandas
- scikit-learn

## Project Structure

```
├── mobile_plan_classifier.ipynb   # Main notebook
├── datasets/
│   └── users_behavior.csv         # Subscriber behavior data
└── README.md
```

## How to Run

1. Clone the repository and install dependencies:
   ```bash
   pip install pandas scikit-learn
   ```
2. Place `users_behavior.csv` in a `datasets/` folder.
3. Open and run `mobile_plan_classifier.ipynb` top to bottom.
