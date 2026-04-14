# Data Science Portfolio — TripleTen Program

A collection of end-to-end data science projects completed during the TripleTen Data Science program. Each project covers a real-world business problem and follows a full workflow: data cleaning and exploration, feature engineering, model development, evaluation, and written findings. Projects span statistical analysis, classical machine learning, time series forecasting, natural language processing, and computer vision.

---

## Projects

| # | Project | Description | Key Techniques | Result |
|:-:|---------|-------------|----------------|--------|
| 1 | [Megaline Plan Revenue Analysis](./SDA_Project/README.md) | Statistical comparison of two prepaid plans — Surf and Ultimate — to determine which generates more revenue and guide advertising budget decisions. | Hypothesis testing, EDA, revenue calculation, Pandas, Matplotlib | Surf plan users generate significantly less revenue; Ultimate plan recommended for budget focus |
| 2 | [Mobile Plan Recommendation](./Mobile_Plan_Classifier/README.md) | Classification model for Megaline to automatically recommend the Ultra or Smart plan to legacy subscribers based on usage behavior. | Decision Tree, Random Forest, Logistic Regression, train/val/test split | Random Forest — **81% test accuracy** (threshold: 75%) |
| 3 | [Customer Churn Prediction](./Customer_Churn_Classifier/README.md) | Binary classifier for Beta Bank to identify customers likely to churn, enabling proactive retention efforts. | kNN, feature scaling, class imbalance handling, F1 / AUC-ROC | kNN (k=3) — **F1 = 0.94** on scaled data |
| 4 | [Gold Recovery Prediction](./Gold_Recovery_Prediction/README.md) | Regression model for Zyfra to predict gold recovery efficiency at two stages of an industrial flotation purification process. | Linear Regression, Decision Tree, Random Forest, custom sMAPE metric | Random Forest — best final sMAPE on held-out test set |
| 5 | [Insurance Benefits Prediction](./Insurance_Benefits_ml/README.md) | Four-task ML project for Sure Tomorrow Insurance: customer similarity search, benefit classification, benefit count regression, and privacy-preserving data obfuscation. | kNN, custom Linear Regression (Normal Equation), matrix obfuscation, F1 / RMSE / R² | Obfuscation proven analytically and verified to leave regression predictions unchanged |
| 6 | [Oil Well Profitability Analysis](./Oil_Well_Profitability/README.md) | Identifies the most profitable region for OilyGiant to develop 200 new oil wells using linear regression and bootstrapped profit simulation with risk constraints. | Linear Regression, Bootstrap simulation, confidence intervals, risk analysis | Region 1 selected — highest expected profit with loss probability below 2.5% |
| 7 | [Used Car Price Prediction](./Used_Car_Price_Prediction/README.md) | Price estimation model for Rusty Bargain's used car marketplace, benchmarking tree-based gradient boosting models against baseline regressors. | LightGBM, XGBoost, Random Forest, Linear Regression, RMSE | LightGBM — **RMSE ≈ 912** (best accuracy / speed trade-off) |
| 8 | [Time Series Taxi Forecasting](./Time_Series_Taxi_forecasting/README.md) | Hourly taxi demand forecasting for Sweet Lift to optimize driver dispatch at airports during peak hours. | Lag features, rolling mean, Linear Regression, Random Forest, Gradient Boosting, RMSE | Linear Regression — **RMSE ≈ 47** (threshold: ≤ 48) |
| 9 | [NLP Movie Review Classification](./nlp_movie_review_classification/README.md) | Sentiment classifier for Film Junky Union to automatically detect negative movie reviews from IMDB data, benchmarking multiple NLP pipelines. | TF-IDF, Logistic Regression, LightGBM, BERT embeddings, F1 score | BERT — strongest performance, **F1 ≥ 0.85** threshold met |
| 10 | [Telecom Customer Churn Prediction](./telecom_customer_churn_prediction/README.md) | End-to-end ML project (plan + code + report) predicting churn for a telecom provider across four joined data tables. Covers full data science workflow from planning through evaluation. | Feature engineering, Logistic Regression, Random Forest, XGBoost, AUC-ROC | Logistic Regression — **AUC-ROC = 0.837** |
| 11 | [Age Detection — Computer Vision](./age_detection_computer_vision/README.md) | Deep learning regression model for Good Seed Supermarket to estimate customer age from facial photographs, eliminating the need for staff intervention on age-restricted purchases. | ResNet50 (transfer learning), ImageDataGenerator, regression, MAE | **MAE ≈ 6.7** on validation (threshold: ≤ 8) |

---

## Tech Stack

**Languages & Core Libraries:** Python 3, Pandas, NumPy, Matplotlib, Seaborn

**Machine Learning:** Scikit-learn, XGBoost, LightGBM

**Deep Learning & NLP:** TensorFlow / Keras, Hugging Face Transformers (BERT), spaCy, NLTK

**Techniques:** EDA, feature engineering, class imbalance handling, hyperparameter tuning, cross-validation, hypothesis testing, time series analysis, transfer learning, data obfuscation

---

## Structure

Each project folder contains:
- A Jupyter notebook with the full implementation
- A `README.md` describing the problem, dataset, approach, and results
