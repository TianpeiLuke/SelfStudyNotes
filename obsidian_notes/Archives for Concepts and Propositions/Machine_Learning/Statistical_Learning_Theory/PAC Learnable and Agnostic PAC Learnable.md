---
tags:
  - concept
  - machine_learning/theory
keywords:
  - Probably_Approximately_Correct
topics:
  - machine_learning_theory
name: PAC Learnable
date of note: 2024-04-18
---

## Concept Definition

>[!important]
>**Name**: Probably Approximately Correct (PAC) Learning

![[Empirical Risk Minimization#^a84128]]

![[Empirical Risk Minimization#^c9ebc0]]


### Probably Approximately Correct (PAC) Learning, Realizable Case

>[!important] Definition
> - Assume that **the realizability assumption** under **non-agnostic setting** holds. 
>   
>A *hypothesis class* $\mathcal H$  is said to be **Probably Approximately Correct**-*learnable* i.e. **PAC-learable**,  if there exists an *algorithm* $\mathcal A$ and a **polynomial function** $\text{poly}(\cdot, \cdot, \cdot)$  such that 
> - for any $\epsilon > 0$ and any $\delta > 0$, 
> - for **all distributions** $\mathcal{P}$ on $\mathcal{X}$ and 
> - for **any target concept** $l \in \mathcal{C}$,  
>
>the following holds when the **sample size** $n \ge n_{\mathcal{H}}(\epsilon, \delta):= \text{poly}(1/\epsilon, 1/\delta, \text{size}(l)):$
> $$
> \mathcal{P}\left\{L_{\mathcal{P}, l}(\mathcal{A}(\mathcal{D}_n))  \le \epsilon\right\} \ge  1 - \delta. 
> $$
> 
>- If $\mathcal{A}$ further runs in $$n_{\mathcal{H}} := \text{poly}(1/\epsilon, 1/\delta, \text{size}(l)),$$ then $\mathcal{H}$ is said to be **efficiently PAC-learnable**. 
>- The *minimal number* of $n_{\mathcal{H}}$ satisfying above inequality is called the **sample complexity** of *learning* $\mathcal{H}$.
>- When such an algorithm $\mathcal{A}$ exists, it is called a **PAC-learning algorithm** *for* $\mathcal{H}$.

^500325

- [[Realizability Assumption for Empirical Risk Minimization]]
- [[Empirical Risk Minimization]]

### Probably Approximately Correct (PAC) Learning, Agnostic Case

![[Empirical Risk Minimization#^0c98ce]]


![[Empirical Risk Minimization#^cf1946]]


>[!important] Definition
> - Assume that **the agnostic setting** holds. 
>   
>A *hypothesis class* $\mathcal H$  is said to be **agnostic Probably Approximately Correct**-*learnable* i.e. **agnostic PAC-learable**,  if there exists an *algorithm* $\mathcal A$ and a **polynomial function** $\text{poly}(\cdot, \cdot)$  such that 
> - for any $\epsilon > 0$ and any $\delta > 0$, 
> - for **all distributions** $\mathcal{P}$ on $\mathcal{X} \times \mathcal{Y}$ 
>
>the following holds when the **sample size** $n \ge n_{\mathcal{H}}(\epsilon, \delta):= \text{poly}(1/\epsilon, 1/\delta):$
> $$
> \mathcal{P}\left\{L_{\mathcal{P}}(\mathcal{A}(\mathcal{D}_n))  \le \inf_{h\in \mathcal{H}}L_{\mathcal{P}}(h) +  \epsilon \right\} \ge  1 - \delta. 
> $$
> 
>- If $\mathcal{A}$ further runs in $$n_{\mathcal{H}} := \text{poly}(1/\epsilon, 1/\delta),$$ then $\mathcal{H}$ is said to be **efficiently agnostic PAC-learnable**. 
>- The *minimal number* of $n_{\mathcal{H}}$ satisfying above inequality is called the **sample complexity** of *learning* $\mathcal{H}$.
>- When such an algorithm $\mathcal{A}$ exists, it is called a **agnostic PAC-learning algorithm** *for* $\mathcal{H}$.

^a09a6f



## Explanation

>[!important]
>A *hypothesis class* $\mathcal H$ is *PAC Learnable* means that there exists an algorithm with **sample complexity** in polynomial with respect to the reciprocal of *accuracy* $1/\epsilon$, the reciprocal of *error rate* $1/\delta$, *dimension* $d$, and *size* of concept set

>[!info]
>- **Probably**, i.e. *with small (but may be non-zero) probability* $\delta$
>- **Approximately**, i.e. *with small error* $\epsilon$
>- **Correct**, measured by *$0$-$1$ error* (*Hamming distance*)

- [[Weighted Hamming Distance]]

>[!info]
>The definition of PAC learnable is in the format of a **concentration inequality**.

- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]


>[!important]
>- Under the **non-agnostic PAC learning**, the *learner* is required to achieve *a small error* in **absolute terms** (i.e. *close to zero* in generalization error)
>- Under the **agnostic PAC learning**, a learner can still declare success if its error is not much larger than **the best error** *achievable* by a predictor *from the class $\mathcal{H}$.* 

## Uniform Consistency

>[!important]
>Unlike *the asymptotic analysis* in statistics such as the definition of **consistency**, PAC learnable is **much stronger**. 
>
>In fact, a hypothesis class $\mathcal{H}$ is guaranteed to be *PAC learnable* if it is **uniform consistent**   for all $h\in \mathcal{H}$, i.e. a **Glivenko-Cantelli class** is PAC learnable.
>$$
>\text{Glivenko-Cantelli class } \implies \text{ (agnostic) PAC Learnable} 
>$$
>
>
>Besides consistency, the PAC learnable concept is **non-asymptotic**, meaning that it is *required* to show that there *exists a __sample efficient solution__* (**polynomial**) that achieve the desired bound. 

- [[Consistency of Point Estimator]]
- [[Glivenko-Cantelli Class]]
- [[Glivenko-Cantelli Theorem]]

>[!info]
>For **binary classification**, Glivenko-Cantelli class is a **sufficient** and **necessary condition**:
>$$
>\text{Glivenko-Cantelli class } \iff \text{ (agnostic) PAC Learnable} 
>$$
>
>For other classification, Glivenko-Cantelli class is a **sufficient condition** only.

## Weak PAC Learnable 

- [[Weak PAC Learnablity]]


-----------
##  Recommended Notes and References

- [[Hoeffding Inequality]]
- [[Bounded Difference Inequality]]

- [[Empirical Risk Minimization]]
- [[Supervised Learning and Unsupervised Learning]]


- [[Foundations of Machine Learning by Mohri]] pp 11 - 15, 24
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Boosting Foundations and Algorithms by Schapire]] pp 45
- [[Probabilistic Graphical Models by Koller]]
- [[Artificial Intelligence Modern Approach by Russell]] pp 714

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/statistical_learning_theory)