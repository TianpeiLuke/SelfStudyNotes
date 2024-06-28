---
tags:
  - concept
  - statistics/inference
keywords:
  - basu_theorem
topics:
  - statistics/inference
name: Basu Theorem
date of note: 2024-06-26
---

## Concept Definition

>[!important]
>**Name**: Basu Theorem

>[!important] Basu Theorem
>Let $V$ and $T$ be two statistics of $X$ from a population $\mathcal{P} \in \mathscr{P}$. 
>
>If $V$ is **ancillary** and $T$ is **boundedly complete** and **sufficient** for $\mathcal{P} \in \mathscr{P}$, then $V$ and $T$ are **independent** *with respect to* **any** $\mathcal{P} \in \mathscr{P}$.

- [[Complete and Bounded Complete Statistics]]
- [[Sufficient Statistics]]
- [[Independent Random Variables]]

## Proof

>[!info] 
>Suppose $B$ is a measurable set in the range of $V$. 
>
>Since $V$ is *ancillary*, $$\mathcal{P}\left(V^{-1}(B)\right) = \mathcal{P}\left(V(X) \in B\right) \equiv  c$$ is *constant*. 

>[!info]
>Since $T$ is *sufficient*, $$\mathbb{E}_{ \mathcal{P} }\left[ \mathbb{1}\{ V(X) \in B \}  \;|\; T \; \right]$$ is *independent* from $\mathcal{P}$.


>[!info]
>Since for any $\mathcal{P} \in \mathscr{P}$,
>$$
>\begin{align*}
>&\mathbb{E}_{ \mathcal{P} }\left[  \mathbb{E}_{ \mathcal{P} }\left[ \mathbb{1}\{ V(X) \in B \}  \;|\; T \; \right] - \mathcal{P}\left(V(X) \in B\right) \right] \\[5pt]
>&=   \mathbb{E}_{ \mathcal{P} }\left[ \mathbb{1}\{ V(X) \in B \}   \right] - \mathcal{P}\left(V(X) \in B\right) \\
>&= 0,
\end{align*}
>$$
>by *bounded completeness* of $T$, we have
>$$
>\mathcal{P}\left(V(X) \in B\,|\, T\right) =  \mathbb{E}_{ \mathcal{P} }\left[ \mathbb{1}\{ V(X) \in B \}  \;|\; T \; \right] = \mathcal{P}\left(V(X) \in B\right) \equiv c, \quad \mathcal{P}\text{-a.s.}
>$$

>[!info]
>Let $A$ be an event in the range of $T$.
>
>$$
>\begin{align*}
>&\mathcal{P}\left\{ X: T(X) \in A \land V(X) \in B \right\} \\[5pt]
>&= \mathbb{E}_{ \mathcal{P} }\left[ \mathbb{1}\left\{ T(X) \in A  \right\} \mathbb{1}\left\{ V(X) \in B  \right\} \right] \\[5pt]
>&= \mathbb{E}_{\mathcal{P}}\left[  \mathbb{E}_{ \mathcal{P} }\left[ \mathbb{1}\left\{ T(X) \in A  \right\} \mathbb{1}\left\{ V(X) \in B  \right\} \;|\;T\right] \right]\\[5pt]
>&= \mathbb{E}_{\mathcal{P}}\left[ \mathbb{1}\left\{ T(X) \in A  \right\}\; \mathbb{E}_{ \mathcal{P} }\left[  \mathbb{1}\left\{ V(X) \in B  \right\} \;|\;T\right] \right]\\[5pt]
>&=  \mathbb{E}_{\mathcal{P}}\left[ \mathbb{1}\left\{ T(X) \in A  \right\}\; \mathcal{P}\left(V(X) \in B\right) \; \right] \\[5pt]
>&= \mathbb{E}_{\mathcal{P}}\left[ \mathbb{1}\left\{ T(X) \in A  \right\}\right] \;\mathcal{P}\left(V(X) \in B\right)\\[5pt]
>&= \mathcal{P}\left(T(X) \in A\right) \;\mathcal{P}\left(V(X) \in B\right)
>\end{align*}
>$$
>Thus $T$ and $V$ are **independent** with respect to $\mathcal{P}$. Q.E.D.

## Explanation





-----------
##  Recommended Notes and References



- [[Mathematical Statistics by Shao]] pp 112