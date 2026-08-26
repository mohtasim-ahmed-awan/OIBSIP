# Wine Quality Prediction — Oasis Infobyte Task 6

## Project Overview

This project was completed as part of the **Oasis Infobyte Internship — Task 6**.

The objective is to predict wine quality categories using machine learning classification algorithms based on the physicochemical properties of white wine.

The project includes data cleaning, exploratory data analysis (EDA), class imbalance analysis, feature engineering, model training, model evaluation, feature-importance analysis, and comparison of multiple classification algorithms.

## Objectives

- Analyze the Wine Quality dataset.
- Inspect the dataset structure and data types.
- Identify and remove duplicate observations.
- Analyze the distribution of wine quality scores.
- Explore the distributions of the physicochemical features.
- Analyze correlations between features and wine quality.
- Investigate class imbalance.
- Convert the original quality scores into three quality categories.
- Perform a stratified train-test split.
- Train and compare Random Forest, SGD Classifier, and SVC.
- Evaluate the models using multiple performance metrics.
- Analyze Random Forest feature importance.
- Select the most suitable model for deployment.

## Dataset

The project uses the **Wine Quality — White Wine** dataset.

The original dataset contains **4,898 observations**, **12 columns**, **11 physicochemical features**, and **1 target variable (`quality`)**.

### Features

1. Fixed acidity
2. Volatile acidity
3. Citric acid
4. Residual sugar
5. Chlorides
6. Free sulfur dioxide
7. Total sulfur dioxide
8. Density
9. pH
10. Sulphates
11. Alcohol

### Target

The original target variable is `quality`, with quality scores ranging from 3 to 9.

## Data Cleaning

Initial inspection identified **937 duplicate rows**.

The duplicates were removed before feature engineering, train-test splitting, and model training.

- Original rows: **4,898**
- Duplicate rows removed: **937**
- Final rows: **3,961**
- Remaining duplicates: **0**

No missing values were present.

Removing duplicates before splitting helps prevent identical observations from appearing in both the training and testing datasets.

## Exploratory Data Analysis

The notebook includes:

- Dataset structure and data types
- Missing-value analysis
- Duplicate-value analysis
- Descriptive statistics
- Wine quality score distribution
- Distribution plots for all 11 physicochemical features
- Correlation heatmap

## Class Imbalance

The original quality scores are not evenly distributed. To create a practical classification problem, the quality scores were grouped into three categories:

| Quality Class | Quality Score |
|---|---|
| Low | ≤ 5 |
| Medium | 6 |
| High | ≥ 7 |

After duplicate removal:

| Class | Count | Percentage |
|---|---:|---:|
| Low | 1,348 | 34.03% |
| Medium | 1,788 | 45.14% |
| High | 825 | 20.83% |

The Medium class is the largest class, while the High class is the smallest. Class imbalance can cause models to favor the majority class, so accuracy alone is not sufficient for evaluation.

The models use balanced class weights where applicable, and precision, recall, F1-score, and confusion matrices are also considered.

## Feature Engineering

The original quality scores were converted into three categories:

- **Low:** quality ≤ 5
- **Medium:** quality = 6
- **High:** quality ≥ 7

Quality score 6 was selected as the Medium category because it represents the central and most common quality level. Scores of 5 or below represent lower-quality wines, while scores of 7 or above represent higher-quality wines.

## Train-Test Split

An **80/20 stratified train-test split** was used with `random_state=42`.

Stratification maintains similar class proportions in the training and testing datasets.

## Machine Learning Models

Three classification algorithms were trained:

1. **Random Forest Classifier**
2. **SGD Classifier**
3. **Support Vector Classifier (SVC)**

Feature scaling was used for the SGD and SVC models.

## Model Evaluation

The models were evaluated using:

- Accuracy
- Weighted Precision
- Weighted Recall
- Weighted F1-Score
- Classification reports
- Confusion matrices

### Final Model Comparison

| Model | Accuracy | Weighted Precision | Weighted Recall | Weighted F1-Score |
|---|---:|---:|---:|---:|
| **Random Forest** | **60.03%** | **61.18%** | **60.03%** | **59.72%** |
| SVC | 56.37% | 57.77% | 56.37% | 55.78% |
| SGD Classifier | 50.69% | 51.32% | 50.69% | 48.43% |

## Random Forest Feature Importance

The Random Forest feature-importance analysis identified the following features among the most important:

1. **Alcohol**
2. **Density**
3. **Volatile acidity**
4. **Free sulfur dioxide**
5. **Total sulfur dioxide**

## Best Performing Model

### Random Forest

Random Forest achieved the strongest overall performance:

- **Accuracy:** 60.03%
- **Weighted Precision:** 61.18%
- **Weighted Recall:** 60.03%
- **Weighted F1-Score:** 59.72%

Therefore, **Random Forest is the most suitable model for deployment among the three models tested**.

## Conclusion

This project demonstrates an end-to-end machine learning classification workflow for predicting wine quality categories.

The dataset was cleaned by removing duplicate observations, followed by exploratory data analysis, class imbalance analysis, feature engineering, stratified train-test splitting, model training, and evaluation.

Among Random Forest, SVC, and SGD Classifier, **Random Forest achieved the strongest overall performance**, with an accuracy of **60.03%** and a weighted F1-score of **59.72%**.

Further improvements could be explored through hyperparameter tuning, cross-validation, and additional techniques for handling class imbalance before production deployment.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## Project Structure

```text
Task 6 - Wine Quality Prediction/
│
├── Wine_Quality_Prediction.ipynb
├── winequality-white.csv
└── README.md
```

## Internship Information

**Program:** Oasis Infobyte Internship  
**Task:** Task 6 — Wine Quality Prediction  
**Project Type:** Machine Learning Classification  
**Dataset:** White Wine Quality Dataset  
**Author:** Mohtasim Ahmed Awan
