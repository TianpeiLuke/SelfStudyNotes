---
tags:
  - concept
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
keywords:
  - temporal_difference_lambda_learning
  - eligibility_traces
topics:
  - reinforcement_learning/algorithm
name: Equivalence of Forward View and Backward View for TD(lambda)
date of note: 2024-08-12
---

## Concept Definition

>[!important]
>**Name**: Equivalence of Forward View and Backward View for TD($\lambda$)

![[lambda-Return and Compound Update#^63443d]]

### Forward View of T($\lambda$)

![[lambda-Return and Compound Update#^e0bff0]]

![[lambda-Return and Compound Update#^fa79cb]]

![[forward_view.png]]
### Backward View of T($\lambda$)

![[Temporal Difference lambda Algorithm#^cba720]]

![[Temporal Difference lambda Algorithm#^1134a1]]

![[backward_view.png]]

>[!important] 
>Let **$\lambda$-return** be 
>$$
>\begin{align*}
>G_{t}^{\lambda} &:= \left(1- \lambda\right)\,\sum_{n=1}^{\infty}\lambda^{n-1}\,G_{t:t+n}
>\end{align*}
>$$
>
>Denote the update for **offline $\lambda$-return algorithm**, i.e. the **offline TD($\lambda$)**
>$$
>\Delta V_{t}^{\lambda}(x) := \alpha\left[ G_{t}^{\lambda} - V_{t}(x) \right]
>$$
>and the update for **TD($\lambda$) algorithm**
>$$
>\Delta V_{t}^{TD}(x) := \alpha \left[R_{t+1} + \gamma V_{t}(X_{t+1})  - V_{t}(X_{t})\right] \;z_{t}(x) = \alpha\, \delta_{t}\,z_{t}(x)
>$$
>
>We show that the *sum* of all the updates *over an episode* is the **same** for **forward view** and **backward view formulation**. That is
>$$
> \sum_{t=0}^{T-1}\Delta V_{t}^{TD}(x) = \sum_{t=0}^{T-1}\Delta V^{\lambda}_{t}(X_{t})\,\mathbb{1}\left\{ X_{t} = x \right\} , \quad \forall x\in \mathcal{X}
>$$

^b3c492

- [[Characteristic Function of Set]]

### Proof

>[!info]
>Note that an accomulating **eligibility trace** can be written as 
>$$
>z_{t}(x) = \sum_{k=0}^{t}\left( \gamma\,\lambda \right)^{t-k}\mathbb{1}\left\{ X_{k} = x \right\}, \quad \forall x\in \mathcal{X}.
>$$

>[!info]
>The LHS of the equation is
>$$
>\begin{align*}
>\sum_{t=0}^{T-1} \Delta V_{t}^{TD}(x) &= \sum_{t=0}^{T-1}\,\alpha\delta_{t}\,z_{t}(x) \\[5pt]
>&= \sum_{t=0}^{T-1}\,\alpha\delta_{t}\,\sum_{k=0}^{t}\left( \gamma\,\lambda \right)^{t-k}\mathbb{1}\left\{ X_{k} = x \right\} \;\\[5pt]
>&\text{(exchange index $t, k$)}\\[5pt]
>&= \sum_{k=0}^{T-1}\alpha\,  \sum_{t=0}^{k}\,\left( \gamma\,\lambda \right)^{k-t}\mathbb{1}\left\{ X_{t} = x \right\}\,\delta_{k}\; \\[5pt]
>&\text{(exchange row-scan and column-scan)}\\[5pt]
>&= \sum_{t=0}^{T-1}\alpha\,  \sum_{k=t}^{T-1}\,\left( \gamma\,\lambda \right)^{k-t}\mathbb{1}\left\{ X_{t} = x \right\}\,\delta_{k}\;\\[5pt]
>&= \sum_{t=0}^{T-1}\alpha\,\mathbb{1}\left\{ X_{t} = x \right\}\,  \sum_{k=t}^{T-1}\,\left( \gamma\,\lambda \right)^{k-t}\delta_{k}
>\end{align*}
>$$

>[!info]
>For the RHS, consider one update
>$$
>\begin{align*}
> \frac{1}{\alpha}\,\Delta V_{t}^{\lambda}(X_{t}) &=\left[ G_{t}^{\lambda} - V_{t}(X_{t}) \right] \\
> &= - V_{t}(X_{t}) \\[5pt]
> &\quad + \left(  1- \lambda \right)\lambda^{0}\,\left[ R_{t+1} + \gamma\,V_{t}(X_{t+1}) \right] \\[5pt]
> &\quad + \left(  1- \lambda \right)\lambda^{1}\,\left[ R_{t+1} + \gamma\,R_{t+2} + \gamma^2\,V_{t}(X_{t+2}) \right] \\[5pt]
> &\quad + \left(  1- \lambda \right)\lambda^{2}\,\left[ R_{t+1} + \gamma\,R_{t+2} + \gamma^2\,R_{t+3} + \gamma^3\,V_{t}(X_{t+3}) \right] \\[5pt]
> &\quad \,{+}\ldots
>\end{align*}
>$$
>- For the first term with $R_{t+1}$, the weight is $$(1-\lambda)\left[\lambda^{0} + \lambda^{1} + \lambda^{2} \,{+}\ldots{}\,  \right] = 1.$$ 
>- Similar trick for $R_{t+2}$ $$(\gamma\,\lambda)^1\,(1-\lambda)\left[\lambda^{0} + \lambda^{1} + \lambda^{2} \,{+}\ldots{}\,  \right] = (\gamma\,\lambda)^1$$ 
>- It follows that the weight for the $R_{t+n}$ term is $(\gamma\,\lambda)^{n-1}$
>
>Thus we switch from **row-scan** to **column-scan** in the sum and we have
>$$
>\begin{align*}
>\frac{1}{\alpha}\,\Delta V_{t}^{\lambda}(X_{t}) &= - V_{t}(X_{t}) \\[5pt]
>&\quad + \left( \gamma\,\lambda \right)^0 \left[ R_{t+1} + \gamma\,V_{t}(X_{t+1}) -\lambda\gamma\,V_{t}(X_{t+1})  \right] \\[5pt]
>&\quad + \left( \gamma\,\lambda \right)^{1} \left[ R_{t+2} + \gamma\,V_{t}(X_{t+2}) -\lambda\gamma\,V_{t}(X_{t+2})  \right] \\[5pt]
>&\quad +\ldots \\[5pt]
>&= \left( \gamma\,\lambda \right)^0\left[ R_{t+1} + \gamma\,V_{t}(X_{t+1})  - V_{t}(X_{t})\right] \\[5pt]
>&\quad +  \left( \gamma\,\lambda \right)^{1} \left[ R_{t+2} + \gamma\,V_{t}(X_{t+2})  - V_{t}(X_{t+1})\right]\\[5pt]
>&\quad + \ldots \\[5pt]
>&\approx \sum_{k=t}^{\infty}\left( \gamma\,\lambda \right)^{k-t}\,\delta_{k}
>\end{align*}
>$$
>This is approximation since in general $V_{t+1} \neq V_{t}$. But for **offline algorithm**, the above equality is **exact**, since $V_{t} = V_{t+1}$ as the value function is updated at the end of each episode.
>
>Then we have
>$$
>\frac{1}{\alpha}\,\Delta V_{t}^{\lambda}(X_{t}) \approx \sum_{k=t}^{\infty}\left( \gamma\,\lambda \right)^{k-t}\,\delta_{k} = \sum_{k=t}^{T-1}\left( \gamma\,\lambda \right)^{k-t}\,\delta_{k}
>$$
>The last equality is exact since **after termination state** is reached, all of the rewards and values are zeros and **TD error is zero**
>

^afdf2a

>[!info]
>For the **offline case**, we have
>$$
>\begin{align*}
>\sum_{t=0}^{T-1} \Delta V_{t}^{TD}(x)&= \sum_{t=0}^{T-1}\alpha\,\mathbb{1}\left\{ X_{t} = x \right\}\,  \sum_{k=t}^{T-1}\,\left( \gamma\,\lambda \right)^{k-t}\delta_{k}\\[5pt]
>&= \sum_{t=0}^{T-1}\alpha\,\mathbb{1}\left\{ X_{t} = x \right\}\,\frac{1}{\alpha}\,\Delta V_{t}^{\lambda}(X_{t})\\[5pt]
>&= \sum_{t=0}^{T-1}\,\Delta V_{t}^{\lambda}(X_{t})\mathbb{1}\left\{ X_{t} = x \right\}
>\end{align*}
>$$



## Explanation

>[!important] Proposition
>This shows an alternative formulation of **$\lambda$-return** in terms of **TD errors**
>$$
>G_{t}^{\lambda}  = V(X_{t}) + \sum_{k=t}^{\infty}\left( \gamma\,\lambda \right)^{k-t}\,\delta_{k}
>$$
>where the **TD error** is defined as
>$$
>\delta_{t} = R_{t+1} + \gamma V(X_{t+1})  - V(X_{t})
>$$




-----------
##  Recommended Notes and References


- [[Temporal Difference lambda Algorithm]]
- [[lambda-Return and Compound Update]]
- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]
- [[Temporal Difference Learning]]



- [[Reinforcement Learning An Introduction by Sutton]]