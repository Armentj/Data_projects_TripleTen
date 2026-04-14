# Megaline Plan Revenue Analysis

A statistical data analysis project comparing two prepaid mobile plans — **Surf** and **Ultimate** — offered by the fictional telecom operator Megaline. The goal is to determine which plan generates more revenue to help the commercial department allocate its advertising budget.

---

## Project Overview

Working from a sample of 500 Megaline clients in 2018, this project analyzes user behavior across calls, messages, and internet usage, then calculates monthly revenue per user to draw data-driven conclusions about plan profitability.

---

## Dataset

The analysis uses five CSV files:

| File | Description |
|---|---|
| `megaline_users.csv` | User demographics, plan assignment, registration and churn dates |
| `megaline_calls.csv` | Individual call records with duration |
| `megaline_messages.csv` | Text message records |
| `megaline_internet.csv` | Internet session records with MB used |
| `megaline_plans.csv` | Plan pricing and included allowances |

**Plan Summary:**

| Plan | Monthly Fee | Minutes | Messages | Data | Overage Rates |
|---|---|---|---|---|---|
| Surf | $20 | 500 min | 50 msgs | 15 GB | $0.03/min, $0.03/msg, $10/GB |
| Ultimate | $70 | 3,000 min | 1,000 msgs | 30 GB | $0.01/min, $0.01/msg, $7/GB |

---

## Methodology

1. **Data preparation** — Parsed dates, rounded call durations up to the nearest minute, converted MB to GB, and enriched each table with month/weekday features.
2. **Aggregation** — Computed total monthly minutes, messages, and GB used per user, then merged all usage data with plan conditions into a single `monthly_usage` DataFrame.
3. **Revenue calculation** — Built a custom function to compute each user's monthly bill: base fee + overage charges for calls, messages, and data beyond their plan's included limits.
4. **Exploratory analysis** — Visualized usage distributions and descriptive statistics (mean, variance, median) broken down by plan using histograms and box plots.
5. **Hypothesis testing** — Used Welch's two-sample t-test (α = 0.05) to test two hypotheses:
   - Whether average revenue differs between Surf and Ultimate users
   - Whether users in the NY-NJ region generate different revenue than users elsewhere

---

## Key Findings

- **Surf users frequently exceed plan limits**, generating significant overage charges in calls, messages, and data — making their monthly revenue highly variable.
- **Ultimate users stay within their generous allowances** most of the time, producing steady, predictable subscription revenue with minimal overages.
- **Statistical test 1**: The difference in average revenue between Surf and Ultimate users is statistically significant (p < 0.05) — we reject the null hypothesis.
- **Statistical test 2**: No statistically significant difference in revenue between NY-NJ users and users in other regions — we fail to reject the null hypothesis.

---

## Conclusions & Recommendations

- **Ultimate generates more reliable revenue** through its flat subscription model.
- **Surf's profitability is driven by overage behavior** — high-usage Surf subscribers represent strong revenue opportunities.
- Surf users who consistently exceed limits are strong candidates for upselling or plan migration to Ultimate.
- Regional advertising budget allocation does not need to differ — location does not significantly impact revenue.
- Hybrid or tiered plans could capture value from moderate Surf users who aren't heavy enough to trigger large overages but frequently approach limits.

---

## Technologies Used

- Python 3
- pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy (stats)

---

## How to Run

1. Clone the repository
2. Place the five Megaline CSV files in a `/datasets/` directory
3. Open `SDA_project.ipynb` in Jupyter Notebook or JupyterLab
4. Run all cells in order

---

## Project Background

This project was completed as part of the **Statistical Data Analysis** sprint at [TripleTen](https://tripleten.com), a data science bootcamp.
