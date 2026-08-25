# 💳 Online Payment Fraud Detection

> Large-scale fraud analytics and machine learning project analyzing 6.3M+ financial transactions to identify fraudulent behavior and evaluate detection approaches.

## 📌 Project Overview

This project analyzes **6,362,620 online payment transactions** to identify patterns associated with fraudulent activity and evaluate data-driven fraud detection techniques.

The analysis combines **exploratory data analysis, feature engineering, supervised machine learning, and anomaly detection** to investigate transaction behavior and identify indicators associated with fraud.

Three classification models were evaluated:

- Logistic Regression
- Decision Tree
- Random Forest

The project focuses particularly on the challenges of **highly imbalanced financial-security data**, where fraudulent transactions represent only **0.13%** of the dataset.

## 🎯 Objectives

- Identify transaction patterns associated with fraudulent activity.
- Analyze fraud risk across different transaction types and amounts.
- Engineer behavioral features from account balance information.
- Compare machine-learning approaches for fraud classification.
- Evaluate models using precision, recall, F1-score, and ROC-AUC.
- Explore anomaly detection for identifying unusual transaction behavior.

## 🛠️ Technologies

`Python` `Pandas` `NumPy` `Scikit-learn` `PyOD` `Matplotlib` `Google Colab`

## 🔍 Analysis Workflow

**Data Quality Assessment → Exploratory Data Analysis → Fraud Pattern Analysis → Feature Engineering → Machine Learning → Model Evaluation → Anomaly Detection → Security Insights**

---

## 📊 Key Results & Visualizations

### 1. Fraud is Rare and Highly Imbalanced

Only **8,213 of 6,362,620 transactions (0.13%)** were fraudulent, compared with more than 6.35 million legitimate transactions.

This extreme imbalance demonstrates why accuracy alone can be misleading when evaluating fraud-detection models.

![Fraud Class Distribution](images/fraud-class-distribution.png)

### 2. Fraud is Concentrated in Specific Transaction Types

Fraudulent activity occurred only within **TRANSFER** and **CASH_OUT** transactions in this dataset.

- **TRANSFER:** 4,097 fraudulent transactions — approximately **0.77% fraud rate**
- **CASH_OUT:** 4,116 fraudulent transactions — approximately **0.18% fraud rate**
- **PAYMENT, CASH_IN and DEBIT:** no fraudulent transactions were observed

![Fraud Rate by Transaction Type](images/fraud-rate-by-transaction-type.png)

### 3. Fraudulent Transactions Tend to Involve Larger Amounts

The median fraudulent transaction amount was approximately **$441,423**, compared with approximately **$74,685** for legitimate transactions.

This suggests transaction amount provides useful discriminatory information, although transaction amount alone is insufficient to identify fraud.

![Transaction Amount Distribution](images/transaction-amount-distribution.png)

### 4. Machine Learning Model Comparison

Three supervised classification models were evaluated using precision, recall, F1-score, and ROC-AUC.

| Model | Precision | Recall | F1-Score | ROC-AUC |
|---|---:|---:|---:|---:|
| Logistic Regression | 89.47% | 43.79% | 58.80% | 98.35% |
| Decision Tree | 99.35% | 99.59% | 99.47% | 99.80% |
| **Random Forest** | **100.00%** | **99.63%** | **99.82%** | **99.82%** |

Random Forest produced the strongest overall performance. Logistic Regression demonstrated why high accuracy alone is insufficient: despite achieving approximately 99.92% accuracy, its fraud recall was only **43.79%**.

![Model Comparison](images/model-comparison.png)

### 5. Random Forest Fraud Detection

On the held-out test set, the Random Forest model:

- Correctly detected **2,455 of 2,464 fraudulent transactions**
- Missed only **9 fraudulent transactions**
- Produced **0 false-positive fraud classifications**
- Achieved **99.63% fraud recall**

![Random Forest Confusion Matrix](images/confusion-matrix.png)

### 6. Feature Engineering Improved Detection

Balance-change and balance-discrepancy features were engineered from the original account balance fields.

A robustness comparison showed that Random Forest fraud recall increased from **77.80% using the original features** to **99.63% with the engineered features**.

Feature-importance analysis showed that sender balance behavior was particularly informative, with `newbalanceOrig`, `orig_balance_change`, and `orig_balance_error` among the strongest predictors.

![Feature Importance](images/feature-importance.png)

### 7. Anomaly Detection

KNN-based unsupervised anomaly detection was also explored.

---

## 💡 Key Takeaways

- **Class imbalance matters:** A baseline model achieved approximately 99.87% accuracy while detecting zero fraudulent transactions, demonstrating why accuracy alone is misleading for highly imbalanced fraud data.

- **Transaction behavior provides useful fraud signals:** Fraud was concentrated in `TRANSFER` and `CASH_OUT` transactions and was associated with differences in transaction amounts and account balance behavior.

- **Feature engineering had a major impact:** Engineering balance-change and balance-discrepancy features increased Random Forest fraud recall from **77.80% to 99.63%**.

- **Model interpretability matters:** Feature-importance analysis showed that sender balance behavior, including `newbalanceOrig`, `orig_balance_change`, and `orig_balance_error`, contributed substantially to the Random Forest predictions.

- **Anomalies are not automatically fraud:** Unsupervised anomaly detection identified only a subset of known fraudulent transactions and also classified some legitimate transactions as anomalous.

---

## ⚠️ Limitations

- The dataset represents **simulated online payment activity**, so the results should not be interpreted as expected performance in a production banking environment.
- Fraud represents only approximately **0.13%** of the complete dataset.
- The strong Random Forest performance is partly associated with highly informative balance-related features.
- Models were evaluated using a single stratified train-test split rather than repeated or temporal validation.
- The anomaly-detection experiment used a deliberately constructed 50,000-transaction sample containing 4% known fraud for evaluation purposes. This does not represent the fraud prevalence of the complete dataset.
- Unsupervised anomaly detection identifies unusual behavior rather than fraud specifically.
- This project is an analytical demonstration and not a production fraud-detection system.

---

## 📁 Repository Structure

```text
online-payment-fraud-detection/
│
├── README.md
│
├── notebooks/
│   └── Online_Payment_Fraud_Detection.ipynb
│
├── images/
│   ├── fraud-class-distribution.png
│   ├── fraud-rate-by-transaction-type.png
│   ├── transaction-amount-distribution.png
│   ├── model-comparison.png
│   ├── confusion-matrix.png
│   └── feature-importance.png
│
└── .gitignore
```

---

## 📓 Full Analysis

The complete Jupyter notebook contains the data-quality assessment, exploratory data analysis, feature engineering, machine-learning development, model evaluation, anomaly detection, visualizations, and interpretation.

➡️ **[View the Complete Analysis Notebook](notebooks/Online_Payment_Fraud_Detection.ipynb)**

---

## 🔐 Skills Demonstrated

`Data Analytics` • `Cybersecurity Analytics` • `Python` • `Pandas` • `NumPy` • `Exploratory Data Analysis` • `Feature Engineering` • `Machine Learning` • `Random Forest` • `Fraud Detection` • `Anomaly Detection` • `Model Evaluation` • `Data Visualization`

---

## 🚀 Project Summary

Analyzed **6.3M+ online payment transactions** using Python to identify fraud patterns, engineer behavioral features, compare machine-learning models, and evaluate anomaly-detection techniques. Feature engineering improved Random Forest fraud recall from **77.80% to 99.63%**, demonstrating the value of transaction-balance behavior for fraud classification within the analyzed dataset.
