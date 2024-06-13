---
tags:
  - concept
  - statistics/concentration_inequality
keywords: 
topics:
  - concentration_inequality
name: 
date of note: 2024-05-31
---

## Concept Definition

>[!important]
>**Name**: Modified Logarithmic Sobolev Inequalities

>[!important] Modified Logarithmic Sobolev Inequalities
>Consider **independent** random variables $Z_1 \,{,}\ldots{,}\, Z_n$ taking values in $\mathcal{X}$, a real-valued function $f: \mathcal{X}^n \to \mathbb{R}$ and the random variable $$X = f(Z_1  \,{,}\ldots{,}\, Z_n).$$ 
>
>Also denote $$Z_{(-i)}= (Z_1  \,{,}\ldots{,}\, Z_{i-1}, Z_{i+1} \,{,}\ldots{,}\, Z_n)$$ and $$X_{(-i)} = f_i(Z_{(-i)})$$ where $f_i: \mathcal{X}^{n-1} \to \mathbb{R}$ is an arbitrary function. Let $$\phi(x) = e^x -x -1.$$
> 
>Then for all $\lambda \in \mathbb{R}$,
>$$
> \begin{align}
> \lambda  \mathbb{E}\left[ X  e^{\lambda X} \right] -  \mathbb{E}\left[ e^{\lambda X} \right] \log\mathbb{E}\left[ e^{\lambda X}\right]  \le \sum_{i=1}^{n} \mathbb{E}_{  }\left[e^{\lambda X} \phi\left( -\lambda(X - X_{(-i)}) \right)  \right]
> \end{align}
>$$ 

- [[Sub-Additivity of Entropy Functional and Tensorization]]
- [[Jackknife Estimator of Variance]]

### Symmetrized Version

>[!important] Symmetrized Modified Logarithmic Sobolev Inequality
>Consider independent random variables $Z_1 \,{,}\ldots{,}\, Z_n$ taking values in $\mathcal{X}$, a real-valued function $f: \mathcal{X}^n \to \mathbb{R}$ and the random variable $$X = f(Z_1 \,{,}\ldots{,}\, Z_n).$$ Also denote $$\widetilde{X}^{(i)} = f(Z_1 \,{,}\ldots{,}\, Z_{i-1}, Z_i', Z_{i+1} \,{,}\ldots{,}\, Z_n).$$ Let $$\phi(x) = e^x -x -1.$$
>
> Then for all $\lambda \in \mathbb{R}$,
> $$
> \begin{align}
> \lambda  \mathbb{E}\left[ X  e^{\lambda X} \right] -  \mathbb{E}\left[ e^{\lambda X} \right] \log\mathbb{E}\left[ e^{\lambda X}\right] &\le \sum_{i=1}^{n} \mathbb{E}\left[e^{\lambda X}\phi(-\lambda(X - \widetilde{X}^{(i)}))  \right]
> \end{align}
>$$  
>
>Moreover, denoting the *poisson rate function* $$\tau(x) = x(e^x - 1),$$ for all $\lambda \in \mathbb{R}$,
>$$
> \begin{align*}
> \lambda  \mathbb{E}\left[ X  e^{\lambda X} \right] -  \mathbb{E}\left[ e^{\lambda X} \right] \log\mathbb{E}\left[ e^{\lambda X}\right]&\le \sum_{i=1}^{n} \mathbb{E}\left[ e^{\lambda X}\tau(-\lambda[X - \widetilde{X}^{(i)}]_{+}) \right],\\
> \lambda  \mathbb{E}\left[ X  e^{\lambda X} \right] -  \mathbb{E}\left[ e^{\lambda X} \right] \log\mathbb{E}\left[ e^{\lambda X}\right] &\le \sum_{i=1}^{n} \mathbb{E}\left[ e^{\lambda X}\tau(\lambda[\widetilde{X}^{(i)} - X]_{-}) \right].
> \end{align*}
>$$ 

>[!info]
>Note that
>$$
>\phi(x) + e^x \phi(-x) = \tau(x) = x(e^x - 1)
>$$

>[!info]
>The left hand side is
>$$
>\begin{align*}
>\text{Ent}\left( e^{\lambda X} \right) &:=  \mathbb{E}\left[e^{\lambda X} \log \left( e^{\lambda X} \right)  \right] -  \mathbb{E}\left[ e^{\lambda X} \right]\log\left( \mathbb{E}\left[ e^{\lambda X} \right] \right) \\
>&= \lambda \mathbb{E}\left[ X e^{\lambda X}  \right] -  \mathbb{E}\left[ e^{\lambda X} \right]\log\left( \mathbb{E}\left[ e^{\lambda X} \right] \right)
\end{align*}
>$$

- [[Herbst Argument]]

## Proof

>[!info]
>We use the **tensorization property** of the* entropy functional* as well as the **variational formulation** of the entropy functional
>$$
>\begin{align*}
> \text{Ent}_{\mu_i}(Y) &\le  \mathbb{E}_{ \mu_{i} }\left[ Y(\log Y - \log u) - (Y -u) \right]
> \end{align*}
>$$
>for any $u > 0.$

- [[Sub-Additivity of Entropy Functional and Tensorization]]
- [[Variational Formula for Entropy Functional]]


## Explanation



>[!info]
>The *logarithmic moment generating function* of **Poisson distribution**
>$$\psi_{Z}(\lambda) = \lambda (e^{\lambda} - 1) = \tau(\lambda)$$
>So the symmetrized modified logarithmic Sobolev Inequality provides a **Poisson tail bound**

## Looser Bound


>[!info]
>Consider
>$$
> \begin{align*}
> h(u) &= (1+ u)\log(1 + u) - u, \quad u \ge -1.
> \end{align*}
> $$  
> 
>The **convex conjugate function** of $h(u)$ is
>$$
> \begin{align*}
> h^{*}(x) &= \sup_{u \ge -1}\set{x u - h(u)} \\
> &=  \sup_{u \ge -1}\set{x u - (1+ u)\log(1 + u) + u} \\
> &= e^x - x - 1\\
> &= \phi(x)
> \end{align*}
>$$  
>where $1+ u^{*}= e^{x}$. 

- [[Convex Conjugate Function]]

>[!info]
>Recall the Bernstein inequality for Poisson distribution.
>
>The modified logarithmic Sobolev inequality will give us a **Poisson Tail Bound**
>$$
> \begin{align*}
> \mathcal{P}\set{Z \ge t } \le \exp\left( - \nu h\left(\frac{t}{\nu}\right) \right).
> \end{align*}
>$$
>where $$h(u) = (1+ u)\log(1 + u) - u, \quad u \ge -1.$$
>and the variance term can be estimated using the Jackknife estimatior.
 
- [[Bernstein Inequality]]
- [[Chernoff Bound for Poisson distribution]]
- [[Jackknife Estimator of Variance]]





## Corollary


>[!important] Proposition
>Assume that $X$ is such that there exists a constant $\nu > 0$ such that, almost surely,
>$$
> \begin{align*}
> \sum_{i=1}^{n}\left( X - \widetilde{X}_{i} \right)^2 \le \nu.
> \end{align*}
>$$  
>
>Then for all $t > 0$,
>$$
> \begin{align}
> \mathcal{P}\set{X -  \mathbb{E}\left[ X \right] \ge t } &\le \exp \left( - \frac{t^2}{2 \nu} \right). 
> \end{align}
>$$ 





-----------
##  Recommended Notes and References

- [[Entropy Functional]]
- [[Sub-Additivity of Entropy Functional and Tensorization]]
- [[Logarithmic Sobolev Inequality for Gaussian Random Variables]]
- [[Logarithmic Sobolev Inequality for Bernoulli Random Variables]]

- [[Jackknife Estimator of Variance]]


- [[Concentration Inequalities by Boucheron]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]