# 🏦 FinSight Bank — NPA Prediction & Credit Risk Modelling

> **End-to-End Data Analysis Capstone Project**  
> EDA • Feature Engineering • Linear Regression

---

## 👤 Student Details

| Field | Details |
|-------|---------|
| **Name** | Gajendra Rathod |
| **Course** | Big data Analytics |
| **Institute** | CDAC  |

---

## 📌 Project Overview

This capstone project performs a full end-to-end exploratory data analysis and predictive modelling pipeline on a synthetic banking dataset representing **FinSight Bank's** retail loan portfolio. The objective is to understand the drivers of **Non-Performing Assets (NPA)** and build a regression model to predict **Loss Given Default (LGD %)**.

The project works with **9 relational CSV datasets** that are joined into a single unified dataframe of **2,000,000 loan records** and taken through every stage of the data science lifecycle — from ingestion and cleaning to modelling and business recommendations.

---

## 📁 Project Structure

```
📦 FinSight-Bank-EDA-CreditRisk/
├── 📓 260240325016_Gajendra_EDA_CASE_STUDY.ipynb   # Main analysis notebook
├── 📄 README.md                                     # Project documentation
└── 📂 data/                                         # Input CSV datasets (9 files)
    ├── loans_master.csv
    ├── branch_region_economy.csv
    ├── collateral_assets.csv
    ├── credit_card_behavior.csv
    ├── customer_bureau.csv
    ├── loan_enquiry_bureau.csv
    ├── loan_performance.csv
    ├── monthly_emi_track.csv
    └── payment_history.csv
```

---

## 🔄 Project Phases

### Phase 0 — Setup
- Library imports (`pandas`, `numpy`, `matplotlib`, `scipy`, `sklearn`, `statsmodels`)
- Display settings configuration

---

### Phase 1 — Data Profiling & 9-Table Join

| Question | Task |
|----------|------|
| **1(a)** | Data Ingestion — Load all 9 CSV files with memory optimization via downcasting |
| **1(b)** | Sequential 9-table left join on `loan_id` with row integrity validation & orphan record detection |
| **1(c)** | Dirty Data Detection — Identified and flagged 8 injected data quality issues (negative income, out-of-bounds CIBIL, extreme utilization, etc.) |
| **1(d)** | Missing Value Classification & Imputation using domain-specific strategies |
| **1(e)** | Outlier Treatment — Winsorization at 1st/99th percentile on top 6 most skewed columns |

---

### Phase 2 — Exploratory Data Analysis (EDA)

A comprehensive suite of **10+ visualizations** covering:
- CIBIL score distribution (KDE) — Defaulted vs. Performing
- Loan purpose default rates
- Grade vs. default rate analysis (A–G)
- EMI-to-income ratio boxplots by loan status
- Dual-axis time-series: repo rate vs. retail default trend
- Geographic and regional risk heatmaps

---

### Phase 3 — Feature Engineering

| Category | Features Created |
|----------|-----------------|
| **Ratio Features** | `emi_to_income_ratio`, `loan_to_income_ratio`, `rate_spread_pct`, `real_interest_rate` |
| **Credit Risk Flags** | `credit_util_composite`, `delinq_severity_score`, `enq_velocity_score` |
| **Behavioural Features** | `income_stability_ratio`, `credit_depth_score`, `collateral_coverage_ratio` |
| **Log Transforms** | `log_annual_inc`, `log_loan_amnt` (skewness reduction) |
| **Hypothesis Test** | COVID-19 structural break test (Welch's T-Test on LGD% pre/post pandemic years) |

---

### Phase 4 — Regression Modelling (LGD Prediction)

| Step | Details |
|------|---------|
| **4(a)** | VIF Analysis — Iterative stepwise feature elimination (VIF threshold = 10) |
| **4(b)** | Baseline OLS Regression with full `statsmodels` summary |
| **4(c)** | Regularized Models — Ridge (L2), Lasso (L1), ElasticNet with 5-fold GridSearchCV |

---

### Phase 5 — Model Diagnostics

4-Panel diagnostic matrix:
1. **Residuals vs Fitted** — Linearity & homoscedasticity
2. **Normal Q-Q Plot** — Normality of errors
3. **Scale-Location Plot** — Heteroscedasticity scan
4. **Cook's Distance** — Influential observation detection

---

### Phase 6 — Business Recommendations

Five board-ready, evidence-backed credit risk policy recommendations:

| # | Recommendation | Key Action |
|---|---------------|------------|
| 1 | Risk-Based Pricing for Speculative Loan Categories | 150–250 bps surcharge on high-risk loan purposes |
| 2 | Macro-Driven Early Warning Triggers | Tighten DTI limits within 30 days of RBI rate hike > 50 bps |
| 3 | Composite Bureau Scoring Beyond Standalone CIBIL | Multi-layered scorecard with `enq_velocity_score`, `credit_util_composite` |
| 4 | Hard Caps on Subprime Credit Grade Allocation | Max 5% of monthly originations for Grade D–G loans |
| 5 | EMI/Income Underwriting Cap | Reject applications where combined DTI > 45% of net monthly income |

---

## 🛠️ Tech Stack

| Library | Purpose |
|---------|---------|
| `pandas` | Data manipulation & joins |
| `numpy` | Numerical computing |
| `matplotlib` | Visualizations |
| `scipy` | Statistical testing |
| `statsmodels` | OLS regression & VIF analysis |
| `scikit-learn` | Ridge, Lasso, ElasticNet, GridSearchCV |

---

## ▶️ How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/finsight-bank-eda-credit-risk.git
   cd finsight-bank-eda-credit-risk
   ```

2. **Install dependencies**
   ```bash
   pip install pandas numpy matplotlib scipy statsmodels scikit-learn jupyter
   ```

3. **Place the 9 CSV data files** inside the `data/` folder (or update the `data_folder` path in the notebook).

4. **Launch Jupyter and open the notebook**
   ```bash
   jupyter notebook 260240325016_Gajendra_EDA_CASE_STUDY.ipynb
   ```

5. **Run all cells** sequentially from Phase 0 through Phase 6.

---

## 📊 Key Findings

- **CIBIL score alone explains only ~18% of default variance** — composite scoring is essential.
- **Grade E–G default rates:** E = 24.7%, F = 38.1%, G = 48.9% — a steep non-linear escalation.
- **EMI-to-income ratio** is one of the strongest linear predictors of LGD% (β = +0.15 to +0.22).
- **COVID-19** caused a statistically significant structural break in LGD distribution (p < 0.05).
- **Repo rate hikes** lead retail default spikes with a 12–18 month transmission lag.

---

## 📜 License

This project is submitted as an academic capstone assignment for CDAC BDA. All data used is synthetic and for educational purposes only.

---

*Made with 💡 by **Gajendra Rathod***
