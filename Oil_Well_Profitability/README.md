# Oil Well Profitability Analysis

A machine learning project that identifies the most profitable region for new oil well development using Linear Regression and Bootstrap simulation to quantify financial risk.

## Problem Statement

OilyGiant Mining Company needs to select one of three candidate regions to develop 200 new oil wells with a fixed budget of $100M. The goal is to maximize expected profit while keeping the probability of financial loss below 2.5%.

## Dataset

Three regional datasets (`geo_data_0.csv`, `geo_data_1.csv`, `geo_data_2.csv`), each containing 100,000 oil well records.

| Feature | Description |
|---|---|
| `f0`, `f1`, `f2` | Geological survey measurements |
| `product` | Target: oil reserve volume (thousand barrels) |

**Business constraints:**
- Budget: $100M across 200 wells ($500K/well)
- Revenue: $4,500 per thousand barrels
- Break-even volume per well: 111.1 thousand barrels

## Approach

1. **Regression modeling** — Train a Linear Regression model on each region's geological data to predict oil reserve volume per well.
2. **Well selection** — From a random sample of 500 candidate wells, select the top 200 by predicted volume for development.
3. **Bootstrap analysis** — Run 1,000 profit simulations to build a statistical distribution of outcomes and calculate risk of loss.
4. **Region selection** — Choose the region with the highest mean profit and risk of loss below 2.5%.

## Results

| Region | Model RMSE | Mean Profit | 95% CI | Risk of Loss |
|---|---|---|---|---|
| Region 0 | 37.58 | $6.01M | [$129K, $12.31M] | 2.0% |
| **Region 1** ✅ | **0.89** | **$6.65M** | **[$1.58M, $11.98M]** | **0.3%** |
| Region 2 | 40.03 | $6.16M | [-$122K, $12.31M] | 3.0% |

**Recommendation: Region 1** — highest expected profit ($6.65M), lowest risk of loss (0.3%), most accurate predictive model (RMSE 0.89), and a confidence interval that remains positive even in worst-case scenarios.

## Tech Stack

- Python 3.9
- pandas, NumPy
- scikit-learn
- Matplotlib

## Project Structure

```
├── oil_well_profitability.ipynb   # Main analysis notebook
├── datasets/
│   ├── geo_data_0.csv             # Region 0 geological survey data
│   ├── geo_data_1.csv             # Region 1 geological survey data
│   └── geo_data_2.csv             # Region 2 geological survey data
└── README.md
```

## How to Run

1. Install dependencies:
   ```bash
   pip install pandas numpy scikit-learn matplotlib
   ```
2. Place the three CSV files in a `datasets/` folder.
3. Open and run `oil_well_profitability.ipynb` top to bottom.
