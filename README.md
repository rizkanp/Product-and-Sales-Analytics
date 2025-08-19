Sales & Customer Analytics Project (Python, ML, Power BI)

End‑to‑end analytics on product and sales data (transactions, customers, products) using Python for analysis & machine learning, and Power BI for executive‑friendly visualization.

- Project Summary
Objective. Transform raw sales and customer data into insights and actions:
* Descriptive statistics & EDA
* Inferential statistics (A/B tests, hypothesis testing)
* RFM segmentation
* Cohort analysis (acquisition & retention)
* Prescriptive (unsupervised): Customer segmentation with K‑Means on RFM
* Predictive (supervised): Customer churn prediction
* Predictive (supervised): Sales forecasting (time series)
* Prescriptive (unsupervised): Market Basket Analysis (association rules)
Deliverables.
* Reproducible Python notebooks & scripts
* ML outputs exported (CSV/Parquet) for visualization
* Interactive Power BI report consolidating all results (included)
* Executive summary with key insights and actions

- Tech Stack
* Python: pandas, numpy, scipy, scikit‑learn, xgboost/lightgbm, statsmodels, prophet, mlxtend, matplotlib/plotly
* BI: Power BI (interactive dashboards; PBIX included)
* Environment: Python ≥3.10, requirements.txt provided

- Analytical Modules (What, How, Output)
1. Descriptive Statistics & EDA
What: KPI baselining and data sanity (sales trends, AOV, order/customer growth, category mix).
How:
* Aggregations by day/week/month; seasonality & holiday overlays
* ABC/Pareto of products; price/discount distributions; geography/channel splits
* Outlier detection; missingness map; type coercions for decimal/comma issues
Output: Cleaned datasets, KPI tables, time‑series plots, product mix charts.

2 Inferential Statistics
What: Causal signals & guardrails for decisions.
How:
* A/B tests for promotion impact on AOV or conversion (Welch t‑test / Mann‑Whitney)
* Chi‑square tests for category vs return rate / churn
* Multiple testing control where applicable (FDR)
Output: Test summaries (effect size, CI, p‑values), decision notes.

3. RFM Segmentation
What: Recency‑Frequency‑Monetary features per customer as a behavioral base.
How:
* Snapshot date = max transaction date
* R = days since last purchase, F = distinct orders, M = net spend
* Transformations: log1p on F & M; standardization
Output: RFM table with normalized features; heatmaps; segment contribution to revenue.

4. Cohort Analysis
What: Acquisition cohorts and retention over time.
How:
* First‑purchase month as cohort; monthly activity grid (0,1,2, … months since)
* Retention = active customers in month t / size of cohort at t=0
Output: Retention matrix, curves by cohort, insights on lifecycle & seasonality.

5. Prescriptive (Unsupervised): Customer Segmentation (K‑Means on RFM)
What: Actionable customer groups for targeting.
How:
* Input: standardized R, F, M
* Model: K‑Means (k selected by elbow + silhouette)
* Post‑labeling: business‑friendly names (e.g., Champions, Loyal, At‑Risk, Hibernating)
Output: Cluster assignments per customer, cluster profiles, recommended actions per segment.

6. Predictive (Supervised): Customer Churn Prediction
What: Predict customers at risk of inactivity.
Label (example): No purchase within next N = 90 days → churned (1), else 0.
Features: Recency, frequency windows (30/90/180d), monetary, tenure, category diversity, discount sensitivity, channel mix, lagged behaviors.
Models: Logistic Regression (baseline), Gradient Boosting (XGBoost/LightGBM).
Evaluation: Time‑aware CV; ROC‑AUC, PR‑AUC, F1 at business threshold; calibration; SHAP explanations.
Output: Customer‑level risk scores, top drivers, CSV for CRM targeting.

7. Predictive (Supervised): Sales Forecasting
What: Forecast demand for planning (overall/by category/store).
Granularity: Daily/weekly; hierarchical reconciliation optional.
Models: Seasonal Naïve (baseline), SARIMA/SARIMAX, Prophet (promo/holiday regressors), tree‑based regressors with lag features for granular series.
Evaluation: Rolling‑origin CV; MAPE/SMAPE/MASE; prediction intervals.
Output: Forecast tables, plots, error diagnostics; CSV for Power BI.

8. Prescriptive (Unsupervised): Market Basket Analysis
What: Cross‑sell/bundle opportunities from basket co‑occurrence.
How: FP‑Growth/Apriori → association rules (support, confidence, lift).
Output: “People who bought X also buy Y” rules, attach‑rate ideas, category‑level bundles.

- Power BI Integration (Results Visualization)
Goal: Present complex analytics/ML outputs in a clear, interactive report for business users.
Pages & Highlights:
1. Overview: Net Sales, Orders, AOV, Customers, Repeat %, trend with slicers (date, channel, region).
2. Customers: RFM clusters (size, revenue share), churn‑risk distribution, top drivers (SHAP import as images).
3. Retention: Cohort heatmap & curves; drill‑through to cohort details.
4. Products: Top movers, ABC/Pareto, bundle suggestions driven by MBA rules.
5. Forecast: 3–6 month forecasts by category/store with error bands.
6. Campaigns: Segment‑specific playbook & expected lift (what‑if parameters).
Artifacts: dashboards/Sales_Customer_Analytics.pbix (+ images in dashboards/assets/).

- Evaluation & Governance
* Data checks: duplicates, nulls, outliers, decimal separators, status filters, timezones
* Model hygiene: no leakage (time‑aware splits), class imbalance handling, calibration
* Metrics reporting: confidence intervals where applicable; compare to baselines
* Privacy: PII handling (hashing/anonymization where needed)
* Reproducibility: fixed random seeds; environment pinned in requirements.txt
