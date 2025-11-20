# Credit Card Customer Churn Analysis

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Libraries](https://img.shields.io/badge/Libraries-Pandas%20|%20Seaborn%20|%20Scipy-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## Project Overview
Customer retention is a critical metric for banking institutions. Losing existing customers (churn) is often more costly than acquiring new ones. This project analyzes a dataset of credit card customers to identify key indicators of attrition.

Using **Exploratory Data Analysis (EDA)** and **Statistical Hypothesis Testing**, this project answers:
* Who is leaving?
* Why are they leaving?
* What can the bank do to stop it?

---

## Table of Contents
- [Project Overview](#-project-overview)
- [Business Questions](#-business-questions)
- [Data Dictionary](#-data-dictionary)
- [Analysis Workflow](#-analysis-workflow)
- [Key Insights](#-key-insights)
- [Statistical Findings](#-statistical-findings)
- [Recommendations](#-recommendations)
- [Technologies Used](#-technologies-used)

---

## Business Questions
1. **Demographic Analysis:** Are there specific age groups, genders, or education levels more prone to churning?
2. **Behavioral Analysis:** Do churned customers transact differently? How do their revolving balances and utilization ratios compare to loyal customers?
3. **Statistical Validation:** Are the observed differences in behavior statistically significant?

---

## Data Dictionary
The dataset (`BankChurners.csv`) contains over 10,000 customer records. Key features analyzed include:
* **Target Variable:** `Attrition_Flag` (Existing Customer vs. Attrited Customer)
* **Demographics:** `Customer_Age`, `Gender`, `Education_Level`, `Income_Category`
* **Credit Usage:** `Total_Revolving_Bal`, `Avg_Utilization_Ratio`
* **Activity:** `Total_Trans_Ct` (Transaction Count), `Total_Trans_Amt` (Transaction Amount)

---

## Analysis Workflow

### 1. Data Preprocessing
* **Data Cleaning:** Checked for null values and data types.
* **Feature Engineering:**
    * Created `avg_amt`: Average spend per transaction.
    * Created `Age_Bins`: Segmented customers into age groups (20-29, 30-39, etc.) for better demographic analysis.
* **Segmentation:** Split data into `Attrited` and `Existing` customers for comparative analysis.

### 2. Exploratory Data Analysis (EDA)
* **Visualizations:**
    * **Stacked Bar Charts:** To visualize churn rates across categories like Gender and Income.
    * **Boxplots & Histograms:** To compare distributions of transaction counts and revolving balances.
    * **Heatmap:** To identify correlations between numerical features (e.g., Credit Limit vs. Avg Utilization).

### 3. Hypothesis Testing
Statistical tests were conducted to validate findings (Alpha = 0.05):
* **Two-Sample T-Test:** Used to compare the means of numerical variables (e.g., Revolving Balance) between attrited and existing customers.
* **Z-Test for Proportions:** Used to determine if the churn rate in specific groups (e.g., Females aged 40-49) is significantly higher than the population average.

---

## Key Insights

### 1. Behavioral Indicators of Churn
* **Low Utilization:** Churned customers have a significantly lower **Average Utilization Ratio** compared to existing customers. They are not using their credit lines.
* **Inactive Accounts:** Attrited customers tend to have a much lower **Total Revolving Balance**, often dropping to zero before leaving.
* **Transaction Drop-off:** Churned customers show a marked decrease in both **Total Transaction Count** and **Total Transaction Amount**.

### 2. Demographic Indicators
* **Gender:** The analysis identified that females, particularly in the **40-49 age group**, have a higher proportion of attrition compared to other segments.

---

## Statistical Findings
| Feature / Group | Test Used | Hypothesis | Result | Interpretation |
| :--- | :--- | :--- | :--- | :--- |
| **Revolving Balance** | T-Test (Left-tailed) | Mean(Attrited) < Mean(Existing) | **Rejected Null** | Churned customers have significantly lower balances. |
| **Transaction Count** | T-Test (Left-tailed) | Mean(Attrited) < Mean(Existing) | **Rejected Null** | Churned customers make fewer transactions. |
| **Utilization Ratio** | T-Test (Left-tailed) | Mean(Attrited) < Mean(Existing) | **Rejected Null** | Churned customers utilize less of their credit limit. |
| **Females (40-49)** | Z-Test (Right-tailed) | Prop(Group) > Prop(Population) | **Rejected Null** | This specific demographic is a high-risk group. |

---

## Strategic Recommendations

Based on the data, the following actions are recommended to reduce churn:

1.  **Re-engagement Campaigns:**
    * **Target:** Customers with low utilization (<10%) and declining transaction counts.
    * **Action:** Offer cashback incentives or points multipliers for the next 3 transactions to restart usage habits.

2.  **Demographic Targeting:**
    * **Target:** Female customers aged 40-49.
    * **Action:** Review product fit. Consider offering rewards relevant to this demographic (e.g., family-oriented benefits, shopping rewards) to increase stickiness.

3.  **Balance Transfer Offers:**
    * **Target:** Customers with $0 revolving balance.
    * **Action:** Offer low-interest balance transfers to encourage them to move debt from other cards to this one, increasing their switching costs.

4.  **Proactive Alerts:**
    * **System:** Set up automated flags when a customer's transaction frequency drops by 50% month-over-month.

---

## Technologies Used
* **Python** (Pandas, NumPy)
* **Data Visualization** (Seaborn, Matplotlib)
* **Statistics** (Scipy, Statsmodels)
