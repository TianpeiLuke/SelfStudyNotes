---
tags:
  - concept
  - deep_learning/generative_models
  - deep_learning/contrastive_learning
keywords: []
topics:
  - machine_learning_theory
  - deep_learning/generative_models
  - representation_learning
  - deep_learning/contrastive_learning
name: Density Ratio Estimation via Binary Classifiers
date of note: 2024-11-07
---

## Concept Definition

>[!important]
>**Name**: Density Ratio Estimation via Binary Classifiers

>[!important]
>Let $P, Q$ be two *probability density functions* on $(\mathcal{X}, \mathscr{F},\mu)$. The task is to measure the difference between them via **ratio of density.**
>
>Consider a *binary classification problem*, where 
>- $(X,Y) \sim p$ follows a joint distribution 
>- and the conditional distribution $$P(x) := p(x|Y=1), \quad Q(x):= p(x|Y=0)$$
>
>Then the *ratio of density* is given by the *log-odds* of a binary classifier $h$ as
>$$
>\begin{align*}
>r(x) := \frac{P(x)}{Q(x)} &:= \frac{p(x|Y=1)}{p(x|Y=0)} \\[5pt]
>&=  \frac{p(Y=1|x)\,p(x)}{p(Y=1)}  / \frac{p(Y=0|x)\,p(x)}{p(Y=0)}\\[5pt]
>&= \frac{p(Y=1|x)}{p(Y=0|x)}\; \frac{1 - \pi}{\pi}\\[5pt]
>&:= \frac{h(x)}{1- h(x)}\; \frac{1 - \pi}{\pi}
>\end{align*}
>$$
>where 
>-  $\pi$ denote the **prior** on label $1$  $$\pi := p(Y=1),$$ 
>- $h$ is the *probabilistic output* of a *binary classifier* $$h(x) := p(Y=1|x)$$ 
>
>This is called the **density ratio estimation (DRE) trick**. 
>- Note that the *marginal data distribution* $p(x)$ is *cancelled* in the ratio.

^010141

- [[Bayes Theorem]]
- [[Classification Problem]]
- [[Bayes Error and Bayes Classifier]]
- [[Logistic Regression]]

### Optimize Classifier 

>[!info]
>Define the *risk* for choosing $h$ as classifier in the density ratio estimation
>$$
>\begin{align*}
>R(h) &=  \mathbb{E}_{ X,Y }\left[ - Y\log h(X) - (1-Y) \log(1 - h(X)) \right] \\[8pt]
>&= \pi\, \mathbb{E}_{ X }\left[ - \log h(X) \right] + (1-\pi)\,  \mathbb{E}_{ X }\left[ - \log \left( 1- h(X) \right)  \right]
>\end{align*}
>$$
>In general, we can define the **risk** *associated with a loss function* $\ell: \mathcal{Y} \times \mathcal{Y} \to \mathbb{R}$ as
>$$
>R^{\ell}(h) :=  \mathbb{E}_{ X,Y }\left[ \ell(Y, h(X)) \right] 
>$$
>
>The *minimal risk* for $h\in \mathcal{F}$ is given by $$R_{\mathcal{F}}^{\ell} := \inf_{h\in \mathcal{F}}R^{\ell}(h)$$

- [[Logistic Regression]]
- [[Statistical Decision Problem]]
- [[Empirical Risk Minimization]]
- [[Estimation Error and Approximation Error]]


## Explanation


## Connection to $f$-Divergence

>[!important] Theorem (Nguyen, X., Wainwright, M. J., & Jordan, M. I. (2009))
>Let $X,Y$ be sample from joint distribution on $\mathcal{X}\times \left\{ -1,1 \right\}$ and $P,Q$ be conditional probability measures on $\mathcal{X}$ given $Y=1$ and $Y=-1$, respectively. $$P(x) = P(x | Y=1), \quad Q(x) = P(x | Y=0).$$
>
>For any **margin-based surrogate loss** function $\ell$, there *exists* an **$f$-divergence** such that $$R^{\ell}_{\mathcal{F}} = - \mathbb{D}_{f}\left( P \left\|\right. Q \right) $$ for some **lower semi-continuous convex function** $f$
>
>*Conversely*, Let $f$ be **lower semi-continuous convex function** satisfying the condition
>- the *convex-conjugate* $$\Psi(x^{*}) = f^{*}(-x^{*})$$ is decreasing, convex
>- $\Psi(\Psi(x^{*})) = x^{*}$ for all $x^{*} \in (x_{1}^{*}, x_{2}^{*})$;
>- there exists a point $u^{*} \in (x_{1}^{*}, x_{2}^{*})$, such that $\Psi(u^{*}) = u^{*}$
>
>Then there exists a **decreasing convex surrogate loss** $\ell$ such that 
>- the following equation holds between $f$ and $\ell$, $$f(u) = -\inf_{\alpha}\left\{ \ell(-\alpha) + \ell(\alpha)\,u \right\} $$	 
>- and, the corresponding **$f$-divergence** satisfies the equation $$R^{\ell}_{\mathcal{F}} = - \mathbb{D}_{f}\left( P \left\|\right. Q \right).$$

^4f1f3a

- Nguyen, X., Wainwright, M. J., & Jordan, M. I. (2009). On surrogate loss functions and f-divergences. _The Annals of Statistics_, _37_(2), 876–904. [https://doi.org/10.1214/08-AOS595](https://doi.org/10.1214/08-AOS595)
- [[f-Divergence]]
- [[Surrogate Loss Minimization]]
- [[Margin-based Loss Function]]
- [[Closed Convex Function and Closure Operation]]
- [[Divergence Function on Manifold]]

>[!quote]
>This establishes a connection between **optimal binary classification** and **distributional divergences**. 
>
>- By using binary classification, we were able to compute the *distributional divergence* **using only samples**, which is the important property needed for learning **implicit generative models**; 
>- as expressed in the guiding principles, we have turned an intractable estimation problem — how to estimate the JSD divergence, into an *optimization problem* — how to learn a classifier which can be used to **approximate that divergence**.
>  
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 887  

### Total Variation and Hinge Loss

>[!example]
>For $\mathcal{Y} := \left\{ -1, +1 \right\}$, the **total variation distance** corresponds to the **hinge loss** $$\ell(\alpha) = \max\left\{0 , 1- \alpha \right\} = [1- \alpha]_{+}$$
>- The Bayes classifier is given by $$h^{*}(x) = \text{sgn}(P(x) - Q(x))$$
>- Assume$$\pi:= P(Y=1) = 1 - \pi := P(Y = 0) = \frac{1}{2}.$$
>
>Then 
> $$
> \begin{align*}
> & 2\mathbb{E}_{ X, Y }\left[ \max\left\{0, 1- Y\,h^{*}(X) \right\}  \right]  \\[8pt] 
> &=  \mathbb{E}_{ X| Y =1 }\left[ \max\left\{0, 1- h^{*}(X) \right\}  \right] + \mathbb{E}_{ X| Y =-1 }\left[ \max\left\{0, 1+ h^{*}(X) \right\}  \right]\\[8pt]
> &=  \mathbb{E}_{ P }\left[ \max\left\{0, 1- h^{*}(X) \right\}  \right] + \mathbb{E}_{ Q }\left[ \max\left\{0, 1+ h^{*}(X) \right\}  \right]\\[8pt]
> &= 2\,\mathbb{E}_{X}\left[ \min\left\{ P(X)\, , \, Q(X) \right\}  \right] \\[8pt] 
> &= 2 - 2\lVert P - Q \rVert_{TV}   \\[8pt] 
>\end{align*}
>$$
>or
>$$\mathbb{E}_{ X, Y }\left[ \max\left\{0, 1- Y\,h^{*}(X) \right\}  \right] = 1 - \lVert P - Q \rVert_{TV} $$


^9345f7

- [[Total Variation between Measures]]
- [[Hinge Loss as Surrogate Loss Function]]
- [[Bayes Error and Bayes Classifier]]

### Hellinger Distance and Exponential Loss

>[!example]
>The **squared Hellinger distance** corresponds to the **exponential loss** $$\ell(\alpha) = \exp(-\alpha)$$
>- The Bayes classifier is given by $$h^{*}(x) = \frac{1}{2}\log \frac{P(x)}{Q(x)}$$
>- Assume $$\pi:= P(Y=1) = 1 - \pi := P(Y = 0) = \frac{1}{2}.$$
>
>Then 
> $$
>\begin{align*}
> &2\mathbb{E}_{ X, Y }\left[ \exp \left( - Y\,h^{*}(X) \right)  \right]\\[5pt]
> &=  \mathbb{E}_{P}\left[ \exp \left( - h^{*}(X) \right)  \right] +  \mathbb{E}_{Q}\left[ \exp \left( h^{*}(X) \right)  \right]\\[5pt]
> &= \int \sqrt{\frac{q(x)}{p(x)}}p(x)dx + \int \sqrt{\frac{p(x)}{q(x)}}q(x)dx\\[5pt]
> &= 2 \int_{\mathcal{X}}\sqrt{ p(x)\,q(x) }dx \\[5pt]
> &= \int (p(x) + q(x)) dx - \int \left(p(x) + q(x) - 2\sqrt{ p(x)\,q(x) }\right) dx \\[5pt]
> &= 2 - \int_{\mathcal{X}} \left( \sqrt{ p(x) } - \sqrt{ q(x) } \right)^2\,dx \\[5pt]
> &=  2 - 2H^2(P,Q) 
>\end{align*} 
>$$
>or
>$$
>\mathbb{E}_{ X, Y }\left[ \exp \left( - Y\,h^{*}(X) \right)  \right] = 1 - H^2(P,Q) 
>$$
>

^f9387f

- [[Hellinger Distance between Distributions]]
- [[Exponential Loss Minimization for AdaBoost]]

### Jensen-Shannon Divergence and Logistic Loss

>[!example]
>The **Jensen-Shannon divergence** corresponds to the **logistic loss** $$\ell(\alpha) = \log \left( 1 + \exp(-\alpha) \right)$$
>- The Bayes classifier is given by $$h^{*}(x) = \log \frac{P(x)}{Q(x)}$$
>- Assume $$\pi:= P(Y=1) = 1 - \pi := P(Y = 0) = \frac{1}{2}.$$
>
>Then 
> $$
>\begin{align*}
> &2\mathbb{E}_{ X, Y }\left[ \log \left( 1 + \exp(-Y\,h^{*}(X)) \right)  \right]  \\[5pt]
> &= \mathbb{E}_{ P }\left[ \log \left( 1 + \exp(-h^{*}(X)) \right)  \right] + \mathbb{E}_{ Q }\left[ \log \left( 1 + \exp(h^{*}(X)) \right)  \right]  \\[5pt]
> &= \int P(x)\,\log \left( \frac{P(x) + Q(x)}{P(x)} \right)\,dx + \int Q(x)\,\log \left( \frac{P(x) + Q(x)}{Q(x)} \right)\,dx \\[5pt]
> &= 2\log(2) - \mathbb{KL}\left( P \left\|\right. \frac{P + Q}{2} \right) + \mathbb{KL}\left( Q \left\|\right. \frac{P + Q}{2} \right) \\[5pt]
> &= 2\log(2) - 2\mathbb{D}_{JSD}\left( P \left\|\right. Q \right)  \\[8pt]
>\end{align*} 
>$$
>or
>$$
>\mathbb{E}_{ X, Y }\left[ \log \left( 1 + \exp(-Y\,h^{*}(X)) \right)  \right]= \log(2) - \mathbb{D}_{JSD}\left( P \left\|\right. Q\right)
>$$
>

^e7d9e0

- [[Jensen-Shannon Divergence]]
- [[Logistic Regression]]

### Triangular Discrimination Distance and Least Square Loss

>[!example]
>The **triangular discrimination** corresponds to the **least square loss** $$\ell(\alpha) = (1 - \alpha)^2$$
>- The Bayes classifier is given by $$h^{*}(x) = \frac{P(x) - Q(x)}{P(x) + Q(x)}$$
>- Assume $$\pi:= P(Y=1) = 1 - \pi := P(Y = 0) = \frac{1}{2}.$$
>
>Then 
> $$
>\begin{align*}
> &2\mathbb{E}_{ X, Y }\left[ (1 - Yh^{*}(X))^2  \right]  \\[5pt]
> &= \mathbb{E}_{ P }\left[ (1 - h^{*}(X))^2 \right] + \mathbb{E}_{ Q }\left[  (1 + h^{*}(X))^2 \right]  \\[5pt]
> &= \int P(x)\, \frac{(2Q(x))^2}{(P(x) + Q(x))^2} \,dx + \int Q(x)\,\frac{(2P(x))^2}{(P(x) + Q(x))^2}\,dx \\[5pt]
> &= \int \frac{4 P(x)\, Q(x)(P(x) + Q(x))}{(P(x) + Q(x))^2} \,dx \\[5pt]
> &= \int \frac{4 P(x)\, Q(x)}{P(x) + Q(x)} \,dx \\[5pt]
> &= \int \frac{(P(x) + Q(x))P(x)}{P(x) + Q(x)} \,dx + \int \frac{(P(x) + Q(x))Q(x)}{P(x) + Q(x)} \,dx  - \int \frac{(P(x) + Q(x))P(x) + (P(x) + Q(x))Q(x) -  4 P(x)\, Q(x)}{P(x) + Q(x)} \,dx\\[5pt]
> &= 2  - \int \frac{(P(x) + Q(x))P(x) + (P(x) + Q(x))Q(x) -  4 P(x)\, Q(x)}{P(x) + Q(x)} \,dx\\[5pt]
> &= 2-  \int \frac{\left(P(x) - Q(x)\right)^2}{P(x) + Q(x)} \,dx \\[5pt]
> &= 2 - 2\Delta(P, Q)
>\end{align*} 
>$$
>or
>$$
>\mathbb{E}_{ X, Y }\left[ (1 - Yh^{*}(X))^2  \right]  = 1 - \Delta(P, Q)
>$$
>where $$\Delta(P, Q) := \frac{1}{2}\int \frac{\left(P(x) - Q(x)\right)^2}{P(x) + Q(x)} \,dx $$

^c559d1

- [[Chi-squared Divergence]]
- [[Least Square Estimation]]
- Topsoe, F. (2000). Some inequalities for information divergence and related measures of discrimination. _IEEE Transactions on information theory_, _46_(4), 1602-1609.


## Connection with Integral Probability Metric

>[!example]
>The **integral probability metric** corresponds to the $$\ell(\alpha) = -2\alpha$$ and assume that $\pi = \frac{1}{2} = 1- \pi.$
>
>Then 
> $$
>\begin{align*}
>R^{\ell}(h) &:=  \inf_{h\in \mathcal{F}} \mathbb{E}_{ X,Y }\left[ \ell(Y\,h(X)) \right]  \\[5pt]
>&=  \inf_{h\in \mathcal{F}} \mathbb{E}_{ X,Y }\left[ -2Y\,h(X) \right]\\[5pt] 
>&= \sup_{h\in \mathcal{F}}\left\{ \pi\,  \mathbb{E}_{X|Y=1}\left[ 2h(X) \right] +  (1-\pi)\,  \mathbb{E}_{X|Y=-1}\left[ -2h(X) \right] \right\} \\[5pt] 
>&= \sup_{h\in \mathcal{F}}\left\{  \mathbb{E}_{P}\left[ h(X) \right] -   \mathbb{E}_{Q}\left[ h(X) \right] \right\} \\[5pt] 
>&:= D_{\mathcal{F}}(P, Q)
>\end{align*} 
>$$

- [[Integral Probability Metric between Probability Measures]]
- [[Maximum Mean Discrepancy between Probability Measures via RKHS]]


## Application in Contrastive Learning

- [[Noise Contrastive Estimation]]
- [[Information Noise Contrastive Estimation as Contrastive Learning]]





-----------
##  Recommended Notes and References


- [[Principle of Learning by Comparison for Implicit Generative Models]]


- [[Convex Function]]
- [[Log-Partition Function of Exponential Family]]
- [[Exponential Family of Distributions]]
- [[Gibbs Distribution]]
- [[Gibbs Measure and Energy-based Model]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 61 - 62


