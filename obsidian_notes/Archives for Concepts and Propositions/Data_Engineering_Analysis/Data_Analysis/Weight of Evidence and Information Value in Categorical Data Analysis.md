---
tags:
  - concept
  - credit_risk_modeling
  - data_engineering/feature_engineering
  - binning
  - weight_of_evidence
  - information_value
  - feature_engineering
keywords:
  - weight_of_evidence
topics: 
name: 
date of note: 2025-05-28
---

## Concept Definition

>[!important]
>**Name**: 

- [[Binning as Categorical Feature Transformation]]

- **Weight of Evidence (WoE)** will help us to determine which categories should be binned together. WOE measures the strength of a bin in differentiating the Good and Bad accounts. WOE < 0 indicates that the variable bin is captures higher proportion of bad accounts.


- **Information Value (IV)** will help in determining which variables are useful for prediction in the logistic regression model. IV is the measure of overall predictive power of the variables and is very useful for feature selection.

## Explanation


- [[Risk Table for Categorical Data Analysis]]
- [[Logistic Regression]]

### IV for Variable Predictive

|Information Value|Variable Predictiveness|
|---|---|
|Less than 0.02|Not useful for prediction|
|0.02 to 0.1|Weak predictive Power|
|0.1 to 0.3|Medium predictive Power|
|0.3 to 0.5|Strong predictive Power|
|>0.5|Suspicious Predictive Power|




-----------
##  Recommended Notes and References


- [[SHapley Additive exPlanations or SHAP]]

- Resources
	- [Weight of Evidence (WOE) and Information Value (IV) Explained](https://www.listendata.com/2015/03/weight-of-evidence-woe-and-information.html)
	- [Kaggle Binning, WoE, IV and PD model](https://www.kaggle.com/code/chandrimad31/credit-risk-part-1-binning-woe-iv-pd-model)
	
- Stack Exchange
	- [Why is Binning, Weight of Evidence and Information Value so ubiquitous in the Credit Risk/Finance industry?](https://stats.stackexchange.com/questions/567489/why-is-binning-weight-of-evidence-and-information-value-so-ubiquitous-in-the-cr)