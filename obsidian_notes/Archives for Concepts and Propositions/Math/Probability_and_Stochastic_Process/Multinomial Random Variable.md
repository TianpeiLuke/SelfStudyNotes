---
tags:
  - concept
  - math/probability
  - statistics/estimation
  - statistics/inference
  - statistics/bayesian
keywords:
  - multinomial_distribution
topics:
  - probability
name: Multinomial Random Variable
date of note: 2024-09-05
---

## Concept Definition

>[!important]
>**Name**: Multinomial Random Variable

>[!important] Definition
>A $k$-dimensional *non-negative discrete* random vector $$X = (X_{1} \,{,}\ldots{,}\,X_{k}) \in \left\{  (x_{1} \,{,}\ldots{,}\,x_{k}): \sum_{i=1}^{k}x_{i} = n, \; x_{i} \in [n], i=1 \,{,}\ldots{,}\,k  \right\}$$ is from the **multinomial distribution** or **categorical distribution** with parameters $$p \in \Delta_{k} := \left\{(p_{1} \,{,}\ldots{,}\, p_{k}):\; \sum_{i=1}^{k}p_{i} = 1,\, p_{i} \ge 0\right\},$$ if the *probability mass function* is given by 
>$$
>\begin{align*}
>&p((x_{1} \,{,}\ldots{,}\,x_{k}); n, (p_{1} \,{,}\ldots{,}\, p_{k}) )\\[5pt]
>&= \mathcal{P}\left(X_{1} = x_{1} \,{,}\ldots{,}\, X_{k} = x_{k} \right) \\[5pt]
>&= \left\{ \begin{array}{ll} \dfrac{n!}{x_{1}! \ldots x_{k}!}\;p_{1}^{x_{1}} \,{\times}\ldots{\times}\,p_{k}^{x_{k}} & \text{ if } \sum_{i=1}^{k}x_{i} = n \\[5pt] 0 & \text{ otherwise} \end{array}\right.\end{align*}
>$$
>It is denoted $Multinomial(p_{1} \,{,}\ldots{,}\, p_{k}).$
>


>[!important] Definition
>The **probability mass function** for the **multinomial distribution**  can be expressed using the Gamma function
>$$
>p((x_{1} \,{,}\ldots{,}\,x_{k}); (p_{1} \,{,}\ldots{,}\, p_{k}) )
> = \frac{\Gamma\left(\sum_{i=1}^{k}x_{i} + 1\right)}{\prod_{i=1}^{k}\Gamma(x_{i} + 1)}\,\prod_{i=1}^{k}p_{i}^{x_{i}}
>$$
>for $x:= (x_{1} \,{,}\ldots{,}\,x_{k}) \in \mathbb{N}^{k}.$

### Support

>[!important] Definition
>The **support** for multinomial distribution is $$\left\{  (x_{1} \,{,}\ldots{,}\,x_{k}): \sum_{i=1}^{k}x_{i} = n, \; x_{i} \in \{ 1\,{,}\ldots{,}\,n \}, i=1 \,{,}\ldots{,}\,k  \right\}  \subset [n]^{k} / \{ n \}.$$



### Mean and Covariance

>[!important] Definition
>The **mean** of each *coordinate component* of $$X \sim Multinomial(n; p_{1} \,{,}\ldots{,}\, p_{k})$$ is $$\mathbb{E}_{ p }\left[  X_{i} \right] = n p_{i}, \quad i=1\,{,}\ldots{,}\,k$$ 
>
>The **variance** of each *coordinate component* of $X$ is $$\text{Var}(X_{i}) = n\,p_{i}(1 - p_{i}), \quad i=1\,{,}\ldots{,}\,k$$
>
>The **covariance** between *coordinate components* of $X$ is $$\text{Cov}(X_{i}, X_{j}) = -n\,p_{i}\,p_{j}, \quad i \neq j.$$

>[!important] Definition
>The vector version of mean and covariance
>- The  **mean of random vector** $$\mathbb{E}_{ p }\left[  X \right] = n p.$$
>- The **covariance matrix** of random vector $$\text{Cov}(X, X) = n\,\left(\text{diag}(p) - pp^{T}\right)$$

### Moment Generating Functions

>[!important] Definition
>The **moment generating function** of $X \sim  Multinomial(n; p_{1} \,{,}\ldots{,}\, p_{k})$ is 
>$$
>M_{X}(t) = \mathbb{E}_{ p }\left[  e^{\left\langle  t\,,\, X   \right\rangle} \right] = \left(\sum_{i=1}^{k}p_{i}e^{t_{i}}\right)^{n}.
>$$
>with $t = (t_{1} \,{,}\ldots{,}\,t_{k}).$



## Explanation

>[!info]
>Consider a set of $n$ **categorical variables** $Z_{i} \in \left\{ 1\,{,}\ldots{,}\, k \right\}$. 
>
>The **count of occurrence** of event $\left\{Z_{i} = j\right\}$ for any $j\in \left\{ 1\,{,}\ldots{,}\, k\right\}$ has **multinomial distribution**
>$$
>X^{j} = \sum_{i=1}^{n}\mathbb{1}\left\{ Z_{i} = j \right\}, \; j=1\,{,}\ldots{,}\, k
>$$
>
>Note that a **histogram** is defined as 
>$$
>X = (X^1 \,{,}\ldots{,}\,X^{k}).
>$$ 
>The **multinomial distribution** describes the **histogram**.

>[!info]
>The **one-hot encoding** representation for each categorical sample $Z_{i} \in \left\{ 1\,{,}\ldots{,}\,k \right\}$ is $$\hat{Z}_{i} := (\mathbb{1}\left\{ Z_{i} = 1 \right\} \,{,}\ldots{,}\,\mathbb{1}\left\{ Z_{i} = k \right\})$$
>
>Then the **multinomial random variable**  can be seen as the sum of $n$ i.i.d.  one-hot encoding $\hat{Z}_{i}$
>$$
>X = \sum_{i=1}^{n}\hat{Z}_{i}
>$$

## Maximum Likelihood Estimation

>[!important] 
>The **log-likelihood function** is
>$$
>\begin{align*}
>&\log p((x_{1} \,{,}\ldots{,}\,x_{k}); (p_{1} \,{,}\ldots{,}\, p_{k}) ) \\[5pt]
>&= \sum_{i=1}^{k} x_{i}\,\log(p_{i}) + \log \left(  \frac{n!}{x_{1}! \ldots x_{k}!} \right)
>\end{align*}
>$$


>[!important] 
>Let $$X_{i} = (X_{i}^{(1)} \,{,}\ldots{,}\, X_{i}^{(k)}) \sim \text{Multinomial}(n; p_{1} \,{,}\ldots{,}\, p_{k})$$ be $m$ i.i.d. Binomial random variables $i=1\,{,}\ldots{,} m,$ then the **MLE** for *parameter* $p_{j}$ is
>$$
>\hat{p}_{j} = \frac{1}{n\,m} \sum_{i=1}^{m}X_{i}^{(j)},\quad j=1\,{,}\ldots{,}\,k
>$$
>where 
>$$
>n = \sum_{j=1}^{k}X_{i}^{(j)}, \quad \forall i=1\,{,}\ldots{,}\,m
>$$
>
>Thus the probability for each class $p_{j}$ can be estimated via **weighted average**
>$$
>\hat{p}_{j} = \frac{1}{m}\sum_{i=1}^{m} \frac{X_{i}^{(j)}}{\sum_{j=1}^{k}X_{i}^{(j)}},\quad j=1\,{,}\ldots{,}\,k
>$$


## Binomial Distribution

- [[Binomial Random Variable]]

## Conjugate Prior

- [[Dirichlet Random Variable]]

## Exponential Family

>[!important] 
>We can reformulate the *Multinomial distribution* in the **natural parameterization** of *exponential family*
>$$
>\begin{align*}
> &p((x_{1} \,{,}\ldots{,}\,x_{k}); (p_{1} \,{,}\ldots{,}\, p_{k}) )\\[5pt]
> &= \exp \left( \sum_{i=1}^{k-1} x_{i}\,\log(p_{i}) + \left( n - \sum_{i=1}^{k-1}x_{i} \right)\log \left( p_{k} \right) \right)\left(  \frac{n!}{x_{1}! \ldots x_{k}!} \right) \\[8pt]
> &= \exp \left( \sum_{i=1}^{k-1} x_{i}\,\log\left( \frac{p_{i}}{p_{k}} \right) + n \log \left( p_{k} \right) \right)\left(  \frac{n!}{x_{1}! \ldots x_{k}!} \right) \\[8pt]
> &= \exp \left( \left\langle \theta(p_{1} \,{,}\ldots{,}\,p_{k-1}) \,,\, T(x_{1} \,{,}\ldots{,}\,x_{k-1}) \right\rangle - A(\theta)  \right)\;h(x_{1} \,{,}\ldots{,}\,x_{k})
>\end{align*}
>$$
>where
>$$
>\begin{align*}
>\theta:= (\theta^1 \,{,}\ldots{,}\,\theta^{k-1})  &= \left[ \log\left(\frac{p_{1}}{p_{k}}\right) \,{,}\ldots{,}\, \log \left(\frac{p_{k-1}}{p_{k}}\right) \right]^{T} \\[5pt]
>\text{ with }p_{k} = 1 - \sum_{i=1}^{k-1}p_{i}\\[5pt]
>T(x_{1} \,{,}\ldots{,}\,x_{k-1}) &= (x_{1} \,{,}\ldots{,}\,x_{k-1})^{T} \\[8pt]
>A(\theta^1 \,{,}\ldots{,}\,\theta^{k-1}) &= - n \log \left( 1 - \sum_{i=1}^{k-1}p_{i} \right) \\[5pt]
>&= n \log \left(  1 + \sum_{i=1}^{k-1} e^{\theta^{i}}\right) \\[5pt]
>&:= n \log \left(\sum_{i=1}^{k} e^{\theta^{i}}\right) \\[5pt]
>\text{ note that } \theta^{k} &= 0
>\end{align*}
>$$
>and
>$$
>h(x_{1} \,{,}\ldots{,}\,x_{k}) := \frac{n!}{x_{1}! \ldots x_{k}!}
>$$
>is the normalization factor for the *counting measure*.

^d94bb5

- [[Exponential Family of Distributions]]
- [[Counting Measure]]

>[!important]
>Note that the *mean parameters* is given by the **softmax (softargmax) function** 
>$$
>\begin{align*}
>p_{i} &= \frac{e^{\theta^{i}}}{\sum_{i=1}^{k}e^{\theta^{i}}} = \nabla_{i} A(\theta), \quad i=1\,{,}\ldots{,}\,k
>\end{align*}
>$$
>
>The *log-partition function* $A(\theta)$ is given by the **log-sum-exponential function**.
>$$
>A(\theta) := \log \left(\sum_{i=1}^{n}e^{\theta^{i}}\right)
>$$

- [[Softmax Function and Log-Sum-Exp Function]]
- [[Convex Function]]
- [[Operations that Preserve Convexity]]
- [[Generalized Linear Models]]
- [[Sigmoid Function as Activation for Deep Learning]]



-----------
##  Recommended Notes and References


- [[Sub-Gaussian Random Variable]]
- [[Dirichlet Random Variable]]


- [[Moment Generating Function]]
- [[Random Element and Random Variable]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]

- Wikipedia [Multinomial_distribution](https://en.wikipedia.org/wiki/Multinomial_distribution)
- Wikipedia [Multinomial_logistic_regression](https://en.wikipedia.org/wiki/Multinomial_logistic_regression)