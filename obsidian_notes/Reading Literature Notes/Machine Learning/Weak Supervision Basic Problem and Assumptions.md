---
tags:
  - machine_learning
  - assumption
  - programmatic_weak_supervision
  - thought
aliases: 
date of note: 2024-03-07
---

# Problem

>[!question]
>What are the common problem of concern behind this topic?

**Weak Supervision** concerns about *the lack of sufficient high quality labeled training data* for sophisticated machine learning models. 

In particular, this problem is of concern because
- Model Deep Learning models are *data-hungry*.
- *Manual labelling* cost is high both in terms of human cost and in terms of time. 
- *Label noise* exists in most of labeled training set. This is in particular severe when the labels come from *crowdsourcing*.
- The model target is *adaptive*. There is not enough samples in the source following the same target distribution.
- The increase of *adversarial attacks*. It affects the data distribution (e.g. *covariate shift*) as well as noise rate in the label. 

This problem is closely related to the problem of 
- **Semi-Supervised Learning**
- **Active Learning**
- **Transfer Learning** and **Domain Adaptation**
- **Robust Learning** and **Noise-tolerate Learning**
- **Unsupervised Learning**


# Assumption

>[!question]
>- What are the common assumptions behind this topic?

- **Traditional Weak Supervision** 
	- **Positive-Unlabeled (PU)** assumes that there exists a small subset of ***positive labeled***  samples and a vast amount of *unlabeled* samples. This is close to the **one-class classification** and **anomaly detection** as well as semi-supervised learning.
	- **Positive-confidence (Pconf)**
	- **Unlabeled-Unlabeled (UU)** learning from different populations
	- **Similar-Dissimilar (SD)** 
	- Different weak information can be systematically combined. 
  
- **Programmatic Weak Supervision** assumes that there exist simple, easy-obtained mechanisms to produce a large amount of "weak" labels that cover majority of dataset. Available labeling mechanisms include
	- Domain expertise
	- Crowdsourcing
	- Heuristics and Rules
	- Simulators (Physics, Robotics etc.)

- Weak labels are labels that are not direct identifier of the ground truth but has strong correlations with the ground truth. They are  


>[!question]
>- How do these assumptions different from related topics?

- **Semi-Supervised Learning**: assume there exists a small portion of ***high quality labeled (both positive and negative)*** samples with a large amount of *unlabeled* sample. 
  
- **Active Learning**: assume there exist mechanisms that can provide ground-truth label for given query and a budget for how many times we can run the query. 
  
- **Transfer Learning**: assume that the ***unlabeled*** *target (joint) distribution* and the ***labeled*** *source (joint) distribution* are different and there exist correlations among them. ^[1]  In general, there is no common assumption on the label sample size on each population. 

- **Unsupervised Learning**: assume no labeled samples are available. Can only learn the intrinsic structure of the distribution $p(x)$ or the structure of dataset such as graph to learn patterns.  



[^1]: For instance, in *covariate shift*, the assumption is that the conditional distribution $p(y|x)$ is unchanged. 

-----------
##  Recommended Notes

- Check on the survey of **Progammatic Weak Supervision** to understand the common assumptions and common problems  [[zhangSurveyProgrammaticWeak2022]]
- 