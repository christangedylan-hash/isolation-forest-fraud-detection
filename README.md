# Isolation Forest for Fraud Detection

This project studies the use of Isolation Forest for anomaly detection in a financial fraud detection setting.

The work was developed as part of an academic data science project at ISFA. It combines a review of the Isolation Forest methodology introduced by Liu et al. with a practical application to bank loan application fraud detection.

## Objective

The objective of this project is to assess whether Isolation Forest can effectively detect fraudulent loan applications in a highly imbalanced financial dataset.

The project focuses on:

- understanding the theoretical foundations of Isolation Forest;
- applying anomaly detection to a bank loan application dataset;
- evaluating the method under strong class imbalance;
- comparing unsupervised anomaly detection with supervised learning models;
- analyzing why Isolation Forest may fail when fraud is contextual rather than marginally extreme.

## Methodological Background

Isolation Forest is based on the idea that anomalies are easier to isolate than normal observations.

Instead of modeling normal behavior or computing distances between observations, the algorithm recursively partitions the feature space using random splits. Observations that require shorter paths to be isolated are assigned higher anomaly scores.

This makes Isolation Forest attractive for financial anomaly detection because it is:

- computationally efficient;
- scalable to large datasets;
- conceptually simple;
- suitable for high-dimensional problems;
- naturally designed for rare observations.

## Financial Application

The practical application focuses on fraud detection in bank loan applications.

The dataset contains variables related to:

- loan characteristics;
- applicant socio-economic profile;
- credit risk indicators;
- loan approval status;
- fraud indicators.

The business objective is to complement traditional credit scoring with early detection of suspicious applications, in order to improve risk monitoring, fraud screening and data quality.

## Modeling Approach

The project includes the following steps:

- data cleaning and preprocessing;
- feature engineering;
- one-hot encoding of categorical variables;
- stratified train-test split due to class imbalance;
- baseline Isolation Forest model;
- hyperparameter optimization using GridSearchCV, RandomizedSearchCV and Optuna;
- comparison with supervised models such as Random Forest and XGBoost;
- use of resampling techniques such as SMOTE and SMOTEENN;
- comparison with other anomaly detection methods including Local Outlier Factor and One-Class SVM;
- evaluation using metrics robust to class imbalance.

## Evaluation Metrics

Because fraud represents only a small fraction of the observations, standard accuracy can be misleading.

The project therefore uses several imbalance-aware metrics:

- AUPRC;
- Precision@k;
- Recall@k;
- F1-score;
- F2-score;
- Balanced Accuracy;
- G-mean;
- Matthews Correlation Coefficient;
- Cohen's Kappa;
- Jaccard Index.

## Key Findings

The results highlight the limitations of purely unsupervised anomaly detection for this fraud detection problem.

Isolation Forest performs weakly because the fraudulent applications do not appear as simple marginal outliers. Instead, fraud appears to be more contextual, depending on combinations of variables and on the consistency between the applicant profile and the loan purpose.

Supervised models with explicit class imbalance handling, especially Random Forest with class weights and XGBoost combined with SMOTEENN and threshold adjustment, provide better results than the optimized Isolation Forest variants.

The project shows that the limited performance of Isolation Forest is not necessarily a methodological failure, but rather a consequence of the mismatch between the algorithm's assumptions and the structure of the fraud detection problem.

## Repository Structure

```text
notebooks/
  01_isolation_forest_fraud_detection.ipynb
  02_critical_analysis_and_limitations.ipynb

data/
  loan_applications.csv

report/
  Data_Science_Anomaly_Detection_Report_FR.pdf

requirements.txt
README.md
```

The original academic report is written in French. This README provides an English summary of the project for international readability.

## Data

The dataset used in this project comes from a public loan application dataset used for fraud detection analysis.

The raw dataset is included as:

```text
data/loan_applications.csv
```

The processed dataset is generated within the notebooks during the preprocessing step and is not stored separately in this repository.

## Tech Stack

- Python
- pandas
- NumPy
- scikit-learn
- XGBoost
- imbalanced-learn
- Optuna
- matplotlib
- seaborn
- Jupyter Notebook

## Authors

Academic group project by:

- Salimata Diouf
- Christ Ange Dylan Kouamé
- Aboubakar Mohamed Ouattara
- Souleymane Ouattara

## Disclaimer

This project is for academic and educational purposes only. It does not constitute financial advice, credit risk advice or fraud detection advice for production systems.
