---
tags:
  - concept
  - machine_learning/strategy
  - programmatic_weak_supervision
keywords:
  - programmatic_weak_supervision
  - pws
topics:
  - machine_learning_strategy
name: Snorkel for Programmatic Weak Supervision
date of note: 2025-04-24
---

## Concept Definition

>[!important]
>**Name**: Snorkel for Programmatic Weak Supervision

### Goal

>[!important] Notations
>Given 
>- an unlabeled dataset $\{x_1, \dots, x_n\}$ 
>- and a collection of $m$ *weak supervision sources* or **labeling functions (LFs)** $\lambda_1, \dots, \lambda_m$, 
>	- where each $$\lambda_j: \mathcal{X} \rightarrow \{-1, 0, +1\}$$ (with $0$ indicating *abstention*), 
>
>the *goal* is to estimate a *probabilistic label model* $$p_\theta(y_i \mid \boldsymbol{\lambda}_i)$$ that approximates the unknown true labels $y_i \in \{-1, +1\}$ using only the *outputs* $$\boldsymbol{\lambda}_i = [\lambda_1(x_i), \dots, \lambda_m(x_i)].$$
>


### Define the Label Model (Generative Model)

>[!important] Definition
> We model the **joint distribution**:
> 
> $$
> \begin{equation}
>     p_\theta(y_i, \boldsymbol{\lambda}_i) = \frac{1}{Z(\theta)} \exp\left( \sum_{j=1}^m \theta_j \cdot \phi_j(\lambda_j(x_i), y_i) \right),
> \end{equation}
> $$
> where
> - $\phi_j$ is a **feature function** capturing the *agreement* between LF $\lambda_j$ and the true label $y_i$, e.g., $$\phi_j(\lambda_j, y_i) = \mathbb{1}\{\lambda_j = y_i\}$$
> - $\theta_j$ represents the accuracy of LF $j$. 
> - $Z(\theta)$ is the *partition function* ensuring the distribution sums to one.

- [[Markov Network on Undirected Graph]]
- [[Exponential Family of Distributions]]
- [[Exponential Family as Probabilistic Graphical Model]]


### Marginal Likelihood

>[!important] Definition
>Since the true labels $y_i$ are *unobserved*, we maximize the **marginal likelihood** of the *observed* LF outputs:
>$$
> \begin{equation}
>     \mathcal{L}(\theta) = \sum_{i=1}^n \log p_\theta(\boldsymbol{\lambda}_i) = \sum_{i=1}^n \log \sum_{y_i \in \{-1, +1\}} p_\theta(\boldsymbol{\lambda}_i, y_i).
> \end{equation}
>$$ 
> The likelihood is differentiable and can be optimized via *stochastic gradient descent*.

- [[Marginalized Likelihood Function]]
- [[Evidence Lower Bound]]
- [[Evidence Lower Bound for Exponential Family]]

### Posterior Inference

>[!important] Definition
>After training, the model outputs a **probabilistic label** via:
>$$
> \begin{equation}
>     \hat{p}_\theta(y_i = y \mid \boldsymbol{\lambda}_i) = \frac{1}{Z(\boldsymbol{\lambda}_i)} \exp\left( \sum_j \theta_j \phi_j(\lambda_j(x_i), y) \right),
> \end{equation}
>$$ 
> which can be used as *soft labels* or converted to hard labels via thresholding.



### Optimization via SGD

> [!important]
> The *gradient* of the log-likelihood with respect to parameter $\theta_j$ is:
>$$ 
> \begin{equation}
>     \frac{\partial \mathcal{L}}{\partial \theta_j} = \sum_{i=1}^n \left( \mathbb{E}_{p_\theta(y_i \mid \boldsymbol{\lambda}_i)} \left[ \phi_j(\lambda_j(x_i), y_i) \right] - \mathbb{E}_{p_\theta}[\phi_j(\lambda_j(x_i), y_i)] \right).
> \end{equation}
>$$ 
>This is the difference between:
> 
> - **Empirical expected feature values** under the model
>     
> - **True expected feature values** (which we approximate via inference)
>

- [[Log-Partition Function and Score Function of Graphical Models]]
- [[Stochastic Gradient Descent Algorithm]]

>[!info]
>In practice, we implement this using **automatic differentiation** (e.g., PyTorch) and **batch updates**.


## Explanation

### Comparison with Majority Vote

|Aspect|**Dawid-Skene**|**Snorkel Label Model**|**Majority Vote**|
|---|---|---|---|
|**Type**|Probabilistic generative (EM)|Factor graph, probabilistic|Heuristic|
|**Handles Abstentions**|❌|✅|✅|
|**Models LF Accuracy**|✅|✅|❌|
|**Models LF Dependencies**|❌|✅ (optional)|❌|
|**Output**|Soft label estimates|Soft label estimates|Hard label|
|**Scalability**|Medium|High (used on millions of data points)|High|
|**Use Cases**|Crowdsourcing (multiple human labelers)|Programmatic weak supervision (LFs)|Simple baselines|



## Extensions

>[!info]
>Snorkel can be extended to model **LF correlations** through higher-order dependencies and to support multi-class settings. It provides a flexible framework for denoising weak supervision sources without requiring labeled data.







-----------
##  Recommended Notes and References


- [[Programmatic Weak Supervision or PWS]]



- [[ratnerDataProgrammingCreating2016]]
- [[ratnerSnorkelRapidTraining2020]]
- [[yuAlfredSystemPrompted2023]]
- [[zhangSurveyProgrammaticWeak2022]]