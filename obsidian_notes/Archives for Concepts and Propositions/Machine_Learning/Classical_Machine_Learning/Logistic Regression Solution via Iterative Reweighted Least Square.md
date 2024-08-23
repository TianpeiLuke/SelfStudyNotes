---
tags:
  - concept
  - machine_learning/models
  - machine_learning/algorithms
  - deep_learning/algorithms
  - deep_learning/models
keywords:
  - logistic_regression
  - iterative_reweighed_least_square
topics:
  - machine_learning_models
  - deep_learning/models
name: Logistic Regression Solution via Iterative Reweighted Least Square
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Logistic Regression Solution via Iterative Reweighted Least Square


![[Logistic Regression#^d3f593]]

- [[Logistic Regression]]
- [[Generalized Linear Models]]

### Maximum Likelihood Estimation

![[Logistic Regression#^fef36f]]

- [[Logistic Regression]]
- [[Maximum Likelihood Estimation]]

### Solution of MLE via Newton's Method

>[!important]
>The **gradient** of *log-likelihood function* (**score function**) is
>$$
>\begin{align*}
>\nabla \ell(\beta) &= \sum_{s=1}^{m}x_{s}\left(y_{s} - p_{1}(x_{s}; \beta)\right)\\[5pt]
>&= X^{T}\,\left(y - p\right)
\end{align*}
>$$
>where 
>- $y := (y_{1} \,{,}\ldots{,}\,y_{m})\in \mathbb{R}^{m}$,  
>- $$X = \left[ \begin{array}{ccccc}x_{1}^{1}& X_{1}^{2}& \ldots & x_{1}^{d} & 1\\ x_{2}^{1}& x_{2}^{2}& \ldots & x_{2}^{d}& 1 \\ \ldots & \ldots & \ldots & \ldots & \ldots \\ x_{m}^{1}& x_{m}^{2}& \ldots & x_{m}^{d} & 1  \end{array} \right]\in \mathbb{R}^{m\times (d+1)},$$ 
>- $p := (p_{1}(x_{1}; \beta) \,{,}\ldots{,}\, p_{1}(x_{m}; \beta))$


>[!important]
>The **Hessian** of log-likelihood function is
>$$
>\begin{align}
>\nabla^2 \; \ell(\beta) &= -\sum_{s=1}^{m}(x_{s}\,x_{s}^{T})\,\left[ p_{1}(x_{s}; \beta)\, (1 - p_{1}(x_{s}; \beta)) \right] \\[5pt] 
>&= - X^{T}\,W\,X
\end{align}
>$$
>where the $W$ is a *diagonal matrix* $$W_{s,s} = \left[ p_{1}(x_{s}; \beta)\, (1 - p_{1}(x_{s}; \beta)) \right].$$

![[Logistic Regression#^373e80]]

>[!info]
>We can find the solution using **Newton's method**
>$$
>\begin{align*}
>\beta_{t+1} &= \beta_{t} - \left[\nabla^2 \ell(\beta_{t}) \right]^{-1}\;\nabla \ell(\beta_{t}) \\[5pt]
>&= \beta_{t} + \left(X^{T}\,W_{t}\,X\right)^{-1}X^{T}\left(y - p_{t}\right) \\[5pt]
>&= \left(X^{T}\,W_{t}\,X\right)^{-1}X^{T}W_{t}\,z_{t} 
\end{align*}
>$$
>where
>$$
>z_{t} = X\,\beta_{t} + W_{t}^{-1}\,\left(y - p_{t}\right)
>$$

- [[Newton Method]]

![[Least Square Estimation Solution and Geometric Interpretation#^17b91f]]

- [[Least Square Estimation Solution and Geometric Interpretation]]

>[!important]
>The Netwon step for logistic regression can be represented as a **weighted least square step**.
>
>In particular, the **iterative reweighted least square (IRLS)** for solving the logistic regression is described as below
>- *Require*: design matrix $X \in \mathbb{R}^{m\times (d+1)}$ whose row is $x_{s}, s=1\,{,}\ldots{,}\,m$
>- *Require*: response vector $y\in \{ 0,1 \}^{m}$
>- *Initialize* weight $\beta_{1} = 0$  
>- For $t=1 \,{,}\ldots{,}\,T$
>	- Collect **logistic function** output  $$p_{t}[s] = \sigma \left(\left\langle  \beta_{t}\,,\,x_{s}\right\rangle\right), \quad s=1  \,{,}\ldots{,}\,m$$
>	- Compute the **gradient** of *logistic function* as diagonal term of $W_{t}$ $$W_{t}[s,s] = p_{t}(s)\,(1- p_{t}(s)), \; s=1\,{,}\ldots{,}\,m.$$
>	- Adjust the **response** with a **reweighted error term**  $$z_{t} = X\,\beta_{t} + W_{t}^{-1}\,(y - p_{t})$$
>	- Solve the **weighted least square estimation problem** $$\begin{align*}\beta_{t+1} &= \arg\min_{\beta}\; \lVert z_{t} - X\beta \rVert_{W_{t}}^2 \\[5pt] &:=  \arg\min_{\beta}\; (z_{t}- X\beta)^{T\,}W_{t}\left(z_{t} - X\beta\right)\end{align*}$$

- [[Least Square Estimation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]


## Explanation

>[!info]
>The **parallel update** of
>$$z_{t+1} = X\,\beta_{t+1} + W_{t+1}^{-1}\,(y - p_{t+1})$$ for each sample coordinate $s=1\,{,}\ldots{,}\,m$
>$$
>z_{s}^{t+1} = \sum_{i=1}^{d}\beta_{i}^{t+1} x_{s}^{i} + \frac{y_{s} -p(x_{s}; \beta_{t+1}) }{p(x_{s}; \beta_{t+1})\;(1 - p(x_{s}; \beta_{t+1})) }
>$$



-----------
##  Recommended Notes and References


- [[Regression Problem]]
- [[Linear Regression]]
- [[Maximum Likelihood Estimation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]
- [[Least Square Estimation with QR Factorization]]



- [[Boosting Foundations and Algorithms by Schapire]]
- [[Elements of Statistical Learning by Hastie]] pp 121
- [[Probabilistic Graphical Models by Koller]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]]
- [[Deep Learning Foundations and Concepts by Bishop]]
- [[All of Statistics A Concise Course by Wasserman]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Foundations of Machine Learning by Mohri]]