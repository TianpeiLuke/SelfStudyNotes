---
tags:
  - "#paper"
aliases:
  - "{{citekey}}"
year:
  "{ date | format (\"YYYY\") }": 
name: Untitled
authors: "{{authors}}"
publication: "{{publicationTitle}}"
type: "{{itemType}}"
DOI: "{{DOI}}"
date of note:
  "{ importDate | format(\"YYYY-MM-DD\") }":
---
# Descriptions

## Direct Acquisition Optimization for Low Budget Active Learning
> [!info] 
> - **Abstract:** {{abstractNote}} 
> - **Sources**: [online]({{uri}}) [local]({{desktopURI}}) {%- for attachment in attachments | filterby("path", "endswith",".pdf") %} [pdf](file:///{{attachment.path | replace(" ","%20")}}) {% if loop.last %}{% endif %}{%- endfor %}
> - **Bibliography**: {{bibliography}}
> - **Cite Key:** [[@{{citekey}}]] 
> - **Conclusion**:
 {%- if hashTags %}
> - **Tags:** {{hashTags}} 
{%- endif %}

# Summary

>[!important] Summary
>Briefly summarize the paper and its contributions. This is not the place to critique the paper; the authors should generally agree with a well-written summary.

>[!info]
>In this paper, the authors present a new Active Learning framework under the low budget setting. The proposed Direct Acquisition Optimization (DAO) algorithm uses the influence function to update the model parameter and estimate the true loss with importance sampling. The main contributions of this paper is a novel AL algorithm with the proposal of selecting samples based on expected loss reduction. Compared to existing approaches, this method do not rely on additional holdout labeled data for loss evaluation and requires less time for model update using influence function using influence function approximation. The experiment results indicate the proposed method is more efficient than the baseline methods including the random selection in image classification use cases.



# Review Questions
## Strengths

>[!important]
>A substantive assessment of the **strengths** of the paper, touching on each of the following dimensions: 
>- **originality**, 
>- **quality**, 
>- **clarity**, 
>- and **significance**. 
>
>We encourage reviewers to be broad in their definitions of originality and significance. For example, originality may arise from a new definition or problem formulation, creative combinations of existing ideas, application to a new domain, or removing limitations from prior results. You can incorporate Markdown and Latex into your review. See [https://openreview.net/faq](https://openreview.net/faq).


>[!question] 
>Decide the *originality* of the idea in this paper.  
>- How this idea compared to existing work? 
>- What are the existing work for the same topic and problem?
>- What happens in this field before this paper?

>[!info]
>This paper focus on extreme low budge setting while using expected loss reduction as criterion for sample selection. Most of active learning are based on heuristics, which emphasize the computational efficiency in sample selection process. But the training objective is different from the heuristic for sample selection, making them less effective. However, evaluating expected loss on test data requires some labeled validation set. This is not suitable for active learning with low budget. For this reason, this paper raised an important challenge in active learning. This paper combines several existing techniques such the the use of surrogate proposal (which is common for sampling-based methods), and the use of variance-reduction importance sampling for estimation of expected loss. It is interesting to see that the influence function is chosen.   



>[!question] 
>Decide the *quality* of this paper.  
>- Is the derivation in this paper correct? 
>- Is the conclusion of this paper sound?
>- Do the results of experiments support the claim in this paper ?
>- Are there any other factors that lead to the result which are not described in the paper?
>- Is the result repeatable?
>- 

>[!info]
>Both derivations and results from this paper seem correct, and are supportive to the author's claim that the heuristic-based methods are sub-optimal and using surrogate function would help to mitigate the lack of labeled samples in low budget setting. No code is shared thus we cannot judge on repeatablilty of experiment.


>[!question] 
>Decide the *clarity* of this paper.  
>- Are the authors able to present their ideas clearly? 
>- Is the structure of the paper well-organized?
>- Is the logic and math in this paper well derived?
>- Is the author using language fluently?
>- Is the graph and other visualization in this paper clear to read?

>[!info]
>This paper has well-organized structure. The objective is clear for the active learning. The presentation is not very clear in Methodology section, esp. when intermediate procedure for parameter update as well as the step for loss evaluation is lengthy and notation heavy.


>[!question] 
>Decide the *significance* of this paper.  
>- What major contribution of this paper? 
>- How this paper would help the other's research?
>- Is the idea and experiment in this paper demonstrate a new direction for the field?
>- How ?

>[!info]



## Weakness

>[!important]
>A substantive assessment of the **weaknesses** of the paper. 
>- Focus on *constructive and actionable insights* on how the work could improve towards its stated goals. 
>- Be *specific*, avoid generic remarks. For example, if you believe the contribution lacks novelty, provide references and an explanation as evidence; if you believe experiments are insufficient, explain why and exactly what is missing, etc.

>[!info]
>Contribution: 
>This paper focus on active learning with low budge setting and the algorithm presented solves three issues: 1) how to obtain pseudo-labels  in unlabeled data; 2) how to approximate new model parameter without retraining; 3) how provide low bias estimation on true expected loss on unlabled data. 
>
> The issue for 1) is that the obtaining a good proposed surrogate function is difficult.This model plays a central role for the success of this algorithm both theoretically and practically showing in experiments. It is always possible to use the old model from last iteration for surrogate, but it is an poor estimate of the oracle given low budget setup. Thus although this framework claims that it is superior to the heuristic it still inject the heuristic within the surrogate model. More issue with surrogate model is the update of the model. Would you retrain the surrogate model and the main model using the same acquired labels? how to make sure that surrogate model guides us towards the true target better than current production? if not, the cross entropy correction would be a misleading term.
> 
> The issue for 2) is that to approximate model parameter using influence function, we have to approximate the influence function itself with some iterative method. Both CG and Quasi-Newton like solution has its own challenge, e.g. in CG, in order to compute the influence of one unlabeled sample. we have to do two back-propagation, which is more time-consuming than retraining the model with early stopping. Another issue for this approximation method is additional memory requirement for large model, like LLM. Finally, when the Hessian is indefinite ( e.g. saddle points), this is not clear that if this second-order estimate would result in severe underwhelming result in parameter estimation. Since the new model parameter is used in cross-entropy correction term in importance sampling, it is likely that the error rate will affect the sample stage.
> 
> The issue for 3) is that since cross-entropy acquisition function is the key for bias-variance reduction, it is critical to have some guarantee that the impact of error in both surrogate function selection, and parameter update is bounded. It is expected that when the cross-entropy is low but both proposal and target function are limited, this active learning would be worse than random selection. 
> 
> All in all, a major concern for this model is that it is a very complicated system with multiple approximation steps, which has its own errors in each step. The good performance is thus not guaranteed. The uninformative choice of surrogate function and the approximation of parameter update would damage the performance of this model in larger and more complicated dataset. As for the computation cost as compared to model retraiin, it is not clear parameter update with second-order gradient like estimation would reduce the cost of computation as compared to partial retrain (like using Contrastive Divergence). 



>[!info]
>Over-Confidence of model,
>
>Complicated Error Reduction computation for LLM => CG, Stochastic approximate
>
>Hessian, not positive definition, 
>
>the acquisition distribution in importance weight need to be proportional to true test loss function in order to achieve variance reduction, but the use of cross entropy between surrogate loss function and model score is not necessarily proportional to the true test loss. Instead it is a disagreement measure 
>
>line 5 is wrong, as n_ivp is from labeled data 
>
>every unlabelled data need to estimate the true loss and sort
>
>surrogate function need to be trained.




>[!info]
>**Clarity**:
>- The plot is small and the line in Figure 2,3 cannot be distinguished in grey-scale printout since the markers and line styles are the same. It is suggested to modify markers and line styles so that it can be visualized without relying on colored pdf file.
>- The interpretability result only covers the MINST, which is a toy dataset. It is not very convincing. On the other hand, it is not convincing that KAE is more interpretable than MLP-based AE. Both has poor interpretability but AE at least maps linearly locally to Euclidean space but KAE maps to feature space via high dimensional kernels, which is hard to interpret. 

>[!info]
>**Significance**
>- The key challenge for KAE or KAN framework is to convince the other researchers that it worth the restructuring of the basic building block. In high-level, KAN layer is a kernel non-parametric regression model, which is in contrast to the MLP layer which is a parametric model. 
>	- The benefit of non-parametric regression is that it learns from a function space which is very high dimensional compared to original parametric space. 
>	- The drawback of this framework, however, lies in the choice of kernel. Like the difficulty we faced in early 2000s, kernel machine need to select a family of kernels apriori, which is hand-crafted. KAE, KAN with B-spline, wavelet, fourier basis are all human crafted feature family. This is the same issue for authors. For your use case which is MINST and CIFAR, polynomial kernel may be good enough. But how about NLP tasks? how about ImageNet, how to choose a family of kernel? in fact, it is critical to choose a good family of kernels for this type of system to work the best. But there is no guidance on that.
>- Another issue is that why only use shadow network? is there limitation for KAN to go deep? AE can benefit strongly by going deep. This is a fundamental question for KAN, since each layer is very expressive, it seems that there is little to learn for the second KAN layer on top. This paper could demonstrate the performance gain by constructing a 6 layer + network, if possible. 
>- Finally, it is the question on whether or not the KAN suffers from vanishing and exploding gradient issue more than MLP. Kernel such as polynomial kernel is not stationary. In a sense, in a long run, the error in gradient computation will grew much faster than ReLU activation. This is a critical issue if we want to go deep. 	  



# Optional: Future Questions



>[!question] 
>What are the *primary assumptions* behind this paper?



>[!question]
>What are the major *problems of concern* behind this paper? If i had to guess, what does the author seems to be concerned. 


## Questions Related to Me


> [!question] 
> Is the problem behind this paper related to problem of mine?



> [!question] 
> What impact does this paper have on me?




----

## Reference and Related Notes