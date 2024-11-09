---
tags:
  - concept
  - machine_learning/models
  - machine_learning/algorithms
  - deep_learning/algorithms
  - deep_learning/models
keywords:
  - logistic_regression
topics:
  - machine_learning_models
  - deep_learning/models
name: Logistic Regression
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Logistic Regression

>[!important] Definition
>Consider the task of *binary classification* given sample $(X,Y) \sim  \mathcal{P}$ where $X = (X^1 \,{,}\ldots{,}\, X^{d}) \in \mathbb{R}^{d}$ and $Y\in \{ 0, 1 \}$. 
>
>The **logistic regression** assumes that the  *logarithmic of likelihood ratio* (**log-odds** or **logit transformation**) is *linear*. That is, 
>$$
> \log \left(\frac{\mathcal{P}(Y=1 \;|\;X = x)}{\mathcal{P}(Y= 0 \;|\;X = x)}\right) = \sum_{i=1}^{d}\beta_{i}\,x^{i} + \beta_{0} = \left\langle  \beta\,,\, \tilde{x} \right\rangle
>$$ 
>where $\tilde{x} = (x, 1)$ and $\beta = (\beta_{1} \,{,}\ldots{,}\,\beta_{d}, \beta_{0} ).$
>
>Note that $\mathcal{P}(Y=1 \;|\;X = x) = 1 - \mathcal{P}(Y=0 \;|\;X = x)$

^608e86

- [[Generalized Linear Models]]
- [[Linear Regression]]

>[!important] Definition
>In **logistic regression**, The conditional distribution of label $Y$ given $X$ is 
>$$
>\begin{align*}
>p_{1}(x;\beta) := \mathcal{P}(Y=1 | X=x; \beta) &= \frac{\exp \left(\sum_{i=1}^{d}\beta_{i}\,x^{i} + \beta_{0}\right)}{1+ \exp \left(\sum_{i=1}^{d}\beta_{i}\,x^{i} + \beta_{0}\right)} \\[5pt]
>&= \frac{1}{1 + \exp \left(-\sum_{i=1}^{d}\beta_{i}\,x^{i} - \beta_{0}\right)} \\[5pt]
>&= \sigma \left(\sum_{i=1}^{d}\beta_{i}\,x^{i} + \beta_{0}\right)
\end{align*}
>$$
>where 
>$$
>\sigma(x) = \frac{1}{1+ \exp(-x)}
>$$

^d3f593

- [[Sigmoid Function as Activation for Deep Learning]]
### Maximum Likelihood Estimation

>[!important] Definition
>Given a set of $m$ i.i.d. samples $(x_{i}, y_{i}) \in \mathcal{X}\times \{ 0,1 \}$, the estimated parameter $\hat{\beta}$  is obtained via the **maximum likelihood estimation**. 
>
>That is, we solve the following *convex optimization problem* 
>$$
>\begin{align*}
>\min_{\beta}\;& -\sum_{s=1}^{m}\left\{ y_{s} \log p_{1}(x_{s}; \beta) + (1- y_{s})\;\log\left(1 - p_{1}(x_{s}; \beta)\right) \right\}  \\[5pt]
>&= -\sum_{s=1}^{m}\left\{ y_{s}\left\langle  \beta\,,\,\tilde{x}_{s}    \right\rangle - \log \left(1+ \exp \left( y_{s} \left\langle  \beta\,,\, \tilde{x}_{s} \right\rangle \right)\right) \right\}\\[5pt]
>&= \sum_{s=1}^{m} \log \left(1 + \exp \left( - \,y_{s} \left\langle  \beta\,,\, \tilde{x}_{s} \right\rangle \right) \right)
\end{align*}
>$$
>The negative log-likelihood function above is called the **binomial deviance** or **binary cross-entropy** 
>$$
>\begin{align*}
>\ell(f, y) &:=  y\,\sigma(f(x)) + (1-y)\,(1- \sigma(f(x))) \\[5pt]
>&= \log \left(1+ \exp \left(-\,y\,f\right)\right).
>\end{align*}
>$$

^fef36f

- [[Maximum Likelihood Estimation]]


>[!important] Properties for Logistic Function
>Let 
>$$
>\sigma(x) = \frac{1}{1+ \exp(-x)}
>$$
>be **logistic function**.
>
>- The first order derivative is 
>$$
> \frac{d}{dx}\sigma(x) = \sigma(x)\,\left(1 - \sigma(x)\right) 
>$$

^373e80

### Solution of MLE via Newton's Method

- [[Logistic Regression Solution via Iterative Reweighted Least Square]]

## Explanation

>[!info]
>The log-likelihood function of logistic regression is related to the **KL-divergence** for **Bernoulli random variables**
>$$
>\begin{align*}
>\mathbb{KL}\left( \mathcal{P}_{y} \left\|\right. \mathcal{P}_{lr} \right) &= y \log \left(\frac{y}{p_{1}(x; \beta)}\right) + (1- y) \log \left(\frac{1 - y}{1- p_{1}(x; \beta)}\right)
\end{align*}
>$$
>where 
>$$
>\mathcal{P}_{y} = (y, 1 - y), \quad \mathcal{P}_{lr} = (p_{1}(x; \beta), 1- p_{1}(x;\beta))
>$$

- [[Kullback-Leibler Divergence]]

>[!info]
>The **logistic function** $$\sigma(x) = \frac{1}{1+ \exp(-x)}$$  is used as **activation function** in *neural network*

- [[Activation Functions for Deep Learning]]
- [[Restricted Boltzmann Machine]]



## Generalized Linear Model

![[Generalized Linear Models#^5ae110]]

- [[Generalized Linear Models]]

## Surrogate Loss Minimization

- [[Surrogate Loss Minimization]]
- [[Empirical Risk Minimization]]

## Jensen-Shannon Divergence and Density Ratio

![[Density Ratio Estimation via Binary Classifiers#^e7d9e0]]

- [[Jensen-Shannon Divergence]]
- [[Density Ratio Estimation via Binary Classifiers]]


## One-Layer Neural Network

- [[Artificial Neural Network and Deep Learning]]


-----------
##  Recommended Notes and References


- [[Regression Problem]]
- [[Linear Regression]]
- [[Maximum Likelihood Estimation]]
- [[Generalized Linear Models]]
- [[Exponential Family of Distributions]]
- [[Likelihood Ratio Test]]


- [[Surrogate Loss Minimization]]
- [[Artificial Neural Network and Deep Learning]]
- [[Perceptron Algorithm]]
- [[Multi-Layer Perceptron and Feed-Forward Network]]

- [[AdaBoost Algorithm]]




- [[Boosting Foundations and Algorithms by Schapire]]
- [[Elements of Statistical Learning by Hastie]] pp 119 - 122
- [[Probabilistic Graphical Models by Koller]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]]
- [[Deep Learning Foundations and Concepts by Bishop]]
- [[All of Statistics A Concise Course by Wasserman]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Foundations of Machine Learning by Mohri]]
- [[Convex Optimization by Boyd]] pp 354 - 355