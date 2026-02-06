# 🏦 Bank Loan Risk & Performance Analysis Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=Power%20BI&logoColor=black)
![Data Analytics](https://img.shields.io/badge/Data%20Analytics-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

## 🚀 Live Demo

Interact with the full dashboard online:
[**👉 Click Here to View Live Power BI Dashboard**](https://app.powerbi.com/links/C2NMXu8zql?ctid=e14e73eb-5251-4388-8d67-8f9f2e2d5a46&pbi_source=linkShare&bookmarkGuid=a0c14fbb-70fd-46d0-bd22-ccb677242154)

---

## 📌 Project Overview

This project involves the development of an interactive **Power BI Dashboard** to analyze a dataset of **20,000 loan records**. The primary objective is to assist financial institutions in assessing portfolio health, identifying high-risk borrower segments, and minimizing default rates through data-driven insights.

### 📂 Data Source
The dataset used for this project is available on Kaggle:
[**Loan Prediction Dataset 2025**](https://www.kaggle.com/datasets/nabihazahid/loan-prediction-dataset-2025)

---

## 🔍 Exploratory Data Analysis (EDA) Process

Before building the dashboard, a comprehensive EDA was conducted to understand data quality and reveal initial patterns. Here is the step-by-step process:

### 1. Data Ingestion & Quality Check
* **Loading:** Imported the `loan_dataset_20000.csv` file containing 20,000 rows and 22 columns.
* **Validation:** Verified the dataset for missing values (0 found) and duplicate records (0 found).
* **Type Casting:** Ensured correct data types for financial columns (Currency) and categorical columns (Text).

### 2. Univariate Analysis (Distribution Check)
* **Loan Characteristics:** Analyzed the distribution of `Loan Amounts` and `Interest Rates`.
* **Categorical Frequency:** Examined counts for `Loan Purpose` (Top: Debt Consolidation) and `Employment Status`.
* **Target Variable:** Calculated the baseline **Global Default Rate** (~20%) to serve as a benchmark for further analysis.

### 3. Feature Engineering
* **Grade Parsing:** Extracted the primary `Grade` (A, B, C...) from the granular `grade_subgrade` column (A1, A2...) to simplify risk grouping.
* **Binning:** Grouped continuous variables like `Age` and `Debt-to-Income Ratio` into bins (e.g., "20s", "30s", "0-5% DTI") for trend analysis.
* **Status Labeling:** Created a readable `Repayment Status` column ("Repaid" vs "Defaulted") for clear visualization legends.

### 4. Bivariate & Multivariate Analysis
* **Correlation Matrix:** Analyzed relationships between numeric variables.
    * *Finding:* Strong negative correlation between `Credit Score` and `Interest Rate`.
    * *Finding:* Weak correlation between `Annual Income` and `Loan Repayment`.
* **Risk Segmentation:** Grouped default rates by key dimensions:
    * **By Grade:** Validated that default rates increase linearly from Grade A (~5%) to Grade F (~30%).
    * **By Employment:** Identified "Unemployed" applicants as a hyper-risky segment (~80% default rate).
* **Trend Analysis:** Plotted `Interest Rate` vs. `Credit Score` to identify clusters of high-risk outliers (High Score + High Rate).

---

## 📸 Dashboard Visuals

### 1. Executive Portfolio Overview
*High-level KPIs tracking total volume, repayment rates, and lending trends.*
![Executive Dashboard Screenshot](screenshots/overview.png)
*(Replace this line with your actual screenshot path)*

### 2. Risk Analysis & Root Cause
*Deep-dive analytics using heatmaps and scatter plots to identify "toxic" risk segments.*
![Risk Dashboard Screenshot](screenshots/risk_analysis.png)
*(Replace this line with your actual screenshot path)*

---

## ⚙️ Technical Methodology (Power BI)

### 1. Data Modeling & DAX Measures
Utilized **Data Analysis Expressions (DAX)** to create complex measures for dynamic analysis.

**Key Measures Created:**
* `Total Loan Volume` = Sum of all disbursed loan amounts.
* `Default Rate` = Percentage of loans not repaid.
* `High Risk Volume` = Total volume exposed to low-grade borrowers (Grades D, E, F).
* `Risk Probability` = Advanced logic to calculate likelihood of default based on selected slicers.

```dax
// Example: Calculating High Risk Ratio
High Risk Ratio = DIVIDE([High Risk Volume], [Total Loan Volume], 0)
