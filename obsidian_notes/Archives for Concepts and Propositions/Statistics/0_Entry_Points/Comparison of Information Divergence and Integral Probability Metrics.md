---
tags:
  - entry_point
  - concept
  - math/information_theory
  - statistics/concentration_inequality
  - statistics/estimation
keywords: 
topics:
  - information_theory
name: 
date of note: 2024-06-01
---

## List of Concepts

### Basics

- [[Concepts and Theorems for Information Geometry]]
- [[Concepts and Theorems of Optimal Transport]]
- [[Concepts and Theorems in Information Theory]]

### Information Divergences on Statistical Manifold

- [[Divergence Function on Manifold]]
- [[Kullback-Leibler Divergence]]
- [[f-Divergence]]
- [[alpha-Divergence]]
- [[Renyi Divergence and Renyi Entropy]]
- [[Hellinger Distance between Distributions]]
- [[Jensen-Shannon Divergence]]
- [[Chi-squared Divergence]]
- [[Total Variation between Measures]]

### Integral Probability Metric and Wasserstein Distance

- [[Integral Probability Metric between Probability Measures]]
- [[Maximum Mean Discrepancy between Probability Measures via RKHS]]
- [[Kernel Mean Embedding of Distribution]]
- [[Wasserstein Distance]]
- [[Wasserstein Space]]

## Comparison

![[integral_prob_f_diverg.png]]

|                                            | **information divergence**                                                                                                                                                                                                                                                                                                                                             | **integral probability metric**                                                                                                                                                                                                                                                                                                                                                                                       |
| ------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Definition                                 | $$\mathbb{D}_{f}\left( P \left\|\right. Q \right) = \int_{\Omega} f\left( \dfrac{dP}{dQ} \right) dQ $$                                                                                                                                                                                                                                                                 | $$D_{\mathcal{F}}\left( P , Q \right) := \sup_{f\in \mathcal{F}} \left\lvert \int f\,dP - \int f\,dQ \right\rvert$$                                                                                                                                                                                                                                                                                                   |
| Condition                                  | - $f: [0, +\infty) \to (-\infty, +\infty]$ as a *convex* function <br>- $f(x) < +\infty$ for $x >0$; <br>- $f(1) = 0$; <br>- $f(0)= \lim_{ x \to 0^+ }f(x)$                                                                                                                                                                                                            | - $\mathcal{F}$ a *bounded measurable function space*                                                                                                                                                                                                                                                                                                                                                                 |
| Example                                    | - [[f-Divergence]]<br>- $f:= x\log x$ [[Kullback-Leibler Divergence]]<br><br>- [[alpha-Divergence]] <br><br>- $f:= (x-1)^2$  [[Chi-squared Divergence]]<br><br>-$f:= (\sqrt{ x }-1)^2$  [[Hellinger Distance between Distributions]] <br><br>-[[Jensen-Shannon Divergence]]                                                                                            | - $\mathcal{F}$ *bounded real-value measurable*  [[Integral Probability Metric between Probability Measures]]<br><br><br>- $\mathcal{F}$ *unit ball in RKHS* [[Maximum Mean Discrepancy between Probability Measures via RKHS]]<br><br><br>- $\mathcal{F}$ *Lipschitz contraction function* [[Wasserstein Distance]]                                                                                                  |
| Overlap                                    | [[Total Variation between Measures]]                                                                                                                                                                                                                                                                                                                                   | [[Total Variation between Measures]]                                                                                                                                                                                                                                                                                                                                                                                  |
| Comparison of p.d.f                        | by **density ratio** $$\frac{dP}{dQ}$$                                                                                                                                                                                                                                                                                                                                 | by **mean difference** (*functional*) $$\int \cdot (dP - dQ)$$                                                                                                                                                                                                                                                                                                                                                        |
| Role of $P, Q$                             | as **probability measure**<br>- [[Radon Measure]]                                                                                                                                                                                                                                                                                                                      | as **bounded linear functional** via expectation<br>- [[Bounded Linear Functional]]                                                                                                                                                                                                                                                                                                                                   |
| Support of Measure **Overlap**             | $\checkmark$<br><br>$P$ and $Q$ support **must overlap**, in fact $$P \ll Q$$                                                                                                                                                                                                                                                                                          | $\times$<br><br>**No requirement** on support of $P$, and $Q$                                                                                                                                                                                                                                                                                                                                                         |
| **Characteristic** of Behavior             | **mode seeking**<br>- trapped in unimodal local optima                                                                                                                                                                                                                                                                                                                 | **mode covering**<br>- covered all the modes                                                                                                                                                                                                                                                                                                                                                                          |
| **Nonnegative**                            | $$\mathbb{D}_{f}\left( P \left\|\right. Q \right) \ge 0$$                                                                                                                                                                                                                                                                                                              | $$D_{\mathcal{F}}\left( P , Q \right) \ge 0$$                                                                                                                                                                                                                                                                                                                                                                         |
| **Positive Definite**                      | $$\mathbb{D}_{f}\left( P \left\|\right. Q \right) = 0$$ if and only if $P = Q$                                                                                                                                                                                                                                                                                         | $$D_{\mathcal{F}}\left( P , Q \right) = 0$$ if and only if $P = Q$.                                                                                                                                                                                                                                                                                                                                                   |
| **Symmetric**                              | $\times$ in general, <br>except:<br>- [[Hellinger Distance between Distributions]] <br>-[[Jensen-Shannon Divergence]]                                                                                                                                                                                                                                                  | $\checkmark$                                                                                                                                                                                                                                                                                                                                                                                                          |
| **Triangle Inequality**                    | $\times$ in general, <br>except:<br>- [[Hellinger Distance between Distributions]]                                                                                                                                                                                                                                                                                     | $\checkmark$                                                                                                                                                                                                                                                                                                                                                                                                          |
| **Metric**                                 | $\times$ in general, <br>except:<br>- [[Hellinger Distance between Distributions]]                                                                                                                                                                                                                                                                                     | $\checkmark$                                                                                                                                                                                                                                                                                                                                                                                                          |
| **Induced Structure**                      | **Smooth Statistical Manifold** $$\mathcal{S} \subset \mathcal{P}(\mathcal{X})$$<br>                                                                                                                                                                                                                                                                                   | - *Space of bounded signed measure* $$\mathcal{M}_{+}$$ for [[Integral Probability Metric between Probability Measures]]<br>- **Reproducing Kernel Hilbert Space** $$\mathcal{P}(\mathcal{X}) \xhookrightarrow{} \mathcal{H}$$ for [[Maximum Mean Discrepancy between Probability Measures via RKHS]]<br><br>- **Wasserstein Space** $$\mathbb{W}_{1} \subset \mathcal{P}(\mathcal{X})$$ for [[Wasserstein Distance]] |
| **Geometry**                               | **Riemannian metric**<br>- $g:=I_{i,j}$ **Fisher metric**<br>- $\nabla^{(\alpha)}$ **$\alpha$-connection**                                                                                                                                                                                                                                                             | - **Normed vector space** for IPM<br>- **Hilbert Space** for MMD<br>- **metric space** for Wasserstein distance                                                                                                                                                                                                                                                                                                       |
| Global vs. Local                           | **Local Metric** $$\left\langle  \cdot\,,\,\cdot    \right\rangle_{p}$$                                                                                                                                                                                                                                                                                                | *Global Metric* $$\lVert P - Q \rVert_{\mathcal{F}} $$                                                                                                                                                                                                                                                                                                                                                                |
| **Topology**                               | Local *Inner Product Space*<br>- *Metric topology* for Helinger distance                                                                                                                                                                                                                                                                                               | - *Norm Topolgy*<br>- *Inner Product Space*<br>- *Metric Topology*                                                                                                                                                                                                                                                                                                                                                    |
| Field                                      | *Riemannian Manifold*                                                                                                                                                                                                                                                                                                                                                  | *Functional Analysis* and *Optimal Transport*                                                                                                                                                                                                                                                                                                                                                                         |
| Application (**Concentration Inequality**) | - [[Information Inequalities]]<br>- *Asympototic Analysis*                                                                                                                                                                                                                                                                                                             | - [[Convergence in Distribution]]<br>- [[Weak Topology of Banach Space]]<br>- [[Glivenko-Cantelli Class]]<br>- [[Transportation Method]]<br>- [[Concepts and Inequalities for Empirical Process]]<br>- [[Concepts and Theorems in Statistical Learning Theory]]<br>                                                                                                                                                   |
| Application (**Machine Learning**)         | - **explicit probabilistic model**<br>- [[Maximum Likelihood Estimation]]<br>- [[Maximum Entropy Learning]]<br>- [[Evidence Lower Bound]]<br>- [[Expectation-Maximization Algorithm]]<br>- [[Variational Auto-Encoder or VAE]]<br>- [[Principle of Learning by Comparison for Implicit Generative Models]]<br>- [[Generative Adversarial Network]]<br>- [[Normalizing Flows]] | - **implicit probabilistic model**<br>- [[Optimal Transport in Space of Measures]]<br>- [[k-Means Clustering]]<br>- [[Parzen Kernel Density Estimation]]<br>- [[Principle of Learning by Comparison for Implicit Generative Models]]<br>- [[Generative Adversarial Network]]<br>- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]                                                                  |
| Application (**Applied Math**)             | - [[Concepts and Theorems in Information Theory]]<br>- *Information Theory*<br>- *Digital Communication*<br>- [[Importance Sampling]]                                                                                                                                                                                                                                  | - [[Gradient Flow in Wasserstein Space]]<br>- [[Stochastic Differential Equations]]<br>- [[Heat Equation and Fokker–Planck Equation via Wasserstein Distance]]<br>- [[Langevin Dynamics and Langevin Sampling]]                                                                                                                                                                                                       |
|                                            |                                                                                                                                                                                                                                                                                                                                                                        |                                                                                                                                                                                                                                                                                                                                                                                                                       |


- [[Statistical Manifold as Parametric Family]]
- [[Reproducing Kernel Hilbert Space]]
- [[Wasserstein Space]]
- [[Fisher Metric or Information Metric of Statistical Manifold]]
- [[alpha-Connection on Statistical Manifold]]
- [[Space of Bounded Signed Measures]]

## Explanation

![[divergence_vs_ipm.png]]


>[!quote]
>One often stated downside of using **divergences** that rely on **density ratios** (such as *$f$-divergences*) is their poor behavior when the distributions $p^{*}$ and $q_{\theta}$ **do not have overlapping support**. 
>- For non-overlapping support, the density ratio $$p^{*} / q_{\theta}$$ will be $\infty$ in the parts of the space where $p^{*}(x) > 0$ but $q_{\theta}(x) = 0$, and $0$ otherwise. 
>- In that case, the $$\mathbb{KL}\left( p^{*} \left\|\right. q_{\theta} \right) = \infty$$ and the $$\mathbb{D}_{JSD}\left( p^{*} \left\|\right. q_{\theta} \right) = \log(2)$$ regardless of the value of $\theta$. 
>- Thus $f$-divergences **cannot** *distinguish* between different model distributions when they *do not have overlapping support* with the data distribution, as visualized in Figure 26.4a. 
>
>This is in contrast with **difference** *based methods* such as **IPMs** such as the **Wasserstein distance** and the **MMD**, 
>- which have *smoothness requirements* built in the definition of the method, by **constraining the norm of the critic** (Equations (26.29) and (26.34)). 
>- We can see the effect of these constraints in Figure 26.3: both the *Wasserstein distance* and the *MMD* provide useful signal in the case of **distributions with non-overlapping support.** 
>
>...  while the case of non-overlapping support provides an important theoretical difference between *IPMs* and *$f$-divergences*, it is **less significant in practice** since bounds on $f$-divergences or class probability estimation are used with *smooth critics* to **approximate** the underlying divergence.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 893 - 894

![[mode_seeking_covering_diverg_ipm.png]]

- Li, C. T., Zhang, J., & Farnia, F. (2024). On Convergence in Wasserstein Distance and f-divergence Minimization Problems. _Proceedings of The 27th International Conference on Artificial Intelligence and Statistics_, 2062–2070. [https://proceedings.mlr.press/v238/ting-li24a.html](https://proceedings.mlr.press/v238/ting-li24a.html)




-----------
##  Recommended Notes and References






- [[Elements of Information Theory by Cover]]
- [[Information Inequalities]]
- [[Concepts and Theorems of Optimal Transport]]
- [[Transportation Method]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]

- Li, C. T., Zhang, J., & Farnia, F. (2024, April). On Convergence in Wasserstein Distance and f-divergence Minimization Problems. In _International Conference on Artificial Intelligence and Statistics_ (pp. 2062-2070). PMLR.