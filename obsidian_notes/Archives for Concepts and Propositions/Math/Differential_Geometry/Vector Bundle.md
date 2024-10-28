---
tags:
  - concept
  - math/differential_geometry
keywords:
  - vector_bundle
topics:
  - differential_geometry
name: Vector Bundle
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Vector Bundle

>[!important] Definition
>Let $M$ be a *topological space*. 
>
>A **(real) vector bundle** of **rank $k$** **over** $M$ is a *topological space* $E$ *together with* a **surjective continuous map** $\pi: E \rightarrow M$ satisfying the following conditions:
> 
> - For each $p \in M$, the **fiber** $$E_{p} = \pi^{-1}(p)$$ over $p$ is *endowed* with the structure of a **$k$-dimensional real vector space**.
> - For each $p \in M$, there *exist a neighborhood* $U$ of $p$ in $M$ and a **homeomorphism** $$\Phi: \pi^{-1}(U) \rightarrow U \times \mathbb{R}^k,$$ called a **local trivialization** of $E$ over $U$, satisfying the following conditions:
> 	-  $$\pi_{U}\circ \Phi = \pi$$ where $\pi_U: U \times  \mathbb{R}^k \rightarrow U$ is the **projection**;
> 	-  for each $q \in U$, the **restriction** of $\Phi$ to $E_q$ is a *vector space* **isomorphism** from $E_q$ to $\set{q} \times \mathbb{R}^k$. That is 
> 	  $$
> 	  E_{q} \simeq  \set{q} \times \mathbb{R}^k \simeq \mathbb{R}^k
> 	   $$
> 
> The space $E$ is called **the total space of the bundle**, $M$ is called its **base**, and $\pi$ is its **projection**. 

- [[Topology of Set]]
- [[Homeomorphism]]
- [[Vector Space over a Field]]
- [[Linear Isomorphism]]
- [[Surjective Function]]
- [[Continuous Function]]

![[local_trivialization.png]]

>[!important]
>The **rank** of a *vector bundle* is the **dimension** of *vector space* $\pi^{-1}(p)$ associated with each point $p$.

>[!important]
>A **rank-1 vector bundle** is often called **a (real) line bundle**. 

>[!important]
>**Complex vector bundles** are defined similarly, with "real vector space" replaced by *"complex vector space"* and $\mathbb{R}^k$ replaced by $\mathbb{C}^k$ in the definition. 


## Explanation

>[!info]
>**Vector bundle** $E$ is a **generalization and abstraction** of *the tangent bundle* $$TM = \bigsqcup_{p\in M}T_{p}M.$$ 
>
>Like the tangle bundle,  the **natural coordinates** constructed on a vector bundle make it look,  *locally*, like *the Cartesian product* of  *an open subset* of $M$ with $\mathbb{R}^n$. 


## Transition Between Local Trivialization

>[!important] Lemma
>Let $\pi: E \rightarrow M$ be a **smooth vector bundle** of rank $k$ over $M$. Suppose $$\Phi: \pi^{-1}(U) \rightarrow U \times \mathbb{R}^{k}$$ and $$\Psi: \pi^{-1}(V) \rightarrow V \times \mathbb{R}^{k}$$ are two **smooth local trivializations** of $E$ with $U \cap V \neq \emptyset$. 
>
>There exists a **smooth map** $$\tau:  U \cap V \rightarrow GL(k, \mathbb{R})$$
> such that the *composition* $$\Phi \circ \Psi^{-1}: (U \cap V )\times \mathbb{R}^k \rightarrow (U \cap V) \times \mathbb{R}^k$$ has the form
>$$ 
> \begin{align*}
> \Phi \circ \Psi^{-1}(p,v)  &=  (p,  \, \tau(p)v),
> \end{align*}
>$$  
>where $\tau(p)v$ denotes the usual action of the $k\times k$ **matrix** $\tau(p)$ on the vector $v \in \mathbb{R}^k$.


![[transition_btw_two_smooth_local_trivializations.png]]


>[!important] Definition
>The *smooth map* $$\tau:  U \cap V \rightarrow GL(k, \mathbb{R})$$ described in this lemma is called the **transition function** between the *local trivializations* $\Phi$ and $\Psi$. 

>[!info]
>For example, if $M$ is a smooth manifold and $\Phi$ and $\Psi$ are the *local trivializations* of **tangent bundle** $TM$ associated with *two different smooth charts*, then the **transition function** between them is **the Jacobian matrix** of the *coordinate transition map*.


## Chart in Vector Bundle

>[!info]
>Like the tangent bundle, **vector bundles** are often most easily described by *giving* **a collection of vector spaces**, *one for each point* of the base manifold. 


>[!info]
>The next lemma shows that in order to **construct a smooth vector bundle**, it is **sufficient to construct the local trivializations**, as long as they **overlap with smooth transition.**


>[!important] Lemma
>
> Let $M$ be a smooth manifold with or without boundary, and suppose that for each $p \in M$ we are given a *real vector space* $E_p$ of some *fixed dimension* $k$. Let $$E = \bigsqcup_{p\in M} E_p,$$ and let $\pi: E \rightarrow M$ be the map that takes each element of $E_p$ to the point $p$. 
> 
> Suppose furthermore that we are given the following data:
> 
>- an **open cover** $\set{U_{\alpha}}_{\alpha \in A}$ of $M$
>- for each $\alpha \in A$, a **bijective map** $$\Phi_{\alpha}: \pi^{-1}(U_{\alpha}) \rightarrow U_{\alpha} \times \mathbb{R}^k$$ whose *restriction* to each $E_p$ is a vector space **isomorphism** from $E_p$ to $\set{p} \times \mathbb{R}^k \simeq \mathbb{R}^k$
>- for each $\alpha, \beta \in A$  with $U_{\alpha} \cap U_{\beta} \neq \emptyset$, a **smooth map** $$\tau_{\alpha, \beta}: U_{\alpha} \cap U_{\beta} \rightarrow  GL(k, \mathbb{R})$$ such that the map $\Phi_{\alpha} \circ \Phi_{\beta}^{-1}$ from $(U_{\alpha} \cap U_{\beta}) \times \mathbb{R}^k$ to itself has the form
>$$ 
> \begin{align}
> \Phi_{\alpha} \circ \Phi_{\beta}^{-1}(p,v)  &=  (p,  \, \tau_{\alpha, \beta}(p)v),  
> \end{align}
>$$
>
>Then $E$ has a **unique topology** and **smooth structure** making it into 
>- **a smooth manifold** with or without boundary and 
>- a **smooth rank-$k$ vector bundle** over $M$; with
>	- $\pi$ as **projection** and 
>	- $\set{(U_{\alpha}, \Phi_{\alpha})}$ as **smooth local trivializations.**






## Extension of Vector Bundle

>[!important] Lemma
>Let $\pi: E \rightarrow M$ be a **smooth vector bundle** over a smooth manifold $M$ with or without boundary. 
>
>Suppose $A$ is a **closed subset** of $M$, and $\sigma: A \rightarrow E$ is a section of $E|_{A}$ that is **smooth** in the sense that $\sigma$ **extends to a smooth local section** of $E$ in a *neighborhood of each point*. 
>
>For each *open subset* $U \subseteq M$ containing $A$, there *exists* a **global smooth section** $\widetilde{\sigma} \in \Gamma(E)$ such that $$\widetilde{\sigma}|_{A} = \sigma$$ and $$\text{supp}(\widetilde{\sigma}) \subseteq U.$$ 



## Tangent and Cotangent Bundle 

>[!important] Proposition
> Let $M$ be a smooth $n$-manifold with or without boundary, and let $TM$ be its **tangent bundle.** 
> 
> With its **standard projection map**, its **natural vector space structure** on each **fiber**, and the **topology** and **smooth structure** constructed as in [[Tangent Bundle]], $TM$ is a **smooth vector bundle** of *rank* $n$ over $M$.

>[!important] Proposition
>Let $M$ be a smooth $n$-manifold with or without boundary. 
>
>With its **standard projection map** and the **natural vector space structure** on each **fiber**, the **cotangent bundle** $T^{*}M$ has a **unique topology** and **smooth structure** making it into a **smooth rank-$n$ vector bundle** over $M$ for which all *coordinate covector fields* are **smooth local sections**.

- [[Tangent Bundle]]
- [[Cotangent Bundle]]

### Uniqueness of Topology and Smooth Structure in Tangent Bundle


>[!important] Proposition
>Let $M$ be a smooth n-manifold with or without boundary. 
>
>The topology and smooth structure on $TM$ constructed in [[Tangent Bundle]]  are **the unique ones** with respect to which $$\pi: TM \rightarrow M$$ is a **smooth vector bundle** with *the given vector space structure* on the *fibers*, and such that **all coordinate vector fields are smooth local sections**.

- [[Smooth Section of Vector Bundle]]


## Sections of Vector Bundle

- [[Section of Vector Bundle]]

### Smooth Sections

- [[Smooth Section of Vector Bundle]]

### Space of All Smooth Sections

- [[Space of all Smooth Sections of Vector Bundle]]



-----------
##  Recommended Notes and References


- [[Tangent Bundle]]

- [[Topology of Set]]
- [[Homeomorphism]]
- [[Vector Space over a Field]]
- [[Linear Isomorphism]]
- [[Surjective Function]]
- [[Bijective Function and Inverse Function]]
- [[Continuous Function]]


- [[Introduction to Smooth Manifolds by Lee]]
- [[Introduction to Riemannian Manifolds by Lee]]