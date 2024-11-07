---
tags:
  - concept
  - machine_learning/ensemble_methods
  - machine_learning/models
keywords:
  - decision_tree_model
topics:
  - machine_learning/ensemble_methods
name: Decision Tree Model for Classification and Regression
date of note: 2024-11-05
---

## Concept Definition

>[!important]
>**Name**: Decision Tree Model for Classification and Regression

>[!important] Definition
>Let $\mathcal{X} \subset \mathbb{R}^{d}$ be feature/covariate domain, and $\mathcal{Y}$ be label/response domain.
>
>Consider a **partition** of feature domain into $k$ mutually exclusive regions $\left\{ R_{s} \right\}$, i.e. $$\mathcal{X} = \bigcup_{s=1}^{k}R_{s}, \quad R_{i} \cap R_{j} = \emptyset$$
>
>A **decision tree** is an *additive model* where each *component function* fits on each *region*. That is, 
>$$
>f(x) = \sum_{s=1}^{k}\beta_{s}\,b(x; \gamma_{s}, R_{s})
>$$
>where 
>- $\beta_{s}, s=1 \,{,}\ldots{,}\,k$ are the *expansion coefficients*, 
>- and each component function is based on each region $b(x; \gamma_{s}, R_{s})\in \mathcal{Y}$. 
>- It is common to design the partition according to each feature coordinate (i.e. $R_{i}$ is a *rectangle*), and fit a *constant* on each region. That is $$R_{i} := \prod_{j=1}^{d}\,[a_{i,j}, b_{i,j}]$$ and $$f(x) = \sum_{s=1}^{k}\beta_{s}\,\mathbb{1}\left\{ x\in R_{s} \right\} $$
>
>This model can be represented as a **recursive binary tree** which from top-down *recursively splitting* each parent region into smaller regions by 
>- picking a *dominant feature*, and
>- adding a *threshold* to *branch* the region along the dominant feature. 
>- The *leaves* of the tree is the *final partition* of the feature space.

^a29d4f

- [[Partition of Set]]
- [[Forward Stagewise Additive Modeling]]
- [[Tree Graph and Forest]]

![[cart_decision_tree.png]]

### Regression Tree 

>[!important] Definition
>Let $\mathcal{D} := \left\{ (x_{i}, y_{i}) \right\}_{i=1}^{n} \subset \mathcal{X}\times \mathcal{Y}$ where $\mathcal{X} \subseteq \mathbb{R}^{d}$.
>
>The **regression tree** is a class of decision tree $$f_{k}(x;\, \beta, R) = \sum_{s=1}^{k}\beta_{s}\,\mathbb{1}\left\{ x\in R_{s} \right\} $$  that *minimize the regression error*
>$$
>  \mathbb{E}_{ \mathcal{D} }\left[ L(y, f_{k}(x)) \right]  = \sum_{i=1}^{n}\left( y_{i} - f_{k}(x_{i}; \beta_{i}, R_{i}) \right)^2
>$$
>- The task is to find $k\in \mathbb{N}$ and a set of $k$ *regions* $\left\{ R_{s} \right\}_{s=1}^{k}$ *partitioning* $\mathcal{X}$, and a set of $k$ *coefficients* $\left\{ \beta_{s} \right\}_{s=1}^{k}$ so that the *regression error is minimized*.

#### Tree Splitting 

>[!important] Definition
>The **tree splitting$(\mathcal{D}, R)$** sub-routine for *regression tree* is described as follows:
>- *Require*: the training data $\mathcal{D}$
>- *Require*: a region $R \subseteq \mathcal{X}$
>- Find the *optimal* **splitting variable** $x^{j}$ and **split point** $\theta$ by solving the optimization problem $$(j^{*}, \theta^{*}) = \arg\min_{j, \theta}\left[ \min_{c_{1}}\sum_{x_{i} \in R_{-}(j, \theta) }\left( y_{i} - c_{1}\right)^2 +  \min_{c_{2}}\sum_{x_{i} \in R_{+}(j, \theta) }\left( y_{i} - c_{2}\right)^2\right] $$ where
>	- $$\begin{align*}R_{-}(j, \theta) &= \left\{ (x^1 \,{,}\ldots{,}\,x^{d})\in R\;|\;x^{j} \le \theta \right\} \\[5pt] R_{+}(j, \theta) &= \left\{ (x^1 \,{,}\ldots{,}\,x^{d}) \in R\;|\;x^{j} > \theta \right\}\end{align*}$$
>	- Note that $$\begin{align*}\hat{c}_{1} &= \arg\min_{c_{1}}\sum_{x_{i} \in R_{s, -}(j, \theta) }\left( y_{i} - c_{1}\right)^2 \\[5pt] &= \frac{1}{|R_{-}(j, \theta)|}\sum_{x_{i}\in R_{-}(j, \theta)}y_{i}\end{align*}$$ and $$\begin{align*}\hat{c}_{2} &= \arg\min_{c_{2}}\sum_{x_{i} \in R_{+}(j, \theta) }\left( y_{i} - c_{2}\right)^2 \\[5pt]  &= \frac{1}{|R_{+}(j, \theta)|}\sum_{x_{i}\in R_{+}(j, \theta)}y_{i}\end{align*}$$
>- *Return*: 
>	- the **partitioned region** $$\left\{ R_{-}(j^{*}, \theta^{*})\,,\,R_{+}(j^{*}, \theta^{*}) \right\} $$
>	- the corresponding **coefficients** $\left\{\hat{c}_{1} \,,\,\hat{c}_{2}  \right\}$

#### Tree Pruning

>[!important] Definition
>Let $T \subseteq T_{0}$ be any subtree obtained by **pruning** $T_{0}$, i.e. *collapsing* any non-terminal nodes.
>
>Define the **cost complexity criterion** for a subtree $T \subseteq T_{0}$ as 
>$$
>C_{\alpha}(T) = \sum_{s=1}^{|T|}\,\sum_{x_{i}\in R_{s}}(y_{i} - \hat{c}_{s})^2 + \alpha\,\lvert T \rvert 
>$$
>where 
>- $R_{s}$ is the partition corresponding to **terminal nodes** in $T$
>- $\lvert T \rvert$ is the number of **terminal nodes** in $T$, i.e. $$\mathcal{R} := \left\{ R_{1} \,{,}\ldots{,}\, R_{|T|}\right\} $$
>- and the *mean estimator* is given by the average of response within each region $$\hat{c}_{s} = \frac{1}{|R_{s}|}\sum_{x_{i} \in R_{s}}y_{i}$$
>
>  
>The task of **pruning** is to find $$T_{\alpha}^{*} \in \arg\min_{T \subseteq T_{0}}\,C_{\alpha}(T)$$  
>- The *tuning parameter* $\alpha$ balances the *tradeoff* between *tree size* $|T|$, and its *goodness of fit* to data.

>[!important] Definition
>Consider the task of **pruning** by finding $$T_{\alpha}^{*} \in \arg\min_{T \subseteq T_{0}}\,C_{\alpha}(T).$$
>
>The **weakest link pruning** algorithm find the optimal solution as follows:
>- *Require*: the training data $\mathcal{D}$
>- *Require*: the initial tree $T_{0} := \left\{ (V_{0}, E_{0}) \right\}$ where 
>	- each non-terminal node $v\in V_{0}$ corresponds to a *splitting* $(j^{v}, \theta^{v})$
>	- each terminal node $s$ represents the partitioned region $R_{s}$.
>- While $\text{improvement } > 0$:
>	- Find *internal node* $v$ so that **per node increase** of $$\sum_{s=1}^{|T|}\,\sum_{x_{i}\in R_{s}}(y_{i} - \hat{c}_{s})^2$$ is **smallest** if $v$ is collapsed. 
>	- Collapse $v$ to obtain $T'$
>	- $$T \leftarrow T'$$

### Classification Tree

>[!important] Definition
>Let $\mathcal{D} := \left\{ (x_{i}, y_{i}) \right\}_{i=1}^{n} \subset \mathcal{X}\times \mathcal{Y}$ where $\mathcal{X} \subseteq \mathbb{R}^{d}$ and $\mathcal{Y} = \{ 1\,{,}\ldots{,}\, K\}$.
>
>Consider a *partition* of feature domain into $k$ mutually exclusive regions $\left\{ R_{s} \right\}$, i.e. $$\mathcal{X} = \bigcup_{s=1}^{k}R_{s}, \quad R_{i} \cap R_{j} = \emptyset$$
>- Denote $$\hat{p}_{s,j} := \frac{1}{|R_{s}|}\sum_{x_{i}\in R_{s}}\mathbb{1}\left\{ y_{i} = j \right\} $$ as the *proportion* of *class* $j$ in $R_{s}$.
>- The predicted label for region $R_{s}$ is given by $$j(s) := \arg\max_{j} \hat{p}_{s,j}.$$
>
>The **classification tree** is a class of decision tree $$f_{k}(x;\, \beta, R) = \sum_{s=1}^{k}\beta_{s}\,\mathbb{1}\left\{ x\in R_{s} \right\} $$  that *minimizes* the **total node impurity**.
>
>For each region $R_{s}$, the **node impurity** can be *measured* in different ways. For instance, 
>- **Misclassification error** $$\frac{1}{|R_{s}|}\sum_{x_{i} \in R_{s}}\mathbb{1}\left\{ y_{i} \neq j(s) \right\} := 1 - \hat{p}_{s,j(s)}$$
>- **Gini Index** $$\sum_{j \neq j'}\hat{p}_{s, j}\,\hat{p}_{s, j'} := \sum_{j=1}^{K}\hat{p}_{s,j}\,\left(1 - \hat{p}_{s, j}\right)$$
>- **Entropy** or **deviance** $$- \sum_{j=1}^{K}\hat{p}_{s,j}\,\log \hat{p}_{s,j}$$
>  

- [[Empirical Risk Minimization]]
- [[Shannon Entropy]]
- [[Cross-Entropy Loss Function]]
- [[Logistic Regression]]

![[node_impurity.png]]

>[!quote]
>All three are similar, but *cross-entropy* and the *Gini index* are **differentiable**, and hence more amenable to numerical optimization. ...
>
>In addition, *cross-entropy* and the *Gini index* are more **sensitive to changes** in the *node probabilities* than the *mis-classification rate*. ... either the Gini index or cross-entropy should be used when **growing the tree**. To guide **cost-complexity pruning**, any of the three measures can be used, but typically it is the *misclassification rate*.
>
>The **Gini index** can be interpreted in two interesting ways. 
>- Rather than classify observations to the *majority class* in the node, we could classify them to class $k$ *with probability* $\hat{p}_{s,k}$. Then the **expected training error rate** of this rule in the node is $$\sum_{k\neq k'}\hat{p}_{m,k}\,\hat{p}_{m,k'}$$ — **the Gini index**. 
>- Similarly,  if we code each observation as $1$ for class $k$ and zero otherwise, the **variance** over the node of this $0$-$1$ response is $$\hat{p}_{m,k}(1 − \hat{p}_{m,k}).$$ Summing over classes $k$ again gives the *Gini index*.
>
>-- [[Elements of Statistical Learning by Hastie]] pp 309 - 310

### Other Issues

#### Categorical Predictors

>[!quote]
>When **splitting** a predictor having $q$ possible *unordered values*, there are $$2^{q−1} − 1$$ *possible partitions* of the $q$ values into two groups, and the computations become **prohibitive** for large $q$. 
>
>However, with a $0$-$1$ outcome, this computation simplifies. We order the predictor classes according to the **proportion** *falling in outcome class* $1$. Then we split this predictor as if it were an ordered predictor. 
>
>- One can show this gives the **optimal split**, in terms of *cross-entropy* or *Gini index*, among all possible $2^{q−1} − 1$ splits.
>  
>  
>-- [[Elements of Statistical Learning by Hastie]] pp 310  

>[!quote]
>The **partitioning algorithm** tends to favor categorical predictors with *many levels* $q$; the number of partitions grows exponentially in $q$, and the more choices we have, the *more likely we can find a good one* for the data at hand. This can lead to **severe overfitting** if $q$ is large, and such variables should be avoided.
>
>-- [[Elements of Statistical Learning by Hastie]] pp 310  

- [[Bias-Complexity Tradeoff and Overfitting]]

#### Missing Predictor Values

>[!quote]
>Suppose our data has some **missing predictor values** in some or all of the variables. 
>- We might **discard** any observation with some missing values, but this could lead to serious depletion of the training set. 
>- Alternatively we might try to **fill in (impute)** the missing values, with say the mean of that predictor over the nonmissing observations.
>  
>-- [[Elements of Statistical Learning by Hastie]] pp 311  

>[!quote]
>For tree-based models, there are two better approaches. 
>- The first is applicable to **categorical predictors**: we simply **make a new category** for “missing.” From this we might discover that observations with missing values for some measurement behave differently than those with nonmissing values. 
>- The second more general approach is the **construction of surrogate variables**. 
>	- When considering a predictor for a **split**, we use only the observations for which that *predictor* is **not missing**. Having chosen the best (primary) predictor and split point, we form **a list of surrogate predictors and split points.** 
>		- The first surrogate is the predictor and corresponding split point that **best mimics** the *split* of the training data achieved by the *primary split*. 
>		- The second surrogate is the predictor and corresponding split point that does **second best**, and so on. 
>		- When sending observations down the tree either in the training phase or during prediction, we **use the surrogate splits in order**, if the *primary splitting predictor is missing*. 
>		- Surrogate splits exploit **correlations between predictors** to try and alleviate the effect of missing data. The higher the correlation between the missing predictor and the other predictors, the smaller the loss of information due to the missing value.
>		  
>-- [[Elements of Statistical Learning by Hastie]] pp 311  		  


## Explanation

>[!quote]
>**Tree-based methods** *partition* the feature space into a set of *rectangles*, and then fit a simple model (like a *constant*) in each one. They are conceptually simple yet powerful.
>
>-- [[Elements of Statistical Learning by Hastie]] pp 305

### Pros and Cons of Decision Tree

>[!important]
>Note that **tree-based ensemble** did partition the input space into several regions similar to **clustering**, but the partition is selected to *optimize the loss* with respect to target $y$, while for the clustering method the partition is selected to optimize some metrics on the input data $x$. 
>
>There are several **advantages** when using tree-based methods:
>- Making predictions is **fast** (no complicated calculations, just looking up
> constants in the tree)
>- It’s easy to understand / **interpret** what variables are important in making the prediction (look at the tree)
>- If some data is **missing**, we might not be able to go all the way down the tree to a leaf, but we can still make a prediction by averaging all the leaves in the sub-tree we do reach
>- The model gives a jagged response, so it can work when the true regression surface is **not smooth**. If it is smooth, though, the piecewise-constant surface can approximate it arbitrarily closely (with enough leaves)
>- There are **fast, reliable algorithms** to learn these trees

- [[k-Means Clustering]]

>[!important] 
>The **limitations** of tree-based methods include
>- **High variance**: Often a small change in the data can result in a very different series of splits, making *interpretation somewhat precarious*. 
>	- The major reason for this instability is the **hierarchical nature** of the *process*: the effect of an **error in the top split** is *propagated down* to all of the splits below it.
>- **Lack of Smoothness**: 
>	- The lack of smoothness of prediction surface can degrade performance in the **regression** setting, where we would normally expect the underlying function to be smooth. 
>- **Difficulty in Capturing Additive Structure**: The decision tree may have more difficulties to model **additive structure.** 
>	- If there are more than $2$ additive effects, it would take many fortuitous splits to recreate the structure, and the data analyst would be hard pressed to recognize it in the estimated tree.









## Ensemble Learning that enhanced Decision Tree

### Bagging

- [[Bagging and Model Averaging]]
- [[Random Forest Algorithm]]

### Boosting

- [[AdaBoost Algorithm]]
- [[Gradient Boosting Trees]]
- [[Gradient Boosting Algorithm]]



-----------
##  Recommended Notes and References


- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Weak PAC Learnablity]]


- [[Elements of Statistical Learning by Hastie]] pp 305 - 317
- [[Boosting Foundations and Algorithms by Schapire]] pp 
- Murphy, K. P. (2012). _Machine learning: a probabilistic perspective_. MIT press.pp 544 - 552