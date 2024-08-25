---
tags:
  - concept
  - machine_learning/theory
  - machine_learning/models
  - deep_learning/discriminative_models
keywords:
  - evidence_lower_bound
topics:
  - machine_learning_models
  - machine_learning_theory
name: Evidence Lower Bound
date of note: 2024-07-05
---

## Concept Definition

>[!important]
>**Name**: Evidence Lower Bound

>[!important] Definition
>Let $(X, Z) \in \mathcal{X} \times \mathcal{Z}$ be a sample pair from *a parametric family* $\{p_{\theta}(x, z), \theta\in \Theta\}$.  The *marginal p.d.f.* of $Z$ is denoted as $p(z)$, and the *conditional p.d.f.* of $X$ given $Z$ is $p_{\theta}(x | z)$. The **complete likelihood function** $\ell(\theta; x, z)$ follows the equation
>$$
>\ell(\theta; x, z) := \log p_{\theta}(x, z)  = \log p_{\theta}(x | z) + \log p(z), \quad \forall x \in \mathcal{X}, z \in \mathcal{Z}.
>$$
>
>
>For an *arbitrary density function* $q(z)$ of $Z$, the **evidence lower bound (ELBO)** or the **variational lower bound**, is given by
>$$
>\begin{align*}
>\mathcal{L}(q, \theta; x) &:= \mathbb{E}_{ q }\left[ \log \left(\frac{p_{\theta}(x, Z)}{q(Z)}\right) \right] \\[5pt]
>&=  \mathbb{E}_{q }\left[ \log \left(\frac{p_{\theta}(x | Z)\,p(Z)}{q(Z)}\right) \right] \\[5pt]
>&= \int_{\mathcal{Z}}\;q(z)\log \left(\frac{p_{\theta}(x | z)\,p(z)}{q(z)}\right)d\nu_{Z},
\end{align*}
>$$
>where $\nu_{Z}$ is the common dominating base measure on $\mathcal{Z}$ for both $q(z)$ and $p(z)$.

^c74005

- [[Parametric Models]]
- [[Probability Density Function of Random Variable]]
- [[Conditional Probability]]

>[!info]
>Note that
>$$
>\begin{align*}
>\mathcal{L}(q, \theta; x) &:= \mathbb{E}_{ q }\left[ \log \left(\frac{p_{\theta}(x, Z)}{q(Z)}\right) \right] \\[10pt]
>&=  \mathbb{E}_{ q }\left[\log p_{\theta}(x, Z)\right] + H(q)
\end{align*}
>$$
>That is, it is represented as two parts
>- **expected (complete) log-likelihood function** with respect to $q\in \mathscr{P}_{Z}$ $$\mathbb{E}_{ q }\left[\log p_{\theta}(x, Z)\right]$$
>- **entropy of variational density** $q$, $$ H(q) := \mathbb{E}_{ q }\left[- \log q(Z)\right] $$
>
>In [[Probabilistic Graphical Models by Koller]] pp 385, 881, the ELBO is called an **energy functional**.

- [[Cross-Entropy Loss Function]]

## ELBO as Lower Bound of Marginalized Likelihood

>[!important] Definition
>The **marginal log-likelihood** or **incomplete log-likelihood** of $\theta$ for $X$ is given by
>$$
> \ell(\theta; x) :=  \log p_{\theta}(x) = \log \int_{\mathcal{Z}}p_{\theta}(x | z)\,p(z)\,d\nu_{Z} = \log \int_{\mathcal{Z}}p_{\theta}(x , z)\,d\nu_{Z} .
>$$
>
>The, **log-marginal likelihood** satisfies the equation below
>$$
>\begin{align*}
>  \log p_{\theta}(x) &= \log \int_{\mathcal{Z}}p_{\theta}(x | z)\,p(z)\,d\nu_{Z}\\
> &= \log \int_{\mathcal{Z}}\frac{p_{\theta}(x | z)\,p(z)}{q(z)}\,q(z)\,d\nu_{Z} \\
> &\ge \int_{\mathcal{Z}}\log \left(\frac{p_{\theta}(x | z)\,p(z)}{q(z)}\right) \,q(z)\,d\nu_{Z} \\
> &:= \mathcal{L}(\theta; x)
>\end{align*}
>$$
>The last inequality is due to the *Jensen's inequality* and the fact that $\log(x)$ is a *concave function*.
>
>Since the *marginal likelihood function* $p_{\theta}(x)$ is called the **evidence** *of* $x$, its lower bound is called the  **evidence lower bound (ELBO)**.

- [[Likelihood Function]]
- [[Jensen Inequality]]
- [[Marginalized Likelihood Function]]

## ELBO via KL-Divergence between Posterior Density on Latent Variable

>[!important] Definition
>Let $p(z | x, \theta)$ be the *posterior density* of $Z$ given $x$ with respect to $\nu_{Z}$ . By *Bayes theorem*, 
>$$
> p(z | x, \theta) = \frac{p_{\theta}(x, z)}{p_{\theta}(x)} = \frac{p_{\theta}(x | z)\,p(z)}{p_{\theta}(x)} 
>$$
>Then the **KL-divergence** *from* $p(z | x, \theta)$ to an *arbitrary density* $q(z)$ of $Z$ satisfies the equation below
>$$
>\begin{align*}
>\mathbb{KL}\left( q(z) \left\|\right. p(z | x, \theta) \right) &= \int_{\mathcal{Z}}\,\log \left(\frac{q(z)}{p(z | x, \theta)}\right)\,q(z)\,d\nu_{Z} \\
>&= \int_{\mathcal{Z}}\,\log \left(q(z) \frac{p_{\theta}(x)}{p_{\theta}(x | z)\,p(z)}\right)\,q(z)\,d\nu_{Z} \\
>&=  \int_{\mathcal{Z}}\left[ \log p_{\theta}(x) \right]  \,q(z)\,  d\nu_{Z} + \int_{\mathcal{Z}}\,\log \left( \frac{q(z)}{p_{\theta}(x | z)\,p(z)}\right)\,q(z)\,d\nu_{Z} \\[5pt]
>&= \log p_{\theta}(x) - \mathcal{L}(q, \theta; x)
\end{align*}
>$$
>In other word, the  **evidence lower bound (ELBO)** can be represented as the marginal likelihood function (**evidence** of $x$) **subtract** the **KL divergence** from *posterior density*  $p(z|x, \theta)$ to a *variational density* $q(z).$
>$$
>\mathcal{L}(q, \theta; x) = \log p_{\theta}(x) - \mathbb{KL}\left( q \left\|\right. p(\cdot | x, \theta) \right).
>$$
>Similarly, we can represent the **marginal likelihood function** using ELBO and KL-divergence
>$$
>\log p_{\theta}(x) = \mathcal{L}(q, \theta; x) + \mathbb{KL}\left( q \left\|\right. p(\cdot | x, \theta) \right).
>$$

^5bbff1

- [[Bayes Theorem]]
- [[Kullback-Leibler Divergence]]

>[!important] 
>We can also derive another **useful equation for ELBO**
>$$
>\begin{align*}
>\mathcal{L}(q, \theta; x) &=  \mathbb{E}_{q }\left[ \log \left(\frac{p_{\theta}(x | Z)\,p(Z)}{q(Z)}\right) \right] \\[5pt]
>&= \mathbb{E}_{ q }\left[  \log p_{\theta}(x | Z) \right] - \mathbb{E}_{q }\left[ \log \left(\frac{q(Z)}{p(Z)}\right) \right] \\[5pt]
>&=  \mathbb{E}_{ q }\left[  \log p_{\theta}(x | Z) \right] - \mathbb{KL}\left( q(z) \left\|\right. p(z)  \right)
>\end{align*}
>$$




>[!info]
>Define $$Q(\theta; \hat{\theta}) := \mathbb{E}_{ p }\left[  \log p_{\theta}(x, z) \;|\; x, \hat{\theta} \right]$$ where the expectation is with respect to  $p(z| x, \hat{\theta} )$. 
>
>We see that the ELBO when $q = p(\cdot | x, \hat{\theta} )$ is 
>$$
>\begin{align*}
>\mathcal{L}(p(\cdot | x, \hat{\theta} ), \theta; x) &= \int_{\mathcal{Z}}\log \left(\frac{p_{\theta}(x | z)\,p(z)}{p(z| x, \hat{\theta} )}\right)\,p(z| x, \hat{\theta} )\,d\nu_{Z}\\
>&= Q(\theta; \hat{\theta}) + H(p(z| x, \hat{\theta} )) \\
>&= Q(\theta; \hat{\theta}) + \text{const.}
>\end{align*}
>$$
>where $H(p) = - \int p\log p\, d\nu$ is the *Shannon entropy*.
>
>Also from the equation for *ELBO* for any $q$, we can obtain
>$$
>\mathcal{L}(p(\cdot | x, \hat{\theta} ), \theta; x) = \log p_{\theta}(x) - \mathbb{KL}\left( p(\cdot | x, \hat{\theta} ) \left\|\right. p(\cdot | x, \theta) \right).
>$$
>Thus
>$$
>Q(\theta; \hat{\theta}) = \log p_{\theta}(x) - \mathbb{KL}\left( p(\cdot | x, \hat{\theta} ) \left\|\right. p(\cdot | x, \theta) \right) - H(p(z| x, \hat{\theta} )) .
>$$

- [[Shannon Entropy]]

## Explanation

>[!info]
>We see that **ELBO** is not the **KL-divergence**
>$$
>\begin{align*}
>\mathcal{L}(\theta) &:= \mathbb{E}_{ \mathcal{Q} }\left[  \log \left(\frac{d\mathcal{P}_{\theta}(X, Z)}{d\mathcal{Q}(Z)}\right) \right] \\
>\mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}(\cdot| x)\right) &:= \mathbb{E}_{ \mathcal{Q} }\left[   \log \left( \frac{d\mathcal{Q}(Z)}{d\mathcal{P}(Z| x) }\right) \right]
>\end{align*}
>$$

>[!important]
>Note that ELBO is of interest because the **marginal density $\log p_{\theta}(x)$ is usually intractable** for complex model $p(x | z)$. 




## ELBO for Exponential Family

- [[Evidence Lower Bound for Exponential Family]]



-----------
##  Recommended Notes and References


- [[Expectation-Maximization Algorithm]]


- [[Radon-Nikodym Derivative]]
- [[Parametric Models]]


- [[Elements of Statistical Learning by Hastie]] pp 277

- [[Probabilistic Graphical Models by Koller]] pp 881
- [[Deep Learning Foundations and Concepts by Bishop]] pp 569 - 578
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 284, 347, 434
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Deep Learning by Goodfellow]] pp 624, 652