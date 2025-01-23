---
tags:
- '#paper'
aliases: "rafailovDirectPreferenceOptimization2023"
year: 2023
name: "Direct Preference Optimization: Your Language Model is Secretly a Reward Model"
authors: "Rafael Rafailov, Archit Sharma, Eric Mitchell, Christopher D. Manning, Stefano Ermon, Chelsea Finn"
publication: ""
type: "conferencePaper"
DOI: ""
date of note: 2025-01-19 
---
# Descriptions

## Direct Preference Optimization: Your Language Model is Secretly a Reward Model 
> [!info] 
> - **Abstract:** While large-scale unsupervised language models (LMs) learn broad world knowledge and some reasoning skills, achieving precise control of their behavior is difficult due to the completely unsupervised nature of their training. Existing methods for gaining such steerability collect human labels of the relative quality of model generations and fine-tune the unsupervised LM to align with these preferences, often with reinforcement learning from human feedback (RLHF). However, RLHF is a complex and often unstable procedure, first fitting a reward model that reflects the human preferences, and then fine-tuning the large unsupervised LM using reinforcement learning to maximize this estimated reward without drifting too far from the original model. In this paper, we leverage a mapping between reward functions and optimal policies to show that this constrained reward maximization problem can be optimized exactly with a single stage of policy training, essentially solving a classification problem on the human preference data. The resulting algorithm, which we call Direct Preference Optimization (DPO), is stable, performant, and computationally lightweight, eliminating the need for fitting a reward model, sampling from the LM during fine-tuning, or performing significant hyperparameter tuning. Our experiments show that DPO can fine-tune LMs to align with human preferences as well as or better than existing methods. Notably, fine-tuning with DPO exceeds RLHF's ability to control sentiment of generations and improves response quality in summarization and single-turn dialogue while being substantially simpler to implement and train. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/K2L39WXQ) [local](zotero://select/library/items/K2L39WXQ) [pdf](file:////home/lukexie/Documents/Papers/storage/VYC84AQ3/Rafailov%20et%20al.%20-%202023%20-%20Direct%20Preference%20Optimization%20Your%20Language%20Mode.pdf)  [pdf](file:////home/lukexie/Documents/Papers/storage/K23L8NIE/NeurIPS-2023-direct-preference-optimization-your-language-model-is-secretly-a-reward-model-Supplemental-Conference.pdf) 
> - **Bibliography**: Rafailov, R., Sharma, A., Mitchell, E., Manning, C. D., Ermon, S., & Finn, C. (2023). Direct Preference Optimization: Your Language Model is Secretly a Reward Model. _Advances in Neural Information Processing Systems_, _36_, 53728–53741. [https://proceedings.neurips.cc/paper_files/paper/2023/hash/a85b405ed65c6477a4fe8302b5e06ce7-Abstract-Conference.html](https://proceedings.neurips.cc/paper_files/paper/2023/hash/a85b405ed65c6477a4fe8302b5e06ce7-Abstract-Conference.html)
> - **Cite Key:** @rafailovDirectPreferenceOptimization2023 
> - **Conclusion**:
> - **Tags:** #Direct-Preference-Optimization, #DPO, #Fine-tuning-LLM


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