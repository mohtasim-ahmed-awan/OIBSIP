# Customer Segmentation Analysis using K-Means Clustering

## 📌 Project Overview

This project was completed as **Task 2** of the **Oasis Infobyte Data Analytics Internship**.

The objective is to segment customers of an e-commerce company into meaningful groups based on their purchasing behavior using **RFM (Recency, Frequency, Monetary) Analysis** and the **K-Means Clustering** algorithm. The resulting customer segments help businesses develop targeted marketing strategies and improve customer retention.

---

## 🎯 Objective

- Analyze customer purchasing behavior.
- Perform RFM (Recency, Frequency, Monetary) analysis.
- Apply K-Means clustering to identify customer segments.
- Visualize customer groups.
- Provide business insights and marketing recommendations for each segment.

---

## 🛠️ Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn

---

## 📂 Dataset

**Dataset:** Online Retail Dataset

The dataset contains one year of transactional data for an online retail company.

### Features

- Invoice Number
- Product Code
- Product Description
- Quantity
- Invoice Date
- Unit Price
- Customer ID
- Country

---

## 📊 Project Workflow

### 1. Data Loading
- Import the dataset.
- Inspect its structure.

### 2. Data Cleaning
- Remove missing Customer IDs.
- Remove duplicate records.
- Remove invalid quantities.
- Remove zero-priced products.
- Create the **TotalAmount** feature.

### 3. Exploratory Data Analysis
- Check data types.
- Handle missing values.
- Generate descriptive statistics.

### 4. Feature Engineering
Create RFM features:

- **Recency**
- **Frequency**
- **Monetary**

### 5. Feature Scaling
- Standardize RFM features using **StandardScaler**.

### 6. K-Means Clustering
- Determine the optimal number of clusters using the **Elbow Method**.
- Apply K-Means clustering.

### 7. Data Visualization
- Elbow Method Plot
- Customer Distribution Bar Chart
- Recency vs Monetary Scatter Plot
- Frequency vs Monetary Scatter Plot

### 8. Cluster Profiling
Analyze the average:

- Recency
- Frequency
- Monetary Value

for each customer segment.

### 9. Business Insights
Recommend marketing strategies for each customer cluster.

---

## 📈 Results

The analysis identified **three distinct customer segments**:

### 🔴 Cluster 0 – Inactive / Low-Value Customers
- High recency
- Low purchase frequency
- Low spending

**Recommended Strategy**
- Re-engagement campaigns
- Discount offers
- Promotional emails

---

### 🟡 Cluster 1 – Regular / Loyal Customers
- Moderate recency
- Moderate purchase frequency
- Moderate spending

**Recommended Strategy**
- Loyalty programs
- Personalized recommendations
- Reward points

---

### 🟢 Cluster 2 – VIP / High-Value Customers
- Very recent purchases
- Very high purchase frequency
- Highest spending

**Recommended Strategy**
- VIP memberships
- Premium customer support
- Exclusive discounts
- Early access to new products

---

## 📁 Repository Structure

```text
Customer-Segmentation-Analysis/
│
├── Customer_Segmentation_Analysis.ipynb
├── OnlineRetail.csv
└── README.md
```

---

## 🚀 Key Learning Outcomes

- Data Cleaning
- Exploratory Data Analysis
- Feature Engineering
- RFM Analysis
- Data Standardization
- K-Means Clustering
- Customer Segmentation
- Data Visualization
- Business Analytics
- Marketing Strategy Development

---

## 📌 Conclusion

This project demonstrates how customer segmentation can be performed using RFM analysis and K-Means clustering. By identifying customer groups based on purchasing behavior, businesses can develop targeted marketing campaigns, improve customer retention, and maximize customer lifetime value.

---

## 👨‍💻 Author

**Mohtasim Ahmed Awan**

Completed as part of the **Oasis Infobyte Data Analytics Internship**.