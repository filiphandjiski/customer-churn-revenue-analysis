# Customer Churn Prediction & Revenue-at-Risk Analysis

Predicting which telecom customers are likely to leave, estimating how much revenue is at risk, and recommending how to keep them.

**Tools:** Python, pandas, scikit-learn, matplotlib, Google Colab

## Business Problem
A telecom company is losing customers. This project answers three questions:
1. Which customers are most likely to leave, and why?
2. How much yearly revenue is at risk?
3. What should the company do to keep them?

## Data
[IBM Telco Customer Churn dataset](https://github.com/IBM/telco-customer-churn-on-icp4d): 7,043 customers and 21 columns (contract type, tenure, monthly charges, services, and whether they left).

## Approach
This project uses all three levels of analytics:

| Type | Question | What I did |
|---|---|---|
| **Descriptive** | What happened? | Cleaned the data (fixed 11 hidden blank TotalCharges values) and compared churn rates by contract, tenure, charges, services and payment method |
| **Predictive** | What will happen? | Built a logistic regression model (80/20 train-test split) to estimate each customer's probability of leaving |
| **Prescriptive** | What should we do? | Converted churn risk into annual revenue at risk and modeled a contract-conversion scenario to recommend retention actions |
## Key Findings
- **26.5%** of customers churned
- Month-to-month customers churn at **42.7%**, compared with **2.8%** for two-year contracts
- Electronic check payers (**45.3%**), fiber optic customers (**41.9%**) and customers without tech support (**41.6%**) churn the most
- Customers who left paid more per month on average (**\$74.4 vs. \$61.3**)

## Model Results
| Metric | Result |
|---|---|
| Accuracy | **79.6%** (vs. 73.5% baseline of guessing "no churn") |
| AUC | **0.837** |
| Churners caught in test set | 197 of 374 (53%) |

Strongest churn drivers: two-year and one-year contracts **reduce** churn, while fiber optic internet, electronic check payments and paperless billing **increase** it.

## Revenue Impact
- **533** current customers have a 50%+ chance of leaving, representing **\$525,267** in annual revenue
- Probability-weighted expected loss: **\$827,438 per year**
- **99.6%** of high-risk revenue comes from month-to-month customers

## Recommendations
1. **Offer annual contracts to month-to-month customers.** Converting 20% of high-risk customers could save **~\$32,890/year**.
2. **Contact high-risk customers monthly** using the model's risk scores.
3. **Promote autopay and tech support**, which are linked to much lower churn.

## Limitations
The 20% conversion rate is an assumption, discount costs aren't included, the data comes from one company, and the model shows links rather than causes.

## Files
- `Customer_Churn_Revenue_Analysis.ipynb`: the full analysis notebook
