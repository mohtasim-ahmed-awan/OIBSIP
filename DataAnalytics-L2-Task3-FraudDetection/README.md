# Oasis Infobyte — Task 7: Fraud Detection

**Author: Mohtasim Ahmed Awan**

## 📌 Project Overview

This project was completed as part of the **Oasis Infobyte Internship — Task 7**.

The objective is to build a machine learning pipeline capable of detecting fraudulent financial transactions from a highly imbalanced credit card transaction dataset.

The project focuses on:

- Understanding severe class imbalance
- Performing exploratory data analysis (EDA)
- Analyzing transaction amounts and transaction times
- Applying SMOTE to handle class imbalance
- Training and comparing Logistic Regression and Random Forest models
- Evaluating models using Precision, Recall, F1-Score, and AUC-ROC
- Analyzing important fraud-related features
- Examining confusion matrices and ROC curves
- Discussing scalability for high-volume transaction processing

## 🎯 Objective

Build a machine learning-based fraud detection system that can identify fraudulent transactions while properly handling the severe imbalance between legitimate and fraudulent transactions.

Accuracy alone is not sufficient for this problem because fraudulent transactions represent only a very small percentage of all transactions. Therefore, the project focuses primarily on **Precision, Recall, F1-Score, and AUC-ROC**.

## 📊 Dataset

The project uses the **Credit Card Fraud Detection dataset** containing transactions made by European cardholders.

### Dataset Characteristics

- **Total transactions:** 284,807
- **Total features:** 31
- **Legitimate transactions:** 284,315
- **Fraudulent transactions:** 492
- **Fraud rate:** approximately 0.17%

The dataset contains:

- `Time` — transaction time
- `V1` to `V28` — anonymized PCA-transformed features
- `Amount` — transaction amount
- `Class` — target variable

### Target Variable

| Class | Meaning |
|------:|---------|
| 0 | Legitimate transaction |
| 1 | Fraudulent transaction |

The dataset contains no missing values.

## 🔍 Exploratory Data Analysis

The project performs exploratory analysis to understand the characteristics of the transaction data.

### EDA includes:

- Dataset structure and data types
- Descriptive statistics
- Missing-value analysis
- Fraud vs legitimate transaction distribution
- Transaction amount analysis
- Transaction time analysis
- Hourly transaction volume
- Hourly fraudulent transaction counts
- Hourly fraud-rate analysis

The analysis shows that fraud is extremely rare compared with legitimate transactions.

The highest observed hourly fraud rate in the analysis occurs around **Hour 2**, at approximately **1.71%**.

## ⚖️ Handling Class Imbalance

Because fraudulent transactions represent only approximately 0.17% of the dataset, class imbalance is a major challenge.

A **stratified train-test split** is first performed to preserve the original class proportions.

### SMOTE

**Synthetic Minority Over-sampling Technique (SMOTE)** is applied only to the training data.

The original training set contains:

```text
227,845 transactions
```

After SMOTE:

```text
454,902 transactions
```

The resulting classes are balanced:

```text
Legitimate: 227,451
Fraudulent: 227,451
```

The test set is **not oversampled** and retains the original class distribution.

This prevents information from the test set from leaking into the training process.

## 🤖 Machine Learning Models

Two classification models are trained and compared.

### 1. Logistic Regression

Logistic Regression is used as a baseline binary classification model.

The model is trained using the SMOTE-balanced training data.

### 2. Random Forest

Random Forest is used as the second classification model.

Because of the severe class imbalance, the Random Forest model uses:

```python
class_weight="balanced"
```

The Random Forest model is trained using the original scaled training data rather than the SMOTE-expanded dataset.

## 📈 Model Evaluation

The models are evaluated using:

- **Precision**
- **Recall**
- **F1-Score**
- **AUC-ROC**

These metrics are more informative than accuracy for this highly imbalanced fraud detection problem.

### Results

| Model | Precision | Recall | F1-Score | AUC-ROC |
|---|---:|---:|---:|---:|
| Logistic Regression | 0.0578 | **0.9184** | 0.1088 | **0.9708** |
| Random Forest | **0.8041** | 0.7959 | **0.8000** | 0.9609 |

## 🏆 Model Comparison

### Logistic Regression

Logistic Regression achieved:

- Precision: **5.78%**
- Recall: **91.84%**
- F1-Score: **10.88%**
- AUC-ROC: **97.08%**

It detected **90 of the 98 fraudulent transactions** in the test set.

However, it produced **1,467 false positives**, resulting in very low Precision.

Therefore, Logistic Regression is particularly strong when maximizing fraud detection Recall is the primary objective.

### Random Forest

Random Forest achieved:

- Precision: **80.41%**
- Recall: **79.59%**
- F1-Score: **80.00%**
- AUC-ROC: **96.09%**

It produced only **19 false positives** and **20 false negatives**.

Therefore, Random Forest provides a much stronger balance between identifying fraudulent transactions and avoiding false alarms.

### Overall Choice

For this project, **Random Forest provides the strongest overall balance**, mainly because it achieves substantially higher Precision and F1-Score.

Logistic Regression remains useful when the primary objective is to maximize Recall and minimize missed fraudulent transactions.

## 🔲 Confusion Matrix Analysis

### Logistic Regression

```text
[[55397, 1467],
 [    8,   90]]
```

Interpretation:

- True Negatives: 55,397
- False Positives: 1,467
- False Negatives: 8
- True Positives: 90

### Random Forest

```text
[[56845,   19],
 [   20,   78]]
```

Interpretation:

- True Negatives: 56,845
- False Positives: 19
- False Negatives: 20
- True Positives: 78

The confusion matrices demonstrate the trade-off between Recall and false-positive reduction.

## 🔬 Feature Importance

Feature importance was analyzed using both Logistic Regression coefficients and Random Forest feature importance.

### Logistic Regression

The strongest absolute coefficients included:

1. `Amount`
2. `V1`
3. `V10`
4. `V14`
5. `V4`
6. `V5`
7. `V17`
8. `V12`
9. `V16`
10. `V20`

### Random Forest

The most important Random Forest features included:

1. `V14`
2. `V17`
3. `V12`
4. `V4`
5. `V3`
6. `V10`
7. `V16`
8. `V2`
9. `V9`
10. `V11`

`V14` was the most important feature in the Random Forest model.

Because `V1`–`V28` are anonymized PCA-transformed features, their underlying business meanings cannot be directly interpreted.

## 📉 AUC-ROC Analysis

ROC curves were generated to compare the classification performance of both models across different decision thresholds.

### AUC-ROC Results

- Logistic Regression: **0.9708**
- Random Forest: **0.9609**

Logistic Regression achieved the higher AUC-ROC, indicating stronger overall class-separation performance across thresholds.

However, AUC-ROC is considered alongside Precision, Recall, and F1-Score when selecting a practical fraud detection model.

## 🚀 Scalability

The project also considers how a fraud detection system could handle approximately **1 million transactions per hour**.

This corresponds to approximately:

```text
278 transactions per second
```

A production-scale fraud detection system could use:

- Real-time model-serving infrastructure
- Apache Kafka or similar streaming technologies
- Distributed processing frameworks such as Apache Spark
- Efficient feature engineering pipelines
- Scalable prediction services
- Model and data monitoring
- Data-drift monitoring
- Periodic model retraining
- Threshold optimization
- Rule-based checks combined with machine learning

A scalable architecture would allow transactions to be processed continuously while maintaining low prediction latency.

## 🛠️ Technologies Used

### Programming Language

- Python

### Data Analysis

- Pandas
- NumPy

### Data Visualization

- Matplotlib
- Seaborn

### Machine Learning

- Scikit-learn
- imbalanced-learn

### Techniques

- Exploratory Data Analysis
- Stratified Train-Test Split
- Standardization
- SMOTE
- Logistic Regression
- Random Forest
- Confusion Matrix
- ROC Curve
- AUC-ROC
- Feature Importance

## 📁 Project Structure

```text
Task-7-Fraud-Detection/
│
├── Fraud_Detection.ipynb
└── README.md
```

> **Note:** The raw `creditcard.csv` dataset is not included in this repository because of its large file size.

## 🧠 Key Takeaways

- Fraud detection is a highly imbalanced classification problem.
- Accuracy alone can be misleading for fraud detection.
- SMOTE can be used to address class imbalance when applied only to training data.
- Logistic Regression achieved the highest Recall and AUC-ROC.
- Random Forest achieved substantially better Precision and F1-Score.
- Random Forest provides the strongest overall balance for this project.
- Feature importance analysis identifies the variables most useful for fraud prediction.
- A production system processing 1 million transactions per hour would require scalable real-time infrastructure.

## ✅ Conclusion

This project demonstrates an end-to-end machine learning workflow for detecting fraudulent credit card transactions.

The analysis covers data exploration, class imbalance handling, feature scaling, model training, model evaluation, feature importance, and scalability considerations.

The results show that **Random Forest is the preferred model for balanced fraud detection performance**, while **Logistic Regression is particularly effective when maximizing fraud detection Recall is the main priority**.

The project highlights the importance of using appropriate evaluation metrics and carefully handling class imbalance when developing fraud detection systems.

---

**Author:** Mohtasim Ahmed Awan
