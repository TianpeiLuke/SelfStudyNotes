---
tags:
- '#paper'
aliases: "keLightGBMHighlyEfficient2017"
year: 2017
name: "LightGBM: A Highly Efficient Gradient Boosting Decision Tree"
authors: "Guolin Ke, Qi Meng, Thomas Finley, Taifeng Wang, Wei Chen, Weidong Ma, Qiwei Ye, Tie-Yan Liu"
publication: ""
type: "conferencePaper"
DOI: ""
date of note: 2024-05-12 
---
# Descriptions

## LightGBM: A Highly Efficient Gradient Boosting Decision Tree 
> [!info] 
> - **Abstract:** Gradient Boosting Decision Tree (GBDT) is a popular machine learning algorithm, and has quite a few effective implementations such as XGBoost and pGBRT. Although many engineering optimizations have been adopted in these implementations, the efficiency and scalability are still unsatisfactory when the feature dimension is high and data size is large. A major reason is that for each feature, they need to scan all the data instances to estimate the information gain of all possible split points, which is very time consuming. To tackle this problem, we propose two novel techniques: \emph{Gradient-based One-Side Sampling} (GOSS) and \emph{Exclusive Feature Bundling} (EFB). With GOSS, we exclude a significant proportion of data instances with small gradients, and only use the rest to estimate the information gain. We prove that, since the data instances with larger gradients play a more important role in the computation of information gain, GOSS can obtain quite accurate estimation of the information gain with a much smaller data size. With EFB, we bundle mutually exclusive features (i.e., they rarely take nonzero values simultaneously), to reduce the number of features. We prove that finding the optimal bundling of exclusive features is NP-hard, but a greedy algorithm can achieve quite good approximation ratio (and thus can effectively reduce the number of features without hurting the accuracy of split point determination by much). We call our new GBDT implementation with GOSS and EFB \emph{LightGBM}. Our experiments on multiple public datasets show that, LightGBM speeds up the training process of conventional GBDT by up to over 20 times while achieving almost the same accuracy. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/I8V392SH) [local](zotero://select/library/items/I8V392SH) [pdf](file:////home/lukexie/Documents/Papers/storage/K4LAURGC/Ke%20et%20al.%20-%202017%20-%20LightGBM%20A%20Highly%20Efficient%20Gradient%20Boosting%20Dec.pdf)  [pdf](file:////home/lukexie/Documents/Papers/storage/NQD6JUER/supplementary-nips.pdf) 
> - **Bibliography**: Ke, G., Meng, Q., Finley, T., Wang, T., Chen, W., Ma, W., Ye, Q., & Liu, T.-Y. (2017). LightGBM: A Highly Efficient Gradient Boosting Decision Tree. _Advances in Neural Information Processing Systems_, _30_. [https://proceedings.neurips.cc/paper/2017/hash/6449f44a102fde848669bdd9eb6b76fa-Abstract.html](https://proceedings.neurips.cc/paper/2017/hash/6449f44a102fde848669bdd9eb6b76fa-Abstract.html)
> - **Cite Key:** [[@keLightGBMHighlyEfficient2017]] 
> - **Conclusion**:
> - **Tags:** #LightGBM


>[!note] Highlights:
>
>-
>-
>-



# Questions
## Questions Regarding to This Paper


>[!question] 
>What are the *primary assumptions* behind this paper?



>[!question]
>What are the major *problems of concern* behind this paper? If i had to guess, what does the author seems to be concerned. 




>[!question]
>What are *the main contributions* of the paper?




>[!todo]
>Highlight the main techniques proposed in this paper. Also highlight the performance comparison to state-of-the-art.



## Questions Related to Me


> [!question] 
> Is the problem behind this paper related to problem of mine?



> [!question] 
> What impact does this paper have on me?




----

## Reference and Related Notes

- [[chenXGBoostScalableTree2016]]
- [[Gradient Boosting Trees]]

- [[Boosting Foundations and Algorithms by Schapire]]