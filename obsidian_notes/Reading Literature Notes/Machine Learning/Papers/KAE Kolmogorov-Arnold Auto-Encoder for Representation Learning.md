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

## KAE: Kolmogorov-Arnold Auto-Encoder for Representation Learning 
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
>In this paper, the author adopts the newly proposed Kolmogorov-Arnold network to the basic auto-encoder network by replacing the MLP layer with KAN. In order to improve the performance, the authors propose the polynomial kernel instead of B-spline kernel in the original KAN paper. The 2-layer KAE model is shown to outperform the shadow auto-encoder and KAN with B-spline, Fourier basis, Wavelet basis in MINST, and CIFAR datasets.  



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

>[!question] 
>Decide the *quality* of this paper.  
>- Is the derivation in this paper correct? 
>- Is the conclusion of this paper sound?
>- Do the results of experiments support the claim in this paper ?
>- Are there any other factors that lead to the result which are not described in the paper?
>- Is the result repeatable?
>- 




>[!question] 
>Decide the *clarity* of this paper.  
>- Are the authors able to present their ideas clearly? 
>- Is the structure of the paper well-organized?
>- Is the logic and math in this paper well derived?
>- Is the author using language fluently?
>- Is the graph and other visualization in this paper clear to read?

>[!info]
>This paper is clearly written with well-organized structure. The presentation is concise. The theorem in the paper demonstrated that using KAN can achieve universal function approximation. 
>
>The structure of experiment section is also good, with KAE showing good performance in similarity search, image classification, image denoising


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

>[!info]
>**originality**:
>One of the major issue of this paper is the lack of originality. The KAE model is simply replacing MLP by KAN in auto-encoder with a simple change of kernel from B-spline to polynomial. 
>
>The auto-encoder network is widely used and simple to implement while KAN is novel, it is not the contribution of this paper. It is expected that to publish in ICLR we need to either propose a novel idea that would challenge the existing belief or we should present the new system that beat the state-of-the-art.  Given that the plain auto-encoder is not the state-of-the-art in either CIFAR or MINST and the two-layer architecture is trivial, we are expecting that the authors would bring new insights from either theory or in implementation point of view to show why KAE is able to challenge MLP. Unfortunately, this paper is not achieving this goal yet. 
>
>

>[!info]
>



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