---
tags:
  - concept
  - math/information_theory
keywords:
  - kl_divergence
  - variational_inference
topics:
  - information_theory
name: Variational Formula for Kullback-Leibler Divergence
date of note: 2024-05-07
---

## Theorem

>[!important]
>**Name**: *Variational Formula* for Kullback-Leibler Divergence

>[!important] Theorem
>If $P$ and $Q$ are *probability measures* on a measurable space $(\Omega, \mathscr{F})$, and $P$ is *absolutely continuous* with respect to $Q$, 
>$$P \ll Q.$$
>Assume that there is a **common dominating** *probability measure* $\lambda$ such that
>$$
>P \ll \lambda, \quad Q \ll \lambda.
>$$ 
>
>Let $f$ be a real-valued *random variable* such that $\mathbb{E}_{Q}\left[ \exp(f) \right]$ exists. Then the following equality holds
>$$
>\begin{align*}
>\log \mathbb{E}_{\mathcal{Q}}\left[ \exp\left(f\right) \right] &= \sup_{P \ll Q}\left\{ \mathbb{E}_{P}\left[f\right] - \mathbb{KL}\left( P \left\|\right. Q \right)  \right\}
\end{align*}
>$$
>
>Further, the **supremum** on the right-hand side is **attained** *if and only if* it holds
>$$
\frac{dP}{dQ} = \frac{dP / d\lambda}{dQ / d\lambda} = \frac{\exp(f)}{\mathbb{E}_{Q}\left[ \exp\left(f\right) \right]}, \quad P\text{-a.s.}  \quad (1)
>$$
>where $dP / d\lambda$ and $dQ / d\lambda$  are *the Radon-Nikodym derivatives* of $P$ and $Q$ with respect to $\lambda$.
>- This theorem is the **Donsker-Varadhan theorem.**

^fd2b28

- [[Kullback-Leibler Divergence]]
- [[Moment Generating Function]]
- [[Radon-Nikodym Derivative]]

- See measure-theoretical proof in [[leeGibbsSamplerCoordinate2022]]

>[!info]
>In practice, we would use the Lebesgue measure for $\lambda$ in $\mathbb{R}^n$ 



>[!info]
>For **centered random variables**, 
>$$
>\begin{align*}
>\log \mathbb{E}_{\mathcal{Q}}\left[ \exp\left(f- \mathbb{E}_{\mathcal{Q}}\left[f\right] \right) \right] &= \sup_{P \ll Q}\left\{ \mathbb{E}_{P}\left[f\right] - \mathbb{E}_{\mathcal{Q}}\left[f\right]  - \mathbb{KL}\left( P \left\|\right. Q \right)  \right\}
\end{align*}
>$$


>[!important]
>The variational theorem provides *the variational representation* of KL divergence
>$$
>\mathbb{KL}\left( P \left\|\right. Q \right) := \sup\left\{\mathbb{E}_{P}\left[f\right] - \log \mathbb{E}_{\mathcal{Q}}\left[ \exp\left(f\right) \right]: f\text{ such that }\exp(f) \in  L^1(\Omega, \mathscr{F}, Q)  \right\}
>$$
>It is called **Donsker–Varadhan representation**.

- [[Variational Formula for f-Divergence]]
## Explanation

>[!important]
>**The variational formula** follows directly from the *strong duality principle* of convex functions. 
>
>Note that $\mathbb{KL}\left( P \left\|\right. Q \right)$ is convex in $P$. 
>
>Thus **the KL divergence** and the **logarithm moment generating function** are *the convex conjugate dual* to each other.
>$$
>\psi_{s\,X, Q} := \log \mathbb{E}_{\mathcal{Q}}\left[ \exp\left(s\,X\right) \right] \longleftrightarrow \mathbb{KL}\left( P \left\|\right. Q \right)
>$$

- [[Convex Conjugate Function]]


>[!info]
>**The variational formula** of relative entropy is the basis for variational inference methods. 
>- [[Variational Auto-Encoder]]
>- [[Expectation-Maximization Algorithm]]

## Gibbs distribution as optimal solution

>[!important] 
>The **optimal probability measure** $P^{*}$ that satisfies the equation (1), which means that $P$ can be represented as 
>$$
dP^{*} = \frac{1}{Z}\exp\left(f\right)\;dQ
>$$
>where the constant $Z = \mathbb{E}_{Q}\left[ \exp\left(f\right) \right]$ is the *normalization factor* or **the partition function**. 
>
>Suppose for some temperature parameter $T$, and energy function $E(x)$
>$$
>f(x) = -\frac{E(x)}{T}.
>$$
>Then optimal measure $P^{*}$ as above is called a **Gibbs measure.** 

- [[Gibbs Measure and Energy-based Model]]
- [[Maximum Entropy Learning]]
- Wikipedia [Gibbs measure](https://en.wikipedia.org/wiki/Gibbs_measure)


## Proof

- See measure-theoretical proof in [[leeGibbsSamplerCoordinate2022]]

>[!info]
>Due to the fact that $P \ll \lambda, \quad Q \ll \lambda$, and   [[Lebesgue-Radon-Nikodym Theorem]], there exists a Radon-Nikodym derivative 
>$$
>p = \frac{dP}{d\lambda}, \quad q = \frac{dQ}{d\lambda},
>$$ 
>unique up to a $\lambda$-null set. The function $p$ and $q$ are both $\lambda$-measurable functions.
>
>Similarly, on the other hand, due to $P \ll Q$, we can find a unique Radon-Nikodym derivative $dP / dQ$ so that the KL divergence is *well-defined and finite*.
>$$
>\mathbb{KL}\left( P \left\|\right. Q \right) = \int \log \left(\frac{dP}{dQ}\right) dP
>$$
>We use the following notion $dP = pd\lambda$, $dQ = q d\lambda$.

>[!info]
>We can then derive the right hand side
>$$
>\begin{align*}
>\mathbb{E}_{P}\left[f\right] - \mathbb{KL}\left( P \left\|\right. Q \right) &= \int f dP - \int \log \left(\frac{dP}{dQ}\right) dP\\
>&= \int f\,p\, d\lambda - \int \log \left(\frac{p\,d\lambda}{q\,d\lambda}\right) p\, d\lambda\\
>&= \int f\,p\, d\lambda - \int \log \left(\frac{p}{q}\right) p\, d\lambda\\
>&= \int \log \left(\frac{e^f\, q}{p}\right)p \,d\lambda
\end{align*}
>$$
>
> By [[Jensen Inequality]], $\phi(x) = \log(x)$ is strictly concave, so 
>$$
>\begin{align*}
>\mathbb{E}_{P}\left[f\right] - \mathbb{KL}\left( P \left\|\right. Q \right) &= \int \log \left(\frac{e^f\, q}{p}\right)p \,d\lambda\\
>&\le \log \left(\int \frac{e^f\, q}{p} p \,d\lambda \right)\\
>&= \log \left(\int e^f\, q \,d\lambda \right)\\
>&= \log \left(\int e^f\, dQ \right)\\
>&= \log \mathbb{E}_{Q}\left[ e^{f} \right]
\end{align*}
>$$
>Note that this inequality holds for all $f$ so that $\exp(f) \in L^1(Q)$ 

>[!info]
>The equality holds if and only if 
>$$
>\frac{e^f\, q}{p} = const.  \implies \frac{p}{q} = \frac{e^f}{const},\quad P-\text{a.s.}
>$$

>[!info]
>So, suppose $k = e^f q / p$, where $k$ is a constant almost surely with respect to $P$. Then we have
>$$
>e^f\,q = k\,p.
>$$
>Taking integral on both sides with respect to measure $\lambda$, we have
>$$
>\mathbb{E}_{Q}\left[ e^f \right] := \int e^f\,q d\lambda = k \int p d\lambda = k.
>$$
>This completes the proof. Q.E.D.



-----------
##  Recommended Notes and References

- [[Radon-Nikodym Derivative]]

- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Elements of Information Theory by Cover]] pp 257, 408
- Donsker, Monroe D.; Varadhan, SR Srinivasa (1983). "Asymptotic evaluation of certain Markov process expectations for large time. IV". _Communications on Pure and Applied Mathematics_. **36** (2): 183–212. [doi](https://en.wikipedia.org/wiki/Doi_(identifier) "Doi (identifier)"):[10.1002/cpa.3160360204](https://doi.org/10.1002%2Fcpa.3160360204).

