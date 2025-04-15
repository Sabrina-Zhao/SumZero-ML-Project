
# SumZero-ML-Project

This project builds a machine learning pipeline to predict excess returns of investment ideas based on structured and unstructured data collected from SumZero, a platform for buyside analysts. It combines data cleaning, sentiment analysis, and model training to evaluate the performance of a stock-picking strategy using NLP-enhanced features.

---

## 📂 Repository Structure

```
SumZero-ML-Project/
├── 1_Data_Cleaning.ipynb             # Cleaning and feature engineering
├── 2_Model_Construction.ipynb        # ML modeling, tuning, and evaluation
├── data/                             # Sample datasets (structure-only, anonymized)
│   ├── sample_final_df.csv
│   ├── sample_comments.csv
│   ├── ... (and others)
├── README.md                         # This file
├── .gitignore                        # Excludes large or sensitive files
```

---

## 📊 Project Workflow

### 1. Data Cleaning and Feature Construction
- Raw data includes investment theses, idea metadata, user interactions (views, likes, comments), and price targets.
- Processing steps:
  - Merge and clean multiple CSVs (`ideas.csv`, `comments.csv`, etc.)
  - Parse fields such as `direction`, `price_target`, `created`, and `fs_perm_sec_id`
  - Engineer features such as text length, engagement score, and target horizon

### 2. Sentiment Analysis
- Sentiment scores were extracted from investment theses using OpenAI's sentiment model.
- Texts were tokenized and filtered using RAKE and custom NLP tools.

### 3. Machine Learning Modeling
- Target: Transformed annualized excess return
- Features: Combined structured fields, user behavior data, NLP scores
- Model: Random Forest Regressor + GridSearchCV for tuning
- Evaluation:
  - R² score, MSE, visual plots
  - Rolling backtest by selecting top-k predicted ideas every 90 days

---

## 📈 Results

- The strategy generated positive alpha on out-of-sample test sets.
- Textual features, especially sentiment polarity, improved predictive power.
- Backtesting confirmed consistent outperformance against benchmark returns.

---

## 📂 Data Access

Due to confidentiality restrictions, original raw data from the SumZero platform cannot be publicly shared.

We provide sample files under `data/`:
- Only first 3 rows per dataset are included
- All contents have been anonymized (`sample_column_name`)
- Full column structure is preserved for reproducibility

Sample files include:

```
sample_final_df.csv
sample_ideas.csv
sample_comments.csv
sample_likes.csv
...
```

---

## ⚙️ Tools Used

- Python, pandas, numpy, scikit-learn
- Jupyter Notebook, Google Colab
- OpenAI GPT API for sentiment
- matplotlib for visualizations

---

## ✍️ Author

**Huiyuan (Sabrina) Zhao**  
Master of Quantitative Economics @ UCLA  
[LinkedIn](https://www.linkedin.com/in/...) | zhl18980305@gmail.com

---

## 🧠 Notes

- This project was part of a real-world collaboration and academic capstone.
- The model can be extended to classification (top vs. bottom ideas) or combined with portfolio construction logic.
- All results are for educational and exploratory purposes only.
