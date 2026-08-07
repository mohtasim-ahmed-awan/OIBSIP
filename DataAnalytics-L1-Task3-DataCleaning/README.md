# Task 3 · Cleaning Data

**Oasis Infobyte Internship — Data Science / Analytics Track**

## Objective

Demonstrate professional-level data cleaning skills by taking a deliberately messy dataset and systematically transforming it into a clean, analysis-ready dataset, with every decision documented.

## Dataset

**Cafe Sales — Dirty Data for Cleaning Training**
Source: [Kaggle](https://www.kaggle.com/datasets/ahmedmohamed2003/cafe-sales-dirty-data-for-cleaning-training)

10,000 rows of synthetic cafe sales transactions, intentionally corrupted with missing values, placeholder errors (`ERROR`, `UNKNOWN`), and inconsistent types to simulate a real-world messy dataset.

| Column | Description |
|---|---|
| Transaction ID | Unique identifier for each transaction |
| Item | Name of the item purchased |
| Quantity | Number of units purchased |
| Price Per Unit | Price of a single unit |
| Total Spent | Total amount spent on the transaction |
| Payment Method | Method used to pay (Cash, Credit Card, Digital Wallet) |
| Location | Where the transaction occurred (In-store, Takeaway) |
| Transaction Date | Date of the transaction |

## Tech Stack

- Python
- pandas
- numpy
- Jupyter Notebook

## Project Structure

```
├── Data_Cleaning.ipynb        # Main notebook — full cleaning pipeline
├── dirty_cafe_sales.csv       # Raw input dataset
├── cleaned_cafe_sales.csv     # Cleaned output dataset
└── README.md
```

## Cleaning Pipeline

The notebook follows a structured, documented pipeline:

1. **Data Quality Report (Before Cleaning)** — nulls per column, missing %, dtypes, unique value counts, and a separate audit of `ERROR`/`UNKNOWN` placeholder counts per column.
2. **Missing Data Handling** — placeholders (`ERROR`, `UNKNOWN`) mapped to `NaN`; each column's strategy is justified in a markdown cell:
   - **Numerical fields** (Quantity, Price Per Unit, Total Spent): reconstructed from their logical relationship (`Total Spent = Quantity × Price Per Unit`) wherever two of the three values are known, before falling back to median imputation for the rest.
   - **Categorical fields** (Item, Payment Method, Location): mode imputation.
   - **Transaction Date**: converted to `datetime`, missing values filled with the mode date.
3. **Duplicate Removal** — checked across all columns; 0 duplicate rows found and documented.
4. **Standardisation** — invalid placeholder text normalized to `NaN` prior to imputation; date column standardized to `datetime64[ns]`.
5. **Outlier Detection** — IQR method applied to all numeric columns; 259 potential outliers identified in `Total Spent`, inspected, and retained as legitimate high-value transactions (documented decision).
6. **Data Type Correction** — final dtypes: `Transaction ID`/`Item`/`Payment Method`/`Location` → `string`, `Quantity` → `int64`, `Price Per Unit`/`Total Spent` → `float64`, `Transaction Date` → `datetime64[ns]`.
7. **Numerical Consistency Check** — verified `Quantity × Price Per Unit = Total Spent` holds for all rows after cleaning.
8. **Before vs. After Summary Table** — null count, duplicate count, row count, and dtype accuracy compared pre/post cleaning.
9. **Export** — cleaned dataset saved to `cleaned_cafe_sales.csv`.

## Results

| Metric | Before Cleaning | After Cleaning |
|---|---|---|
| Total Missing Values | 6,826 | 0 |
| Duplicate Rows | 0 | 0 |
| Row Count | 10,000 | 10,000 |
| Correct Data Types | 0 / 8 | 8 / 8 |
| Numerical Inconsistencies (Qty × Price ≠ Total) | — | 0 |

## How to Run

1. Clone/download this repository.
2. Ensure `dirty_cafe_sales.csv` is in the same directory as the notebook.
3. Install dependencies:
   ```
   pip install pandas numpy jupyter
   ```
4. Open and run the notebook top to bottom:
   ```
   jupyter notebook Data_Cleaning.ipynb
   ```
5. The cleaned dataset will be saved as `cleaned_cafe_sales.csv` in the same directory.

## Author

Mohtasim
Oasis Infobyte Internship — Task 3
