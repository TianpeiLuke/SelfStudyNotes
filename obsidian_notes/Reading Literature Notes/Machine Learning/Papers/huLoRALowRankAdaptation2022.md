---
tags:
- '#paper'
aliases: "huLoRALowRankAdaptation2022"
year: 2022
name: "LoRA: Low-Rank Adaptation of Large Language Models"
authors: "Edward J. Hu, Yelong Shen, Phillip Wallis, Zeyuan Allen-Zhu, Yuanzhi Li, Shean Wang, Lu Wang, Weizhu Chen"
publication: ""
type: "conferencePaper"
DOI: ""
date of note: 
---
# Descriptions

## LoRA: Low-Rank Adaptation of Large Language Models 
> [!info] 
> - **Abstract:** An important paradigm of natural language processing consists of large-scale pre-training on general domain data and adaptation to particular tasks or domains. As we pre-train larger models, full fine-tuning, which retrains all model parameters, becomes less feasible. Using GPT-3 175B as an example -- deploying independent instances of fine-tuned models, each with 175B parameters, is prohibitively expensive. We propose Low-Rank Adaptation, or LoRA, which freezes the pre-trained model weights and injects trainable rank decomposition matrices into each layer of the Transformer architecture, greatly reducing the number of trainable parameters for downstream tasks. Compared to GPT-3 175B fine-tuned with Adam, LoRA can reduce the number of trainable parameters by a factor of 10,000 and the GPU memory requirement by a factor of 3. LoRA performs on-par or better than fine-tuning in model quality on RoBERTa, DeBERTa, GPT-2, and GPT-3, despite having fewer trainable parameters, a higher training throughput, and, unlike adapters, no additional inference latency. We also provide an empirical investigation into rank-deficiency in language model adaptation, which sheds light on the efficacy of LoRA. We release a package that facilitates the integration of LoRA with PyTorch models and provide our implementations and model checkpoints for RoBERTa, DeBERTa, and GPT-2 at https://github.com/microsoft/LoRA. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/YZ46EBS7) [local](zotero://select/library/items/YZ46EBS7) [pdf](file:////home/lukexie/Documents/Papers/storage/NRFTLTBJ/Hu%20et%20al.%20-%202022%20-%20LoRA%20Low-Rank%20Adaptation%20of%20Large%20Language%20Models.pdf) 
> - **Bibliography**: Hu, E. J., Shen, Y., Wallis, P., Allen-Zhu, Z., Li, Y., Wang, S., Wang, L., & Chen, W. (2022, April 25). LoRA: Low-Rank Adaptation of Large Language Models. _The 10th International Conference on Learning Representations (ICLR)_. International Conference on Learning Representations (ICLR 2022). [https://openreview.net/forum?id=nZeVKeeFYf9](https://openreview.net/forum?id=nZeVKeeFYf9)
> - **Cite Key:** @huLoRALowRankAdaptation2022
> - **Conclusion**:
> - **Tags:** #Large-language-model, #LoRA, #Low-Rank-Approximation


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


- [[Large Language Model and Pretrained Language Models]]
- [[vaswaniAttentionAllYou2017]]