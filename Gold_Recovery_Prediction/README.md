# Gold Recovery Prediction — Integrated ML Project

A machine learning project that predicts the efficiency of gold recovery from ore at two stages of an industrial flotation purification process, enabling mining operations to optimize output and minimize losses.

## Problem Statement

Zyfra develops efficiency solutions for the heavy industry. This project builds a regression model that predicts gold recovery rates at both the **rougher output** and **final output** stages of ore purification, using sensor readings collected throughout the processing pipeline.

Accurate recovery predictions allow process engineers to identify suboptimal conditions early and make data-driven adjustments without costly physical experiments.

## Dataset

Three CSVs covering 22,716 time-indexed records of ore processing sensor data:

| File | Rows | Columns | Purpose |
|---|---|---|---|
| `gold_recovery_train.csv` | 16,860 | 86 | Model training |
| `gold_recovery_test.csv` | 5,856 | 52 | Prediction (targets excluded) |
| `gold_recovery_full.csv` | 22,716 | 86 | True test targets for evaluation |

Features describe reagent volumes, feed concentrations, and output concentrations of gold (Au), silver (Ag), and lead (Pb) at each processing stage.

**Targets:**
- `rougher.output.recovery` — gold recovery at the rougher (initial) flotation stage
- `final.output.recovery` — gold recovery at the final purification stage

## Evaluation Metric

**Final sMAPE** (symmetric Mean Absolute Percentage Error), averaged equally across both targets:

$$\text{Final sMAPE} = 0.5 \cdot \text{sMAPE}_{\text{rougher}} + 0.5 \cdot \text{sMAPE}_{\text{final}}$$

## Approach

1. **Data validation** — Recalculate rougher recovery from raw inputs using the industry formula to confirm data integrity (MAE = 0.0000 ✅)
2. **Preprocessing** — Drop post-process columns absent from the test set, handle missing values, align features across splits
3. **EDA** — Analyze metal concentration distributions across purification stages, compare feed size distributions between train/test, identify outliers
4. **Modeling** — Train and compare three models using 5-fold cross-validation with sMAPE scoring
5. **Final evaluation** — Retrain the best model on full training data and evaluate on the held-out test set

## Results

| Model | Rougher sMAPE | Final sMAPE | Avg sMAPE |
|---|---|---|---|
| **Linear Regression** ✅ | **11.9253** | **9.7461** | **10.84** |
| Random Forest | 13.0189 | 10.4686 | 11.74 |
| Decision Tree | 21.1571 | 17.0132 | 19.08 |

**Final Test sMAPE: 10.3727** — consistent with cross-validation, confirming strong generalization.

Linear Regression outperformed ensemble methods, suggesting that the dominant relationships between sensor features and recovery rates are approximately linear — consistent with the physics-based nature of flotation chemistry.

## Tech Stack

- Python 3.9
- pandas, NumPy
- scikit-learn (LinearRegression, RandomForestRegressor, DecisionTreeRegressor, Pipeline, StandardScaler, cross_val_score)
- Matplotlib

## Project Structure

```
├── gold_recovery_prediction.ipynb   # Main analysis notebook
├── datasets/
│   ├── gold_recovery_train.csv
│   ├── gold_recovery_test.csv
│   └── gold_recovery_full.csv
└── README.md
```

## How to Run

1. Install dependencies:
   ```bash
   pip install pandas numpy scikit-learn matplotlib
   ```
2. Place the three CSV files in a `datasets/` folder.
3. Open and run `gold_recovery_prediction.ipynb` top to bottom.
