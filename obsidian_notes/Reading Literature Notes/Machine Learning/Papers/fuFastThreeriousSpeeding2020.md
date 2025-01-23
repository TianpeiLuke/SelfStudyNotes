---
tags:
  - "#paper"
  - programmatic_weak_supervision
aliases:
  - fuFastThreeriousSpeeding2020
year: 2020
name: "Fast and Three-rious: Speeding Up Weak Supervision with Triplet Methods"
authors: Daniel Fu, Mayee Chen, Frederic Sala, Sarah Hooper, Kayvon Fatahalian, Christopher Re
publication: Proceedings of the 37th International Conference on Machine Learning (ICML 2020)
type: conferencePaper
DOI: ""
date of note: 2024-03-13
---
# Descriptions

## Fast and Three-rious: Speeding Up Weak Supervision with Triplet Methods 
> [!info] 
> - **Abstract:** Weak supervision is a popular method for building machine learning models without relying on ground truth annotations. Instead, it generates probabilistic training labels by estimating the accuracies of multiple noisy labeling sources (e.g., heuristics, crowd workers). Existing approaches use latent variable estimation to model the noisy sources, but these methods can be computationally expensive, scaling superlinearly in the data. In this work, we show that, for a class of latent variable models highly applicable to weak supervision, we can find a closed-form solution to model parameters, obviating the need for iterative solutions like stochastic gradient descent (SGD). We use this insight to build FlyingSquid, a weak supervision framework that runs orders of magnitude faster than previous weak supervision approaches and requires fewer assumptions. In particular, we prove bounds on generalization error without assuming that the latent variable model can exactly parameterize the underlying data distribution. Empirically, we validate FlyingSquid on benchmark weak supervision datasets and find that it achieves the same or higher quality compared to previous approaches without the need to tune an SGD procedure, recovers model parameters 170 times faster on average, and enables new video analysis and online learning applications. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/K5SNU4SC) [local](zotero://select/library/items/K5SNU4SC) [pdf](file:////Users/lukexie/Zotero/storage/B4UL7UH8/Fu%20et%20al.%20-%202020%20-%20Fast%20and%20Three-rious%20Speeding%20Up%20Weak%20Supervision.pdf)  [pdf](file:////Users/lukexie/Zotero/storage/PHTUR78Q/Fu%20et%20al.%20-%202020%20-%20Fast%20and%20Three-rious%20Speeding%20Up%20Weak%20Supervision.pdf) 
> - **Bibliography**: Fu, D., Chen, M., Sala, F., Hooper, S., Fatahalian, K., & Re, C. (2020). Fast and Three-rious: Speeding Up Weak Supervision with Triplet Methods. _Proceedings of the 37th International Conference on Machine Learning_, 3280–3291. [https://proceedings.mlr.press/v119/fu20a.html](https://proceedings.mlr.press/v119/fu20a.html)
> - **Cite Key:** @fuFastThreeriousSpeeding2020 
> - **Conclusion**:
> - **Tags:** #Weak-supervision, #FlyingSquid, #Programmatic-Weak-Supervision


>[!Personal Summary] 


# Questions
## Questions Regarding to This Paper


>[!question] 
>What are the *primary assumptions* behind this paper?



>[!question]
>What are the major *problems of concern* behind this paper? If i had to guess, what does the author seems to be concerned. 



>[!question]
>What are *related publications* before this paper? What may be *after* this paper? What excites you and why?



>[!question]
>What are *the main contributions* of the paper?



>[!question]
>What *technical terms and vocabulary* it used?




>[!question] Other Questions
> - What is the specific case that the study focus on?
> - What is the argument in this paper?
> - What is the specific questions posed by the study of the paper?


## Primary Sources


>[!question]
>What are the *primary sources* to the problem of this paper? list important the datasets, code repositories, literature citations




>[!question]
>*How* is the source _primary_ to the problem of this paper? List major results from *literary, theoretical and experimental perspectives* that support the conclusion of the paper. Also explain the success criteria that are used in this paper.






> [!question]
> What do I notice about the source (data, theory, reference)? list feature-question pair from the sources






>[!question] 
>Which of the feature-question in this paper lights my fire?





>[!question]
>What is the *very next primary source* that the author might want to find?


## Questions Related to Me


> [!question] 
> Is the problem behind this paper related to problem of mine?



> [!question] 
> What impact does this paper have on me?



> [!question] 
> How does the author call my problem of concern?



>[!question]
>What aspects of the paper that *excite* me the most? Why, if i have to guess?



>[!question]
>What aspects of the paper that are *boring* to me? Why, if i have to guess?




>[!question]
  What vocabulary does this author, who clearly seems to be kept awake at night by the same gnawing question as I am, use to describe themself, whether professionally, intellectually, or otherwise?



## Advanced Questions

### Limitations and Restrictions


>[!question]
>What are the *limitations* of this paper? What criticism towards the perspective of this paper?
>> [!question] Follow-Up Questions
>> - What question the author did not ask? but for me they should.
>> - What are the limitations on the assumptions of the paper?
>> - What are the limitations and restrictions for primary sources in the paper? 
>> - Are there untold tricks to achieve the results?
>> - Are we satisfied with the conclusion of the paper? why or why not?
>> - Under what situation the conclusion of this paper do not hold?
>> - Under what condition the major argument do not hold? 
>> - How much resources do we need to replicate the results?
>> - Can we use this paper in real world applications?
>> - What are the costs to use this paper in real life applications?




> [!question] 
> What questions and concerns that i might have after reading the paper?
> 


### Connection, Expansion and Generalization


>[!todo] Connect More Papers
>- What are related genres of questions that might related to the author's problem?
>- Listed all the author's questions, connected to other papers. Identify as many questions as possible.



>[!todo] Problem Summarization and Expansion
>
>- Identity patterns among these questions of the author. What does this author seem to be concerned about or preoccupied with? 
>- try to identify a common theme that connect different author's problems; 
>- see past the author’s case study, and identify the deeper-seated problem



> [!question]
> Change one variable regarding the features of the problem behind this paper. What new problem do you see? Could you find related papers? 





>[!todo]
> Try to group papers of different author together




----

## Reference and Related Notes

- [[Triplet Loss Minimization for Contrastive Learning]]