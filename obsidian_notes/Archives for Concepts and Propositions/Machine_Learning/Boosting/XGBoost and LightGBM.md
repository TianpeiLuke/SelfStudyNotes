---
tags:
  - concept
  - machine_learning/boosting
keywords: 
topics: 
name: 
date of note: 2024-07-30
---

## Concept Definition

>[!important]
>**Name**: 

### XGBoost

>[!info]
> [XGBoost](https://xgboost.readthedocs.io/en/stable/) (eXtreme Gradient Boosting) is a machine learning algorithm that focuses on computation speed and model performance. It was introduced by Tianqi Chen and is currently a part of a wider toolkit by DMLC (Distributed Machine Learning Community). The algorithm can be used for both regression and classification tasks and has been designed to work with large and complicated datasets.

- [[chenXGBoostScalableTree2016]] Chen, T., & Guestrin, C. (2016). XGBoost: A Scalable Tree Boosting System. _Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining_, 785–794.

#### Features

>[!info]
> The model supports the following kinds of boosting:
> 
> - Gradient Boosting as controlled by the learning rate
> - Stochastic Gradient Boosting that leverages sub-sampling at a row, column or column per split levels
> - Regularized Gradient Boosting using L1 (Lasso) and L2 (Ridge) regularization 
> 
> Some of the other features that are offered from a system performance point of view are:
> 
> - Using a cluster of machines to train a model using [distributed computing](https://docs.neptune.ai/how-to-guides/neptune-api/distributed-computing)
> - Utilization of all the available cores of a CPU during tree construction for *parallelization*
> - *Out-of-core computing* when working with datasets that do not fit into memory
> - Making the best use of *hardware* with *cache optimization*
> 
> In addition to the above the framework:
> 
> - Accepts multiple types of input data
> - Works well with sparse input data for tree and linear booster
> - Supports the use of customized objective and evaluation functions

### LightGBM

>[!info]
>Similar to XGBoost, [LightGBM](https://lightgbm.readthedocs.io/en/latest/) (by Microsoft) is a distributed high-performance framework that uses decision trees for ranking, classification, and regression tasks.

- [[keLightGBMHighlyEfficient2017]] Ke, G., Meng, Q., Finley, T., Wang, T., Chen, W., Ma, W., Ye, Q., & Liu, T.-Y. (2017). LightGBM: A Highly Efficient Gradient Boosting Decision Tree. _Advances in Neural Information Processing Systems_, _30_. 

#### Features

>[!info]
>The advantages are as follows:
>
> - *Faster training speed and accuracy* resulting from LightGBM being a **histogram-based algorithm** that performs **bucketing of values** (also requires lesser memory)
> - Also compatible with large and complex datasets but is much faster during training
> - Support for both parallel learning and GPU learning
> 
> In contrast to the **level-wise (horizontal) growth** in XGBoost, LightGBM carries out **leaf-wise (vertical) growth** that results in *more loss reduction* and in turn *higher accuracy* while being faster. But this may also result in *overfitting* on the training data which could be handled using the max-depth parameter that specifies where the splitting would occur. Hence, XGBoost is capable of building more **robust** models than LightGBM.


## Structural Difference between XGBoost and LightGBM

### Leaf Growth

>[!info]
> **LightGBM** has a faster rate of execution along with being able to maintain good accuracy levels primarily due to the utilization of two novel techniques:

>[!quote]
>The **costliest operation** in GBDT is **training the decision tree** and the most **time consuming** task is to **find the optimum split points**.
>
>-- https://towardsdatascience.com/what-makes-lightgbm-lightning-fast-a27cf0d9785e

>[!quote]
>Split finding algorithms are used to find candidate splits.  One of the most popular split finding algorithm is the **_Pre-sorted algorithm_** which enumerates all possible split points on pre-sorted values. This method is simple but highly *inefficient* in terms of computation power and memory .  
>
> The second method is the **_Histogram based algorithm_** which buckets continuous features into discrete bins to construct feature histograms during training. It costs **$O(\#data * \#feature)$ for histogram building and $O(\#bin * \#feature)$ for split point finding**. As bin << data histogram building will dominate the computational complexity.
> 
>-- https://towardsdatascience.com/what-makes-lightgbm-lightning-fast-a27cf0d9785e 


>[!quote]
>LightGBM aims to reduce complexity of histogram building ( **$O(data * feature)$** ) by *down sampling* data and feature using **_GOSS_** and **_EFB._** This will bring down the complexity to **($O(data2 * bundles)$)** where **$data2 < data$ and $bundles \ll feature$**.
>
>-- https://towardsdatascience.com/what-makes-lightgbm-lightning-fast-a27cf0d9785e


>[!important]
> **1. Gradient-Based One-Side Sampling (GOSS):**
> 
> - In Gradient Boosted Decision Trees, the data instances have *no native weight* which is leveraged by GOSS.
> - Data instances with **larger gradients** *contribute more* towards information gain.
> - To maintain the accuracy of the information, GOSS **retains** instances with **larger gradients** and performs **random sampling** on instances with **smaller gradients.**
> - We can learn more about this concept in the article – [What makes LightGBM lightning fast?](https://towardsdatascience.com/what-makes-lightgbm-lightning-fast-a27cf0d9785e)
> - The YouTube channel Machine Learning University also released a [video](https://www.youtube.com/watch?v=NsCdkzi2soE&ab_channel=MachineLearningUniversity) on LightGBM speaking about GOSS.

>[!quote]
>**Intuitive steps for GOSS calculation**  
> 1.  *Sort* the instances according to **absolute gradients** in a descending order  
> 2. Select the top $a * 100\%$ instances. \[ Under trained / large gradients \]  
> 4. **Randomly samples** $b * 100\%$ instances from the rest of the data. This will reduce the contribution of well trained examples by a factor of $b$ ( $b < 1$ )  
> 5. Without point 3 count of samples having small gradients would be $1-a$ (currently it is $b$ ). In order to maintain the original distribution LightGBM **amplifies** the contribution of samples having small gradients **by a constant** $(1-a)/b$ to put more focus on the under-trained instances. This puts more focus on the under trained instances without changing the data distribution by much.
>    
>-- https://towardsdatascience.com/what-makes-lightgbm-lightning-fast-a27cf0d9785e    


![[LightGBM_GOSS.png]]


>[!important]
> **2. Exclusive Feature Bundling (EFB):**
> 
> - EFB is a near lossless method to **reduce the number of effective features**.
> - Just like One-Hot encoded features, in the sparse space, many features rarely take non-zero values *simultaneously*. 
> - To reduce dimensionality, improve efficiency, and maintain accuracy, EFB *bundles* these features, and this bundle is called an **Exclusive Feature Bundle**.
> - [This](https://datascience.stackexchange.com/questions/41907/lightgbm-why-exclusive-feature-bundling-efb) thread on EFB and [LightGBM’s paper](https://proceedings.neurips.cc/paper/2017/file/6449f44a102fde848669bdd9eb6b76fa-Paper.pdf) can be referred to gain better insight.
> 
> On the other hand, **XGBoost** uses a **pre-sorted** and **histogram-based algorithm** for computing the best split, which is done with **GOSS** in LightGBM. The **pre-sorting** splitting works as:
> 
> 1. For each node, enumerate over all features
> 2. For every feature, sort instances by the feature value
> 3. Using linear scan, decide the split along with the **feature basis information gain**
> 4. Pick the best-split solution along with all the features

>[!quote]
>Remember histogram building takes $O(\#data * \#feature)$. If we are able to down sample the $\#feature$ we will speed up tree learning. LightGBM achieves this by **bundling features together**. We generally work with high dimensionality data. Such data have many features which are **mutually exclusive** i.e they **never take zero values simultaneously**. LightGBM safely identifies such features and bundles them into a single feature to reduce the complexity to **$O(\#data * \#bundle)$** where $\#bundle \ll \#feature$.


>[!quote]
> Intuitive explanation for creating feature bundles
> 
> 1. Construct a graph with *weighted* (measure of conflict between features) edges. **Conflict** is measure of the fraction of **exclusive features** which have **overlapping non zero values**.
> 2. **Sort** the features by **count of non zero** instances in descending order.
> 3. Loop over the ordered list of features and **assign** the feature to an existing bundle (if $conflict < threshold$) or **create** a new bundle (if $conflict > threshold$).
>    
>-- https://towardsdatascience.com/what-makes-lightgbm-lightning-fast-a27cf0d9785e    


![[LightGBM_EFB.webp]]

>[!quote]
>**Intuitive explanation for merging features**
> 
> 1. Calculate the **offset** to be added to *every feature* in feature bundle.
> 2. Iterate over every data instance and feature.
> 3. **Initialise the new bucket** as zero for instances where *all features are zero*.
> 4. Calculate the **new bucket** for *every non zero instance* of a feature by adding respective offset to original bucket of that feature.

![[LightGBM_EFB_Merge.webp]]



### Handling Categorical Features

>[!info]
>Both LightGBM and XGBoost accept **numerical features only**. This means that the nominal features in our data need to be transformed into numerical features.

Let’s assume we want to predict if it’s “Hot”, “Cold” or “Unknown” i.e. 2, 1, or 0. Since they are categorical features and are not ordered (which means that 1 greater than 0 actually is not a correct interpretation), the algorithm needs to avoid comparing the greatness of the two values and focus more on creating rules for equality.


>[!important]
> **XGBoost**, by default, treats such variables as *numerical variables* with *order* and we don’t want that. Instead, if we can create dummies for each of the categorical values (one-hot encoding), then XGboost will be able to do its job correctly. But for larger datasets, this is a problem as encoding takes a longer time.
> 
> On the other hand, **LightGBM** accepts a *parameter* to check which column is a categorical column and handles this issue with ease by **splitting on equality**. However, the H2O library provides an implementation of XGBoost that supports the native handling of categorical features.

### Handling Missing Values

>[!important]
> Both the algorithms treat missing values by **assigning** them to the **side** that **reduces loss the most** in each split.

## Feature Importance methods

### Gain:

>[!important]
> - Every feature in a dataset has some sort of importance/ weightage in helping build an accurate model.
> - **Gain** refers to the **relative contribution** of a particular feature in the context of a particular tree.
> - This can also be understood by the *extent of relevant information* that the model gains from a feature for making better predictions.
> - Available *both* in XGBoost and LightGBM.

### Split/Frequency/Weight:

>[!important]
> - **Split** for LightGBM and **Frequency or Weight** for XGBoost method calculates the *relative count of times* a particular feature occurs in *all splits of the model’s trees*. One issue with this method is that it is **prone to bias** when there are a large number of categories in categorical features.
> - Available *both* in XGBoost and LightGBM.

### Coverage:

>[!important]
> - The **relative number of observations per feature**.
> - Available *only* in XGBoost.


## Other key differences between XGBoost and LightGBM

### Processing Unit

>[!info] 
> The algorithm we want to use often depends upon the type of **processing unit** we have for running the models. Although XGBoost is comparatively **slower** than LightGBM on **GPU**, it is actually **faster** on **CPU**. LightGBM requires us to *build the GPU distribution separately* while to run XGBoost on GPU we need to pass the `‘gpu_hist’` value to the `‘tree_method’` parameter when initializing the model.
> 
> When working in an institution with access to **GPUs** and **strong CPUs**, we should go for XGBoost as it is **more scalable** than LightGBM. But personally, I think LightGBM makes more sense as the training time saved can be used for better experimentation and feature engineering. We can train our final model to have model robustness.

### Community

>[!info] 
> A framework is as good as the community behind maintaining it. In the case of [XGBoost](https://xgboost.ai/community), it is much easier to work with as compared to [LightGBM](https://github.com/microsoft/LightGBM) solely due to the strong community behind it and the *availability* of a myriad of helpful sources. Since LightGBM still has a *smaller community*, when it comes to issues and features that are advanced, it becomes a bit difficult to navigate to the solution.

### Documentation

>[!info] 
> Since XGBoost has been around for longer and is one of the **most popular algorithms** for data science practitioners, it is extremely easy to work with due to the abundance of literature online surrounding it. This can either be in the form of framework documentation or errors/ issues faced by various users around the globe.
> 
> When looking at the two offerings at a high level, [LightGBM’s documentation](https://lightgbm.readthedocs.io/en/latest/) feels very comprehensive. But at the same time, [XGBoost’s documentation](https://xgboost.readthedocs.io/en/stable/) feels very structured which in my opinion is easier to read and understand in comparison to LightGBM’s often wordy documentation, which of course is no deal-breaker as both of them keep improving.


## Important hyperparameters

>[!quote]
> Decision Tree-based algorithms can be complex and prone to overfitting. Depending on the data availability and various statistical metrics that give us an overall understanding of how the data is, it becomes important for us to do the right set of hyperparameter adjustments.
> 
> Since hyperparameter tuning/ optimization is a broad topic on its own, in the following subsections we are going to aim to get an overall understanding of some of the important hyperparameters for both XGBoost and LightGBM.
> 
>-- https://neptune.ai/blog/xgboost-vs-lightgbm 

### XGBoost parameters

>[!info]
> Here are the most important XGBoost parameters:
> 
> 1. **_n_estimators [default 100] –_** Number of trees in the ensemble. A higher value means more weak learners contribute towards the final output but increasing it significantly slows down the training time. 
> 2. **_max_depth [default 3] –_** This parameter decides the complexity of the algorithm. The lesser the value assigned, the lower is the ability for the algorithm to pick up most patterns (underfitting). A large value can make the model too complex and pick patterns that do not generalize well (overfitting).
> 3. **_min_child_weight [default 1] –_**  We know that an extremely deep tree can deliver poor performance due to overfitting. The min_child_weight parameter aims to regularise by limiting the depth of a tree. So, the higher the value of this parameter, the lower are the chances of the model overfitting on the training data.
> 4. **_learning_rate/ eta [default 0.3] –_** The rate of learning of the model is inversely proportional to the accuracy of the model. Lowering the learning rate, although slower to train, improves the ability of the model to look for patterns and learn them. If the value is too low then it raises difficulty in the model to converge.
> 5. **_gamma/ min_split_loss [default 0] –_** This is a regularization parameter that can range from 0 to infinity. Higher the value, higher is the strength of regularization, lower are the chances of overfitting (but can underfit if it’s too large). Hence, this parameter varies across all types of datasets.
> 6. **_colsample_bytree [default 1.0] –_** This parameter instructs the algorithm on the fraction of the total number of features/ predictors to be used for a tree during training. This means that every tree might use a different set of features for prediction and hence reduce the chances of overfitting and also improve the speed of training as not all the features are being used in every tree. The value ranges from 0 to 1.
> 7. **_subsample [default 1.0] –_** Similar to colsample_bytree, the subsample parameter instructs the algorithm on the fraction of the total number of instances to be used for a tree during training. This also reduces the chances of overfitting and improves training time.
> 
> Find more parameters [here](https://xgboost.readthedocs.io/en/stable/parameter.html).

### LightGBM parameters

>[!info]
> Here are the most important LightGBM parameters:
> 
> 1. **_max_depth –_** Similar to XGBoost, this parameter instructs the trees to not grow beyond the specified depth. A higher value increases the chances for the model to overfit.
> 2. **_num_leaves –_** This parameter is very important in terms of controlling the complexity of the tree. The value should be less than $2^{\text{max\_depth}}$ as a leaf-wise tree is much deeper than a depth-wise tree for a set number of leaves. Hence, a higher value can induce overfitting.
> 3. **_min_data_in_leaf –_** The parameter is used for controlling overfitting. A higher value can stop the tree from growing too deep but can also lead the algorithm to learn less (underfitting). According to the LightGBM’s official documentation, as a best practice, it should be set to the order of hundreds or thousands.
> 4. **_feature_fraction –_** Similar to _colsample_bytree_ in XGBoost
> 5. **_bagging_fraction –_** Similar to _subsample_ in XGBoost



-----------
##  Recommended Notes and References


- [[Gradient Boosting Algorithm]]
- [[Functional Gradient Descent]]
- [[Gradient Boosting Trees]]


- [[chenXGBoostScalableTree2016]] Chen, T., & Guestrin, C. (2016). XGBoost: A Scalable Tree Boosting System. _Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining_, 785–794.
- [[keLightGBMHighlyEfficient2017]] Ke, G., Meng, Q., Finley, T., Wang, T., Chen, W., Ma, W., Ye, Q., & Liu, T.-Y. (2017). LightGBM: A Highly Efficient Gradient Boosting Decision Tree. _Advances in Neural Information Processing Systems_, _30_. 
- Blog [XGBoost vs LightGBM: How Are They Different](https://neptune.ai/blog/xgboost-vs-lightgbm)

- [[Boosting Foundations and Algorithms by Schapire]] pp 188 - 193
- [[Elements of Statistical Learning by Hastie]]