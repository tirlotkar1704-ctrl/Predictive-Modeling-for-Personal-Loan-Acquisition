# Bank Personal Loan Eligibility Analysis

## 📋 Project Overview
This repository contains a comprehensive exploratory data analysis (EDA) and predictive insight framework conducted on a dataset of 5,000 banking customers. The primary objective is to analyze customer demographic, financial, and behavioral attributes to identify key drivers of personal loan acceptance, enabling data-driven target marketing and optimized customer acquisition strategies.

---

## 🛠️ Tech Stack & Tooling
* **Language:** Python 3.x
* **Data Manipulation:** Pandas, NumPy
* **Data Visualization:** Seaborn, Matplotlib

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
* Conducted comparative analysis evaluating the variance of continuous variables across target partitions (Loan Depositors vs. Non-Depositors).

---

## 📈 Strategic Insights

* **Financial Profile Dominance:** Income distributions show stark variations based on loan status. Personal loan adopters consistently sit in significantly higher income brackets, validating asset-to-liability safety thresholds.
* **Cross-Selling Synergy:** Customers holding active personal loans exhibit higher average monthly credit card spending (`CCAvg`), signaling strong cross-selling opportunities for premium financial tiers.
* **Demographic Headwinds:** A larger family size structurally correlates with a lower average individual income metric within this cohort, introducing an essential risk-modeling weight for loan evaluation engines.
* **Education Multiplier:** Higher formal educational achievement correlates strongly with higher income brackets, marking it as a critical demographic filter for prospective pre-approved loan outreach campaigns.

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