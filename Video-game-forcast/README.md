# Instacart Customer Shopping Habits

## Summary
**Problem:** Understand Instacart customer shopping patterns to uncover actionable insights for product strategy and marketing.  
**Approach:** Cleaned and merged five datasets (orders, products, aisles, departments, order_products) with Pandas and SQL.  
Performed exploratory data analysis (EDA) to identify trends in order timing, product popularity, and reorder behavior.  
**Outcome:** Delivered insights into peak shopping times, most popular product categories, and customer reorder tendencies.

## Features
- **Data preprocessing:** Fixed data types, handled missing values, removed duplicates
- **Exploratory analysis:** Verified sensible ranges for order times/days, analyzed order frequency and reorder behavior
- **Visualizations:** Plots of order distribution by hour/day, reorder proportions, top products ordered/reordered
- **Statistical analysis:** Compared order hour distributions across weekdays/weekends, tested hypotheses on product performance

## Demo
- Notebook: `./notebooks/instacart_analysis.ipynb`
- Screenshots: `./assets/` (charts of hourly orders, weekly shopping patterns, top products)

## Setup
- Python 3.11+
- Install dependencies:
  ```bash
  pip install -r ../../requirements.txt
