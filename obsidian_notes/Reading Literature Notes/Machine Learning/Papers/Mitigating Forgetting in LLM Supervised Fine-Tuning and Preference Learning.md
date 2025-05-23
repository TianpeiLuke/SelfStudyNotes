---
tags:
  - "#paper"
aliases:
  - "{{citekey}}"
year:
  "{ date | format (\"YYYY\") }": 
name: Mitigating Forgetting in LLM Supervised Fine-Tuning and Preference Learning
authors: "{{authors}}"
publication: "{{publicationTitle}}"
type: "{{itemType}}"
DOI: "{{DOI}}"
date of note:
  "{ importDate | format(\"YYYY-MM-DD\") }":
---
# Descriptions

## Mitigating Forgetting in LLM Supervised Fine-Tuning and Preference Learning 
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
>In this paper, the authors provide a thorough analysis on the suboptimality of the traditional 2-stage process of preference learning and supervised fine-tunining for LLM training. It is shown that this sub-optimality is due to the incompatibility between the objectives in preference learning and supervised fine-tuning. The authors then proposed two algorithms (ALRIGHT, and MAXRIGHT) that treat this problem as multi-objective learning. Both of these algorithms achieve the Pareto optimal solution for multi-objective problem. Experiments show that the proposed algorithms requires little increase in runtime and GPU utilization. The proposed algorithms also achieve large improvement in both SFT and DPO objectives.


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
>The problem concerned in this paper is novel as the SFT and RLHF are industrial standard in LLM training, but not many discussion on the joint suboptimality of the entire process. This paper deepens the understanding on the mismatch between labeling logic in training data and additional labeling logic from human preference or RL agent. The proposal which treats this problem as a multi-objective learning is novel as well.



>[!question] 
>Decide the *quality* of this paper.  
>- Is the derivation in this paper correct? 
>- Is the conclusion of this paper sound?
>- Do the results of experiments support the claim in this paper ?
>- Are there any other factors that lead to the result which are not described in the paper?
>- Is the result repeatable?
>- 

>[!info]
>The proof looks correct based on my brief review. The visualization of suboptimality of sequential two-stage process in Figure 2 is interesting. The experiments which indicates that the proposed method is able to reach Pareto front of multi-objective problem is convincing.


>[!question] 
>Decide the *clarity* of this paper.  
>- Are the authors able to present their ideas clearly? 
>- Is the structure of the paper well-organized?
>- Is the logic and math in this paper well derived?
>- Is the author using language fluently?
>- Is the graph and other visualization in this paper clear to read?

>[!question] 
>Decide the *significance* of this paper.  
>- What major contribution of this paper? 
>- How this paper would help the other's research?
>- Is the idea and experiment in this paper demonstrate a new direction for the field?
>- How ?


## Weakness

>[!important]
>A substantive assessment of the **weaknesses** of the paper. 
>- Focus on *constructive and actionable insights* on how the work could improve towards its stated goals. 
>- Be *specific*, avoid generic remarks. For example, if you believe the contribution lacks novelty, provide references and an explanation as evidence; if you believe experiments are insufficient, explain why and exactly what is missing, etc.







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