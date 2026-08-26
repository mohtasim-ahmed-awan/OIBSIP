# 🏠 House Price Prediction using Linear Regression

## 📌 Project Overview

This project was completed as **Task 5 of the Oasis Infobyte Data Analytics Internship**.

The objective is to build a machine learning model to predict house prices using numerical and categorical housing features. The project covers exploratory data analysis, preprocessing, One-Hot Encoding, correlation analysis, Linear Regression, model evaluation, residual analysis, coefficient analysis, and a bonus comparison with Ridge and Lasso Regression.

## 👨‍💻 Author

**Mohtasim Ahmed Awan**

**Internship:** Oasis Infobyte Data Analytics Internship  
**Task:** Task 5 — House Price Prediction  
**Project Type:** Machine Learning / Regression  
**Primary Model:** Linear Regression  
**Bonus Models:** Ridge Regression & Lasso Regression  
**Language:** Python

## 🎯 Objectives

- Explore and understand the housing dataset
- Analyze the distribution of house prices
- Identify numerical and categorical features
- Check for missing values and duplicate records
- Apply One-Hot Encoding to categorical variables
- Analyze feature relationships using a correlation heatmap
- Split the data using an 80/20 train-test split
- Build and evaluate a Linear Regression model
- Calculate MSE, RMSE, and R²
- Compare actual and predicted house prices
- Analyze residuals and regression coefficients
- Compare Linear Regression with Ridge and Lasso Regression

## 📊 Dataset

The dataset contains **545 observations and 13 columns**. The target variable is `price`.

### Numerical Features
- `area`
- `bedrooms`
- `bathrooms`
- `stories`
- `parking`

### Categorical Features
- `mainroad`
- `guestroom`
- `basement`
- `hotwaterheating`
- `airconditioning`
- `prefarea`
- `furnishingstatus`

### Target Variable
- `price`

The dataset contains **no missing values** and **no duplicate rows**.

## 🛠️ Technologies & Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn

### Machine Learning Models
- Linear Regression
- Ridge Regression
- Lasso Regression

## 🔎 Project Workflow

### 1. Data Loading & Inspection
The dataset was loaded and inspected for dimensions, columns, data types, missing values, duplicates, and summary statistics.

### 2. Exploratory Data Analysis
EDA included descriptive statistics, identification of numerical and categorical features, and analysis of the house-price distribution.

### 3. Data Preprocessing
Categorical variables were converted into numerical representations using **One-Hot Encoding** with `drop_first=True`.

### 4. Correlation Analysis
A correlation heatmap was created to examine relationships between the target variable and the numerical/encoded features.

### 5. Train-Test Split
The dataset was divided into **80% training data** and **20% testing data**, using `random_state=42`.

## 🤖 Linear Regression Results

The Linear Regression model was trained on the processed features and evaluated on the test set.

| Metric | Result |
|---|---:|
| MSE | 1,754,318,687,330.66 |
| RMSE | 1,324,506.96 |
| R² | **0.6529** |

The model achieved an **R² of 0.6529**, meaning approximately **65.29% of the variation in house prices** is explained by the features included in the model.

## 📈 Model Visualizations

The notebook includes:

- House price distribution
- Correlation heatmap
- Actual vs. predicted house prices
- Residual plot
- Regression coefficient visualization

These visualizations were used to understand the data and assess model performance.

## ⭐ Bonus: Ridge & Lasso Regression

The project also compares Linear Regression with Ridge and Lasso Regression.

| Model | MSE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 1.754319 × 10¹² | 1,324,507 | **0.652924** |
| Ridge Regression | 1.756474 × 10¹² | 1,325,320 | 0.652498 |
| Lasso Regression | 1.754321 × 10¹² | 1,324,508 | **0.652924** |

### Comparison Result

Linear Regression produced the best overall performance. Ridge Regression performed slightly worse, while Lasso Regression produced almost identical results.

Therefore, regularization did not provide a meaningful improvement over standard Linear Regression for this dataset.

## 📝 Conclusion

This project demonstrates a complete machine learning workflow for house price prediction, including EDA, preprocessing, feature engineering, regression modeling, model evaluation, visualization, residual analysis, and regularization.

The Linear Regression model achieved an **R² score of 0.6529**, explaining approximately **65.29% of the variation in house prices**.

The Ridge and Lasso comparison showed that regularization did not meaningfully improve performance over the standard Linear Regression model.

## 📂 Project Structure

```text
Task 5/
│
├── House_Price_Prediction_Linear_Regression.ipynb
├── Housing.csv
└── README.md
```

## 🚀 How to Run

1. Download or clone the repository.
2. Place `Housing.csv` in the same directory as the notebook.
3. Open `House_Price_Prediction_Linear_Regression.ipynb` in Jupyter Notebook or JupyterLab.
4. Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

5. Run the notebook cells sequentially.

## 📌 Internship Information

**Organization:** Oasis Infobyte  
**Internship:** Data Analytics Internship  
**Task:** Task 5 — House Price Prediction  
**Author:** Mohtasim Ahmed Awan
