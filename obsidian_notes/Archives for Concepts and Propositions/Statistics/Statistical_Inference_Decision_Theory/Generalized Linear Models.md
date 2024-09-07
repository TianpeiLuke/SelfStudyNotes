---
tags:
  - concept
  - statistics/estimation
keywords:
  - generalized_linear_model
  - statistical_estimation
  - exponential_family
topics:
  - statistics/estimation
name: Generalized Linear Models
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: Generalized Linear Models

![[Exponential Family of Distributions#^6d86a1]]

![[Exponential Family of Distributions#^056e11]]

>[!important] Definition
>Let $(X_{1} \,{,}\ldots{,}\,X_{k})$ be a sequence of $d$-dimensional random vectors,  $$X_{j} = (X_{j}^1 \,{,}\ldots{,}\, X_{j}^{d}) \in \mathbb{R}^{d}, \quad j\in [k]$$ and $\mathscr{F}_{k} = \sigma(X_{1} \,{,}\ldots{,}\,X_{k})$ be *$\sigma$-algebra generated* by $(X_{1} \,{,}\ldots{,}\,X_{k})$. 
>
>A sample $Y\in \mathbb{R}^{d}$ is from a **generalized linear model (GLM)** if 
>- the *conditional probability density* of $Y$ given $\mathscr{F}_{k}$  (with respect to a $\sigma$-finite measure $\nu$) is from an *exponential family*, i.e. 
>$$
>\mathcal{p}_{\eta}\left( y \,|\, \mathscr{F}_{k} \right) = \exp\left( \left\langle  \eta\,,\, y   \right\rangle - A(\eta) \right)\;h(y)\,, \quad y \in \mathcal{Y}. 
>$$
>where $A(\eta)$ is a log-partition function, and $\eta := (\eta^1 \,{,}\ldots{,}\,\eta^{d}) \in \mathbb{R}^{d}$ is the *natural parameter*;
>- and there *exists* some *bijective* measurable function $g: \mathcal{M} \to \mathbb{R}^{d}$ such that the *mean parameters* $\mu \in \mathcal{M}$ of the exponential family satisfies the equation
>$$
>\mu := \mathbb{E}_{ \eta }\left[\, Y \,|\,\mathcal{F}_{k}\right] = g^{-1}\left( \beta^T\,X \right)
>$$
>where $X := (X_{1} \,{,}\ldots{,}\,X_{k})^T \in \mathbb{R}^{k \times d}$ is the matrix of random vectors and $\beta \in \mathbb{R}^{k}$. 
>- Denote the *mean feasible region* $$\mathcal{M} := \left\{ \mu(\eta): \eta \in \Omega \right\}\,,\text{where } \Omega := \left\{ \eta: A(\eta) < \infty \right\}.$$ 
>- The function $g: \mathcal{M} \to \mathbb{R}$ is called the **link function**. Assume that $g$ is *third-order continuous differentiable*.
>	- If the mean parameterization $$\mu(\eta) = g^{-1}(\eta) \; \iff \; \eta = \beta^T\,X$$ then $g$ is called the **canonical** or **natural link function**.

^16bb2c


- [[Exponential Family of Distributions]]

- [[Conditional Probability]]
- [[Parametric Models]]
- [[Bijective Function and Inverse Function]]


>[!important] Definition (System Perspective)
>A **generalized linear model** on $Y := (Y^1 \,{,}\ldots{,}\,Y^{d})$ given a sequence of $k$ random vectors $(X_{1} \,{,}\ldots{,}\,X_{k})$ in $\mathbb{R}^d$ can be represented by a system of stochastic equations $$Y^{i} = g^{-1}\left( \left\langle \beta ,  X^{i}\right\rangle \right) + \xi_{i}, \quad i=1 \,{,}\ldots{,}\,d.$$ where
>- $\left\langle \beta ,  X^{i}\right\rangle$ is called the **system component.** It is assume that the $i$-component $X^i \in \mathbb{R}^{k}$ are independent random vectors for all $i$.
>- $\xi_{i}$ are i.i.d. random variables with *zero mean* and $\xi_{i}$ is *independent* from $X^i$.
>- $Y^i$ is called the **random component**. We can see that $Y^i$ are *independent* random variables.
>- $g:\mathbb{R} \to \mathbb{R}$ is called the **link function**.


## Explanation

>[!info]
>It is common to simply assume that
>$$
>\mathcal{p}_{\eta}\left( y | \mathscr{F}_{k} \right) = \exp\left( \left\langle  \eta\,,\, y   \right\rangle - A(\eta) \right)\;h(y)\,, \quad y \in \mathcal{Y}.
>$$
>i.e. $T$ is identity mapping. Thus the definition of **GLM** is that the *conditional expectation* of $Y$ given $X$ is a **generalized linear function**
>$$
>\mu = \mathbb{E}_{ \eta }\left[ Y \;|\;\mathcal{F}_{k}\right] = g^{-1}\left( \beta^T\,X \right).
>$$

>[!info]
>A GLM consists of **three components**:
>- the distribution of $Y$ given $X$ are from the **exponential family**
>- a **linear predictor** is defined as $$\beta^T\,X$$
>- a **link function** $g$ that satisfies $$\mu =  \mathbb{E}_{ \eta }\left[\, Y \;|\;\mathcal{F}_{k}\right] = g^{-1}\left( \beta^T\,X \right)$$

## Examples

>[!example]
>Consider the independent **Bernoulli random variables** $Y^{i} \in \left\{ 0, 1 \right\}$ with success parameter $p_{i} \in [0,1]$, i.e. for $i=1\,{,}\ldots{,}\,d$, the conditional p.d.f.
>$$
>\begin{align*}
>P(y^i | x_{1}^i \,{,}\ldots{,}\, x_{k}^{i}) &= (1 - p_{i})\left( \frac{p_{i}}{1- p_{i}} \right)^{y_{i}} \\
>&= (1 - p_{i})\exp \left( y_{i}\log \left( \frac{p_{i}}{1- p_{i}} \right) \right)
>\end{align*}
>$$
>where 
>- the **natural parameter**
>$$\eta_{i} = \log \left( \frac{p_{i}}{1- p_{i}}\right) = \sum_{j=1}^{k}\beta_{j}x_{j}^{i} = g(p_{i})$$
>- the **mean parameter** $$\mu_{i} = p_{i} = \frac{e^{\eta_{i}}}{e^{\eta_{i}} + 1} = g^{-1}(\eta_{i}) = \text{sigmoid}(\eta_{i}).$$ where $$\text{sigmoid}(x) = \frac{e^x}{e^x + 1} = \frac{1}{e^{-x} + 1}$$ is the **sigmoid function**.
>  
>The corresponding GLM model is called **the logistic regression** model. In particular, the logistic regression model 
>$$
>\begin{align*}
>\mathbb{E}\left[ Y^{i} \;|\;\mathcal{F}_{k}\right] &= P(Y^i = 1 | X_{1}^i \,{,}\ldots{,}\, X_{k}^{i})\\   
>&= \text{sigmoid}\left( \sum_{j=1}^{k}\beta_{j}X_{j}^{i} \right) \\
>&:= \frac{1}{e^{- \sum_{j=1}^{k}\beta_{j}X_{j}^{i}} + 1} 
>\end{align*}
>$$ 

^5ae110

- [[Bernoulli Random Variable]]
- [[Logistic Regression]]


>[!example]
>Consider the independent random variables $Y^{i} \in \left\{ 1 \,{,}\ldots{,}\,m\right\}$ from **categorical distribution**  for $i=1\,{,}\ldots{,}\,d.$
>
>Then the corresponding GLM is called the **multinomial logistic regression**
>$$
>\begin{align*}
>P(Y^i = j | x_{1}^i \,{,}\ldots{,}\, x_{k}^{i}) &= \text{soft-max}\left( \sum_{s=1}^{k}\beta_{s}^{j}x_{s}^{i},\; j\in [m] \right), \quad j\in \left\{ 1 \,{,}\ldots{,}\,m \right\}\\
>&:= \frac{\exp \left( \sum_{s=1}^{k}\beta_{s}^{j}x_{s}^{i}  \right)}{\sum_{j=1}^{m}\exp \left( \sum_{s=1}^{k}\beta_{s}^{j}x_{s}^{i}  \right)}
>\end{align*}
>$$

- [[Multinomial Random Variable]]
- Wikipedia [Multinomial_logistic_regression](https://en.wikipedia.org/wiki/Multinomial_logistic_regression)

>[!example]
>Consider the independent **Gaussian random variables** $Y^{i} \in \mathbb{R}$ with  parameter $(\mu^{i}, \sigma)$, i.e. for $i=1\,{,}\ldots{,}\,d$, the conditional p.d.f.
>$$
>\begin{align*}
>P(y^i | x_{1}^i \,{,}\ldots{,}\, x_{k}^{i}) &= \frac{1}{\sqrt{2\pi  \sigma^2 }}\exp \left( -\frac{1}{2\sigma^2}\left\lVert  y^{i} - \left( \sum_{j=1}^{k}\beta_{j}\,x_{j}^{i} \right)  \right\rVert_{2}^2  \right) 
>\end{align*}
>$$
>
>The corresponding GLM is the **linear regression model** where
>$$
>\mathbb{E}\left[ Y^{i} \;|\;\mathcal{F}_{k}\right] = \mu^{i} =  \sum_{j=1}^{k}\beta_{j}\,X_{j}^{i}
>$$

- [[Linear Regression]]
- [[Gaussian Random Variable]]
- [[Gaussian Random Vector]]

## Maximum Likelihood Estimation

>[!important]
>In GLM, the parameter of interest is the **weight** $\beta \in \mathbb{R}^{k}$ as
>- the *mean parameters* $\mu$ depend on $\beta$ only via $$\mu = g^{-1}\left( \beta^T\,X \right)$$
>- the *natural parameters* $\eta$ depend on $\beta$ via the one-to-one *forward mapping* $\nabla A: \eta \mapsto \mu$ with the mean parameter $$\mu = \nabla A(\eta) = g^{-1}\left( \beta^T\,X \right) \; \iff \; \eta = \left( \nabla A \right)^{-1}\left( g^{-1}\left( \beta^T\,X \right) \right)$$
>

- [[Log-Partition Function of Exponential Family]]
- [[Maximum Likelihood Estimation of Generalized Linear Models]]







-----------
##  Recommended Notes and References


- [[Point Estimator]]
- [[Likelihood Function]]
- [[Least Square Estimation]]


- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]
- [[Maximum Likelihood Estimation]]
- [[sigma Algebra Generated by Measurable Functions]]

- [[Local Probabilistic Models]]

- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]] pp 280
- [[Probabilistic Graphical Models by Koller]] 
