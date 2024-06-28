---
tags:
  - concept
  - statistics/inference
keywords:
  - complete_statistics
  - bounded_complete_statistics
topics:
  - statistics/inference
name: Complete and Bounded Complete Statistics
date of note: 2024-06-25
---

## Concept Definition

>[!important]
>**Name**: Complete and Bounded Complete Statistics

>[!important] Definition
>A statistic $V(X)$ is said to be **ancillary** if its distribution does *not depend* on the *population* $\mathcal{P}.$

- [[Population and Sample and Statistical Problem]]

>[!important] Definition
>A statistic $V(X)$ is said to be **first-order ancillary** if its expectation $$\mathbb{E}\left[  V(X) \right]$$ is *independent* from the *population* $\mathcal{P}.$

- [[Independence of Events]]

>[!important] Definition
>A statistic $T(X)$ is said to be **complete** for $\mathcal{P} \in \mathscr{P}$ if and only if, for *any Borel function* $f$, $$(\forall \mathcal{P} \in \mathscr{P})\; \mathbb{E}_{ \mathcal{P} }\left[  f(T) \right] = 0 \quad \implies \quad f(T) = 0 \quad \mathcal{P}\text{-a.s.}.$$ 
>
>$T$ is said to be **boundedly complete** if and only if the previous statement holds for *any **bounded** Borel $f$*.

- [[Measurable Function]]
- [[Borel sigma Field]]



## Explanation

>[!important]
>If $V (X)$ is a *nontrivial ancillary statistic*, then $$\sigma(V (X)) \subset  \sigma(X)$$ is a **nontrivial $\sigma$-field**  that **does not contain any information about $\mathcal{P}$**.

>[!quote]
>if $S(X)$ is a *statistic* and $V(S(X))$ is a **nontrivial ancillary statistic**, it indicates that $$\sigma(S(X))$$ contains a *nontrivial $\sigma$-field* that does *not contain any information about* $\mathcal{P}$ and, hence, the **“data” $S(X)$ may be further reduced.**
>
>-- - [[Mathematical Statistics by Shao]] pp 109

>[!info]
>- A **complete** statistic is **boundedly complete.** 
>- If $T$ is **complete** (or **boundedly complete**) and $$S = \psi(T)$$ for a *measurable* $\psi$, then $S$ is **complete** (or **boundedly complete**).

## Minimal Sufficient

![[Lehmann-Scheffé Theorem#^e0b496]]

- [[Lehmann-Scheffé Theorem]]
- [[Sufficient Statistics]]
- [[Minimal Sufficient Statistics]]


## Example

>[!example]
>A trivial **ancillary statistic** is the **constant statistic** $$V(X) \equiv c \in \mathbb{R}.$$



-----------
##  Recommended Notes and References


- [[Statistics]]
- [[Sufficient Statistics]]
- [[Minimal Sufficient Statistics]]


- [[Mathematical Statistics by Shao]] pp 109
