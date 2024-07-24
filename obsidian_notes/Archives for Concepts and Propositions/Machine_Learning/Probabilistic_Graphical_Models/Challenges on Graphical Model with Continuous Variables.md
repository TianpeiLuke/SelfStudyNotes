---
tags:
  - concept
  - probabilistic_graphical_models/theory
keywords:
  - probabilistic_graphical_model
topics:
  - probabilistic_graphical_model
name: Challenges on Graphical Model with Continuous Variables
date of note: 2024-07-23
---

## Concept Definition

>[!important]
>**Name**: Challenges on Graphical Model with Continuous Variables

>[!quote]
>At an abstract level, the introduction of **continuous variables** in a graphical model is not difficult. As we saw in section 5.5, we can use a range of different representations for the CPDs or factors in our network. We now have a set of factors, over which we can perform the same operations that we utilize for inference in the discrete case:...
>
>Unfortunately, a little more thought reveals that the correct implementation of these basic operations poses a range of **challenges**, whose solution is far from obvious. 
>
>The **first challenge** involves the **representation of factors** involving **continuous variables**. Unlike discrete variables, there is **no universal representation** of a **factor** *over continuous variables*, and so we must usually select a parametric family for each CPD or initial factor in our network. Even if we pick the same parametric family for each of our initial factor in the network, it may *not be the case* that multiplying factors or marginalizing a factor leaves it within the parametric family. If not, then it is not even clear how we would *represent* the intermediate results in our inference process. ... In this case, it is generally **unlikely** that we can find a **single parametric family** that can *correctly encode* *all* of the **intermediate factors** in our network.
>
>A **second challenge** involves the *marginalization step*, which now requires integration rather than summation. Integration introduces a new set of subtleties. First, not all functions are integrable: in some cases, the integral may be infinite or even ill defined. Second, even functions where the integral is well defined may *not have a closed-form integral*, requiring the use of a numerical integration method, which is usually approximate.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 605 - 606

### Benefits for Gaussian Graphical Model

![[Canonical Form of Gaussian Graphical Model#^777073]]


- [[Canonical Form of Gaussian Graphical Model]]





## Explanation





-----------
##  Recommended Notes and References



- [[Probabilistic Graphical Models by Koller]] pp 605 - 606