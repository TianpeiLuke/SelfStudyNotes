---
tags:
  - concept
  - machine_learning/ensemble_methods
  - machine_learning/theory
keywords:
  - random_forest_model
  - decision_tree_model
topics:
  - machine_learning/ensemble_methods
name: Random Forest Algorithm
date of note: 2024-10-24
---

## Concept Definition

>[!important]
>**Name**: Random Forest Algorithm

![[Bagging and Model Averaging#^56f716]]


>[!important] Definition
>Let $\mathcal{D} := \left\{ (x_{i}, y_{i}) \right\}_{i=1}^{n}$ be samples from $\mathcal{X}\times \mathcal{Y}$, where $\mathcal{X} \subset \mathbb{R}^{d}.$
>
>The **random forest** for *regression* or *classification* is described as below:
>- *Require*: the dataset  $\mathcal{D} := \left\{ (x_{i}, y_{i}) \right\}_{i=1}^{n}$
>- *Require*: total rounds $B >0$
>- For $b=1\,{,}\ldots{,}\,B$:
>	- **Bootstrap resampling**: select a *sub-population* by resampling with repetition from $\mathcal{D}$ $$\mathcal{D}^{(b)}\sim \mathcal{D}$$
>	- **Learning**: grow a **random forest tree** $T^{(b)}$ based on *sub-population* $\mathcal{D}^{(b)}$ by *recursively* repeating the following steps for each **terminate node** of the tree, until **minimium node size** $n_{min}$ is reached 
>		- *Select $p$ variables __at random__* from $d$ variables;
>		- Pick the **best variable / split point** among selected $p$ variables
>		- **Split** the node into two children nodes.
>- *Output*:
>	- The **ensemble** of trees $$\{ T^{(b)} \}_{b=1}^{B}$$
>	- The **prediction** of ensemble for a new point $x$ is given by 
>		- **regression**: $$\hat{f}_{B}(x) := \frac{1}{B} \sum_{b=1}^{B}\,T^{(b)}(x)$$
>		- **classification**: $$\hat{f}_{B}(x) = \text{MajorityVote}\left(\hat{f}(T^{(1)}) \,{,}\ldots{,}\,\hat{f}(T^{(B)})\right)$$ where $\hat{f}(T^{(b)})$ is the *class prediction* of $b$-th random forest tree.


- [[Bagging and Model Averaging]]
- [[Ensemble Learning]]
- [[Decision Tree Model for Classification and Regression]]
- [[Bootstrap Method]]


>[!important]
>- For **classification**, the default value for $p$ is  $$\lfloor \sqrt{d} \rfloor $$ and the *minimum node size* is $n_{min} = 1$
>- For **regression**, the default value for $p$ is  $$\lfloor d / 3 \rfloor $$ and the *minimum node size* is $n_{min} = 5.$

### Variable Importance

>[!quote]
>**Variable importance plots** can be constructed for random forests in exactly the same way as they were for *gradient-boosted models* (Section 10.13). 
>- At each **split** in each tree, the **improvement** in the **split-criterion** is the *importance measure* attributed to the **splitting variable**, and is *accumulated over all the trees* in the forest separately for each variable.
>  
>-- [[Elements of Information Theory by Cover]] pp 593  

- [[Gradient Boosting Trees]]

![[variable_importance_random_forest.png]]


## Explanation


## Compare with Boosting


>[!quote]
>**Boosting** in Chapter 10 was initially proposed as a **committee method** as well, although unlike bagging, the *committee of weak learners* **evolves over time**, and the members cast a *weighted vote*. Boosting appears to *dominate* bagging on most problems, and became the preferred choice. 
>
>**Random forests** (Breiman, 2001) is a *substantial modification* of **bagging** that builds a large collection of **de-correlated trees**, and then *averages them*. On many problems the performance of *random forests* is very similar to *boosting*, and they are simpler to train and tune. As a consequence, random forests are popular, and are implemented in a variety of packages.
>
>-- [[Elements of Statistical Learning by Hastie]] pp 587

- [[AdaBoost Algorithm]]
- [[Gradient Boosting Trees]]
- [[Gradient Boosting Algorithm]]





-----------
##  Recommended Notes and References


- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Weak PAC Learnablity]]


- [[Elements of Statistical Learning by Hastie]] pp 409, 587–604
- [[Boosting Foundations and Algorithms by Schapire]] pp 113
- [[Deep Learning Foundations and Concepts by Bishop]] pp 277 - 279
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 651