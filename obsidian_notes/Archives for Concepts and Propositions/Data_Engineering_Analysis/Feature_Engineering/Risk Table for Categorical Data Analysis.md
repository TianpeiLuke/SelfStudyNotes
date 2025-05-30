---
tags:
  - concept
  - credit_risk_modeling
  - data_engineering/feature_engineering
  - feature_engineering
  - machine_learning/feature_engineering
  - binning
  - target_encoding
  - categorical_data_analysis
keywords:
  - risk_table
topics:
  - feature_engineering
  - credit_risk_analysis
name: Risk Table for Categorical Data Analysis
date of note: 2025-05-28
---

## Concept Definition

>[!important]
>**Name**: Risk Table for Categorical Data Analysis

>[!important]
>A **risk table** maps each category (or combination of categories) of a categorical variable to the *observed outcome rate*.
>- *Risk table* is often interpreted as a *risk*, *probability*, or *proportion* of a particular class.
>- This "table" is typically pre-computed based on historical data and the relationship between the variable's values/bins and a target variable (e.g., default status, fraud occurrence).


- [[Binning as Feature Categorization]]
- [[Weight of Evidence or WoE in Categorical Data Analysis]]

### Formula for Risk Table Mapping with Bayesian Smoothing 

>[!important] Definition
>Assume $$C(f_{1}, y)$$ be the count of co-occurence of feature-label pair $(f_{1}, y)$ where
>-  $y\in \mathcal{Y} := \left\{ 0,1 \right\}$
>- and $N$ is the count of all samples,
>- and additional parameters
>	- *smooth factor* $\alpha$
>	- *default risk* $p_{1} \in (0,1]$, which is the *marginal label probability* $$p_{1} = \frac{C(1)}{\sum_{y\in \mathcal{Y}}C(y)}$$ where $C(y)$ is the count of samples with label $y$
>
>Formula for **risk-table mapping** with **Bayesian smoothing** is given by the following $$r(f_{1}) :=  \frac{C(f_{1}, 1) + \alpha \cdot  N \cdot p_{1}}{\sum_{y\in \mathcal{Y}}C(f_{1}, y) + \alpha \cdot N}$$ 
>- when $C(f_{1}, 1) \to \infty$, it converges to histogram $$r(f_{1}) \to \hat{p}(1| f_{1})  = \frac{C(f_{1}, 1)}{\sum_{y\in \mathcal{Y}}C(f_{1}, y)}$$
>- when  $\sum_{y\in \mathcal{Y}}C(f_{1}, y) \to 0$, it converges to default risk $$r(f_{1}) \to \frac{\alpha \cdot p_{1}}{\alpha} = p_{1}$$


### Input and Output

>[!info]
> - **Input Data:**
>     
>     - Can be *raw continuous* or *categorical* variables.
>     - Very often applied to **binned variables**. 
>     - Binning is frequently a preprocessing step before WoE or scorecard point assignment.
>         
> - **Output:**
>     
>     - A numerical variable where the original values/categories are replaced by a **risk-related measure** (e.g., WoE value, points, a risk indicator).
>     - This transformed variable is often directly usable in linear models or for risk calculation.

- [[Binning as Feature Categorization]]
- [[Weight of Evidence or WoE in Categorical Data Analysis]]


## Explanation

>[!info]
>**Risk table mapping** involves replacing the original values (or binned categories) of a variable with a new value that directly represents its associated risk or a measure related to risk.

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
> - **Quantify risk contribution:** 
> 	- Directly embeds the risk information associated with each attribute/bin into the feature itself.
> - **Linearize relationships:** 
> 	- WoE transformation, for example, aims to create a linear relationship between the transformed feature and the log-odds of the target variable, making it suitable for logistic regression.
>     
> - **Standardize scales:** 
> 	- All variables (after WoE transformation, for instance) are on the same log-odds scale.
>     
> - **Handle categorical variables:** 
> 	- WoE can transform categorical variables into meaningful numerical values for modeling.
>     
> - **Model interpretability:** 
> 	- Scorecards are highly interpretable. WoE values also provide insights into how each bin relates to risk.
> - **Building risk scorecards:** 
> 	- A primary application in credit risk.


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

- [[Processor Risk Table Mapping]]
- [[Binning]]

## Compare with Weight of Evidence and Information Value

| Metric         | Output Type | Measures                               | Used For                   |
| -------------- | ----------- | -------------------------------------- | -------------------------- |
| **Risk Table** | Proportion  | **Outcome rate** per category          | EDA, encoding, audit       |
| **WoE**        | Log-odds    | **Signal strength (SNR)** per category | Logistic modeling          |
| **IV**         | Scalar      | **Predictive power** of variable       | Feature selection, ranking |

- [[Weight of Evidence or WoE in Categorical Data Analysis]]
- [[Information Value for Predictive Power of Categorical Data]]

>[!info]
>Note that **WoE** can be used as a risk table.




-----------
##  Recommended Notes and References

