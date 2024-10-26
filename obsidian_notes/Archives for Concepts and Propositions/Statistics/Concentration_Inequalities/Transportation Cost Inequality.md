---
tags:
  - concept
  - statistics/concentration_inequality
  - math/information_theory
  - math/optimal_transport
keywords:
  - transportation_cost_inequality
topics:
  - information_theory
  - optimal_transport
name: Transportation Cost Inequality
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Transportation Cost Inequality

>[!important] Proposition (Transportation Lemma)
>Let $X$ be a real-valued integrable random variable. Let $\phi$ be a **convex** and **continuously differentiable** function on a (possibly unbounded) interval $[0, b)$ and assume that $\phi(0) = \phi'(0) = 0$. 
>
>Define, for every $x \ge 0$, the **Legendre transform** $$\phi^{*}(x) = \sup_{\lambda \in (0,b)}(\lambda x - \phi(\lambda)),$$ and let, for every $t \ge 0$,  $$\phi^{*-1}(t) = \inf\{x \ge 0: \phi^{*}(x) > t\},$$ i.e. the **the generalized inverse** of $\phi^{*}$. 
>
>Then the following two statements are **equivalent**:
>
>- for every $\lambda \in (0,b)$,
>$$
> \begin{align*}
> \psi_{X - \mathbb{E}\left[X\right] }(\lambda) &\le \phi(\lambda)
> \end{align*}
>$$  
>where $\psi_{X}(\lambda):= \log \mathbb{E}_{\mathcal{P}}\left[e^{\lambda X}\right]$ is the **logarithm of moment generating function**;
>- for any probability measure $\mathcal{Q}$ *absolutely continuous* with respect to $\mathcal{P}$ such that $$\mathbb{KL}\left(\mathcal{Q}\left\|\right.\mathcal{P}\right) < \infty,$$ and
>$$  
> \begin{align}
>  \mathbb{E}_{\mathcal{Q}}\left[X\right] - \mathbb{E}_{\mathcal{P}}\left[X\right] &\le \phi^{*-1}\left(\mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}  \right)\right). 
> \end{align} 
>$$ 

^8653e5

>[!important] Proposition
> In particular, given $\nu > 0$, $X$ follows a **sub-Gaussian distribution**, i.e.
>$$ 
> \begin{align*}
> \psi_{X - \mathbb{E}_{\mathcal{P}}\left[X\right] }(\lambda) &\le \frac{\nu\lambda^2}{2}
> \end{align*}
>$$  
>for every $\lambda >0$  **if and only if** for any probability measure $\mathcal{Q}$ *absolutely continuous* with respect to $\mathcal{P}$ and such that $$\mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}  \right) < \infty,$$  and
>$$
> \begin{align}
> \mathbb{E}_{\mathcal{Q}}\left[X\right] - \mathbb{E}_{\mathcal{P}}\left[X\right] &\le \sqrt{2\nu \mathbb{KL}\left( \mathcal{Q} \left\|\right.  \mathcal{P} \right)  }. 
> \end{align}
>$$ 

^8d0c96

- [[Variational Formula for Kullback-Leibler Divergence]]
- [[Kullback-Leibler Divergence]]

- [[Moment Generating Function]]
- [[Legendre Transform]]
- [[Sub-Gaussian Random Variable]]

>[!important] Definition
>Let $(\mathcal{X}, d)$ be a **metric space** with metric $d$,  and $(\mathcal{X}, \mathscr{B})$ be a *measurable space*, where $\mathscr{B}$ is the Borel $\sigma$-algebra induced by metric $d$.
>
>The *probability measure* $\mathcal{P}$ on $\mathscr{B}$ is said to satisfy a **$d$-transportation cost inequality** with *parameter* $\nu > 0$ if
>$$
> \begin{align}
> \mathcal{W}_{1,d}(\mathcal{Q}, \mathcal{P}) &\le \sqrt{2\nu \mathbb{KL}\left( \mathcal{Q} \left\|\right.  \mathcal{P} \right)  } 
> \end{align}
>$$  
>for *all probability measure* $\mathcal{Q} \ll \mathcal{P}$ on $\mathscr{B}$.
> 

^4642e4

## Explanation

>[!info]
>The inequality above are called **information inequality** in [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]] due to the role of **Kullback-Leibler Divergence** in information theory. 

- [[Kullback-Leibler Divergence]]


>[!info]
>By [[Variational Representation of Wasserstein Distance]], the **Wasserstein-1 distance** can be represented as
>$$
>\mathcal{W}_{1}(\mathcal{Q}, \mathcal{P}) = \sup_{X \in \text{Lip}_1}\left\{\mathbb{E}_{\mathcal{Q}}\left[X\right] - \mathbb{E}_{\mathcal{P}}\left[X\right]  \right\}. 
>$$
>
>The inequality for **sub-Gaussian distribution** can be rewritten as 
>$$
>\mathcal{W}_{1}(\mathcal{Q}, \mathcal{P}) \le \sqrt{2\nu \mathbb{KL}\left( \mathcal{Q} \left\|\right.  \mathcal{P} \right)  }.
>$$
>Hence comes the origin of the name of "*transportation cost*".

- [[Variational Representation of Wasserstein Distance]]

## Proof

>[!info]
>Based on [[Variational Formula for Kullback-Leibler Divergence]],
>$$
>\begin{align*}
>\log \mathbb{E}_{ \mathcal{P} }\left[ \exp \left(f(X)\right) \right] = \sup_{\mathcal{Q}\ll \mathcal{P}}\left\{ \mathbb{E}_{ \mathcal{Q} }\left[  f(X) \right] - \mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}  \right) \right\} 
\end{align*}
>$$

>[!info]
>$$
>\begin{align*}
>\psi_{X-\mathbb{E}_{\mathcal{P}}\left[X\right]}(\lambda) &:=  \log \mathbb{E}_{ \mathcal{P} }\left[ \exp \left(\lambda (X- \mathbb{E}_{\mathcal{P}}\left[X\right])\right) \right]\\
>&= \log \mathbb{E}_{ \mathcal{P} }\left[ \exp \left(\lambda X)\right) \right] - \lambda \mathbb{E}_{\mathcal{P}}\left[X\right]\\ 
>&= \lambda \sup_{\mathcal{Q}\ll \mathcal{P}}\left\{ \left(\mathbb{E}_{ \mathcal{Q} }\left[ X  \right] -  \mathbb{E}_{\mathcal{P}}\left[X\right]\right) - \mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}  \right) \right\} \\
>&\ge  \lambda \mathbb{E}_{ \mathcal{Q} }\left[ X  \right] -  \lambda \mathbb{E}_{\mathcal{P}}\left[X\right] - \mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}  \right)\\
> \implies \mathbb{E}_{ \mathcal{Q} }\left[  X \right] - \mathbb{E}_{ \mathcal{P} }\left[  X \right] &\le \frac{\psi_{X-\mathbb{E}_{\mathcal{P}}\left[X\right]}(\lambda)  + \mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}  \right)}{\lambda}
\end{align*}
>$$
>Taking infimum on the right hand side with $\lambda \in (0, b)$, we have
>$$
>\begin{align*}
>\mathbb{E}_{ \mathcal{Q} }\left[  X \right] - \mathbb{E}_{ \mathcal{P} }\left[  X \right] &\le \inf_{\lambda \in (0,b)} \frac{\psi_{X-\mathbb{E}_{\mathcal{P}}\left[X\right]}(\lambda)  + \mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}  \right)}{\lambda} \\
>&\le \inf_{\lambda \in (0,b)} \frac{ \phi(\lambda) + \mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}  \right)}{\lambda}
\end{align*}
>$$

>[!info]
>In  other words, the condition (1) holds if and only if for any $Q\ll P$
>$$
>\mathbb{E}_{ \mathcal{Q} }\left[  X \right] - \mathbb{E}_{ \mathcal{P} }\left[  X \right] \le  \inf_{\lambda \in (0,b)} \frac{ \phi(\lambda) + \mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}  \right)}{\lambda}
>$$


>[!important]
>From [[Legendre Transform#Property]], we see that for a **convex, continuous differentiable function** $\phi$ with $\phi(0) = \phi'(0) = 0$, 
>$$
>\inf_{\lambda \in (0,b)} \frac{\phi(\lambda) + t}{\lambda} = (\phi^{*})^{-1}(t)
>$$


>[!info]
>Thus the condition (1) holds if and only if for any $Q\ll P$
>$$
>\begin{align*}
>  \mathbb{E}_{ \mathcal{Q} }\left[  X \right] - \mathbb{E}_{ \mathcal{P} }\left[  X \right] &\le (\phi^{*})^{-1}\left( \mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}  \right) \right)
\end{align*}
>$$
>Q.E.D.


## Hamming Metric Space

- [[Transportation Cost Inequality in Hamming Metric Space]]






-----------
##  Recommended Notes and References


- [[Variational Representation of Wasserstein Distance]]
- [[Variational Formula for Kullback-Leibler Divergence]]

- [[Wasserstein Distance]]
- [[Kullback-Leibler Divergence]]
- [[Moment Generating Function]]
- [[Legendre Transform]]

- [[Sub-Gaussian Random Variable]]


- [[Optimal Transport Old and New by Villani]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Elements of Information Theory by Cover]]