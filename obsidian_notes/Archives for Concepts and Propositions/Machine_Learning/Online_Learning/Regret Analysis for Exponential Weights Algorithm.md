---
tags:
  - concept
  - online_learning/theory
  - online_learning/algorithms
  - machine_learning/online_learning
keywords:
  - regret_online_learning
  - regret_analysis
topics:
  - online_learning
name: Regret Analysis for Exponential Weight Algorithm
date of note: 2024-08-06
---

## Concept Definition

>[!important]
>**Name**: Regret Analysis for Exponential Weight Algorithm

![[Regret for Online Learning#^c8c1f8]]

## Sub-Gaussian Regret Bound for Convex Loss

![[No-Regret Learning#^873808]]


>[!important] Theorem
>Assume that the loss $\ell: \mathcal{D}\times \mathcal{Y} \to [0,1]$ is **convex** in its *first argument* and *bounded* within $[0,1]$.
>
>For any $T$, $\eta >0$ and for all outcomes $(y_{1}\,{,}\ldots{,}\,y_{T})\subset \mathcal{Y}$, the **maximum regret** for the **exponentially weighted algorithm** is bounded by 
>$$
> \max_{1 \le i \le k}\,R_{i, T} = \left( \widehat{L}_{T} - \min_{1 \le i \le k} L_{i, T}  \right) \le \frac{\log(k)}{\eta} + \frac{T\eta}{8}.
>$$
>After we choose an **optimal parameter** $\eta^{*} = \sqrt{ 8\log(k) / T }$, the inequality becomes
>$$
> \max_{1 \le i \le k}\,R_{i, T} = \left( \widehat{L}_{T} - \min_{1 \le i \le k} L_{i, T}  \right) \le \sqrt{ \frac{\log(k)\, T}{2} }.
>$$

- [[Hoeffding Inequality]]
- [[Convex Function]]
- [[No-Regret Learning]]
- [[Sub-Gaussian Random Variable]]
- [[Algorithm Big-O Notations and Dominance Relation]]
- [[Prediction Learning and Games by Cesa-Bianchi]] pp 14 - 16

### Proof of Theorem

![[Hoeffding Inequality#^dbac1c]]

>[!important]
>By **Hoedfing's lemma**, for $X\in [0,1]$,
>$$
>\log  \mathbb{E}\left[ e^{\lambda X} \right] \le \lambda\,  \mathbb{E}\left[ X \right] + \frac{\lambda^2}{8}
>$$

![[Potential Function for Weighted Average Forecast#^f29770]]


>[!info]
>Denote $$w_{t} = \sum_{i=1}^{k}w_{i}^{(k)}$$ where $w_{i}^{(k)}$ is the exponential weights in EWA. 
>
>Define the **potential function** in terms of *exponential weights* $$\Phi_{t} := -\log w_{t}.$$

- [[Potential Function for Weighted Average Forecast]]

![[Potential Function for Weighted Average Forecast#^57afc0]]

>[!info]
>We see that the *difference of potential*
>$$
>\begin{align*}
> \Phi_{t+1} - \Phi_{t} &= -\log w_{t+1} + \log w_{t} \\
> &= - \log \left( \frac{w_{t+1}}{w_{t}} \right) \\[5pt]
> &= - \log \left( \frac{\sum_{i = 1}^{k}w_{i}^{(t+1)}}{\sum_{i = 1}^{k}w_{i}^{(t)}} \right) \\[5pt]
> &= - \log \left( \frac{\sum_{i = 1}^{k}w_{i}^{(t)}\,\exp \left( -\eta\, \ell_{i, t} \right) }{\sum_{i = 1}^{k}w_{i}^{(t)}} \right),\quad (1)
>\end{align*}
>$$

>[!info]
>Define a *discrete random variable* $X_{t} \in \left\{ \ell_{1,t} \,{,}\ldots{,}\, \ell_{k,t}\right\} \subset [0,1]$ so that
>$$
>\mathcal{P}(X_{t} = \ell_{i, t}) = \frac{w_{i}^{(t)}}{\sum_{i=1}^{k}w_{i}^{(t)}}, \quad i=1 \,{,}\ldots{,}\,k
>$$ 

>[!info]
>Then we can reformulate the RHS of the *difference of potential* equation $(1)$
>$$
>\begin{align*}
>- \log \left( \sum_{i = 1}^{k} \frac{w_{i}^{(t)}}{\sum_{i = 1}^{k}w_{i}^{(t)}}\,\exp \left( -\eta\, \ell_{i, t} \right) \right) &= -\log  \mathbb{E}_{ \mathcal{P} }\left[ e^{- \eta X_{t}} \right] 
>\end{align*}
>$$

>[!info]
>By Hoedfing's lemma, 
>$$
>\begin{align*}
>-\log  \mathbb{E}_{ \mathcal{P} }\left[ e^{- \eta X_{t}} \right] &\ge \eta\,  \mathbb{E}\left[ X_{t} \right] - \frac{\eta^2}{8}\\[5pt]
>&=  \eta\,\sum_{i = 1}^{k} \frac{w_{i}^{(t)}}{\sum_{i = 1}^{k}w_{i}^{(t)}}\,\ell_{i, t} - \frac{\eta^2}{8}\\
>\end{align*}
>$$

>[!info]
>Substitute this lower bound to the equation $(1)$, we have
>$$
>\begin{align*}
> \sum_{t=1}^{T}\left( \Phi_{t+1} - \Phi_{t}  \right)&\ge \eta\,\sum_{t=1}^{T}\sum_{i = 1}^{k} \frac{w_{i}^{(t)}}{\sum_{i = 1}^{k}w_{i}^{(t)}}\, \ell_{i, t} - \frac{T\eta^2}{8} \\[5pt]
>&\equiv  \eta \sum_{t=1}^{T} \left(\sum_{i = 1}^{k}\frac{w_{i}^{(t)}}{\sum_{i = 1}^{k}w_{i}^{(t)}}\,\ell(f_{i}^{(t)}, y_{t})   \right) - \frac{T\eta^2}{8} \\[5pt] 
>& \ge \eta \sum_{t=1}^{T} \ell \left(\sum_{i = 1}^{k}\frac{w_{i}^{(t)}}{\sum_{i = 1}^{k}w_{i}^{(t)}}f_{i}^{(t)},\, y_{t}  \right) - \frac{T\eta^2}{8} \\[5pt] 
>&= \eta \sum_{t=1}^{T} \ell \left(\hat{y}_{t},\, y_{t}\right) - \frac{T\eta^2}{8}  \\[5pt] 
>&\equiv \eta\, \widehat{L}_{T}  - \frac{T\eta^2}{8}.\qquad \qquad (2)
>\end{align*}
>$$
>The last inequality is due to **convexity** of $\ell$ function in its first argument, and *Jenson's inequality*

- [[Jensen Inequality]]

>[!info]
>On the other hand, we can find an upper bound 
>$$
>\begin{align*}
> \Phi_{T+1} - \Phi_{1} &= -\log w_{T+1} + \log w_{1} \\[5pt]
> &= -\log w_{T+1} + \log(k)  \quad \left( w_{i}^{(1)} = 1 \right) \\[5pt]
>&=   -\log \left( \sum_{i=1}^{k}w_{i}^{(T)}\exp \left(-\eta\, \ell_{i, T} \right) \right) + \log(k)\\[5pt]
>&=  -\log \left( \sum_{i=1}^{k}\prod_{s=1}^{T}\exp \left(-\eta\, \ell_{i, s} \right) \right) + \log(k)\\[5pt]
>&=  -\log \left( \sum_{i=1}^{k}\exp \left(-\eta\, \sum_{s=1}^{T}\ell_{i, s} \right) \right) + \log(k)\\[5pt]
>&=  -\log \left( \sum_{i=1}^{k}\exp \left(-\eta\,  L_{i, T} \right) \right) + \log(k)\\[5pt]
>&\le - \log \left( \exp(-\eta\, L_{i, T}) \right)  +\log(k) \\[5pt]
>&= \eta\, L_{i, T} + \log(k)\qquad \qquad (3)
>\end{align*}
>$$
>The last inequality is due to the *non-negativity* of $\exp(-\eta\,  L_{i, T})$.

>[!info]
>Combining $(2)$ and $(3)$, we have
>$$
> \eta\, L_{i, T} + \log(k) \ge \eta\, \widehat{L}_{T}  - \frac{T\eta^2}{8}
>$$
>so 
>$$
>\widehat{L}_{T}  \le L_{i, T} + \frac{\log(k)}{\eta} + \frac{T\eta}{8}, \quad i=1 \,{,}\ldots{,}\,k.
>$$

>[!info]
>Taking $\eta^{*} = \sqrt{ 8\log(k) / T }$, we can use the **inequality of arithmetic and geometric means** and we hve
>$$
> \widehat{L}_{T}  \le L_{i, T} + \sqrt{ \frac{\log(k)\, T}{2} }.
>$$
>Q.E.D.

## Bernstein-Like Regret Bound for Small Convex Loss

>[!important] Theorem
>Let $(y_{1} \,{,}\ldots{,}\,y_{T})$ be outcome received and $(\hat{y}_{1} \,{,}\ldots{,}\,\hat{y}_{T})$ be the weighted prediction from the **exponentially weighted algorithm** with parameter $\eta >0$.  Denote $$\widehat{L}_{T} := \sum_{t=1}^{T}\ell(\hat{y}_{t}, y_{t}), \quad L_{i, T} := \sum_{t=1}^{T}\ell(f_{i}^{(t)}, y_{t}).$$
>
>Assume that the loss $\ell: \mathcal{D}\times \mathcal{Y} \to [0,1]$ is **convex** in its *first argument* and *bounded* within $[0,1]$.
>
>Then for each expert $i=1 \,{,}\ldots{,}\,k$, the **regret** is *bounded above* as
>$$
>\begin{align*}
> \widehat{L}_{T} \le \frac{1}{1 - e^{-\eta}}\left( \eta\, L_{i, T} + \log(k) \right)
>\end{align*}
>$$
>Thus
>$$
> \widehat{L}_{T} \le \frac{\eta}{1 - e^{-\eta}}\,\left( \min_{i} L_{i, T}  \right) + \frac{\log(k)}{1 - e^{-\eta}}
>$$

- [[Bernstein Inequality]]
- [[Regret for Online Learning]]
- [[No-Regret Learning]]

- [[Prediction Learning and Games by Cesa-Bianchi]] pp 21


>[!important] Corollary
>Denote $$\widehat{L}_{T} := \sum_{t=1}^{T}\ell(\hat{y}_{t}, y_{t}), \quad L_{i, T} := \sum_{t=1}^{T}\ell(f_{i}^{(t)}, y_{t}).$$
>
>For **optimal parameter** $\eta^{*} >0$,
>$$
>\widehat{L}_{T} \le L_{i, T} + \sqrt{ 2 \log(k)\, L_{i, T} } + \log(k),\quad i=1 \,{,}\ldots{,}\,k.
>$$

- [[Bernstein Inequality]]
- [[Prediction Learning and Games by Cesa-Bianchi]] pp 21

### Proof

>[!info]
>We use the following Lemma

>[!important] Lemma
>For any $\eta$ and any random variable $X\in[0,1]$, we have
>$$
>\log  \mathbb{E}\left[ e^{\eta X} \right] \le \left( e^{\eta} - 1 \right) \mathbb{E}\left[ X \right]
>$$

>[!important] Hint
>$$
>e^{\eta x} \le \left(e^{\eta}-1 \right)x + 1, \quad x \in (0,1)
>$$
>


>[!info] Proof of Theoerm
>Denote $$w_{t} = \sum_{i=1}^{k}w_{i}^{(k)}$$ where $w_{i}^{(k)}$ is the exponential weights in EWA. 
>
>Define the **potential function** in terms of *exponential weights* $$\Phi_{t} := -\log w_{t}.$$

>[!info]
>We see that the *difference of potential*
>$$
>\begin{align*}
> \Phi_{t+1} - \Phi_{t} &= -\log w_{t+1} + \log w_{t} \\
> &= - \log \left( \frac{w_{t+1}}{w_{t}} \right) \\[5pt]
> &= - \log \left( \frac{\sum_{i = 1}^{k}w_{i}^{(t+1)}}{\sum_{i = 1}^{k}w_{i}^{(t)}} \right) \\[5pt]
> &= - \log \left( \frac{\sum_{i = 1}^{k}w_{i}^{(t)}\,\exp \left( -\eta\, \ell_{i, t} \right) }{\sum_{i = 1}^{k}w_{i}^{(t)}} \right),\quad (1)
>\end{align*}
>$$

>[!info]
>Define a *discrete random variable* $X_{t} \in \left\{ \ell_{1,t} \,{,}\ldots{,}\, \ell_{k,t}\right\} \subset [0,1]$ so that
>$$
>\mathcal{P}(X_{t} = \ell_{i, t}) = \frac{w_{i}^{(t)}}{\sum_{i=1}^{k}w_{i}^{(t)}}, \quad i=1 \,{,}\ldots{,}\,k
>$$ 

>[!info]
>Then we can reformulate the RHS of the *difference of potential* equation $(1)$
>$$
>\begin{align*}
>\Phi_{t+1} - \Phi_{t} &= - \log \left( \sum_{i = 1}^{k} \frac{w_{i}^{(t)}}{\sum_{i = 1}^{k}w_{i}^{(t)}}\,\exp \left( -\eta\, \ell_{i, t} \right) \right) \\[5pt]
>&= -\log  \mathbb{E}\left[ e^{- \eta X_{t}} \right] \\[5pt]
>& \ge -\left( e^{-\eta} - 1 \right) \mathbb{E}\left[ X_{t} \right] \\[5pt]
>& = \left( 1 - e^{-\eta}  \right)\;\sum_{i = 1}^{k} \frac{w_{i}^{(t)}\,\ell_{i, t}}{\sum_{i = 1}^{k}w_{i}^{(t)}}\\[5pt]
>&\ge   \left( 1 - e^{-\eta}  \right)\;\ell \left(\frac{w_{i}^{(t)}\,f_{i}^{(t)}}{\sum_{i = 1}^{k}w_{i}^{(t)}},\, y_{t}  \right) \\[5pt]
>&= \left( 1 - e^{-\eta}  \right)\;\ell(\hat{y}_{t}, y_{t})
>\end{align*}
>$$
>The last inequality is due to [[Jensen Inequality]] since $\ell$ is convex in its first argument.

>[!info]
>Thus
>$$
>\begin{align*}
> \left( 1- e^{-\eta} \right)\widehat{L}_{T} &:= \left( 1- e^{-\eta} \right)\,\sum_{t=1}^{T}\ell(\hat{y}_{t}, y_{t}) \\
> &\le \sum_{t=1}^{T}\left( \Phi_{t+1} - \Phi_{t} \right) \\
> &= \Phi_{T+1} - \Phi_{1} \\[5pt]
> &= -\log \left( \sum_{i=1}^{k}w_{i}^{(T+1)} \right) + \log(k) \\[5pt]
> &\le - \log(w_{i}^{(T+1)}) + \log(k) \\[5pt]
> &= - \log \left( \prod_{s=1}^{T}\exp \left( -\eta\, \ell_{i,s} \right) \right)  + \log(k) \\[5pt]
> &= \eta\, \sum_{s=1}^{T}\ell_{i,s} + \log(k) \\[5pt]
> &= \eta\, L_{i, T} + \log(k) 
>\end{align*}
>$$
>Q.E.D.

### Proof of Corollary

>[!important]
>Note that
>$$
> 0 \le \eta \le \sinh(\eta) := \frac{e^{\eta} - e^{-\eta}}{2}, \quad \forall \eta \ge 0
>$$

>[!info]
>By above theorem,
>$$
>\begin{align*}
>  \widehat{L}_{T} &\le \frac{1}{1 - e^{-\eta}}\left( \eta\, L_{i, T} + \log(k) \right) \\[5pt]
>  &\le \frac{\log(k)}{1 - e^{-\eta}} + \frac{1}{1 - e^{-\eta}}\,\frac{e^{\eta} - e^{-\eta}}{2}\,L_{i, T} \\[5pt]
>  &= \frac{\log(k)}{1 - e^{-\eta}} + \frac{(1 - e^{-\eta})\,(1 + e^{\eta})}{2 (1 - e^{-\eta})}\,L_{i, T} \\[5pt]
>  &= \frac{\log(k)}{1 - e^{-\eta}} + \frac{1 + e^{\eta}}{2}\,L_{i, T} \\[5pt]
>\end{align*}
>$$
>Let $\eta^{*} = \log \left( 1 + \sqrt{ 2 \log(k) / L_{i,T} } \right)$. We have
>$$
>\begin{align*}
> \frac{\log(k)}{1 - e^{-\eta^{*}}}  + \frac{1 + e^{\eta^{*}}}{2}\,L_{i, T}  &= \log(k) + \sqrt{ \frac{\log(k) L_{i,T}}{2} } + L_{i, T} + \sqrt{ \frac{\log(k)\,L_{i,T}}{2} }\\
> &= L_{i, T} + \sqrt{ 2 \log(k)\, L_{i, T} } + \log(k)
>\end{align*}
>$$
>Q.E.D.


## Explanation

>[!info]
>If $\min_{i} L_{i,T} = 0$, then 
>$$
>\widehat{L}_{T} = O(\log(k)).
>$$
>

>[!info]
>If $$\min_{i} L_{i,T} = O(T),$$ then 
>$$
>\widehat{L}_{T} = O\left( \sqrt{ T \log(k) } \right).
>$$

>[!info]
>The **EWA** has **no-regret property**, i.e.
>$$
> \frac{1}{T}\left( \widehat{L}_{T} - \min_{i} L_{i, T}  \right) = O\left( \frac{1}{\sqrt{ T }} \right) \to 0.
>$$

>[!info]
>The second bound is better than the first one if $\min_{i}L_{i, T} \ll \sqrt{ T }.$




-----------
##  Recommended Notes and References

- [[Exponential Weights Algorithm for Convex Loss]]
- [[Weighted Average Forecast via Potential]]

- [[Regret for Online Learning]]
- [[No-Regret Learning]]

- [[Hoeffding Inequality]]


- [[Prediction Learning and Games by Cesa-Bianchi]] pp 16, 21
- [[Foundations of Machine Learning by Mohri]] pp 157 - 159
- [[Concentration Inequalities by Boucheron]]