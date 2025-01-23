---
tags:
- '#paper'
aliases: "shazeerOutrageouslyLargeNeural2017"
year: 2017
name: "Outrageously Large Neural Networks: The Sparsely-Gated Mixture-of-Experts Layer"
authors: "Noam Shazeer, *Azalia Mirhoseini, *Krzysztof Maziarz, Andy Davis, Quoc Le, Geoffrey Hinton, Jeff Dean"
publication: ""
type: "conferencePaper"
DOI: ""
date of note: 2025-01-03 
---
# Descriptions

## Outrageously Large Neural Networks: The Sparsely-Gated Mixture-of-Experts Layer 
> [!info] 
> - **Abstract:** The capacity of a neural network to absorb information is limited by its number of parameters. Conditional computation, where parts of the network are active on a per-example basis, has been proposed in theory as a way of dramatically increasing model capacity without a proportional increase in computation. In practice, however, there are significant algorithmic and performance challenges. In this work, we address these challenges and finally realize the promise of conditional computation, achieving greater than 1000x improvements in model capacity with only minor losses in computational efficiency on modern GPU clusters. We introduce a Sparsely-Gated Mixture-of-Experts layer (MoE), consisting of up to thousands of feed-forward sub-networks. A trainable gating network determines a sparse combination of these experts to use for each example. We apply the MoE to the tasks of language modeling and machine translation, where model capacity is critical for absorbing the vast quantities of knowledge available in the training corpora. We present model architectures in which a MoE with up to 137 billion parameters is applied convolutionally between stacked LSTM layers. On large language modeling and machine translation benchmarks, these models achieve significantly better results than state-of-the-art at lower computational cost. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/ZQFTJBEZ) [local](zotero://select/library/items/ZQFTJBEZ) [pdf](file:////home/lukexie/Documents/Papers/storage/YLTZHE5I/Shazeer%20et%20al.%20-%202016%20-%20Outrageously%20Large%20Neural%20Networks%20The%20Sparsely-G.pdf) 
> - **Bibliography**: Shazeer, N., Mirhoseini, Azalia, Maziarz, Krzysztof, Davis, A., Le, Q., Hinton, G., & Dean, J. (2017, April 24). Outrageously Large Neural Networks: The Sparsely-Gated Mixture-of-Experts Layer. _5th International Conference on Learning Representations_. International Conference on Learning Representations (ICLR 2017), Palais des Congrès Neptune, Toulon, France. [https://openreview.net/forum?id=B1ckMDqlg](https://openreview.net/forum?id=B1ckMDqlg)
> - **Cite Key:** @shazeerOutrageouslyLargeNeural2017 
> - **Conclusion**:
> - **Tags:** #MoE, #Sparsely-Gated-Mixture-of-Experts-layer


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

- [[fedusSwitchTransformersScaling2022]]
- [[lepikhinGShardScalingGiant2020]]