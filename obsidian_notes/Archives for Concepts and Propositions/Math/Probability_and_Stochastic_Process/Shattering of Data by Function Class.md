---
tags:
  - concept
  - math/stochastic_process
  - machine_learning/theory
  - math/functional_analysis
  - statistics/concentration_inequality
keywords:
  - shattering_function_class
topics:
  - stochastic_process
  - machine_learning_theory
name: Shattering of Function Class
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Shattering of Function Class

![[Restriction of Function Class to Data#^60c89d]]

- [[Restriction of Function Class to Data]]


>[!important] Definition
>A *function class* $\mathcal{F}$ **shatters** *a finite set* $\mathcal{D} \subset \mathcal{X}$ if *the restriction* of $\mathcal{F}$ to $\mathcal{D}$}} is the set of *all functions* from $\mathcal{D}$ to $\set{0,1}$. 
>
>That is, 
>$$
> \begin{align*}
> |\mathcal{F}_{\mathcal{D}}| &= 2^{|\mathcal{D}|}.
> \end{align*}
>$$ 
>or
>$$
>\mathcal{F}_{\mathcal{D}} = \{0, 1\}^{\mathcal{D}}
>$$

^0ab3b0

- [[Restriction of Function Class to Data]]

## Explanation

### Functional Analysis Perspective

>[!important]
>If $\mathcal{F}$ shatters  $\mathcal{D}$, the **linear operator** $I_{\mathcal{D}}: \mathcal{F} \to \{ 0,1 \}^{\mathcal{D}}$  defined by 
>$$
> I_{\mathcal{D}}: f \mapsto (f(x_{1}) \,{,}\ldots{,}\, f(x_{n}))
>$$
>is **surjective**.

- [[Surjective Function]]

### Classification Perspective

>[!important]
>From **classification perspective**, if $\mathcal{F}$ shatters $\mathcal{D}$, it means that for the given data $\mathcal{D}$, *no matter what possible outcome*, we can **always find a classifier** that **perfectly predict** the outcome.
>
>In other word, we *cannot tell* if the model can **generalize the prediction** on the unknown data based on existing dataset $\mathcal{D}$
>
>It means that
>- the data is *too easy*, 
>- the model class is *too large*
>
>The model has **overfited** the data.

>[!important]
>In machine learning, we say that
>>[!quote]
>>A system that can *__perfectly predict all possible outcomes__*  **cannot be used in prediction**. Since no one would be able to tell what prediction it would give in a new sample.  


-----------
##  Recommended Notes and References

- [[Restriction of Function Class to Data]]
- [[VC Dimension]]

- [[Shattering of Set by Set Family]]

- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Bounded Difference Inequality]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]

