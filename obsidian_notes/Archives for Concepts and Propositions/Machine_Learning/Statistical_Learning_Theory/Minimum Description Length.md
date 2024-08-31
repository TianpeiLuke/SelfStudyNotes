---
tags:
  - concept
  - machine_learning/theory
  - math/information_theory
keywords:
  - minimum_description_length
  - structural_risk_minimization
topics:
  - machine_learning_theory
name: Minimum Description Length
date of note: 2024-08-30
---

## Concept Definition

>[!important]
>**Name**: Minimum Description Length

![[Structural Risk Minimization#^e11f9f]]

![[Structural Risk Minimization#^d8d375]]

![[Structural Risk Minimization#^f6ae3e]]

![[Structural Risk Minimization#^b95023]]

### String and Description of Hypothesis

>[!important] Definition
>Let $\mathcal{H}$ be the hypothesis class we wish to describe. Fix some *finite set* $\Sigma$ of **symbols** (or "characters"), which we call the **alphabet**. For concreteness, we let $\Sigma = \{0,1\}$.  
>
>A **string** is a *finite sequence of symbols* from $\Sigma$; for example,  $\sigma = (0,1,1,1,0)$ is a string of *length* $5$. 
>- We denote by $|\sigma|$ **the length** of a string. 
>- The set of all *finite length strings* is denoted $\Sigma^{*}$. 

>[!important] Definition
>A **description language** for $\mathcal{H}$ is a function $$d: \mathcal{H} \to \Sigma^{*}$$ mapping *each member* $h$ of $\mathcal{H}$ to a *string* $d(h)$. 
>- $d(h)$ is called the **description** of $h$, and its **length** is denoted by $|h|$.

### Prefix-Free String

>[!important] Definition
>A description language is **prefix-free** if for every *distinct* $h, h'$,  $d(h)$ is *not a prefix* of $d(h')$. 
>$$
>h \neq h' \implies d(h) \neq [d(h'), \sigma'],\;  d(h') \neq [d(h), \sigma]
>$$
> 
> That is, we do not allow that any string $d(h)$ is *exactly the first* $|h|$ *symbols* of any longer string $d(h')$.

![[Kraft Inequality#^9e266e]]

- [[Kraft Inequality]]


### Generalization Error Bound for Prefix-Free Description

>[!important] Proposition
>Let $\mathcal{H}$ be a hypothesis class and let $$d: \mathcal{H} \to \set{0,1}^{*}$$ be a **prefix-free description language** for $\mathcal{H}$ over binary values $\{ 0,1 \}$. 
>
>Then, for every sample size, $m$, every confidence parameter, $\delta > 0$, and every probability distribution, $\mathcal{P}$, *with probability* greater than $1 - \delta$ over the choice of $\mathcal{D}_m \sim \mathcal{P}$ we have that,
>$$
> \begin{align}
> L_{\mathcal{P}}(h) \le L_{\mathcal{D}_{m}}(h)  + \sqrt{\frac{|h| + \log(2/\delta)}{2m}} 
> \end{align}
>$$  
>where $|h|$ is the **length of description** $d(h)$ of $h$. 

- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Hoeffding Inequality]]


### Minimum Length Description

>[!important] Definition
>With the definition of *description language* of hypothesis, the goal of a **Minimum Description Length (MDL) learning** is to find a hypothesis $h \in \mathcal{H}$ such that 
>$$
> \begin{align}
> \min_{h \in \mathcal{H}}\left\{L_{\mathcal{D}_{m}}(h) + \sqrt{\frac{|h| + \log(2/\delta)}{2m}} \right\}  
> \end{align}
>$$  
>In particular, it suggests *trading off*  *empirical risk* for *saving description length*. 

- [[Structural Risk Minimization]]
- [[Bias-Complexity Tradeoff and Overfitting]]


## Explanation

>[!info]
>Intuitively, the *description* $d(h)$ of a *function* $h\in \mathcal{H}$ is the **size (in bits) of the program** that encodes the function. 

>[!info]
>As we know from the basic Hoeffding's bound, if we commit to any hypothesis *before seeing the data*, then we are guaranteed a rather small estimation error term. 
>
> **Choosing a description language** (or, equivalently, some **weighting of hypotheses**) is a **weak form** of committing to a hypothesis. Rather than committing to a *single* hypothesis, we *spread* out our commitment among *many*. As long as it is done *independently* of the *training sample*, our generalization bound holds. Just as the *choice of a single hypothesis* to be evaluated by a sample can be **arbitrary**, so is the *choice of description language*.




## Restriction of Hypothesis Class to Data

![[Restriction of Function Class to Data#^60c89d]]

- [[Restriction of Function Class to Data]]

>[!info]
>For each $h \in \mathcal{H}$, $h_{\mathcal{D}} \in \mathcal{H}_{\mathcal{D}} \subset \set{0, 1}^{*}$ is a **description** of $h$ which is a *binary* string of *fixed length* $m$. 
>
>It is not a *prefix-free string* and is *data-dependent* which is not preferred in MDL.










-----------
##  Recommended Notes and References


- [[Structural Risk Minimization]]
- [[Tikhonov Regularization in Optimization and Learning]]
- [[Regularized Loss Minimization]]
- [[Bias-Complexity Tradeoff and Overfitting]]
- [[Occam Razor]]
- [[Upper Confidence Bound Algorithm]]

- [[Shannon Entropy]]


- [[Understanding Machine Learning by Shalev-Shwartz]] pp 63 -  65
- [[Elements of Statistical Learning by Hastie]] pp 235
- [[Elements of Information Theory by Cover]]