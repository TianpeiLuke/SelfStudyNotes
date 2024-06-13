---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - herbst_argument
topics:
  - concentration_inequality
name: Herbst Argument
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: The Herbst's Argument

>[!important] Entropy Functional of Exponential Function
>Let $X = (X_{1} \,{,}\ldots{,}\, X_{n})$ be $n$ independent random variables.  Define $$Z = f(X_{1} \,{,}\ldots{,}\, X_{n})$$ and  $g(x) = e^{\lambda f(x)/2}.$ 
>
>
>The **entropy functional** of $g(X) = \exp\left(\lambda Z /2\right)$ becomes
>$$
>\begin{align*}
>\text{Ent}(g^2) = \text{Ent}(e^{\lambda Z}) &= \mathbb{E}\left[\lambda Z e^{\lambda Z}\right] - \mathbb{E}\left[  e^{\lambda Z} \right]\log \left(\mathbb{E}\left[  e^{\lambda Z} \right]\right) \\
>&= \lambda\, \frac{d}{d\lambda}M_{Z}(\lambda) - M_{Z}(\lambda) \log \left(M_{Z}(\lambda) \right) \\
>&= \lambda^2 M_{Z}(\lambda)  \frac{d}{d\lambda}\left(\frac{\log \left(M_{Z}(\lambda) \right)}{\lambda}\right) 
>\end{align*}
>$$
>
>Thus
>$$
>\begin{align*}
>\frac{\text{Ent}(e^{\lambda Z})}{M_{Z}(\lambda) } &= \lambda^2 \frac{d}{d\lambda}\left(\frac{\log \left(M_{Z}(\lambda) \right)}{\lambda}\right) := \lambda^2 \frac{d}{d\lambda}\left(\frac{ \psi_{Z}(\lambda) }{\lambda}\right) 
>\end{align*}
>$$
>where $M_{Z}(\lambda)$ is the **moment generating function** of $Z$
>$$
>M_{Z}(\lambda) := \mathbb{E}_{}\left[ e^{\lambda Z} \right],\quad \psi_{Z} = \log \mathbb{E}_{}\left[ e^{\lambda Z} \right].
>$$

^2525f4

- [[Entropy Functional]]
- [[Moment Generating Function]]


>[!info]
>We can check the derivative of $M_{Z}(\lambda)$ with respect to $\lambda$
>$$
>\begin{align*}
>\frac{d}{d\lambda}M_{Z}(\lambda) &= \frac{d}{d\lambda} \int e^{\lambda Z} d\mathcal{P}\\
>&= \int \frac{d}{d\lambda} e^{\lambda Z} d\mathcal{P} \\
>&= \int Z e^{\lambda Z} d\mathcal{P} \\
>&= \mathbb{E}\left[\lambda e^{\lambda Z} \right]
\end{align*}
>$$


>[!important] Proposition
>Let $Z$ be an integrable random variable such that for some $\nu > 0$, we have, for every $\lambda > 0$,
>$$
> \begin{align}
> \frac{\text{Ent}(e^{\lambda Z})}{\mathbb{E}_{}\left[ e^{\lambda Z} \right]} &\le \frac{\nu \lambda^2}{2}. 
> \end{align}
>$$  
>
>Then, for every $\lambda >0$, the **logarithmic moment generating function** of centered random variable $(Z - \mathbb{E}\left[  Z \right])$ satisfies
>$$
> \begin{align*}
> \psi_{Z - \mathbb{E}\left[Z\right]}(\lambda) := \log \mathbb{E}\left[ e^{\lambda (Z - \mathbb{E}\left[Z\right])} \right] &\le \frac{\nu \lambda^2}{2} .
> \end{align*} 
>$$ 

^acd61a


>[!important] The Herbst's Argument
>The idea of **Herbst’s argument**:
>- **Bounding** $\text{Ent}(g^2)$ using **the logarithmic Sobolev inequality**, 
>  $$
>  \text{Ent}(g^2) \le C \; \mathbb{E}\left[ \lVert \nabla g \rVert_{2}^2  \right]
> $$
>- Let $g(X) = e^{\lambda f(X)/2}$, then
>$$
>\text{Ent}(e^{\lambda f(X)}) \le \frac{C \lambda^2}{4} \; \mathbb{E}\left[ \lVert \nabla f \rVert_{2}^2  \,e^{\lambda f(X)}\right]
>$$ 
>- If we **bound the variation** $\lVert \nabla f \rVert_{2}^2 \le K$,  we have
>$$
>\text{Ent}(e^{\lambda f(X)}) \le \frac{C\,K\, \lambda^2}{4} \; \mathbb{E}\left[ \,e^{\lambda f(X)}\right]
>$$
>- On the other hand, for $Z = f(X)$
>$$
>\frac{\text{Ent}(e^{\lambda Z})}{M_{Z}(\lambda) } = \lambda^2 \frac{d}{d\lambda}\left(\frac{\log \left(M_{Z}(\lambda) \right)}{\lambda}\right) := \lambda^2 \frac{d}{d\lambda}\left(\frac{ \psi_{Z}(\lambda) }{\lambda}\right) 
>$$
>- A **differential inequality** for $M_{Z}(\lambda)$ can be achieved. 
>$$
>  \lambda^2 \frac{d}{d\lambda}\left(\frac{ \psi_{Z}(\lambda) }{\lambda}\right) \le \frac{C\,K\, \lambda^2}{4}
>$$
>- By solving the **differential inequality** we obtain an *upper bound* for the *moment-generating function*
>$$
>\begin{align*}
>\lambda^2 \frac{d}{d\lambda}\left(\frac{ \psi_{Z}(\lambda) }{\lambda}\right) 
>&\le \frac{C\,K\, \lambda^2}{4} \\
> \implies \frac{d}{d\lambda}\left(\frac{ \psi_{Z}(\lambda) }{\lambda}\right) 
>& \le  \frac{C\,K}{4} \\
> \implies \frac{ \psi_{Z}(\lambda) }{\lambda} &\le  \frac{C\,K}{4} \lambda\\
> \implies \psi_{Z}(\lambda) &\le \frac{C\,K\, \lambda^2}{4}
\end{align*}
>$$
>- The upper bound of log moment generating function would used in the **Cramér–Chernoff bound**.  For instance, for above derivations, the Chernoff bound would be 
> $$
> \mathcal{P}\left\{ Z -  \mathbb{E}\left[ Z \right] \ge t\right\}  \le \exp \left( - \frac{\nu t^2}{2} \right)
> $$
> where 
>  $$
>  \nu := \frac{C\,K}{2}
> $$

^9bfe27


- [[Cramér–Chernoff Method]]
- [[Logarithmic Sobolev Inequality for Gaussian Random Variables]]
- [[Logarithmic Sobolev Inequality for Bernoulli Random Variables]]


## Explanation

>[!info]
>Note that 
>$$g^2 = \exp \left( \lambda f\right) = \frac{d\mathcal{Q}}{d\mathcal{P}}$$
>can be seen as the *density function* of **Gibbs measure** $\mathcal{Q}$ on random variable $Y:= g(Z)$ and $\lambda = T^{-1}$ is the inverse temperature. 
>
>In terms of this, 
>$$
>\text{Ent}(g^2) = \mathbb{KL}\left( \mathcal{Q} \left\|\right.  \mathcal{P} \right)
>$$



## Proof of the Proposition

>[!info]
>Given that 
>$$
>\begin{align*}
>\text{Ent}(g^2) &=  \lambda\, \frac{d}{d\lambda}M_{Z}(\lambda) - M_{Z}(\lambda) \log \left(M_{Z}(\lambda) \right) ,
\end{align*}
>$$
>we substitute the inequality in the condition to obtain 
>$$
>\begin{align*}
>  \lambda\, \frac{d}{d\lambda}M_{Z}(\lambda) - M_{Z}(\lambda) \log \left(M_{Z}(\lambda) \right)  &\le  \frac{\nu \lambda^2}{2}M_{Z}(\lambda) \\
>   \frac{1}{\lambda}\, \frac{1}{M_{Z}(\lambda)} \frac{d}{d\lambda}M_{Z}(\lambda) -  \frac{1}{\lambda^2}\, \log \left(M_{Z}(\lambda) \right)  &\le \frac{\nu }{2} \\
> \frac{d}{d\lambda}\left(\frac{\log \left(M_{Z}(\lambda) \right)}{\lambda}\right)  &\le \frac{\nu }{2}
\end{align*}
>$$

>[!info]
>BY l' Hospital's rule, we note that 
>$$
>\lim_{ \lambda \to 0 } \frac{\log \left(M_{Z}(\lambda) \right)}{\lambda} = \frac{\frac{d}{d\lambda}M_{Z}(\lambda)|_{\lambda = 0}  }{M_{Z}(0)} = \mathbb{E}\left[  Z\right]
>$$

>[!info]
>Thus
>$$
>\begin{align*}
>\frac{\log \left(M_{Z}(\lambda) \right)}{\lambda} &\le \mathbb{E}\left[  Z\right] + \frac{\nu \lambda}{2} \\
> \implies M_{Z}(\lambda)&\le \exp\left(\lambda \mathbb{E}\left[  Z\right] + \frac{\nu \lambda^2}{2} \right)
>\end{align*}
>$$
>

>[!info]
>Finally, applying [[Cramér–Chernoff Method]],
>$$
>\begin{align*}
>\mathcal{P}\{ Z > \mathbb{E}\left[  Z\right]  + t  \} &\le \inf_{\lambda >0}M_{Z}(\lambda)\exp\left(-\lambda \mathbb{E}\left[  Z\right] - \lambda t\right)\\
>&\le \inf_{\lambda >0}\exp\left(\frac{\nu \lambda^2}{2}  - \lambda t\right) \\
>&\le \exp\left(-\frac{t^2}{2\,\nu}\right) 
>\end{align*}
>$$


## Example Using Logarithmic Sobolev Inequality

>[!info]
>Assume that $X$ is **uniformly distributed over $\set{-1, +1}^n$**, and $Z = f(X_{1} \,{,}\ldots{,}\, X_{n})$, $g(x) = e^{\lambda f(x)/2}.$
>
>Then by [[Logarithmic Sobolev Inequality for Bernoulli Random Variables]], we have
>$$
> \begin{align}
> \text{Ent}(g^2) &\le 2  \mathcal{E}(g) 
> \end{align}
>$$ 
>where
>$$
>\mathcal{E}(g) := \frac{1}{2}\mathbb{E}\left[ \sum_{i=1}^{n} \left(g(X) - g(\widetilde{X}^{(i)}) \right)^2 \right]
>$$
>and  $X := (X_{1} \,{,}\ldots{,}\, X_{n})$ and $$\widetilde{X}^{(i)} := \left(X_{1} \,{,}\ldots{,}\, X_{i-1}, X_{i}^{'}, X_{i+1} \,{,}\ldots{,}\, X_{n}\right)$$
>is obtained by **replacing** $i$-th component of $X$ by an *independent copy* $X_{i}^{'}$.

>[!important]
>Substituting $g(x) = e^{\lambda f(x) /2}$, we have 
>$$
>\text{Ent}(e^{\lambda f(X)}) \le \mathbb{E}\left[ \sum_{i=1}^{n} \left(g(X) - g(\widetilde{X}^{(i)}) \right)^2\right]
>$$ 

>[!info]
>Use the following *first-order inequality* for the convex function $e^x$
>$$
>e^{z/2} - e^{y/2} \le (z- y) e^{z/2} / 2
>$$

>[!important]
>Substituting $g(x) = e^{\lambda x /2}$, we have 
>$$
>\text{Ent}(e^{\lambda f(X)}) \le \frac{\lambda^2}{4} \mathbb{E}\left[e^{\lambda f(X)} \sum_{i=1}^{n} \left(f(X) - f(\widetilde{X}^{(i)}) \right)_{+}^2\right]
>$$ 

>[!info]
>Define the quantity
>$$
>\nu = \max_{x \in \{ -1, +1 \}^n}\sum_{i=1}^{n} \left(f(x) - f(\bar{x}^{(i)}) \right)_{+}^2
>$$
>where $\bar{x}^{(i)} := (x_{1} \,{,}\ldots{,}\, x_{i-1}, -x_{i}, x_{i+1} \,{,}\ldots{,}\, x_{n}).$

>[!important]
>Using the quantity developed, 
>$$
>\text{Ent}(e^{\lambda f(X)}) \le \frac{\nu \lambda^2}{4} \mathbb{E}\left[e^{\lambda f(X)} \right]
>$$
>Then we can apply the Proposition above to derive the Chernoff bound.







-----------
##  Recommended Notes and References

- [[Entropy Functional]]
- [[Moment Generating Function]]

- [[Logarithmic Sobolev Inequality for Bernoulli Random Variables]]

- [[Concentration Inequalities by Boucheron]]