# TripleTen Sprint Project - Beta Bank Churn Prediction

This was another project I worked on in the TripleTen Data Science program. It was my first supervised machine learning project, and I enjoyed applying classification techniques to a real-world business case. The challenge was to predict customer churn and improve retention strategies.

### Beta Bank Churn

The goal of the project was to build a predictive model that identifies customers likely to leave the bank. By analyzing demographic, financial, and behavioral data, I aimed to maximize the F1 score (minimum threshold: 0.59) and compare it with the AUC-ROC metric to evaluate model performance.

#### The Data

The dataset contained information about Beta Bank customers, with the following features:

- `RowNumber`: Data string index  
- `CustomerId`: Unique customer identifier  
- `Surname`: Customer surname  
- `CreditScore`: Credit score  
- `Geography`: Country of residence  
- `Gender`: Gender  
- `Age`: Age  
- `Tenure`: Years of fixed deposit maturity  
- `Balance`: Account balance  
- `NumOfProducts`: Number of banking products used  
- `HasCrCard`: Whether the customer has a credit card  
- `IsActiveMember`: Customer’s activeness  
- `EstimatedSalary`: Estimated salary  
- **Target:** `Exited` — whether the customer left the bank  

The dataset was provided by TripleTen, adapted from open-source churn data.

#### The Process

- **Data preparation:**  
  - Cleaned and processed feature types (categorical, numerical)  
  - Handled missing values and ensured consistency  
  - Split data into training, validation, and test sets  

- **Class imbalance investigation:**  
  - Examined distribution of churn vs. non-churn customers  
  - Trained baseline models without imbalance handling to compare results  

- **Model improvement:**  
  - Applied at least two techniques to fix class imbalance (SMOTE resampling, class weight adjustments)  
  - Trained multiple models (e.g., Logistic Regression, Random Forest, Gradient Boosting)  
  - Tuned hyperparameters using grid search and cross-validation  

- **Final testing:**  
  - Selected the best-performing model based on validation metrics  
  - Evaluated on the test set using F1 score and AUC-ROC  

### Results

Explaining my results at each step was a key part of the process. I found that:

- The baseline model struggled with class imbalance, underpredicting churn cases.  
- Resampling techniques (SMOTE) and class weight adjustments significantly improved recall for minority classes.  
- The final model achieved an **F1 score above 0.59**, meeting the project requirement.  
- AUC-ROC provided additional validation of model reliability, confirming strong separation between churn and non-churn predictions.  
- Insights into churn drivers (e.g., age, tenure, product usage) informed targeted retention strategies.  

Please have a look at the Jupyter Notebook included for a full description of results.
