---
tags:
  - concept
  - statistics/monte_carlo_simulation
keywords:
  - monte_carlo
topics:
  - statistics/monte_carlo
name: Application of Monte Carlo
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Monte Carlo and Applications

>[!important]
>The most fundamental operations in probabilistic modeling and statistics involve **integration** on **high dimensional spaces**:
>$$
> \begin{align*}
> I := \int_{\mathcal{X}} g(x)dx
> \end{align*}
>$$ 
>The applications include
>- **Expectation**: $$\mathbb{E}_{ \mathcal{P} }\left[ h(X) \right]$$
>- **Marginalization**: $$p(x_{1} \,{,}\ldots{,}\,x_{n}) = \int_{\mathcal{X}_{i}}p(x_{1} \,{,}\ldots{,}\,x_{i} \,{,}\ldots{,}\,x_{n})dx_{i}$$
>- **Conditioning**: $$p(x_{1} \,{,}\ldots{,}\,x_{i-1},\,x_{i+1} \,{,}\ldots{,}\,x_{n} \,|\, X_{i}= x_{i}) = \frac{p(x_{1} \,{,}\ldots{,}\,x_{n})}{\int_{\mathcal{X}_{-i}} p(x_{-i}, x_{i})dx_{-i}}$$ where $x_{-i} = (x_{j}, j\neq i)$
>- **Bayesian inference**: by Bayes Theorem, 
>  $$\begin{align*}
>P(\Theta | \mathcal{D}) &= \frac{P(\mathcal{D} | \Theta) P(\Theta)}{P(\mathcal{D})}\\
 &= \frac{P(\mathcal{D} | \Theta) P(\Theta)}{\int_{\Theta} P(\mathcal{D} | \Theta) P(\Theta) d \Theta}\\
 \Rightarrow \log P(\Theta | \mathcal{D})  &= \log P(\mathcal{D} | \Theta) + \log P(\Theta)  - \log \int_{\Theta} P(\mathcal{D} | \Theta) P(\Theta) d \Theta
>\end{align*}
>$$
 >where $\mathcal{D}: =\{X_1, \ldots, X_n\}$ are i.i.d. samples and $\Theta$ is a set of parameters for model $p(\mathcal{D} | \Theta)$.
 >- Computing the **log-partition function**: $$\log \int_{\Theta} P(\mathcal{D} | \Theta) P(\Theta) d \Theta$$

>[!important] Definition
>It is natural to propose using a sample $\mathcal{D}: =\{X_1, \ldots, X_n\}$ generated from the density $p$ to **approximate integration** by the *empirical average*. This approach is referred to as the **Monte Carlo methods**. 
>
>Specifically,
>$$ 
>\begin{align}
>\overline{h}_{m} &= \frac{1}{m}\sum_{i=1}^{m}h(X_{i})
>\end{align}
>$$
>since $\overline{h}_{m}$ converges almost surely to  $\mathbb{E}_{\mathcal{P}}\left[ h(X) \right]$ by the *Strong Law of Large Numbers*. 
>

>[!info]
>When $\overline{h}_{m}$ has a *finite expectation* under $p$, the **rate of convergence** of $\overline{h}_{m}$ can be assessed since the variance 
>$$
> \begin{align*}
> \text{Var}\left( \overline{h}_{m} \right) &= \frac{1}{m}\int_{\mathcal{X}}\left( h(x) -  \mathbb{E}_{ \mathcal{P} }\left[ h(X) \right] \right)^{2}p(x) dx
> \end{align*}
> $$
> can also be estimated from the sample $\mathcal{D}$ through
> $$
> \begin{align*}
> v_{m} &= \frac{1}{m}\sum_{i=1}^{m}\left( h(X_{i}) - \overline{h}_{m} \right)^2
> \end{align*}
>$$
> 
> For $m$ large,
>$$ 
> \begin{align*}
> \frac{h(X) - \overline{h}_{m}}{\sqrt{v_{m}}} \rightarrow \mathcal{N}(0, 1).
> \end{align*}
>$$  
>This leads to the construction of a **convergence test** and of **confidence bounds** on the approximation of $\mathbb{E}_{ \mathcal{P} }\left[ h(X) \right]$.

- [[Kolmogorov Strong Law of Large Numbers]]
- [[Central Limit Theorem]]



## Explanation





-----------
##  Recommended Notes and References

