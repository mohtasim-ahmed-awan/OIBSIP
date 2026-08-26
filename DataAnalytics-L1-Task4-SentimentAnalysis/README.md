# Sentiment Analysis

## Task 4 – Oasis Infobyte Internship

### Objective
This project builds a machine learning model that classifies the sentiment of text data as **positive**, **negative**, or **neutral**, providing insights into public opinion or customer feedback.

---

## Dataset
- **Source:** [Sentiment Analysis Dataset (Kaggle)](https://www.kaggle.com/datasets/abhi8923shriv/sentiment-analysis-dataset)
- **File used:** `train.csv`
- **Size:** ~27,500 tweets
- **Columns used:** `text`, `sentiment`
- **Classes:** `positive`, `negative`, `neutral`

---

## Tech Stack
- Python
- pandas, numpy
- scikit-learn
- NLTK
- matplotlib, seaborn
- WordCloud
- Jupyter Notebook

---

## Project Workflow

1. **Data Loading & Inspection**
   - Loaded the dataset and inspected shape, column types, and missing values
   - Checked class distribution across positive, negative, and neutral sentiment

2. **Data Cleaning**
   - Removed the single missing text record
   - Selected only the relevant `text` and `sentiment` columns

3. **Text Preprocessing**
   - Lowercasing
   - Punctuation and special character removal
   - Tokenization
   - Stopword removal
   - Lemmatization

4. **Feature Extraction**
   - TF-IDF Vectorization (with unigrams and bigrams) to convert cleaned text into numerical features

5. **Train/Test Split**
   - 80/20 split with stratification to preserve class balance

6. **Model Training**
   - **Naive Bayes** (Multinomial NB)
   - **Logistic Regression**

7. **Model Evaluation**
   - Accuracy, Precision, Recall, and F1-score for both models
   - Confusion matrices for both models
   - Classification reports

8. **Visualization**
   - Bar chart of sentiment class distribution
   - WordClouds for positive, negative, and neutral sentiment classes

9. **Error Analysis**
   - Reviewed 5 misclassified examples from the best-performing model
   - Discussed common causes of misclassification (short/ambiguous text, sarcasm, boundary confusion between neutral and emotional classes, loss of punctuation cues during preprocessing)

10. **Conclusion**
    - Compared both models and identified the best performer
    - Discussed real-world applications of the sentiment classification pipeline

---

## Results

| Model | Accuracy | Precision | Recall | F1-Score |
|---|---|---|---|---|
| Naive Bayes | 64% | 0.68 | 0.62 | 0.64 |
| Logistic Regression | 69% | 0.71 | 0.68 | 0.69 |

**Logistic Regression** was selected as the best-performing model.

---

## Real-World Applications
- Monitoring customer feedback and social media mentions
- Flagging negative reviews or complaints for faster response
- Tracking public opinion on a product or brand launch over time
- Summarizing overall customer sentiment trends at scale

---

## How to Run
1. Clone or download this repository
2. Install the required libraries:
   ```bash
   pip install pandas numpy scikit-learn nltk matplotlib seaborn wordcloud
   ```
3. Open `Sentiment_Analysis.ipynb` in Jupyter Notebook
4. Run all cells sequentially

---

## Acknowledgment
This project was completed as part of **Task 4** of the **Oasis Infobyte Internship** program.

---

**Mohtasim Ahmed Awan**
