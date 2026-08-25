# 📈 SumZero Investment Thesis Return Modeling

An exploratory machine learning case study that combines structured idea metadata, engagement signals, and text-derived features to study subsequent excess returns on investment theses published to SumZero.

> 🗂️ **Project status:** Completed research case study. The notebooks retain the original saved outputs so the full analysis can be reviewed without access to the confidential source data.

## 🔎 Project overview

The project follows an end-to-end research workflow:

1. Assemble idea, author, engagement, and security-reference data.
2. Create 30-day post-publication engagement features.
3. Estimate horizon-adjusted security and benchmark returns.
4. Add rule-based and language-model-derived text features.
5. Train a time-ordered Random Forest regression model.
6. Review feature effects with SHAP and run exploratory portfolio diagnostics.

The modeling target is a signed log transformation of annualized excess return. The repository presents the complete research workflow from raw data preparation through model interpretation and portfolio analysis.

## 🗃️ Repository structure

```text
.
├── 1_Data_Cleaning.ipynb        # Data integration and feature engineering
├── 2_Model_Construction.ipynb   # Return construction, NLP features, modeling, and diagnostics
├── data/
│   ├── README.md                # Public-data scope and limitations
│   └── sample_*.csv             # Anonymized structural previews
├── requirements.txt             # Python dependencies used by the notebooks
└── README.md
```

## 📓 Notebook guide

### 1️⃣ Data cleaning and feature engineering

[`1_Data_Cleaning.ipynb`](1_Data_Cleaning.ipynb) joins the investment-idea table with security identifiers and aggregates activity observed during the first 30 days after publication. Feature groups include views, comments, updates, attachments, catalysts, author ratings, likes, follows, and buyside-consensus responses.

[Open in Colab](https://colab.research.google.com/github/Sabrina-Zhao/SumZero-ML-Project/blob/main/1_Data_Cleaning.ipynb)

### 2️⃣ Modeling and evaluation

[`2_Model_Construction.ipynb`](2_Model_Construction.ipynb) constructs security and S&P 500 benchmark returns, incorporates stored text scores, performs a chronological 80/20 train-test split, fits a Random Forest regressor, and presents SHAP and portfolio-selection diagnostics.

[Open in Colab](https://colab.research.google.com/github/Sabrina-Zhao/SumZero-ML-Project/blob/main/2_Model_Construction.ipynb)

## 🖼️ Viewing the archived results

GitHub renders the notebooks with their original saved tables, metrics, and figures. No execution is required to review those outputs. The output cells are intentionally retained because the confidential source dataset is no longer distributed with the project.

The stored holdout evaluation reports a positive out-of-sample R². The notebook also compares top-ranked, bottom-ranked, and randomly selected ideas, then evaluates performance across rolling windows to show how the signal changes over time.

## 🚀 Reproducing the workflow

The public sample files are anonymized previews and are **not sufficient to rerun the full pipeline**. Reproduction requires an authorized export with the original schema and the intermediate sentiment and price files referenced by the notebooks.

For an environment with those inputs:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

Run the notebooks in numerical order. The original notebooks use a Google Drive path; update `base_path` to the location of the authorized data before execution. Networked steps may also require Yahoo Finance access and an `OPENAI_API_KEY`.

## 🔐 Data and confidentiality

The underlying SumZero data cannot be published because of confidentiality restrictions. Files in [`data/`](data/) contain short, anonymized previews intended only to show the types of source tables used. They do not preserve executable production data or contain the full research sample.

See [`data/README.md`](data/README.md) for the public file inventory and handling notes.

## 🧠 Modeling design

- Chronological 80/20 train-test split preserves the time order of investment ideas.
- Random Forest regression captures nonlinear relationships across structured, engagement, and text-derived features.
- SHAP analysis explains the features that contribute most strongly to model predictions.
- Top-k selection and rolling-window evaluation connect model scores to a portfolio-oriented research question.
- Saved language-model scores keep the published analysis stable and avoid unnecessary API reruns.

## 🛠️ Technology

Python, pandas, NumPy, NLP, scikit-learn, yfinance, OpenAI API, SHAP, matplotlib, and Jupyter.

## 👤 Author

Huiyuan (Sabrina) Zhao — [GitHub](https://github.com/Sabrina-Zhao)

## ⚠️ Disclaimer

This repository is provided for educational and research purposes only. It does not constitute investment advice, a recommendation, or an offer to buy or sell any security.
