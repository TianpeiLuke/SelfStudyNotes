---
tags:
  - concept
  - math/measure_theory
  - math/real_analysis
  - math/functional_analysis
keywords:
  - essential_supremum
  - essential_infimum
topics:
  - functional_analysis
  - measure_theory
  - real_analysis
name: Essential Supremum and Essential Infimum
date of note: 2024-06-20
---

## Concept Definition

>[!important]
>**Name**: Essential Supremum and Essential Infimum

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F},\mu)$ be a measure space and $f: \mathcal{X} \to \mathbb{R}$ is a *measurable function*.
>
>The **essential supremum** of *function* $f$ is characterized by the following property:
>- $$f(x) \le \text{ess }\sup_{\mathcal{X}} f \le \infty, \quad \forall x \in \mathcal{X}, \quad \mu\text{-a.e.}$$
>- If for some $a \in \mathbb{R}\cup \left\{ + \infty \right\}$, we have $$f(x) \le a, \quad \mu\text{-a.e.}$$ then $$\text{ess }\sup_{\mathcal{X}}f \le a.$$

- [[Bounded Function and Space of Bounded Functions]]
- [[Measurable Function]]
- [[Measure Space and Countably Additive Measure]]
- [[Pointwise Almost Everywhere Convergence]]

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F},\mu)$ be a measure space and $f: \mathcal{X} \to \mathbb{R}$ is a *measurable function*.
>
>The **essential infimum** of *function* $f$ is characterized by the following property:
>- $$f(x) \ge \text{ess }\inf_{\mathcal{X}} f \ge -\infty, \quad \forall x \in \mathcal{X}, \quad \mu\text{-a.e.}$$
>- If for some $a \in \mathbb{R}\cup \left\{ - \infty \right\}$, we have $$f(x) \ge a, \quad \mu\text{-a.e.}$$ then $$\text{ess }\inf_{\mathcal{X}}f \ge a.$$

### Set Theoretical Definition

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F},\mu)$ be a measure space and $f: \mathcal{X} \to \mathbb{R}$ is a *measurable function*.
>
>The **essential supremum** of *function* $f$ is the *infimum* of *essential upper bounds*
>$$
>\text{ess }\sup_{\mathcal{X}}f  := \inf\left\{ a\in \mathbb{R}: \mu\left(f^{-1}(a, \infty)\right) = 0 \right\}
>$$
>
>And the **essential infimum** of *function* $f$ is the *supremum* of *essential lower bounds*
>$$
>\text{ess }\inf_{\mathcal{X}}f  := \sup\left\{ b\in \mathbb{R}: \mu\left(f^{-1}(-\infty, b)\right) = 0 \right\}
>$$


## Explanation



## Property

>[!important] Proposition
>If $\mu(\mathcal{X}) > 0$, then
>$$
>\inf_{\mathcal{X}} f \le \text{ess }\inf_{\mathcal{X}}f \le \text{ess }\sup_{\mathcal{X}}f \le \sup_{\mathcal{X}} f
>$$



-----------
##  Recommended Notes and References

- [[Lp Space]]
- [[L-infinite Space]]
- [[Measurable Function]]
- [[Measure Space and Countably Additive Measure]]

- [[Supremum and Infimum of Sets]]
- [[Bounded Function and Space of Bounded Functions]]


- [[Real Analysis by Royden]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Functional Analysis by Reed]]