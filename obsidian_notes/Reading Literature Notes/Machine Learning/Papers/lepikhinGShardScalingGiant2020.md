---
tags:
- '#paper'
aliases: "lepikhinGShardScalingGiant2020"
year: 2020
name: "GShard: Scaling Giant Models with Conditional Computation and Automatic Sharding"
authors: "Dmitry Lepikhin, HyoukJoong Lee, Yuanzhong Xu, Dehao Chen, Orhan Firat, Yanping Huang, Maxim Krikun, Noam Shazeer, Zhifeng Chen"
publication: ""
type: "conferencePaper"
DOI: ""
date of note: 2025-01-03 
---
# Descriptions

## GShard: Scaling Giant Models with Conditional Computation and Automatic Sharding 

> [!info] 
> - **Abstract:** Neural network scaling has been critical for improving the model quality in many real-world machine learning applications with vast amounts of training data and compute. Although this trend of scaling is affirmed to be a sure-fire approach for better model quality, there are challenges on the path such as the computation cost,ease of programming, and efficient implementation on parallel devices. In this paper we demonstrate conditional computation as a remedy to the above mentioned impediments, and demonstrate its efficacy and utility. We make extensive use of GShard, a module composed of a set of lightweight annotation APIs and an extension to the XLA compiler to enable large scale models with up to trillions of parameters. GShard and conditional computation enable us to scale up multilingual neural machine translation Transformer model with Sparsely-Gated Mixture-of-Experts. We demonstrate that such a giant model with 600 billion parameters can efficiently be trained on 2048 TPU v3 cores in 4 days to achieve far superior quality for translation from 100 languages to English compared to the prior art. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/9S2R48II) [local](zotero://select/library/items/9S2R48II) [pdf](file:////home/lukexie/Documents/Papers/storage/9Q4RJ8F9/Lepikhin%20et%20al.%20-%202020%20-%20GShard%20Scaling%20Giant%20Models%20with%20Conditional%20Comp.pdf) 
> - **Bibliography**: Lepikhin, D., Lee, H., Xu, Y., Chen, D., Firat, O., Huang, Y., Krikun, M., Shazeer, N., & Chen, Z. (2020, October 2). _GShard: Scaling Giant Models with Conditional Computation and Automatic Sharding_. International Conference on Learning Representations. [https://openreview.net/forum?id=qrwe7XHTmYb](https://openreview.net/forum?id=qrwe7XHTmYb)
> - **Cite Key:** @lepikhinGShardScalingGiant2020 
> - **Conclusion**:


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