# Bank Personal Loan Eligibility Analysis

## 📋 Project Overview
This repository contains a comprehensive exploratory data analysis (EDA) and predictive modeling pipeline conducted on a dataset of 5,000 banking customers. The primary objective is to analyze customer demographic, financial, and behavioral attributes to identify key drivers of personal loan acceptance, then train and validate a classifier that scores customers by acceptance likelihood — enabling data-driven target marketing and optimized customer acquisition strategies.

All insights below are re-derived from the data inside the notebook (Section 11) rather than asserted, and any claim the data contradicts is recorded as such.

---

## 🛠️ Tech Stack & Tooling
* **Language:** Python 3.x
* **Data Manipulation:** Pandas, NumPy
* **Data Visualization:** Seaborn, Matplotlib
* **Predictive Modeling:** Scikit-learn (Logistic Regression, Decision Tree, Random Forest)

---

## 📂 Dataset Profile
* **Volume:** 5,000 Customer Records
* **Key Features:** Income, Experience, Age, Family Size, Education, CCAvg (Credit Card Average Spend), Securities Account, CD Account, Online Banking, Credit Card, and Personal Loan (Target variable).
* **Primary Source:** [Kaggle Bank Personal Loan Modelling Dataset](https://www.kaggle.com/datasets/krantiswalke/bank-personal-loan-modelling)

---

## 🔬 Methodology & Core Workflow

### 1. Data Quality Assurance & Preprocessing
* Inspected data types, schema structures, and missing/null value counts to ensure data integrity.
* Identified and resolved systemic data anomalies, such as negative/invalid entries within the `Experience` column, using logical imputation.

### 2. Exploratory Data Analysis (EDA)
* Generated descriptive statistical metrics (mean, median, variance, percentiles) for continuous attributes.
* Constructed distribution plots (Histograms, KDE plots) to evaluate data skewness, particularly for financial fields like `Income` and `CCAvg`.
* Utilized Box plots and Scatter plots to capture multi-variable interactions across cross-sections of the cohort.

### 3. Feature Correlation & Segmentation
* Executed a Pearson correlation matrix to pinpoint high-affinity variables related to loan adoption.
* Segmented customer cohorts by `Education` and `Account Types` to analyze aggregated behavioral distributions.
* Conducted comparative analysis evaluating the variance of continuous variables across target partitions (Loan Depositors vs. Non-Depositors), quantifying separation via Cohen's d effect sizes.

### 4. Predictive Modeling & Campaign Targeting
* Constructed a leakage-guarded feature matrix, explicitly excluding row identifiers (`ID`), nominal codes (`ZIP Code`), collinear duplicates (`Experience`, r = 0.994 with `Age`), and all engineered labels derived from the target.
* Trained and cross-validated three classifiers (Logistic Regression, Decision Tree, Random Forest) using stratified 5-fold validation on a training partition, with `class_weight='balanced'` to address the 15.6:1 class imbalance.
* Evaluated on a held-out 25% test partition using precision, recall, F1, ROC-AUC and PR-AUC. Accuracy is reported but deliberately de-emphasised — a naive "predict nobody converts" classifier scores 90.4% while identifying zero prospects.
* Translated model scores into an operational targeting rule via a decision-threshold sweep and score-decile lift analysis.

---

## 📈 Strategic Insights

* **Financial Profile Dominance:** Income distributions show stark variations based on loan status. Personal loan adopters consistently sit in significantly higher income brackets, validating asset-to-liability safety thresholds.
* **Cross-Selling Synergy:** Customers holding active personal loans exhibit higher average monthly credit card spending (`CCAvg`), signaling strong cross-selling opportunities for premium financial tiers.
* **Demographic Headwinds:** A larger family size correlates with a lower average individual income metric within this cohort (r = -0.16). The effect is weak and non-monotonic — income actually peaks at a family size of 2 — so it belongs in a loan evaluation engine as a minor risk weight rather than a primary driver.
* **Education Filter (not an income proxy):** Higher formal education does **not** imply higher income in this dataset. The correlation is *negative* (r = -0.19): Undergraduate customers carry the highest mean income ($85.59K) versus Graduate ($64.31K) and Advanced/Professional ($66.12K). Education nonetheless remains a valid targeting filter, because loan acceptance still climbs with it (4.4% → 13.7%) — it influences conversion through a channel other than raw earnings.
* **Deposit Relationship as the Strongest Signal:** CD Account holders convert at **46.4%** against **7.2%** for non-holders — a 4.8× lift on the 9.6% baseline. Only 302 of 5,000 customers hold one, making the existing deposit book the highest-yield, lowest-volume pool for pre-approved outreach.
* **Model-Backed Targeting:** A Random Forest classifier reaches **0.98 PR-AUC** and **0.83 precision at 0.97 recall** on held-out data, against a 0.096 random-model baseline. Score deciles concentrate conversions sharply: contacting the top 10% of scored customers reaches 94% of all adopters, and the top 20% reaches 100%.
* **Collinearity Caution:** `Age` and `Experience` are near-perfectly collinear (r = 0.994) and both show effectively zero correlation with acceptance. Neither should carry weight in a targeting rule, and one must be dropped before modeling.

---

## 👨‍💻 Project Information

* **Author:** Divya Tirlotkar
---

## 🤝 Contribution Framework
Contributions to optimize the statistical methodologies or introduce predictive modeling architectures are welcome.
1. Fork the repository.
2. Initialize an isolated feature branch (`git checkout -b feature/optimization-improvement`).
3. Commit structured changes following descriptive commit naming styles (`git commit -m 'Optimize data pipeline'`).
4. Push code to the upstream remote branch (`git push origin feature/optimization-improvement`).
5. Open a formal Pull Request for peer review.