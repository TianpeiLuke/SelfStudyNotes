---
tags:
- '#paper'
aliases: "caiActiveCostawareLabeling2023"
year: 2023
name: "Active Cost-aware Labeling of Streaming Data"
authors: "Ting Cai, Kirthevasan Kandasamy"
publication: ""
type: "conferencePaper"
DOI: ""
date of note: 2025-03-26 
---
# Descriptions

## Active Cost-aware Labeling of Streaming Data 
> [!info] 
> - **Abstract:** We study actively labeling streaming data, where an active learner is faced with a stream of data points and must carefully choose which of these points to label via an expensive experiment. Such problems frequently arise in applications such as healthcare and astronomy. We first study a setting when the data’s inputs belong to one of K discrete distributions and formalize this problem via a loss that captures the labeling cost and the prediction error. When the labeling cost is B, our algorithm, which chooses to label a point if the uncertainty is larger than a time and cost dependent threshold, achieves a worst-case upper bound of 𝑂̃ (𝐵13𝐾13𝑇23)O~(B13K13T23)\tilde O(B^{\frac{1}{3}} K^{\frac{1}{3}} T^{\frac{2}{3}}) on the loss after T rounds. We also provide a more nuanced upper bound which demonstrates that the algorithm can adapt to the arrival pattern, and achieves better performance when the arrival pattern is more favorable. We complement both upper bounds with matching lower bounds. We next study this problem when the inputs belong to a continuous domain and the output of the experiment is a smooth function with bounded RKHS norm. After T rounds in d dimensions, we show that the loss is bounded by 𝑂̃ (𝐵1𝑑+3𝑇𝑑+2𝑑+3)O~(B1d+3Td+2d+3)\tilde O(B^{\frac{1}{d+3}} T^{\frac{d+2}{d+3}}) in an RKHS with a squared exponential kernel and by 𝑂̃ (𝐵12𝑑+3𝑇2𝑑+22𝑑+3)O~(B12d+3T2d+22d+3)\tilde O(B^{\frac{1}{2d+3}} T^{\frac{2d+2}{2d+3}}) in an RKHS with a Matérn kernel. Our empirical evaluation demonstrates that our method outperforms other baselines in several synthetic experiments and two real experiments in medicine and astronomy. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/WUI65I2F) [local](zotero://select/library/items/WUI65I2F) [pdf](file:////Users/lukexie/Zotero/storage/2IXT6KDD/Cai%20and%20Kandasamy%20-%202023%20-%20Active%20Cost-aware%20Labeling%20of%20Streaming%20Data.pdf) 
> - **Bibliography**: Cai, T., & Kandasamy, K. (2023). Active Cost-aware Labeling of Streaming Data. _Proceedings of The 26th International Conference on Artificial Intelligence and Statistics_, 9117–9136. [https://proceedings.mlr.press/v206/cai23a.html](https://proceedings.mlr.press/v206/cai23a.html)
> - **Cite Key:** @caiActiveCostawareLabeling2023
> - **Conclusion**:


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



## Highlight of Technical Details


>[!todo]
>Highlight the main techniques proposed in this paper. Also highlight the performance comparison to state-of-the-art.



## Questions Related to Me


> [!question] 
> Is the problem behind this paper related to problem of mine?



> [!question] 
> What impact does this paper have on me?




----

## Reference and Related Notes