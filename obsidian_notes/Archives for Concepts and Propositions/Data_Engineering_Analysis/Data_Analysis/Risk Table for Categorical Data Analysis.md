---
tags:
  - concept
  - credit_risk_modeling
  - data_engineering/feature_engineering
  - feature_engineering
  - machine_learning/feature_engineering
  - binning
  - target_encoding
keywords: 
topics: 
name: 
date of note: 2025-05-28
---

## Concept Definition

>[!important]
>**Name**: 

>[!important]
>A **risk table** maps each category (or combination of categories) of a categorical variable to the *observed outcome rate*.
>- *Risk table* is often interpreted as a *risk*, *probability*, or *proportion* of a particular class.

- [[Binning as Categorical Feature Transformation]]
- [[Weight of Evidence in Categorical Data Analysis]]

## Explanation



### Use Cases

>[!info]
> - **EDA (Exploratory Data Analysis)**:
>     - Helps understand association between categories and outcomes.
>         
> - **Modeling**:
>     - Used for **target encoding**, where categories are replaced by their risk (target mean).
>     - Helps detect **high-risk groups** in fraud, medical diagnosis, marketing, etc.
>         
> - **Fairness Audits**:
>     - Evaluates if certain groups experience higher negative outcomes.

### Additional Concerns

>[!info]
>- Risk tables should be computed **only on training data** to avoid data leakage.
>     
> - Small groups can have unstable risk estimates — **smoothing** (e.g., **Bayesian target encoding**) is often needed.
>     
> - For *multiclass outcomes*, risk tables can be extended to show per-class proportions.


## Code

- [[Binning and Pivot Table - Count Frequency of Pairs of Features]]
- [[Risk Value Mapping of Categorical Field]]

- [[Processors Risk Binning]]
- [[Binning]]

## Compare with Weight of Evidence and Information Value

|Metric|Output Type|Measures|Used For|
|---|---|---|---|
|**Risk Table**|Proportion|Outcome rate per category|EDA, encoding, audit|
|**WoE**|Log-odds|Signal strength per category|Logistic modeling|
|**IV**|Scalar|Predictive power of variable|Feature selection, ranking|

- [[Weight of Evidence in Categorical Data Analysis]]
- [[Information Value for Predictive Power of Categorical Data]]



-----------
##  Recommended Notes and References

